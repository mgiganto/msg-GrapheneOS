# msg-GrapheneOS

Custom GrapheneOS builds featuring **custota** integration for seamless OTA updates. 

### 🌐 Official Website: [https://mgiganto.github.io/msg-GrapheneOS/](https://mgiganto.github.io/msg-GrapheneOS/)

These builds allow you to switch between different variants without requiring a data wipe. Refer to the website for variant URLs, step-by-step guides, and detailed information about experimental features.

-----

## Available Variants

| Variant | Description | Custota Update URL |
| :--- | :--- | :--- |
| **Clean** | A "vanilla" experience that mimics the official GrapheneOS release, with the only addition being `custota` support. | `https://mgiganto.github.io/msg-GrapheneOS/user-clean/` |
| **Custom** | Includes experimental enhancements, such as **Apps Isolation (Work In Progress)** which prevents apps from seeing other installed applications. **To activate it, go to the App Info of the desired application.** | `https://mgiganto.github.io/msg-GrapheneOS/user-custom/` |
| **Rooted** | Includes **KernelSU (SukiSU)** + **SUSFS** and custom changes. Features a unique "on-demand" root mechanism. Required for full system backups. | `https://mgiganto.github.io/msg-GrapheneOS/user-rooted/` |

-----

## On-Demand Root (Rooted Variant)

The Rooted variant is designed with a "security-first" approach. Root functionality is not active by default; it must be explicitly triggered during the boot process.

### How to Activate Root

1.  Reboot the device.
2.  When the **GrapheneOS logo** appears, press **Volume Up**.
3.  If the button is not pressed, the kernel will boot without exposing any root functionality.

### Why On-Demand?

  * **Security:** Prevents persistent root access from being exploited by background processes when not needed.
  * **Stealth:** If the phone reboots automatically, it returns to a non-rooted state.
  * **Maintenance:** Easily enable root only when you need to perform specific tasks, such as full backups (e.g., using **NeoBackup**) or system-level configurations.

### Managing Permissions

To manage root access, you must boot with root enabled and install the **[SukiSU Manager APK](https://github.com/SukiSU-Ultra/SukiSU-Ultra)**.

  * **Granular Control:** KernelSU allows you to grant only the specific capabilities an app requires (e.g., granting Network Admin to a firewall without granting full file system access).
  * **Minimal Footprint:** The manager app is only required to configure profiles. Once permissions are granted, you can uninstall the manager; the kernel will remember the settings.

#### NeoBackup SukiSU Configuration

For full system backups via **NeoBackup**, the following SukiSU profile configuration is required:

- **App profile:** `Custom`
- **Capabilities:** `DAC_OVERRIDE`, `SYS_ADMIN`, `SYS_CHROOT`, `SYS_PTRACE`
- **SELinux context:** `u:r:su:s0`

-----

## Installation & Updates

These builds utilize **custota** for OTA (Over-The-Air) installations.

  * **Switching Variants:** You can move between Clean, Custom, and Rooted variants freely. **No data wipe is required** when switching between these specific builds.
  * **OTA Update Policy:** Incremental OTAs are provided for updates from the previous version. Full OTA updates are available for any other version.
  * **Kernel Modules:** For manual flashing of `dlkm` files, ensure you utilize `fastboot` mode.

### How to Switch Variants (Detailed)

To switch between variants without losing data, follow these steps in **Custota**:

1.  **Enable Debug Mode:** Open Custota settings and **long-press the version number** until debug options are unlocked.
2.  **Activate Reinstall:** Locate and enable the **"Reinstall"** toggle.
3.  **Update URL & Check:** Paste the desired variant's Update URL and tap **"Check for Updates"**.
4.  **Finish:** Once the switch is complete, **deactivate the "Reinstall" option** to prevent unnecessary reinstallations of the same variant.

-----

### Credits & Resources

  * [GrapheneOS](https://grapheneos.org/)
  * [custota](https://github.com/chenxiaolong/Custota)
  * [SukiSU-Ultra](https://github.com/SukiSU-Ultra/SukiSU-Ultra)
  * [SUSFS](https://gitlab.com/simonpunk/susfs4ksu)

