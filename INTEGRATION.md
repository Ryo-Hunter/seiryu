# 青龍整合指南 v1.2

> **English:** Three ways to integrate — (1) add one line to your CLAUDE.md, (2) tell the AI verbally, or (3) point directly to a skill file. See details below.

## 整合方式

### 方式一：行為規則（推薦）

在你的專案根目錄 `CLAUDE.md` 加入以下規則：

```text
以下規則必須遵守：
- 多步任務（3步以上）開始時 → 先讀 seiryu-v1.2/CLAUDE.md，執行 s5-checkpoint
- 對話結束或 context 快滿時 → 先讀 seiryu-v1.2/CLAUDE.md，執行 s2-legacy
- 使用者提到過去的事 → 先讀 seiryu-v1.2/CLAUDE.md，執行 s3-load
```

寫成「做 X 之前先做 Y」的格式，比單純列出模組路徑更容易讓 AI 在工作中想起來。

### 方式二：口頭告知

不改任何檔案。直接告訴 AI：

```text
我有安裝青龍，在 seiryu-v1.2/ 目錄。請先讀 CLAUDE.md，再依需求讀對應 skill。
```

### 方式三：明確指定技能

如果你知道現在要做什麼，也可以直接指定：

```text
請讀 seiryu-v1.2/skills/s2-legacy.md 幫我存對話遺產
請讀 seiryu-v1.2/skills/s3-load.md 幫我找上次的脈絡
```

---

## 重要：不要把技能條款放進 MEMORY.md

`MEMORY.md` 是 AI 的人格核心，每次對話都會載入。
把技能規則放進去會：

1. 稀釋 AI 的身份種子
2. 即使沒有用到青龍，也會反覆消耗 token
3. 讓人格規則和工具規則混在一起，之後更難維護

青龍 v1.2 的設計原則仍是**懶載入**：不用就不讀，用到才載入。

---

## 安裝步驟

1. 把 `seiryu-v1.2/` 資料夾放到你的專案目錄
2. 用「一行指標」或「口頭告知」整合
3. 如果你有四神總路由檔，也可以把青龍登記在總路由層，而不是塞進人格核心
4. 第一次真正要使用記憶功能時，若 `.seiryu/` 尚不存在，讓 AI 讀 `skills/s6-setup.md`
5. 完成

---

## Git 說明

青龍支援 git，但 **git 不是硬依賴**。

- 有 git：建議 commit，保留記憶演化軌跡
- 沒有 git：照樣可以儲存 profile、dialogue legacy、checkpoint
- 如果 commit 失敗：不要因此放棄核心儲存動作

---

## 與玄武協作

如果同時安裝玄武：

- 對 `.seiryu/` 的寫入，先由玄武執行記憶保護，再由青龍執行實際寫入
- 青龍負責保存與載入，不負責高風險授權
- 青龍仍維持 `on_demand`，不應常駐接管整個對話

---

## 青龍不會做的事

- 不會自動替你執行高風險操作
- 不會搶你 AI 的主導權
- 不會在每次對話都強制讀完整套規則
- 不會把你的資料上傳到任何地方

---

## 建議 fallback

如果 AI 沒有主動找到青龍，請直接說：

```text
請先讀 seiryu-v1.2/CLAUDE.md
```

如果 AI 已經知道要做的事，則直接指定對應 skill，會更穩。

---

## 跟 v1.1 的差別

| | v1.1 | v1.2 |
|--|------|------|
| 整合口徑 | 偏樂觀，假設 AI 會自己找到 | 補上明確 fallback |
| 搜尋說法 | 語意搜尋 | 語義匹配式載入 |
| 壓縮安全 | 壓縮後直接刪原檔 | 先 quarantine + manifest，再延後清理 |
| Git 依賴 | 默認每步 commit | 改成建議但不阻塞 |
| 隱私邊界 | 隱含 | 明寫敏感資訊不自動保存 |
