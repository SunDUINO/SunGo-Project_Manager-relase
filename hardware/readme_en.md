[BUILD] SunGo MacroPAD — Build Your Own 3x3 Macro Pad with RGB

Below is a complete guide for those who want to build their own MacroPAD. The firmware is in a stable version and works perfectly with the dedicated VSCode extension — you can jump right in.

🛒 Shopping List

Switches: 9x mechanical keyboard switches (e.g., Cherry MX Blue or any popular clone).

Backlight: 9x WS2812B addressable LEDs (individual units cut from an LED strip can be used).

Microcontroller: An RP2040 based board (recommended: Pimoroni PGA2040, Waveshare RP2040 Zero, or any compatible board).

Wiring: Thin wires, or a piece of Ethernet cable (solid core wire is excellent for connecting the matrix).

Enclosure: 3D printed. This project uses: SunGo MacroPAD on MakerWorld.

🔧 Switch Wiring

The switches are wired in a 3x3 matrix using Direct mode with a common ground (GND).

Layout Schema:







SW1

SW2

SW3

SW4

SW5

SW6

SW7

SW8

SW9

GPIO Pin Mapping:

Switch

GPIO Pin

Switch

GPIO Pin

Switch

GPIO Pin

SW1

GPIO2

SW2

GPIO3

SW3

GPIO4

SW4

GPIO7

SW5

GPIO6

SW6

GPIO5

SW7

GPIO8

SW8

GPIO9

SW9

GPIO10

🌈 WS2812B (RGB) Connection

The LEDs are connected in a series "snake" configuration. This means the signal zig-zags under the switches, which simplifies wiring and optimizes the signal path.

LED Connection Schema:

LED0 (SW1) ──► LED1 (SW2) ──► LED2 (SW3)
                                 │
LED5 (SW4) ◄── LED4 (SW5) ◄── LED3 (SW6)
  │
LED6 (SW7) ──► LED7 (SW8) ──► LED8 (SW9)


Data Pin (DIN): Connected to GPIO16.

Power Supply: LEDs can be powered by either 3.3V or 5V.

Power Management: Firmware brightness is limited to 40%. This ensures great visibility while keeping power consumption safe for USB 2.0 and newer standards.

[!IMPORTANT]
NOTE: During assembly, pay close attention to the orientation of the LEDs. The arrows on the WS2812B housing indicate the data flow direction (Data Out).

💾 Software & Configuration

Firmware Installation

Prepare the firmware file in .uf2 format.

Connect the RP2040 board to your computer while holding the BOOTSEL button.

The device will be detected as a removable drive.

Drag and drop the .uf2 file onto this drive. After a successful flash, the MacroPAD will reboot and be ready to use.

Keycaps

If you are using a Bambu Lab printer with the AMS system (e.g., Model A1), you can find dedicated keycap designs in the attachments to give your project a professional finish.

Project SunGo MacroPAD — 2026
