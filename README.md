# ApprenticeVR Using vrSrc

This fork of ApprenticeVR uses vrSrc now that VRP is dead. For more about ApprenticeVR, please read [their official github's README](https://github.com/jimzrt/apprenticeVr/blob/main/README.md).


### macOS Specifics

**Important:** Since the application is not signed by an Apple Developer ID, when you first try to open `apprenticevr.app` on macOS after building or downloading it, you might encounter an error message stating: `"apprenticeVR is damaged and can't be opened. You should move it to the Trash."`

This error occurs because macOS Gatekeeper flags applications downloaded from the internet or built by unidentified developers as potentially unsafe. The `com.apple.quarantine` extended attribute is added to the application bundle by the system.

To resolve this, you can remove this extended attribute by running the following command in your Terminal:

```bash
xattr -c /Applications/apprenticevr.app
```

**Note:**
*   You might need to adjust the path `/Applications/apprenticevr.app` if you have placed the application in a different location.
*   The `-c` flag in the `xattr` command stands for "clear," and it removes all extended attributes from the specified file or application bundle. By removing the quarantine attribute, you are essentially telling macOS that you trust this application.

After running this command, you should be able to open ApprenticeVR without any issues. 

## Logs

By default, it writes logs to the following locations:

 - **on Linux:** `~/.config/apprenticevr/logs/main.log`
 - **on macOS:** `~/Library/Logs/apprenticevr/main.log`
 - **on Windows:** `%USERPROFILE%\AppData\Roaming\apprenticevr\logs\main.log`

**Note:** When opening an issue, please include the latest log output from the appropriate log file above to help with debugging and troubleshooting.

You can also upload the current log file in the settings menu and share the url.

You can view live logs on MacOS using `/Applications/apprenticeVr.app/Contents/MacOS/apprenticeVR`

# Troubleshooting Guide

If ApprenticeVR fails to connect, download, or mount, follow the steps below to identify and resolve the issue:

---

## ✅ Use the Latest Version

Make sure you're using the latest version of the fork.

---

## 📦 Install MacFUSE (Mac Specific)

On some Macs, you may have to install [MacFUSE](https://macfuse.github.io/) if indicated in your logs. I'm not sure why this happens, but installing it worked for me.

---

## 🌐 Check Network Access

Ensure you can access the following URLs from your browser:

- [https://raw.githubusercontent.com/](https://raw.githubusercontent.com/)  
  (Should redirect to the GitHub homepage)

- [https://downloads.rclone.org/](https://downloads.rclone.org/)

- [https://go.srcdl1.xyz/](https://go.srcdl1.xyz/)
  ⛔ Getting a message like **"Sorry, you have been blocked"** means it's working!

- [https://pastebin.com](https://pastebin.com)

---

## 🌍 Change DNS Settings

Some ISPs block specific domains. Switch to a public, non-censoring DNS provider:

- [Cloudflare DNS (1.1.1.1)](https://developers.cloudflare.com/1.1.1.1/setup/windows/)
- [Google Public DNS (8.8.8.8)](https://developers.google.com/speed/public-dns/docs/using)
- [OpenDNS](https://www.opendns.com/setupguide/)

---

## 🔐 Try a VPN

If DNS changes don't help, your ISP might be blocking access. Use a VPN to bypass restrictions:

- [ProtonVPN (free)](https://protonvpn.com/)
- [1.1.1.1 VPN (free)](https://one.one.one.one/)
- [Alternate VPN Example](https://gprivate.com/5yxo8)

---

## 🛜 Router or Firewall Blocking?

If a VPN works, but a direct connection doesn't, your router or antivirus/firewall may be blocking access.  
Check out this guide for help:

➡️ [https://rentry.co/ASUSRouterBlock](https://rentry.co/ASUSRouterBlock)

You can either:

- Continue using a VPN  
- OR identify and whitelist the following domains in your router/firewall settings:
  - `raw.githubusercontent.com`
  - `downloads.rclone.org`
  - `go.srcdl1.xyz`
  - `pastebin.com`

---

## 🛡️ Windows Defender or Antivirus

Sometimes Windows Defender or other Antiviruses will block `rclone` from downloading, presenting the client with a "Failed to Mount" error. Try completely disabling Windows Defender or your Antivirus temporarily instead of creating an exception.

---

If you're still stuck, feel free to open an issue or ask for help in the community. Happy VR-ing!

