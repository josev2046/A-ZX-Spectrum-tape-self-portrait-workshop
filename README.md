# A ZX Spectrum tape self-portrait workshop

> **"A pixel-perfect selfie built by POKE-ing raw data directly into the Spectrum’s heart, one byte of SCREEN$ memory at a time."**

## Overview

Within the framework of "obsolescence and media fragmentation," this practical workshop moves from theory to physical interaction with legacy hardware. The Sinclair ZX Spectrum (1982) serves as a primary case study for understanding the fragility of magnetic storage and the complexities of preserving software as cultural heritage. Students will engage with the challenges of recovering data from a format that is physically degrading and technically orphaned (Velazquez, 2026).

This project allows for the creation of high-fidelity Attribute Art for the ZX Spectrum (1982) using modern web technologies, then bridging that data back into physical magnetic tape. By bypassing standard drawing commands and manipulating the Spectrum's VRAM directly via POKE statements, this workflow achieves a "low-level" digital painting style that respects the specific hardware constraints and quirks of the original Sinclair machine.

---

## Workflow
The process moves from high-level design to low-level memory injection, culminating in an analog archive.

### Deployment sequence
<img width="1108" height="891" alt="image" src="https://github.com/user-attachments/assets/826c0488-16b5-4295-946f-35bcb8587502" />

---

## Component breakdown

### Production 
A bespoke web-based graphics editor that acts as a translation engine.
* **The Stage:** A 256x192 canvas locked to the Spectrum's native resolution.
* **Trace Mode:** Allows for a modern photo to be used as a "ghost" layer for precision pixel-tracing.
* **Import Engine:** A reverse-engineering tool that scans Sinclair BASIC POKE strings and reconstructs the image visually.
* **Tape Mastering:** Integrated logic to generate .TAP and .TZX files, including the generation of checksums and proper header timings for real hardware compatibility.

### Sample source code (self-portrait.bas)
The raw Sinclair BASIC output. This file contains the brute-force POKE commands required to rebuild the Attribute (color) map of the portrait.
* **Memory Range:** 22528 to 23295 (The Attribute Zone).
* **Format:** Plain text Sinclair BASIC.

---

## Technical specifications
* **Target Hardware:** ZX Spectrum 48k / 128k
* **VRAM Start:** Address 16384 (Pixels)
* **Attribute Start:** Address 22528 (Colors)
* **Resolution:** 256 x 192 pixels
* **Color Grid:** 32 x 24 (8x8 pixel attribute blocks)

## How to Run
1. **In an Emulator:** Load the produced virtual tape file (.TAP or .TZX) directly using the emulator's "Open" or "Smart Load" feature.
2. **On Real Hardware:** * Connect your PC or mobile device's headphone jack to the Spectrum's **EAR** port.
   * Play the tape file via an audio gateway or playback tool (ensuring volume is set to roughly 80-90%).
   * Enter the command `LOAD "" SCREEN$` on the Spectrum and initiate audio playback on your modern device.
   * Once the image is successfully loaded into the Spectrum's memory, disconnect the cable from the device and connect the Spectrum's **MIC** port to a cassette recorder's input.
   * Place a physical cassette into the recorder, press **RECORD**, and enter `SAVE "selfie" SCREEN$` on the Spectrum.
3. **Note:** The physical tape is now a permanent analog copy. It can be used and loaded exactly like a commercial game on any real Sinclair ZX Spectrum by simply using the standard `LOAD ""` command.

---




