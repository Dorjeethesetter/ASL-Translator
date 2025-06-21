# ASL-Translator
Please note, for efficency, this document was partially written with the assistance of Artifical Intelligence
Project Purpose

The PCB was created as part of a personal hardware project intended to interface physical inputs with sensor data for potential gesture or motion-based control systems.

Design Process and Struggles

1. Understanding ESP32 GND Pads

Confusion around the multiple GND pins in the center of the ESP32 module.

Initially didn’t understand their role as thermal pads and grounding vias.

Modified hole sizes manually, unsure if this would affect performance (resolved by looking into datasheet recommendations).

*2. Copper Zone Misconception*

Thought a copper fill zone meant I didn’t need to connect GND pins manually.

Didn’t initially add vias or ensure copper fill was making electrical contact with GND net.

Learned that a copper fill must be explicitly tied to a net and that zones do not auto-connect across layers without vias.

3. DRC Errors & Ghost Arrows

Faced a range of DRC (Design Rule Checker) errors related to:

Missing GND connections

Incorrect net associations

Solved these by refilling zones, deleting obsolete DRC markers, and ensuring all pads had proper net connections.

4. Component Placement & Trace Routing

Initially cluttered layout with many traces manually connecting GND.

After copper fill was added, realized many GND traces could be removed.

Learned about via stitching and ground plane efficiency.

5. Keep-Out Zones

Accidentally placed a copper fill in a signal keep-out zone for the ESP32.

Resolved after learning about RF considerations for wireless modules.

Key Design Decisions

Copper Fill on Bottom Layer:

Used to simplify GND connections

Routed signal traces on top, avoiding GND trace clutter

Horizontal Button Layout:

Allows for ergonomic physical testing

All connected to resistors tied to ground

Compact Module Arrangement:

ESP32 and MPU-6050 placed on opposite sides

Reduced trace length for SDA/SCL (I2C)

3.3V Power Flag:

Used to prevent ERC (electrical rule check) warnings

Minimal Vias Used:

Kept design as close to single-layer as possible for simplicity and low cost

What I Learned

How copper zones work and how to tie them to a net

Importance of design rule checking in PCB validation

Basics of ESP32 module layout constraints

How to use PWR_FLAGs to inform KiCad of external power

Realized that GND nets require intentional connections, not just visual proximity
