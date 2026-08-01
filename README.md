# BattleMetrics Rust Player Tracker

A Tampermonkey userscript that watches specific Rust players on
[BattleMetrics](https://www.battlemetrics.com/servers/rust) and sends you a
desktop notification the moment their status changes — online, offline, or
unknown, in any direction.

Useful for keeping tabs enemy players to raid them 
as soon as they go offline

![status](https://img.shields.io/badge/status-working-brightgreen)
![platform](https://img.shields.io/badge/platform-Tampermonkey-blue)

- **Google Chrome** (or any Chromium-based browser — Edge, Brave, etc.)
- **[Tampermonkey](https://www.tampermonkey.net/)** browser extension
- A BattleMetrics account is *not* required — this works on public server pages

---

## Installation

1. **Install Tampermonkey** for your browser, if you don't have it already:
   [tampermonkey.net](https://www.tampermonkey.net/)

2. **Install the userscript:**
   - Click the Tampermonkey icon in your browser toolbar → **Dashboard**
   - Go to the **Utilities** tab (or **+** to create a new script)
   - Open [`scripts/battlemetrics-rust-tracker.user.js`](scripts/battlemetrics-rust-tracker.user.js)
     from this repo, copy its full contents
   - Paste into a new Tampermonkey script and save (Ctrl+S)

3. **Visit any Rust server page on BattleMetrics**, for example:
   `https://www.battlemetrics.com/servers/rust/<server-id>`

   A small panel titled **"Rust Player Tracker"** will appear on the right
   side of the page.

4. **Grant notification permission** when your browser prompts you (usually
   on first load). If you miss the prompt, click the lock/info icon next to
   the address bar → Notifications → **Allow**.

That's it — you're ready to track players.

## Troubleshooting

### I'm not getting any notifications at all

Run the .bat to fix notifications being disabled when tabbed into your game 

### Notifications stop while I'm playing Rust (or any fullscreen game)

This is expected Windows/browser behavior, not a script bug. Fullscreen
exclusive apps typically block the OS from rendering notification popups on
top of the game, and Windows' Focus Assist can auto-suppress notifications
whenever it detects a fullscreen app running.

Two ways to fix it:

1. Run [`scripts/fix-notifications-fullscreen.bat`](scripts/fix-notifications-fullscreen.bat)
   **as Administrator**. This attempts to disable Focus Assist's automatic
   "when I'm playing a game" rule. It also prints manual steps to double
   check in Settings, since Microsoft doesn't expose a fully reliable
   registry key for this on every Windows build.

## Disclaimer

This project is not affiliated with or endorsed by BattleMetrics. It works
by reading publicly visible page content client-side in your own browser;
it does not use any private API or authenticated data.
