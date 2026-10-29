# Cellar

Cellar runs Windows games and apps on macOS. It downloads Wine runtimes for you, keeps each set of games in
its own "bottle", and gets the current Windows Steam client running, with sign-in, the library and
multiplayer.

This repository holds **release downloads only**. Get the latest from
[Releases](https://github.com/alimicious/cellar-releases/releases/latest). Cellar's **Check for Updates…**
looks here too.

## Needs
- macOS 26 or later
- A Mac with Apple silicon is best. Intel Macs can only use the Wine Staging runtime
- Rosetta 2: `softwareupdate --install-rosetta --agree-to-license`

## Install or update
1. Download **Cellar-x.y.z.zip** from the latest release, unzip it, and drag **Cellar** into **Applications**
   (choose **Replace** when updating).
2. Open it. Cellar isn't notarized by Apple, so macOS stops it the first time: click **Done**, then go to
   **System Settings → Privacy & Security**, scroll down, and click **Open Anyway**. Updates ask again once.
3. Your bottles, runtimes, Steam and games live in `~/Library/Application Support/Cellar` and stay there
   when you update.

## Getting started
1. **Runtimes** (bottom-left of the sidebar): download **Wine Staging**.
2. **⌘N**: make a bottle on Wine Staging.
3. **Install Steam**, sign in, install a game, and press **Play**.

Games with kernel-level anti-cheat (Valorant, Fortnite and many online shooters) won't run.

## What Cellar downloads
Cellar itself contains no Wine. On first use it downloads:
- [Wine Staging](https://github.com/Gcenx/macOS_Wine_builds) and, if you choose it,
  [Game Porting Toolkit](https://github.com/Gcenx/game-porting-toolkit), both built by Gcenx
- [DXVK-macOS](https://github.com/Gcenx/DXVK-macOS) for DirectX 10 and 11
- Steam's own installer, from Valve

