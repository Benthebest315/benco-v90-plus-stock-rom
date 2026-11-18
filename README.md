# benco-v90-plus-stock-rom

Stock ROM partition dumps and bootloader unlock helper scripts for the **Benco V90 Plus** (Unisoc T606 / UMS9230), codename **AEOP519**.

---

## ⚠️ Important Disclaimer
- **NVRAM / Persistent Partitions:** Partition dumps containing device-specific calibration data (`nvram`, `nvdata`, `persist`) are intentionally excluded to protect your unique IMEI numbers and MAC addresses. 
- Flash partition images at your own risk. Always back up your current state before running low-level BROM commands.

---

## Repository Structure & Downloads
- **[GitHub Releases](../../releases)** — Core stock partition dumps (`super.img`, `vendor_boot.bin`, `boot.bin`, etc.) exceed Git file size limits and are hosted directly under repository **Releases**.
- **`fdl/`** — First Download Loader binaries (`fdl1.bin`, `fdl2.bin`) required for UNISOC BROM mode communication.
- **Bootloader_Unlock.zip** — Zip edited from TomKing062's BL Unlock script to work with the Benco V90 Plus.

---

## Credits & Acknowledgments
- **Bootloader Unlock Exploit:** Huge credits to [TomKing062](https://github.com/TomKing062) for the `CVE-2022-38694_unlock_bootloader` implementation used in the helper scripts.
