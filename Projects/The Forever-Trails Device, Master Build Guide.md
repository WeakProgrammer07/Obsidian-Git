# The "Forever-Trails" Device: Master Build Guide (No-Solder Edition)

**Goal:** To build an ultra-low-power, pocket-sized backcountry GPS device that runs on solar power indefinitely. It uses a tile-based map rendering system on an E-Ink display, entirely bypassing heavy Android OS requirements. **This version requires zero soldering.**

## 1. Bill of Materials (BOM) - Plug & Play

To avoid soldering, we rely on boards that integrate multiple components and use standardized plugs (FPC ribbons, JST connectors, and Dupont headers).

|                       |                                              |                                                                                                                                                                         |
| --------------------- | -------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Component**         | **Part / Model**                             | **Rationale**                                                                                                                                                           |
| **The "Brain" Board** | **Waveshare e-Paper ESP32 Driver Board**     | **The Magic Bullet:** This single board contains the ESP32, a MicroSD card slot, and a ribbon cable clamp for the E-Ink screen. No wiring needed for the hardest parts! |
| **Display**           | **Waveshare 3.7" E-Paper (Raw Panel)**       | Buy the _raw panel_ (just the glass and ribbon cable), not the one with the HAT attached. The ribbon plugs directly into the Brain Board.                               |
| **GPS Module**        | **u-blox MAX-M10S (with header pins)**       | Ensure you buy a version with pins pre-soldered. You will connect this using Female-to-Female Dupont jumper wires.                                                      |
| **Storage**           | **MicroSD Card**                             | Plugs directly into the Waveshare Driver Board.                                                                                                                         |
| **Battery**           | **3.7V 2000mAh LiPo (with JST PH 2.0 plug)** | Must have a pre-crimped JST connector so it can plug directly into the solar charger board.                                                                             |
| **Solar Charger**     | **DFRobot Sunflower (Solar Lipo Charger)**   | Has plug-in JST ports for the battery and screw-terminals for the solar panel. Zero soldering required.                                                                 |
| **Solar Panel**       | **5V / 1W Monocrystalline**                  | Buy one with exposed wire leads to screw into the DFRobot terminal block.                                                                                               |

## 2. Hardware Assembly (The "Lego" Method)

Because you aren't soldering, assembly is essentially just plugging things into the right slots and using a tiny screwdriver.

### Step A: The Core Stack (Screen + Brain + Storage)

1. **The Screen:** Gently lift the tiny black latch on the FPC connector on the Waveshare ESP32 board. Slide the E-Ink screen's ribbon cable in, and snap the latch down.
    
2. **The SD Card:** Push your loaded MicroSD card into the slot on the board. _(Boom. You just completed 80% of the SPI wiring without touching a soldering iron.)_
    

### Step B: The GPS Connection (Dupont Wires)

Use standard Female-to-Female Dupont jumper wires.

1. Connect **GPS TX** to **ESP32 GPIO 16** (or any available RX pin on the Waveshare headers).
    
2. Connect **GPS RX** to **ESP32 GPIO 17** (or any available TX pin).
    
3. Connect **GPS VCC** to the **3.3V** pin on the Waveshare board.
    
4. Connect **GPS GND** to the **GND** pin.
    

> **Trail-Proofing Tip:** Once the Dupont wires are pushed onto the pins, put a generous dab of **hot glue** over the connections. This locks the plastic connectors together so they will never vibrate loose while you are hiking.

### Step C: The Power System

1. Use a small screwdriver to clamp the bare red and black wires of your **Solar Panel** into the **"SOLAR IN" screw terminal** on the DFRobot Sunflower board.
    
2. Plug the **LiPo Battery's JST connector** directly into the **"BAT IN" JST port** on the Sunflower board.
    
3. Use two female jumper wires to connect the **"VOUT" pins** on the Sunflower board to the **5V and GND pins** on the Waveshare ESP32 board. (Hot glue these in place as well).
    

## 3. The Power Budget & Solar Math

How does it last forever? By spending 95% of its life mathematically "dead."

1. **Deep Sleep State:** ESP32 (~10µA) + Screen (0µA) = **0.01mA draw.**
    
2. **Active State:** ESP32 (80mA) + GPS (15mA) + Screen Refresh (15mA) = **110mA draw.**
    

If the device wakes up every 60 seconds, takes 3 seconds to get a GPS fix/update the screen, and goes back to sleep, your **Average Current Draw is ~5.5mA**.

- A 2000mAh battery alone will run this for **~15 days of continuous hiking** (360 hours).
    
