# benco-v90-plus-stock-rom

Stock ROM partition dumps, FDL loaders, and bootloader unlock helper scripts for the **Benco V90 Plus** (Unisoc T606 / UMS9230, Linux Kernel 5.4), codename **AEOP519**.

---

## ⚠️ Important Disclaimer
- **NVRAM / Persistent Partitions Excluded:** Partition dumps containing device-specific radio calibration and hardware identifiers (`prodnv`, `persist`, `l_fixnv1`, `l_fixnv2`) are intentionally excluded to protect unique IMEI numbers and MAC addresses.
- **Flash at Your Own Risk:** Always dump a full backup of your own device's partitions before executing low-level BROM flashing or unlock commands.

---

## Repository Structure & Downloads

- **[GitHub Releases (`v1.0-stock`)](../../releases/tag/v1.0-stock)** — Clean stock partition binaries and flashing utilities:
  - **Boot & Recovery Images:** `boot.bin` (`_a`/`_b`), `vendor_boot.bin` (`_a`/`_b`), `dtbo.bin` (`_a`/`_b`)
  - **Bootloader & Verified Boot:** `uboot.bin` (`_a`/`_b`), `vbmeta.bin` (`_a`/`_b`)
  - **BROM Tools & Loaders:** `fdl1-dl.bin`, `fdl2-dl.bin`, `gen_spl-unlock.exe`
- **`Bootloader_Unlock.zip`** — Modified Windows `.bat` scripts and exploit binaries based on TomKing062's UNISOC bootloader unlock tool, configured specifically for the Benco V90 Plus (`AEOP519`).
- **[`bl_unlock.md`](./bl_unlock.md)** — Step-by-step Windows guide covering full BROM partition backup, active A/B slot detection, and executing the unlock script.

---

## Credits & Acknowledgments
- **Bootloader Unlock Exploit (`CVE-2022-38694`):** Huge credits to [TomKing062](https://github.com/TomKing062/CVE-2022-38694_unlock_bootloader) for the original UNISOC bootloader unlock implementation used in the helper scripts.
