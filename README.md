This is a straightforward process, but it is important to understand that you are working with **low-level firmware**.[/color]  
Improper flashing always carries risk.[/color]  


* The ASUS ROG STRIX Z790 series supports **USB BIOS FlashBack**, giving you a reliable recovery path.  
* Keep a second USB stick with the **official firmware (same version)** ready so you can quickly revert if needed.  
* This modded BIOS unlocks many hidden settings — some are experimental and can destabilize your system.  
* Change only what you understand, and document any adjustments you make.  

---

## Scope of Modification
- **Source:** Official ASUS UEFI package for the Z790-A GAMING WIFI D4 (DDR4).  
- **Change:** Advanced setup menus unlocked; AI Tweaker expanded; voltage sections and BCLK tuning exposed.  
- **Stability focus:** Hazardous options (PCIe base clocks, debug voltages, experimental menus known to freeze UEFI or break boot selection) remain hidden.  
- **Unlocked & functional:**  
  - CFG Lock  
  - BIOS Lock  
  - Overclock Lock  
  - Additional OC & debug options (research before enabling)  

---

## Board / Version
- **Motherboard:** ASUS ROG STRIX Z790-A GAMING WIFI D4  
- **Current Mod:** Version 3001 (unlocked advanced menus)  

---

## Flashing Instructions (USB BIOS FlashBack)
1. **Prepare the USB Drive**  
   - Format as **FAT32** (MBR partition table).  
   - Copy the BIOS file to the root of the USB drive:  
     `SZ790AD4.CAP`  

2. **Power State**  
   - Shut the system down completely.  
   - Leave the PSU switch set to **ON** so the board has standby power.  

3. **Start FlashBack**  
   - Insert the USB into the dedicated **BIOS FLASHBACK** port (rear I/O, labeled).  
   - Press and hold the **FLASHBACK button** for ~3 seconds until the LED blinks three times.  

4. **Wait for Completion**  
   - Flashing typically takes 1–8 minutes.  
   - Do **not** unplug power, remove the USB, or press any buttons.  
   - Completion is indicated when the FlashBack LED turns off.  

5. **First Boot**  
   - Power on and press **DEL** or **F2** to enter BIOS.  
   - Confirm version reads **3001** on the Main page.  
   - Press **F7** for Advanced Mode and reapply settings manually.  
   - Do not restore saved profiles from older BIOS versions.  

---

## Recovery & Warnings
- **FlashBack is your primary safety net.** If something goes wrong, re-run with a clean official BIOS of the same version on another USB stick.  
- Avoid flashing during storms or unstable power.  
- If FlashBack cannot recover the board, a hardware programmer (**CH341A + SOIC clip**) can reflash the BIOS chip. Tutorials are available on this forum.  

---

## Downloads (Version 3001)
- **Google Drive (7z):**  
  [ASUS-Z790-MOD-SZ790AD4-v.3001.7z](https://drive.google.com/file/d/1J9ouznNMKamQJ349FlTuUjKXuglQTLcT/view?usp=sharing)  
  SHA-256: `5e2580c6a9b0134870eed1c482c1dbd2dda95fa6797122d0519afe3222884277`  

- **Google Drive (ZIP):**  
  [ASUS-Z790-MOD-SZ790AD4-v.3001.zip](https://drive.google.com/file/d/1XGDSGi-zCav_Ib8sICg9wnf6Dy2VYS7k/view?usp=sharing)  
  SHA-256: `364bd095b7e1f3b16fd7b31319bee0211b644be5b1b0980798a58467dc7d754e`  

- **VirusTotal Report:**  
  [Link](https://www.virustotal.com/gui/file/d194e738fad73853b766ab571e24b49b0374c80399b1440f3066df48ee2060d5)


---

## Unlocked Advanced Menus

| Category | Description | Safe to Adjust | Risky / Leave Alone |
|----------|-------------|----------------|----------------------|
| Intel Platform Debug | DSP routing, ICC clock tuning | Rarely needed outside dev work | May destabilize audio/bus |
| Secure Boot Modes | AuditMode, DeployedMode, SecureVarPresent | Switch Standard ↔ Custom | Deployed/FIPS lock may brick |
| Debug Configuration | DebugSetupVolatileData & DebugConfigData | Leave disabled | Can flood NVRAM, hurt perf |
| Board / Platform Overrides | BoardInfoSetup & SIBoardItemControl | Not recommended | Breaks updates & drivers |
| Extended OC Registers (OCMR) | Memory training beyond GUI | For extreme OC only | POST loops / black screens |
| iGPU / Display Options | Intel PEI, DVMT, VBT, CdClock | DVMT Pre-Alloc, enable/disable iGPU | VBT wrong panel = no display; CdClock unstable |
| Intel ME Configuration | ME State, PTT, FIPS, erase/unconfig | PTT, ME State (caution) | Erase/Unconfig wipes ME; FIPS lock |
| Intel ME Debug Menus | HECI timeouts, polling, MCTP | None for normal use | Breaks PCIe/USB/ME → POST fail |

