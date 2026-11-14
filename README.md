# Lodestone

Lodestone is a free, native Windows app for managing Minecraft: Java Edition setups and mods. Browse and install mods from Modrinth, keep separate setups for different loaders and versions, back up your worlds, and hand a setup off to the official Minecraft Launcher with one click.

It is a hobby project made by an individual player, for friends and anyone else who finds it useful. It is not affiliated with Mojang, Microsoft or Modrinth.

## Features

- **Workshop:** search Modrinth for mods, shaders, resource packs and modpacks, review what will be installed (including required dependencies), and install into a setup.
- **Setups:** each setup has its own Minecraft version, loader (Fabric, Quilt, Forge or NeoForge) and mod list. Duplicate, rename, pin and sort them.
- **Update checker:** see which mods have newer versions, update them, and roll back if something breaks.
- **World backups:** automatic or manual backups of a setup's worlds, with restore.
- **Modpack import and export:** `.mrpack` files.
- **Launcher handoff:** writes the setup into the official launcher's profile list and opens it, so you launch with the official launcher.
- **Live updates:** the app reflects changes on disk without needing a refresh.
- **Themes:** 18 colour themes plus fine-tuning, and an app icon that follows the theme.

## Microsoft sign-in (how it works and why)

Lodestone can sign you in with your Microsoft account so it can check that you own Minecraft and, in a future version, launch the game itself.

- It uses Microsoft's **device-code flow**. Lodestone shows a short code, you open `microsoft.com/link` in your own browser, enter the code and sign in on Microsoft's own page.
- **Lodestone never sees or asks for your password.** All password and two-factor entry happens on Microsoft's website.
- The chain after that is the standard one used by Minecraft launchers: Microsoft, then Xbox Live, then XSTS, then Minecraft services, then your ownership and profile.
- Your Microsoft refresh token is stored on your PC, encrypted with Windows DPAPI so only your Windows user can read it. The short-lived Minecraft access token is kept in memory only.
- You can sign out at any time in Settings, which deletes the stored token.
- The sign-in uses a public Azure app registration with the `XboxLive.signin` and `offline_access` scopes only.

## Privacy

Lodestone has no accounts, analytics or telemetry. Your setups, settings and backups stay on your PC (`%APPDATA%\Lodestone`). The app only talks to:

| Service | Used for |
|---|---|
| `api.modrinth.com`, `cdn.modrinth.com` | Searching and downloading mods |
| `piston-meta.mojang.com` | Minecraft version information |
| `meta.fabricmc.net`, `meta.quiltmc.org`, `maven.minecraftforge.net`, `maven.neoforged.net` | Loader versions |
| `login.microsoftonline.com`, `user.auth.xboxlive.com`, `xsts.auth.xboxlive.com`, `api.minecraftservices.com` | Microsoft sign-in (only if you choose to sign in) |
| `mc-heads.net` | Showing your Minecraft head as an avatar once signed in |

The app's interface is served from a local-only web server on `127.0.0.1` that requires a custom header on every action, so other websites cannot control it.

## Install

1. Download `Lodestone-Setup.exe` from the Releases page.
2. Run it. It installs for your Windows user only and needs no administrator rights.
3. Windows may show a SmartScreen warning because the installer is not code-signed. Choose **More info**, then **Run anyway**.

Requires Windows 10 or 11, .NET Framework 4.8 (included with Windows) and the Microsoft Edge WebView2 Runtime (included with Windows 11 and most Windows 10 PCs; the installer tells you if it is missing).

Uninstall from Windows Settings, Installed apps. You are asked whether to keep or delete your data.

## About the Azure app and Mojang approval

Lodestone's sign-in uses its own Azure app registration. Mojang requires new third-party apps that use the Java game service APIs to be reviewed and added to an allow list, and Lodestone has applied for that review. Until approval, signing in stops at the final Minecraft step and launching from the official launcher is unaffected.

## Contact

Questions or concerns: open an issue on this repository.

## Disclaimer

Minecraft is a trademark of Mojang AB. Fabric, Quilt, Forge, NeoForge and Modrinth belong to their respective projects. Lodestone is an unofficial tool and ships no Minecraft game files.
