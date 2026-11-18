# benco-v90-plus-stock-rom

Stock ROM partition dumps and bootloader unlock helper scripts for the **Benco V90 Plus** (Unisoc T606 / UMS9230).

---

## ⚠️ Important Disclaimer
* **NVRAM / Persistent Partitions:** Partition dumps containing device-specific calibration data (`nvram`, `nvdata`, `persist`) are intentionally excluded to protect your unique IMEI numbers and MAC addresses. 
* Flash partition images at your own risk. Always back up your current state before running low-level BROM commands.

---

## Repository Structure
* **`images/`** — Core stock partition dumps (`boot`, `vendor`, `dtbo`, `vbmeta`, `recovery`, etc.)
* **`fdl/`** — First Download Loader binaries (`fdl1.bin`, `fdl2.bin`) required for UNISOC BROM mode communication.
* **Scripts** — Custom Windows batch scripts for unlocking and partition management on Slot A and Slot B.

---

## Credits & Acknowledgments
* **Bootloader Unlock Exploit:** Huge credits to [TomKing062](https://github.com/TomKing062) for the `CVE-2022-38694_unlock_bootloader` implementation used in the helper scripts.