- A **1W solar panel** generates ~150mA in direct sunlight. Just **1 hour of direct sun per day** covers 24 hours of device operation, making the battery life theoretically infinite.
    

## 4. The Data Pipeline (PC Side)

The ESP32 does not have the power to decode JPEGs or render vector graphics efficiently. To handle the map and the **trail path**, you must pre-render them together into **4-bit Grayscale BMPs** on your computer before copying them to the SD card.

### The Conversion Script (Python 3)

Run this logic on your PC. It will take your downloaded map tiles, overlay the GPX trail onto them, and convert them to an E-Ink friendly format:

```
from PIL import Image, ImageDraw
import os
import gpxpy # requires: pip install gpxpy

def bake_trail_and_convert(input_dir, output_dir, gpx_file):
    # 1. Load GPX Data
    with open(gpx_file, 'r') as gpx_file:
        gpx = gpxpy.parse(gpx_file)
        
    for filename in os.listdir(input_dir):
        if filename.endswith(".png") or filename.endswith(".jpg"):
            img = Image.open(os.path.join(input_dir, filename))
            
            # 2. Draw the GPX Trail onto the map tile
            draw = ImageDraw.Draw(img)
            # (Note: Requires mapping GPX lat/lon coordinates to pixel X/Y for this specific tile bounding box)
            # draw.line(mapped_pixel_coordinates, fill="black", width=4)
            
            # 3. Resize to E-Ink resolution (480x280) if not already tiled
            img = img.resize((480, 280))
            
            # 4. Convert to Grayscale
            img = img.convert('L')
            
            # 5. Quantize to 4-colors (2-bit/4-bit depending on library)
            # This matches the Waveshare's 4-grayscale capability
            img = img.quantize(colors=4)
            
            # 6. Save as uncompressed BMP for zero-overhead reading on ESP32
            output_filename = filename.split('.')[0] + ".bmp"
            img.save(os.path.join(output_dir, output_filename), format='BMP')

print("Baking trail lines and converting map tiles for ESP32...")
```

_Note: Because the trail is "baked" into the image, the ESP32 doesn't use any battery calculating the path!_

## 5. The Device Software (MicroPython)

The code on the ESP32 operates on a strict **Interrupt & Sleep** loop. Because the trail is already drawn on the background image, the ESP32 only needs to worry about your live location.

### Core Logic Loop:

1. **Wake up** (Triggered by internal timer).
    
2. **Power up GPS** (Read NMEA `$GPRMC` sentence over UART pins 16/17).
    
3. **Wait for Fix** (Usually 1-3 seconds if outside).
    
4. **Calculate Map Tile:** Convert Lat/Lon to Tile X/Y coordinates using standard Web Mercator math.
    
5. **Read SD Card:** Locate `/sd/maps/zoom15/x/y.bmp`.
    
6. **Frame Buffer Composition (In PSRAM):**
    
    - Load the BMP into a MicroPython `framebuf`.
        
    - Calculate pixel X/Y offset for your current live GPS coordinate.
        
    - Draw a 5-pixel circle (the "You are Here" dot).
        
7. **Partial Refresh:** Send only the changed frame buffer to the E-Ink via the pre-wired ribbon cable.
    
8. **Deep Sleep:** `machine.deepsleep(60000)` (Sleep for 1 minute).
    

## 6. Mechanical Design (The Thicker "Plug & Play" Enclosure)

Because we are using pre-crimped plastic Dupont headers instead of flat soldered wires, the device will be roughly **18mm to 20mm thick** instead of 12mm. Print the chassis using **ASA filament** for UV and heat resistance.

### The "Modular" Architecture

Design your 3D-printed case in two halves (like a clamshell):

1. **The Front Shell (Display & Brain):**
    
    - Create a bezel for the Waveshare E-Ink display.
        
    - Directly beneath the display, design standoffs to screw down the Waveshare ESP32 Driver Board.
        
2. **The Back Shell (Power & GPS):**
    
    - **Crucial:** Design a pocket for the u-blox M10 GPS antenna at the very top of the device so it faces the sky. _Do not stack the battery under the GPS ceramic antenna._
        
    - Screw the DFRobot Solar board onto standoffs in the lower half.
        
    - Leave a cutout in the rear wall of the shell so the 1W Solar Panel sits flush with the outside plastic.
        
    - Tuck the LiPo battery between the boards.
        
3. **Closing it up:**
    
    - When closing the clamshell, ensure the Dupont wires and JST cables fold neatly into the empty space.
        
    - Use a bead of silicone sealant along the seam before screwing the two halves together to make it highly water-resistant.