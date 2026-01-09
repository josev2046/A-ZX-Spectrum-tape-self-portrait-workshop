# A ZX Spectrum tape self-portrait workshop

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.18202890.svg)](https://doi.org/10.5281/zenodo.18202890)

> **"A pixel-perfect selfie built by POKE-ing raw data directly into the Spectrum’s heart, one byte of SCREEN$ memory at a time."**

## Overview

Within the framework of "obsolescence and media fragmentation," this practical workshop moves from theory to physical interaction with legacy hardware. The Sinclair ZX Spectrum (1982) serves as a primary case study for understanding the fragility of magnetic storage and the complexities of preserving software as cultural heritage. Students will engage with the challenges of recovering data from a format that is physically degrading and technically orphaned (Velazquez, 2026).

This project allows for the creation of high-fidelity Attribute Art for the ZX Spectrum (1982) using modern web technologies, then bridging that data back into physical magnetic tape. By bypassing standard drawing commands and manipulating the Spectrum's VRAM directly via POKE statements, this workflow achieves a "low-level" digital painting style that respects the specific hardware constraints and quirks of the original Sinclair machine.

https://github.com/user-attachments/assets/270ceb32-235f-462b-b035-217261994a88

---

## Workflow
The process moves from high-level design to low-level memory injection, culminating in an analog archive.

### Deployment sequence
<img width="1108" height="891" alt="image" src="https://github.com/user-attachments/assets/826c0488-16b5-4295-946f-35bcb8587502" />

---

## Component breakdown

### Production 
A bespoke web-based graphics editor that acts as a translation engine.
* **Canvas:** A 256x192 canvas locked to the Spectrum's native resolution.
* **Trace modd:** Allows for a modern photo to be used as a "ghost" layer for precision pixel-tracing.
* **Import engine:** A reverse-engineering tool that scans Sinclair BASIC POKE strings and reconstructs the image visually.
* **Tape mastering:** Integrated logic to generate `.TAP` and `.TZX` files, including the generation of checksums and proper header timings for real hardware compatibility.

### Sample source code (self-portrait.bas)
The raw Sinclair BASIC output. This file contains the brute-force POKE commands required to rebuild the Attribute (colour) map of the portrait.
* **Memory range:** 22528 to 23295 (The Attribute Zone).
* **Format:** Plain text Sinclair BASIC.

---

## The mechanics: binary & SCREEN$

To understand this workshop, one must understand how the Spectrum "sees" an image:

* **The binary map:** Every image is a 6,912-byte binary blob. The first 6,144 bytes define the pixels (on/off), and the final 768 bytes define the "Attributes" (colors). In this workshop, we treat the screen as raw data rather than a visual coordinate system.
* **The SCREEN$ command:** This is a powerful Sinclair BASIC keyword that acts as a shortcut for the memory range `CODE 16384, 6912`. When we use `SAVE "name" SCREEN$`, we are telling the computer to take an exact binary snapshot of the video RAM and stream it out as audio pulses to the tape.
* **Linearity vs. Reality:** While we draw in a linear fashion, the binary data is stored in a **non-linear** format to suit the hardware of 1982. The tool handles this translation automatically, ensuring the binary "shuffles" into the correct positions on the physical CRT.

---

## Technical specifications
* **Target hardware:** ZX Spectrum 48k / 128k
* **Binary size:** 6,912 Bytes (6.75 KB)
* **VRAM start:** Address 16384 (Pixels)
* **Attribute start:** Address 22528 (Colors)
* **Resolution:** 256 x 192 pixels
* **Color grid:** 32 x 24 (8x8 pixel attribute blocks)

---

## How to run

### 1. In an emulator
Load the produced virtual tape file (`.TAP` or `.TZX`) directly using the emulator's "Open" or "Smart Load" feature.

### 2. On real hardware

**Phase A: Digital Injection (Loading)**
1.  Connect your PC or mobile device's headphone jack to the Spectrum's **EAR** port.
    > **⚠️ Note:** Modern devices output Stereo signals, but the Spectrum requires **Mono**. Ensure your audio cable is mono-compatible, or force your device audio to Mono. If using a smartphone, ensure volume is at 85-90% and "EQ/Sound Enhancements" are disabled.
2.  Enter the command `LOAD ""` on the Spectrum.
3.  Initiate audio playback of the `.TAP` file on your modern device.
4.  The Spectrum will load the BASIC program. If it does not auto-run, type `RUN` to execute the POKE commands and watch the image build itself.

**Phase B: Analog Archive (Saving)**
Once the image is successfully rendered in the Spectrum's memory:
1.  Disconnect the cable from the device and connect the Spectrum's **MIC** port to a physical cassette recorder's **MIC/INPUT** jack.
2.  Place a blank physical cassette into the recorder and press **RECORD**.
3.  Enter `SAVE "selfie" SCREEN$` on the Spectrum.

### 3. Verification
The physical tape is now a permanent analog master. It can be used and loaded exactly like a commercial game on any real Sinclair ZX Spectrum. Because we saved it using the `SCREEN$` command, you can now load it back instantly using the shortcut:

```basic
LOAD "" SCREEN$
