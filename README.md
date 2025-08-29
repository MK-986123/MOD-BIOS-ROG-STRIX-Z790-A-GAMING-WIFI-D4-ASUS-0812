# ASUS Z790-A Gaming D4 (Modded BIOS) Flashback Guide

This guide explains how to safely flash a modded BIOS using the built-in USB Flashback feature on your ASUS Z790-A Gaming D4 motherboard.  
Follow these steps exactly. Improper handling during a flash can render your board unbootable.

---

## Important Notes & Warnings

- **Verify the file yourself**: Always download the BIOS file and scan it independently. The modded ROM linked here has been scanned, but you should get into the habit of verifying files yourself.  
  VirusTotal link for reference:  
  https://www.virustotal.com/gui/file/ac0ae61b23c0ac6007c2981a12cc824f66b08e21d51308015d425c69881852c5

- **Clear CMOS first**: Ensure your system is on optimized defaults. This prevents conflicts with prior settings. Use the rear CMOS reset button (just above the Flashback button) if necessary.

- **Do not interrupt power**: Loss of power during flashing will corrupt the BIOS. If this happens, recovery may require an external programmer (CH341A). Do not attempt this procedure during storms or unstable power conditions.

- **No restoring old profiles**: Saved BIOS profiles from earlier versions can cause instability. Reconfigure settings manually after flashing.

---

## Preparation

1. **USB drive setup**  
   - Use a small USB stick (≤ 32 GB recommended).  
   - Format it as **FAT32**, single partition only (no hidden EFI partitions).  
   - Copy both files into the root directory:  
     - `SZ790AD4.CAP`  
     - `ASUS.CAP`  
     (They are identical; some boards require one name, others the other.)

2. **System state**  
   - Shut down the PC completely.  
   - Leave the PSU switch **ON** so the board receives standby power.  
   - The system must remain OFF (not in sleep, not rebooting).

---

## Flashing Procedure

1. Insert the USB stick into the dedicated **BIOS Flashback port** (clearly labeled, usually below the Flashback button on the rear I/O).  

2. Press and hold the **BIOS Flashback button** for ~3 seconds.  
   - The Flashback LED will begin blinking.  
   - This indicates the update process has started.

3. Wait patiently.  
   - Typical duration: **1–8 minutes**.  
   - Do not press any keys, power off, or remove the USB stick.

4. Completion is indicated when:  
   - The Flashback LED stops blinking, OR  
   - The board powers itself on automatically.  

---

## After Flashing

1. If the board powers on, press the **CMOS reset button** once more for a clean start.  
2. Enter the BIOS by pressing **DEL** during boot.  
3. Press **F7** to switch to Advanced Mode.  
4. Re-apply your preferred settings manually.  
   - Do not restore old profiles.  
   - Keep a backup of your new stable config once tested.

---

## Recovery (if needed)

- If the system fails to boot after flashing:  
  - Clear CMOS using the rear button.  
  - Retry with the correctly named `.CAP` file.  
- If the BIOS is corrupted:  
  - Use an external programmer (CH341A) to reflash the chip directly. Tutorials are widely available online.

---

## Disclaimer

This BIOS has been tested for stability under normal operation. However, flashing modified firmware always carries risk. Proceed only if you are comfortable with recovery methods.  
You assume full responsibility for your hardware.

---
