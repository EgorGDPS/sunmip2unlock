Here is the full cleaned-up guide with the corrected BROM procedure, battery pin removal wording, and formatting:

---

# Sunmi P2 Flashing & Root Guide

## Downloads & Prerequisites

### Required Files

**Unlocked Firmware:**
[https://drive.google.com/file/d/1CwfmmqLgOqc22xBI1lrbAlqPo2Kselvg/view?usp=sharing](https://drive.google.com/file/d/1CwfmmqLgOqc22xBI1lrbAlqPo2Kselvg/view?usp=sharing)

**Modded MTKClient:**
[https://drive.google.com/file/d/1xutiSOtTqBfz1bMjr3FxrWHcHx_foFiI/view?usp=sharing](https://drive.google.com/file/d/1xutiSOtTqBfz1bMjr3FxrWHcHx_foFiI/view?usp=sharing)

**Official MTKClient Repository:**
[https://github.com/bkerler/mtkclient](https://github.com/bkerler/mtkclient)

---

## Notes

* Works on Windows too, but no technical support is provided for Windows setups.
* Required cable:

  * USB-A to USB-C **data cable**

---

# 1. Configure User Group & Run Launcher

## Linux Automated Launch

1. Extract the downloaded **modded MTKClient ZIP** folder.

2. Open a terminal inside the extracted directory.

3. Add your user to the `dialout` group for USB access:

```bash
sudo usermod -a -G dialout $USER
```

4. Make the launcher executable:

```bash
chmod +x "MTKClient_GUI 2.0.sh"
```

5. Start MTKClient:

```bash
./"MTKClient_GUI 2.0.sh"
```

The script will automatically:

* Create the Python virtual environment
* Install required dependencies
* Open the MTKClient GUI

---

### Tip: Apply USB Permission Changes

If you added your user to the `dialout` group for the first time, log out and log back in.

Alternatively, run:

```bash
su - $USER
```

---

# 2. Connect Sunmi P2 & Unlock Bootloader

## Enter BROM Mode & Unlock Bootloader

1. Remove the back cover of the Sunmi P2.

2. Completely disconnect the battery by removing it from the battery pins.

3. Open the **MTKClient GUI**.

4. Leave MTKClient running and wait until it shows:

```
Waiting for device...
```

5. Enter BROM mode:

* Hold down **both hardware buttons** on the Sunmi P2.
* While holding both buttons, connect the USB cable to the PC.
* Keep holding the buttons until MTKClient detects the device.

6. In the MTKClient GUI, go to:

```
Flash Tools
```

7. Click:

```
Unlock Bootloader
```

8. Wait for the unlock process to complete.

---

# 3. Dump eMMC (Backup Partitions)

## Safety Backup

1. Open the:

```
Read Partition(s)
```

tab in MTKClient.

2. Click:

```
Select all partitions
```

This will back up all partitions, especially:

* `nvram`
* `nvdata`
* 'proinfo' 

These contain important device calibration and configuration data.

3. Click:

```
Read Partition(s)
```

4. Select or create a backup folder.

Example:

```
backup_p2
```

# 4. Select Firmware Folder & Flash

## eMMC Write

1. Extract the downloaded Sunmi P2 firmware ZIP into a clean folder.

2. Open:

```
Write Partition(s)
```

tab.

3. Click:

```
Select from Folder
```

4. Select the extracted firmware folder.

MTKClient will automatically detect and map the partition `.img` files.

5. Click:

```
Write Partition(s)
```
6. Wait a while until the flashing process is complete

7. Power on the Sunmi P2 if it powers on you are done with the flashing part

---

# 5. Bypass POS Security & Install Magisk

## Post-Boot Verification & Root Setup

1. Allow the Sunmi P2 to complete its first Android boot.

2. Open the app with Chinese characters labeled:

```
DEMO
```

3. Tap the first option inside the app. WARNING: DONT PLAY WITH OTHER OPTIONS CUZ SOME OF THEM CAN FACTORY RESET UR TERMINAL

4. Check the result:

If a red circle appears saying:

```
Your device is at risk, do not deal
```

then the POS security lock has been bypassed for the current session.

5. Install the **Magisk APK**.

Magisk can be used to:

* Manage root permissions
* Install custom APKs

---

# Important Note About Rebooting

After rebooting, the device automatically returns to secure mode.

To enable non-secure mode again:

1. Open the Chinese **DEMO** app.
2. Select the first option again.

This must be repeated after every reboot before:

* Installing APKs
* Using root permissions
* Managing system modifications
