# Guide to Unlock Benco V90 Plus's Bootloader (codename AEOP519)

**As of now I have only fixed the `.bat` files, so currently this will only work on Windows.**  
**This guide assumes that you have already installed the Unisoc / Spreadtrum USB drivers (and ADB/Fastboot tools).**

> ⚠️ **Warning:** Unlocking the bootloader performs a factory reset and wipes all user data on your device. Additionally, **never share** your `prodnv`, `persist`, `l_fixnv1`, or `l_fixnv2` partition backups publicly, as they contain your unique IMEI numbers and MAC addresses.

---

## Step 1: Download & Extract the Unlock Package
1. Download `Bootloader_Unlock.zip` from this repository.
2. Locate the downloaded ZIP file on your PC and extract it to a dedicated folder (e.g., `C:\Users\<YourName>\Desktop\Bootloader_Unlock`).
3. Open the newly extracted folder, click the address bar at the top of File Explorer, type `cmd`, and press **Enter**. This opens a Windows Command Prompt directly inside the working directory.

---

## Step 2: Full Partition Backup (Mandatory)
Before modifying the bootloader, dump a complete backup of your device's stock partitions so you can recover from a soft-brick if anything goes wrong:

1. Power off your **Benco V90 Plus** completely.
2. Hold either **Volume Down** only or **both Volume Up + Volume Down** simultaneously, and plug the USB cable into your computer to enter **BROM mode**.
3. Back in your Command Prompt window, run the following command to dump every partition:
   ```cmd
   spd_dump.exe --wait 300 fdl fdl1-dl.bin 0x65000800 fdl fdl2-dl.bin 0x9efffe00 exec r all
   ```
4. Once the dump completes, **copy all of the newly dumped `.bin`/`.img` files into a separate safe backup folder** on your PC.
5. **Delete all of the dumped files from the bootloader unlock directory** so they do not interfere with or get overwritten by the unlock script.

---

## Step 3: Temporarily Disable Antivirus
1. If you use Windows Defender or any third-party antivirus, **temporarily disable real-time protection** or add a folder exclusion for your extracted `Bootloader_Unlock` directory.
   - *Note:* Antivirus software frequently flags `gen_spl-unlock.exe` or `spd_dump.exe` as false positives. If a binary gets quarantined mid-flash, it can leave your device in a soft-bricked state.

---

## Step 4: Check Your Active Boot Slot (`_a` or `_b`)
Because the Benco V90 Plus uses A/B seamless system updates, you must run the batch script corresponding to your currently active boot slot:

- **If your phone is booted into Android** (with USB Debugging enabled in Developer Options):
  ```cmd
  adb shell getprop ro.boot.slot_suffix
  ```
- **If your phone is booted into Fastboot / Bootloader mode**:
  ```cmd
  fastboot getvar current-slot
  ```

*(If you have never installed an OTA system update on the device, your active slot is almost certainly **Slot A** / `_a`).*

---

## Step 5: Run the Bootloader Unlock Script
1. Power off your phone completely again.
2. In your `Bootloader_Unlock` folder, double-click (or run via Command Prompt) the `.bat` script matching your active slot:
   - Run the **unlock_autopatch_9230_a** `.bat` file if your active slot is `_a` (or `a`).
   - Run the **unlock_autopatch_9230_b** `.bat` file if your active slot is `_b` (or `b`).
3. Hold the volume button(s) (**Volume Down** or **Volume Up + Volume Down**) and plug the USB cable into your PC when prompted by the script.
4. Wait for `spd_dump` and the exploit payload (`gen_spl-unlock.exe`) to complete flashing and reboot the device. Do not unplug the cable until the script finishes.

---

## Step 6: Verify Bootloader Unlock Status
1. Once the device reboots (or by running `adb reboot bootloader`), enter **Fastboot mode**.
2. Run the following command to confirm the bootloader state:
   ```cmd
   fastboot getvar unlocked
   ```
3. If the output reads `unlocked: yes` (and you see the unlocked bootloader warning screen during startup), your Benco V90 Plus is officially unlocked and ready for `vbmeta` patching, Magisk root, or Custom GSI installation.

---

## Credits & Acknowledgments
- **Bootloader Unlock Exploit (`CVE-2022-38694`):** Huge thanks to [TomKing062](https://github.com/TomKing062/CVE-2022-38694_unlock_bootloader) for the original UNISOC unlock exploit implementation.
