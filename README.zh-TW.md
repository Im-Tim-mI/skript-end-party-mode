# 派對遊戲系統（末地派對模式）

[English](README.md) | **繁體中文**

把末地變成限時打怪派對：每位玩家身邊定時刷怪，並自動開啟死亡不掉落。比賽模式還會依擊殺計分、顯示排行榜，並頒發獎盃方塊給前三名。

> 本儲存庫包含同一個腳本的兩個版本：**繁體中文（zh-TW）** 是作者伺服器實際使用的原始版本；**English** 為完整英文翻譯版（指令、訊息與變數名稱皆為英文），功能相同。

## 功能特色

- 三種難度（簡單／普通／困難），怪物種類、數量與 Boss 機率（守望者、凋零、末影龍）各不相同
- 活動期間自動開啟末地死亡不掉落，結束後關閉；腳本載入時也會檢查，避免崩潰後卡在開啟狀態
- 比賽模式：依怪物種類計分、動作列即時顯示分數、每 5 波顯示排行，結束時公布前 10 名
- 前三名頒發具名的金塊／鐵塊／銅塊紀念品；離線得主會在下次登入時自動補發
- 開始、剩一分鐘與結束時皆有標題、音效與廣播
- 派對進行中玩家可用 `/前往派對現場` 傳送過去

## 需求

- [Paper](https://papermc.io/) 伺服器（開發環境 Paper 26.2 / Minecraft 26.2）
- [Skript](https://github.com/SkriptLang/Skript)（開發環境 2.16.2）

## 安裝

1. 先安裝[需求](#需求)中列出的插件。
2. 下載**其中一個**版本：

   | 版本 | 檔案 |
   |---|---|
   | 繁體中文（原始版本） | [`zh-TW/派對遊戲系統.sk`](zh-TW/%E6%B4%BE%E5%B0%8D%E9%81%8A%E6%88%B2%E7%B3%BB%E7%B5%B1.sk) |
   | English（英文） | [`en/end-party-mode.sk`](en/end-party-mode.sk) |

3. 把 `.sk` 檔案放進伺服器的 `plugins/Skript/scripts/`。
4. 執行 `/sk reload 派對遊戲系統`（請換成你放入的檔名），或重新啟動伺服器。

> [!IMPORTANT]
> **只能安裝其中一個版本。** 兩個版本是同一個腳本的不同語言，同時載入會互相衝突或重複執行。

## 指令

| 指令（中文版） | 英文版 | 說明 | 權限 |
|---|---|---|---|
| `/派對開始 [簡單\|普通\|困難] [分鐘] [間隔秒]`<br>別名：`/partystart` | `/partystart [easy\|normal\|hard] [minutes] [interval]` | 開始一般派對（不計分；預設：普通、30 分鐘、10 秒） | OP |
| `/派對開始-比賽 [難度] [分鐘] [間隔秒]`<br>別名：`/partycontest` | `/partycontest [difficulty] [minutes] [interval]` | 開始比賽模式（計分） | OP |
| `/派對刷怪 [難度] [數量]`<br>別名：`/partyspawn` | `/partyspawn [difficulty] [amount]` | 手動刷一波怪（最多 100 隻） | OP |
| `/派對停止`<br>別名：`/partystop` | `/partystop` | 停止派對（比賽模式會結算並頒獎） | OP |
| `/派對清除`<br>別名：`/partyclear` | `/partyclear` | 清除末地所有非玩家實體 | OP |
| `/派對狀態`<br>別名：`/partystatus` | `/partystatus` | 查看派對狀態 | OP |
| `/派對排行`<br>別名：`/partyrank` | `/partyrank` | 顯示比賽排行榜 | OP |
| `/前往派對現場`<br>別名：`/partygo`、`/派對現場` | `/partygo` | 傳送到派對現場（僅派對期間） | 所有人 |
| `/我的分數`<br>別名：`/myscore` | `/myscore` | 查看比賽中的個人分數 | 所有人 |
| `/派對`<br>別名：`/party` | `/partyhelp`<br>別名：`/party` | 顯示說明 | 所有人 |

## 設定

- 最上方的 `options:`：`party_world` 與 `party_tp_x/y/z`（`/前往派對現場` 的傳送座標）。
- 怪物清單與分數在兩個 `on script load` 區塊；各難度的機率設定在各指令中。

## 注意事項

- ⚠️ `/派對清除` 與活動結束時的自動清除會移除 `world_the_end` 內**所有非玩家實體**，包含物品展示框、盔甲座、寵物、村民、礦車與掉落物。
- 除了 `party_world` 之外，程式中還有多處直接寫死 `world_the_end`；若你的末地世界名稱不同，請全部取代。
- 使用新版 Minecraft（例如 26.x）的遊戲規則名稱 `keep_inventory`；舊版請改成 `keepInventory`。
- 比賽資料與待補發獎勵存放在 `{party.*}` 變數，兩個版本共用。

## 相關專案

- [skript-weekly-end-reset](https://github.com/Im-Tim-mI/skript-weekly-end-reset)－末地每週重置腳本

## 授權

**MIT + Commons Clause**，完整條款請見 [LICENSE](LICENSE)。

- ✅ 可自由使用、複製、修改與分享本腳本。
- ✅ 本授權明確允許在收費或營利的 Minecraft 伺服器上安裝與運行本插件（含修改版）。
- ❌ 禁止的僅限於直接或間接販售本插件本體、修改版本，或以付費方式取得其檔案或原始碼。

Copyright (c) 2026 廷廷小教室、廷廷的家（Tim945）
