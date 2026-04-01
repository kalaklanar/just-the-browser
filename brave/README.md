---
layout: layout.njk
title: Brave Browser configuration
permalink: "brave/index.html"
---

Brave Browser features can be configured with group policies. This project uses Windows Registry settings on Windows, and a Profile Manager file on macOS.

You can check which policies are applied in Brave Browser by navigating to the `brave://policy/` page.

### Windows installation

1. Open the [registry file for installation](https://raw.githubusercontent.com/corbindavenport/just-the-browser/main/brave/install.reg) and save it (`Ctrl+S`) anywhere on your computer.
2. In the File Explorer, right-click the file and select Open with > Registry Editor.
3. Follow the prompts to install the registry keys to the Windows Registry.
5. Restart Brave.

To remove the custom configuration, follow the same steps with the [registry file for uninstallation](https://raw.githubusercontent.com/corbindavenport/just-the-browser/main/brave/uninstall.reg). This will remove the modified registry keys from your system.

### macOS installation

1. Open the [configuration file](https://raw.githubusercontent.com/corbindavenport/just-the-browser/main/brave/brave.mobileconfig) and save it (`Command+S`) anywhere on your computer.
2. In the Finder, open the configuration file you downloaded. You should see a prompt that the profile is ready for review.
3. Open the System Settings application (Apple menu > System Settings) and navigate to General > Device Management. If you are on macOS 12 Monterey or an older version, the application is called System Preferences, and you need to open the Profiles section.
4. Double-click on the 'Brave Browser settings' configuration, then click the Install button and follow the prompts.

To remove the custom configuration, open the Device Management settings (or Profiles pane) again, select the 'Brave Browser settings' configuration, and then click the remove (-) button.

### Linux installation

These instructions work for both Chromium and Brave Browser. You can check what you're running by opening `brave://version` and checking if it says "Chromium" or "Brave Browser" at the top-right corner of the page.

1. Open the [configuration file](https://raw.githubusercontent.com/corbindavenport/just-the-browser/main/brave/managed_policies.json) and save it (`Ctrl+S`) anywhere on your computer. Make sure the file is called "managed_policies.json" (without the quotes).
2. Open a new Terminal window in the directory where the file is located. For example, if it's in your Downloads folder, open a Terminal and run `cd ~/Downloads` to switch to the Downloads directory.
3. Create the managed policies directory with one of the below commands.
    - For Brave Browser: `sudo mkdir -p /etc/opt/brave/policies/managed`
    - For Chromium: `sudo mkdir -p /etc/chromium/policies/managed`
4. Copy the file to the new folder with one of the below commands.
    - For Brave Browser: `sudo cp ./managed_policies.json /etc/opt/brave/policies/managed`
    - For Chromium: `sudo cp ./managed_policies.json /etc/chromium/policies/managed`
5. Restart the browser.

To remove the custom configuration, delete the `managed_policies.json` file from the managed policies directory and restart the browser. You can do that with one of the below commands.
 - For Brave Browser: `sudo rm /etc/opt/brave/policies/managed/managed_policies.json`
 - For Chromium: `sudo rm /etc/chromium/policies/managed/managed_policies.json`

### Browser settings

These are the policy settings in the Just the Browser configuration file.

| Feature | Information |
| ------- | ----------- |
| AIModeSettings | Turns off Google's AI Mode integrations in the address bar and the New Tab page search box. |
| BraveWalletDisabled | Disables Wallet, web3, and decentralized DNS settings and functionality. |
| BraveVPNDisabled |  |
| BraveAIChatEnabled |  |
| BraveNewsDisabled |  |
| BraveP3AEnabled |  |
| BraveStatsPingEnabled |  |
| CreateThemesSettings | Turns off the ability to create custom themes and wallpapers with generative AI. |
| GeminiSettings | Blocks Gemini app integrations. |
| GenAILocalFoundationalModelSettings | Prevents the local AI model from being downloaded. |
| HelpMeWriteSettings | Turns off the Help Me Write feature powered by AI. |
| HistorySearchSettings | Turns off AI History Search. |
| NewTabPageLocation |  |
| TabCompareSettings | Turns off the AI-powered Tab Compare feature. |
| BuiltInDnsClientEnabled | Forces Chrome to use the host operating system's DNS client instead of the built-in DNS client. This has no effect when using DNS-over-HTTPS. |
| DefaultBrowserSettingEnabled | Prevents Chrome from checking if it's the default browser and showing notifications about it. |
| DevToolsGenAiSettings | Turns off debugging in the Dev Tools powered by generative AI models. |
| TorDisabled |  |

### Documentation

- [Brave Group policy list](https://support.brave.app/hc/en-us/articles/360039248271-Group-Policy)
