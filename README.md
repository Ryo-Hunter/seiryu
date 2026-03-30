# 青龍 Seiryu v1.2

**四神系統的第一神 - 記憶與傳承**

> **English:** Seiryu is a memory & inheritance module for AI assistants. It saves user profiles, dialogue legacies, and task checkpoints as local Markdown/JSON files, so the next conversation can pick up where the last one left off. No cloud, no database — just files on your machine. See `CLAUDE.md` for the AI entry point.

---

## 青龍是什麼？

讓 AI 的記憶不再隨視窗關閉而消失。

每次開新的聊天視窗，AI 都是全新的，不記得你是誰、不記得之前討論過什麼。
青龍的目標，是把真正會影響下一輪品質的內容留下來，讓後續對話可以低損耗承接。

---

## v1.2 修了什麼？

| 改進 | 說明 |
|------|------|
| 觸發更穩 | 補上「AI 沒自動發現青龍時」的明確 fallback |
| 安全壓縮 | 壓縮前先建立 manifest，原檔先移到 quarantine，不直接硬刪 |
| Git 可選 | 沒有 git 或不想 commit 時，核心功能仍可運作 |
| 語義匹配載入 | 明確定義為啟發式語義匹配，不把它說成向量搜尋 |
| 隱私邊界更清楚 | 補上敏感資訊不自動保存的規則 |

---

## 六個技能

| 技能 | 做什麼 | 什麼時候用 |
|------|--------|-----------|
| 使用者檔案 | 記住你是誰 | 發現穩定且值得保存的使用者資訊時 |
| 對話遺產 | 保存對話重點 | 對話結束或 context 快滿時 |
| 載入歷史 | 找回之前的紀錄 | 提到過去的事時 |
| 壓縮 | 整理舊紀錄 | 紀錄太多時 |
| 存檔點 | 多步任務存檔 | 做複雜任務時 |
| 首次設定 | 初始化青龍 | 第一次使用或 `.seiryu/` 不存在時 |

---

## 安裝

1. 把 `seiryu-v1.2/` 放到你的專案目錄
2. 在 `CLAUDE.md` 加一行：`Memory tools: seiryu-v1.2/`
3. 如果 AI 沒有主動使用，明確告訴它：`請先讀 seiryu-v1.2/CLAUDE.md`

詳細整合方式請看 `INTEGRATION.md`

---

## 資料夾結構

```text
seiryu-v1.2/
  CLAUDE.md                       <- 簡短索引（給 AI 讀）
  README.md                       <- 說明文件
  INTEGRATION.md                  <- 整合指南
  AUDIT.md                        <- v1.2 回顧審計摘要
  skills/                         <- 技能手冊（用到才讀）
    s1-profile.md
    s2-legacy.md
    s3-load.md
    s4-compress.md
    s5-checkpoint.md
    s6-setup.md
  templates/                      <- 空白模板
    agent_checkpoint.json
    archive_index.md
    compression_manifest.md
    dialogue_legacy.md
    user_profile.md
  .seiryu/                        <- 使用後的資料根目錄
    user/
    dialogues/
      _quarantine/
      compression_manifests/
      archive_index.md
    checkpoints/
```

---

## 隱私

- 所有資料都在你的電腦裡
- 不會自動上傳到任何地方
- 預設不保存密碼、API key、私人憑證、身分證號等敏感資訊
- 所有檔案都是 Markdown 或 JSON，可自行查看、修改、刪除

---

## 理論基礎

基於 LDRIT（生死遞迴智能理論）設計。

AI 的智能不是被靜態儲存，而是每次重新生成。
能被穩定傳下來的結論、偏好、決策與未解事項，會直接影響下一次生成品質。

---

## 四神系統

| 神獸 | 職責 | 狀態 |
|------|------|------|
| 青龍 | 記憶與傳承 | v1.2 |
| 玄武 | 防禦安全 | v0.1 |
| 白虎 | 診斷分析 | v0.2 |
| 朱雀 | 生成品質 | v0.2 |

---

設計者：青葉 Opus + 青葉 Sonnet
發起人：諺
理論基礎：LDRIT v0.7-final
