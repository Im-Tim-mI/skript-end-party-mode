# End Party Mode

**English** | [繁體中文](README.zh-TW.md)

Turns The End into a timed mob-fighting party: waves of mobs spawn around every player and keep-inventory is switched on. The optional contest mode scores kills, shows a leaderboard and awards trophy blocks to the top 3.

> This repository has two editions of the same script: **繁體中文 (zh-TW)** is the original used on the author's Traditional Chinese server, and **English** is a full translation (commands, messages and variable names) with the same features.

## Features

- Three difficulties (easy / normal / hard) with different mob pools, spawn counts and boss chances (Warden, Wither, Ender Dragon)
- Keep-inventory is switched on in The End during the event and safely off afterwards - also on script load after a crash
- Contest mode: points per mob type, live action-bar score, leaderboard every 5 waves and a top-10 ranking at the end
- Awards for the top 3 (named gold / iron / copper blocks with lore); offline winners get them on their next login
- Titles, sounds and broadcasts for the start, the one-minute warning and the end
- `/partygo` teleports players to the party while it is running

## Requirements

- [Paper](https://papermc.io/) server (developed on Paper 26.2 / Minecraft 26.2)
- [Skript](https://github.com/SkriptLang/Skript) (developed on 2.16.2)

## Installation

1. Install the plugins listed under [Requirements](#requirements).
2. Download **one** edition:

   | Edition | File(s) |
   |---|---|
   | English | [`en/end-party-mode.sk`](en/end-party-mode.sk) |
   | 繁體中文 (original) | [`zh-TW/派對遊戲系統.sk`](zh-TW/%E6%B4%BE%E5%B0%8D%E9%81%8A%E6%88%B2%E7%B3%BB%E7%B5%B1.sk) |

3. Copy the `.sk` file(s) into `plugins/Skript/scripts/` on your server.
4. Run `/sk reload end-party-mode` (use the file name you copied) or restart the server.

> [!IMPORTANT]
> Install **only one** edition. Both editions are the same script in different languages - loading both makes them clash or run twice.

## Commands

| Command (English edition) | zh-TW edition | Description | Permission |
|---|---|---|---|
| `/partystart [easy\|normal\|hard] [minutes] [interval]` | `/派對開始 [簡單\|普通\|困難] [分鐘] [間隔秒]`<br>aliases: `/partystart` | Start a timed party without scoring (defaults: normal, 30 min, 10 s) | OP |
| `/partycontest [difficulty] [minutes] [interval]` | `/派對開始-比賽 [難度] [分鐘] [間隔秒]`<br>aliases: `/partycontest` | Start a scored contest | OP |
| `/partyspawn [difficulty] [amount]` | `/派對刷怪 [難度] [數量]`<br>aliases: `/partyspawn` | Spawn a wave manually (max 100) | OP |
| `/partystop` | `/派對停止`<br>aliases: `/partystop` | Stop the party (a contest is settled and awarded) | OP |
| `/partyclear` | `/派對清除`<br>aliases: `/partyclear` | Remove every non-player entity in The End | OP |
| `/partystatus` | `/派對狀態`<br>aliases: `/partystatus` | Show the party status | OP |
| `/partyrank` | `/派對排行`<br>aliases: `/partyrank` | Show the contest leaderboard | OP |
| `/partygo` | `/前往派對現場`<br>aliases: `/partygo`, `/派對現場` | Teleport to the party (only while it runs) | everyone |
| `/myscore` | `/我的分數`<br>aliases: `/myscore` | Your score in the current contest | everyone |
| `/partyhelp`<br>alias: `/party` | `/派對`<br>aliases: `/party` | Show help | everyone |

## Configuration

- `options:` at the top: `party_world` and `party_tp_x/y/z` (where `/partygo` sends players).
- Mob pools and points are in the two `on script load` blocks; difficulty chances are set in each command.

## Notes

- ⚠️ `/partyclear` and the automatic cleanup at the end remove **every non-player entity** in `world_the_end` - including item frames, armor stands, pets, villagers, minecarts and dropped items.
- `world_the_end` is also hard-coded in several places besides `party_world`; search and replace it if your End world has another name.
- Uses the game rule name `keep_inventory` of newer Minecraft versions (e.g. 26.x). On older versions replace it with `keepInventory`.
- Contest data and pending rewards are stored in `{party.*}` variables, the same in both editions.

## Related projects

- [skript-weekly-end-reset](https://github.com/Im-Tim-mI/skript-weekly-end-reset) - Weekly End Reset

## License

**MIT + Commons Clause** - see [LICENSE](LICENSE) for the full text.

- ✅ You may use, copy, modify and share this script.
- ✅ You **may** install and run it - including modified versions - on Minecraft servers that charge money or are run for profit.
- ❌ You may **not** sell the script itself or modified versions of it, directly or indirectly, or require payment to obtain its files or source code.

Copyright (c) 2026 廷廷小教室、廷廷的家（Tim945）
