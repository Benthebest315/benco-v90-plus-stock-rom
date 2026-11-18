# Guide to Unlock Benco V90 Plus's Bootloader (codename AEOP519) 

**As of now I have only fixed the bat files, so currently this will only work on Windows.**
**This guide assumes that you have installed Unisoc and Spreadtrum Drivers.**

> ⚠️ **Warning:** Unlocking the bootloader will perform a factory reset and wipe all user data on your device. Make sure you have backed up your important files before proceeding.

1. **Download the Package:** First, download the `Bootloader_Unlock.zip` file from this repo.
2. **Extract the Archive:** Second, locate the file on your computer and unzip it.
3. **Open Command Prompt:** Third, open the newly unzipped directory, click the directory bar of File Explorer, and type `cmd`. This should open a Command Prompt in the directory.
4. **Enter BROM Mode:** Fourth, power off your Benco V90 Plus and hold either only Volume Down or both volume buttons and plug it into your computer.
5. **Backup All Partitions:** Fifth, go back into the Command Prompt that you opened and run this command to dump every partition:
   ```cmd
   spd_dump.exe --wait 300 fdl fdl1-dl.bin 0x65000800 fdl fdl2-dl.bin 0x9efffe00 exec r all
