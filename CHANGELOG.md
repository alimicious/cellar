# What's new in Cellar

Downloads are on the [releases page](https://github.com/alimicious/cellar/releases). Versions before 1.2.4 were shared directly and aren't published here.

## 1.3.1 (2026-10-29)
- **Performance notices.** While a game plays, Cellar tells you what's costing it frames, and what to do about it:
  - **Retina mode** is on for the game. It draws up to four times the pixels
  - **Low Power Mode** is on
  - your Mac is **running hot** and slowing itself down
  - your Mac is **short of memory** and swapping to disk

  You get a notification while the game is in front, and a **While you play** panel in the bottle.
- We benchmarked Cellar's graphics settings on a demanding DirectX 11 game, and none made a real difference. A game's own quality setting and the four things above decide the frame rate.

## 1.3.0 (2026-10-29)
- **Game Settings** for each game: Windows version, FPS counter, Retina mode, AVX, DXVK and launch options can follow the bottle or be set for that game alone. Find it under **⋯ Options** on the wheel.
- **Playtime:** each game shows how long you've played it and when, even when you start it from Steam. The wheel opens on the game you played last.
- **Anti-cheat badge** for games with EasyAntiCheat, BattlEye and similar, which can't run on a Mac.
- **Launch doctor:** when a game quits as it starts, Cellar says why (Steam not running, AVX needed, Visual C++ missing, DirectX 11 or 12 trouble, a crash) and offers a one-click fix.
- **Copy and paste:** ⌘C, ⌘V and the other ⌘ shortcuts work in Windows programs, and Option works as Alt.
- **FPS counter:** the frame rate only, or the full Metal HUD. Press Shift-F9 in a game to hide or show it.

## 1.2.5 (2026-10-29)
- **Cellar updates itself.** **Update and Restart** downloads the new version, checks its signature, installs it and reopens Cellar. Open games keep running, and macOS doesn't ask for **Open Anyway** again.
- Updates are signed with an Ed25519 key. Cellar installs only a download that matches it, has Cellar's identity and the promised version, and has an intact code signature.
- Cellar is now signed with its own certificate, so macOS remembers permissions such as the microphone across updates. It asks once more after you install 1.2.5.

## 1.2.4 (2026-10-29)
- **Check for Updates** looks at this public repository, so it can find new versions. Before, it looked somewhere only the developer could see and always said there was no release.

## 1.2.3 (2026-10-29)
- **Microphone works.** macOS now asks once, the first time a game or Steam uses it. Before, it turned Cellar down without asking.
- **Headphones reminder.** Windows programs keep the sound output they started with, so when you switch output while a game runs, Cellar tells you to restart the game.

## 1.2.2 (2026-10-29)
- **Logs stay small.** A DirectX 11 game could fill one log with over a gigabyte of graphics warnings. Those warnings are now off, any log over 16 MB is cut down while the game runs, and each bottle keeps its newest 30 logs.

## 1.2.1 (2026-10-28)
- **Install Steam works on a new bottle.** It no longer stops at "Failed to load steamui.dll". A bottle stuck there finishes Steam's update the next time you open Steam from Cellar.

## 1.2.0 (2026-10-28)
- **Cellar → Check for Updates…**, plus a quiet check once a day when Cellar opens. When there's a newer version, light runs round the window's edge and a card shows what's new.

## 1.1.0 (2026-10-28)
- **The current Windows Steam client runs** in Wine Staging bottles: sign-in, library, downloads, multiplayer and lobbies. Getting there took three fixes, all built in:
  - **No more hang at start-up:** proxy auto-detection is turned off in every bottle.
  - **Steam's windows draw:** a small stand-in starts Steam's web helper the way Chromium needs on a Mac.
  - **DirectX 11 games start:** DXVK is set up in Wine Staging bottles, and a new **DXVK** setting turns it off.
- **Install Steam** runs Steam's first update and puts the fixes in before you see Steam.
- Game Porting Toolkit bottles explain that the current Steam client can't run there.
- Each bottle's games on a wheel of covers, with Steam box art.

## 1.0.1 (2026-10-28)
- New app icon, a new sidebar, and a dock with search, quick actions (⌘K) and runtimes.
- Steam's helper programs no longer show up as games, and games are named after their install folder.

## 1.0.0 (2026-10-28)
- First version. Download Wine Staging or Apple's Game Porting Toolkit, create bottles, run `.exe`, `.msi` and `.bat` files, and see each bottle's programs.
- Per-bottle settings, Wine's tools in a menu, and a log for every run.
