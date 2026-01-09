# zx-spectrum-tape-self-portrait
zx spectrum tape self portrait

# JV's TZX Master: The Tape Self-Portrait Project

> **"A pixel-perfect selfie built by POKE-ing raw data directly into the Spectrum’s heart, one byte of SCREEN$ memory at a time."**

## Overview
This project represents a complete "Modern-to-Retro" production pipeline. It allows for the creation of high-fidelity Attribute Art for the ZX Spectrum (1982) using modern web technologies, then bridging that data back into physical magnetic tape.

By bypassing standard drawing commands and manipulating the Spectrum's VRAM directly via POKE statements, this workflow achieves a "low-level" digital painting style that respects the specific hardware constraints and quirks of the original Sinclair machine.

---

## The Workflow
The process moves from high-level design to low-level memory injection, culminating in an analog archive.

### Deployment Sequence
[PLACEHOLDER: UML SEQUENCE DIAGRAM SHOWING PC TO SPECTRUM FLOW]

---

## Component Breakdown

### 1. The Production Suite (index.html)
A bespoke web-based graphics editor that acts as a translation engine.
* **The Stage:** A 256x192 canvas locked to the Spectrum's native resolution.
* **Trace Mode:** Allows for a modern photo to be used as a "ghost" layer for precision pixel-tracing.
* **Import Engine:** A reverse-engineering tool that scans Sinclair BASIC POKE strings and reconstructs the image visually.
* **Tape Mastering:** Integrated logic to generate .TAP and .TZX files, including the generation of checksums and proper header timings for real hardware compatibility.

### 2. The Source Code (self-portrait.bas)
The raw Sinclair BASIC output. This file contains the brute-force POKE commands required to rebuild the Attribute (color) map of the portrait.
* **Memory Range:** 22528 to 23295 (The Attribute Zone).
* **Format:** Plain text Sinclair BASIC.

[PLACEHOLDER: SINCLAIR BASIC SOURCE CODE]

---

## Technical Specifications
* **Target Hardware:** ZX Spectrum 48k / 128k
* **VRAM Start:** Address 16384 (Pixels)
* **Attribute Start:** Address 22528 (Colors)
* **Resolution:** 256 x 192 pixels
* **Color Grid:** 32 x 24 (8x8 pixel attribute blocks)

## How to Run
1. **In an Emulator:** Load the produced virtual tape file directly.
2. **On Real Hardware:** * Connect your PC or mobile device's headphone jack to the Spectrum's EAR port.
   * Play the tape file via an audio gateway or playback tool.
   * Enter the command `LOAD "" SCREEN$` on the Spectrum and initiate playback on your modern device.
   * Once the image is loaded into memory, connect the MIC port to a cassette recorder to archive the data to physical magnetic tape.

---
*Created by JV - Bridging the gap between 1982 and today.*

<img width="1108" height="891" alt="image" src="https://github.com/user-attachments/assets/826c0488-16b5-4295-946f-35bcb8587502" />

