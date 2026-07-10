# Code QA Workflow

> 代碼品質保證工作鏈 — 5 步自動檢測 + 修正 Flutter / HTML / Python 代碼。
> 已實戰驗證：VIM App 457 → 134 issues (-71%)

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

## 這是什麼？

`code-qa-workflow` 是一個給 AI Agent（Hermes、Claude Code 等）使用的 Skill。載入後自動掃描代碼，分類問題，逐一修正。支援 Flutter、HTML、JavaScript、Python、CSS。

### 實戰數據：VIM App

| 指標 | 修正前 | 修正後 |
|------|--------|--------|
| 總 Issues | **457** | **134** |
| Errors | 0 | 0 |
| Warnings | 56 | ~50 |
| Info | 403 | ~83 |
| 改善率 | — | **-71%** |

## 5 步檢測流水線

```
🔍 Step 1: 語法檢查 ─→ 編譯錯誤、import 錯誤、類型錯誤
🎨 Step 2: 風格審查 ─→ 命名規範、代碼結構、設計一致性
⚡ Step 3: 效能分析 ─→ Row overflow、渲染效能、載入速度
🔒 Step 4: 安全掃描 ─→ API 密鑰、敏感數據、注入漏洞
♿ Step 5: 無障礙   ─→ 對比度、標籤、語音朗讀
```

## 按代碼類型自動選用 Skills

| 類型 | 語法 | 風格 | 效能 | 安全 | 無障礙 |
|------|------|------|------|------|------|
| **Flutter** | `dart-flutter-patterns` | `flutter-dart-code-review` | Row overflow 專檢 | `security-scan` | `accessibility` |
| **HTML** | `browser-qa` | `frontend-patterns` | `browser-qa` | `security-scan` | `frontend-a11y` |
| **Python** | `systematic-debugging` | `coding-standards` | `python-patterns` | `security-review` | — |

## 特色

- 🔍 **全套 QA** — 語法 + 風格 + 效能 + 安全 + 無障礙，一站完成
- ⚡ **Flutter Row Overflow 專檢** — #1 runtime bug 自動檢測 + 修正模板
- 🔒 **安全掃描** — API Key 硬編碼、敏感數據洩露、HIPAA 合規
- ♿ **無障礙** — 對比度、標籤、TextScaler 1.2x 測試
- 📊 **實戰數據** — VIM App 457→134 issues 的真實改善

## 調用的核心 Skills

- `systematic-debugging` — 系統性調試
- `flutter-dart-code-review` — Flutter 代碼審查
- `dart-flutter-patterns` — Flutter 架構模式
- `coding-standards` — 代碼風格規範
- `security-scan` / `security-review` — 安全掃描
- `accessibility` / `frontend-a11y` — 無障礙檢查
- `browser-qa` — 瀏覽器 QA
- `frontend-patterns` — 前端模式

## 安裝

### Hermes Agent

```bash
git clone https://github.com/jeremychum1030/code-qa-workflow.git ~/.hermes/skills/code-qa-workflow
```

或在對話中載入：
```
/skill code-qa-workflow
```

## 使用方法

| 指令 | 效果 |
|------|------|
| `/skill code-qa-workflow` | 啟動完整 QA 流程 |
| 「檢查 Flutter 代碼」 | Step 1-3 Flutter 專用 |
| 「檢查 HTML」 | Step 1-5 HTML 完整掃描 |
| 「只檢查安全」 | Step 4 安全掃描 |
| 「修復 overflow」 | Row overflow 專項修正 |

## License

MIT — 自由使用、修改、分發。

---

*Made with ❤️ by Jeremy Chum*
