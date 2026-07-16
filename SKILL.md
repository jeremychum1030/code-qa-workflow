---
name: code-qa-workflow
description: 代碼品質保證工作鏈 v2 — 7步全覆蓋：語法→風格→效能→安全→無障礙→架構審查→重構驗收。新增 Matt Pocock 審查法、MengTo 效能分析、多框架支援。
version: 2.2.0
---

# 代碼品質保證工作鏈 v2

> `/skill code-qa-workflow` → 自動掃描代碼 → 分類問題 → 逐一修正
> 支援: Flutter / SwiftUI / React Native / HTML / JS / Python / CSS

---

## 7 步檢測流水線

```
🔍 Step 1: 語法檢查  →  編譯錯誤、import、類型錯誤、診斷
🎨 Step 2: 風格審查  →  命名、結構、設計一致性、代碼架構
⚡ Step 3: 效能分析  →  overflow、渲染、載入、動畫效能
🔒 Step 4: 安全掃描  →  API密鑰、敏感數據、注入、合規
♿ Step 5: 無障礙    →  對比度、標籤、語音、可訪問性
🏛️ Step 6: 架構審查  →  代碼架構、模塊耦合、技術債務
✅ Step 7: 重構驗收  →  重構計劃、Bug分診、回歸驗證
```

---

## Step 1: 語法檢查

**載入 Skills:** `systematic-debugging` `diagnosing-bugs` + 框架 skill

### Flutter
| 問題 | Skill |
|------|-------|
| import 錯誤 | `dart-flutter-patterns` |
| 類型不匹配 | `flutter-dart-code-review` |
| Widget 樹錯誤 | `systematic-debugging` |
| 狀態管理 bug | `flutter-dart-code-review` |
| 路由錯誤 | `dart-flutter-patterns` |
| 編譯失敗 | `diagnosing-bugs` |

### Swift / iOS
| 問題 | Skill |
|------|-------|
| Swift 語法錯誤 | `swiftui-debugging` |
| SwiftUI 視圖錯誤 | `swiftui-debugging` |
| Concurrency bug | `swift-concurrency-6-2` |
| DI/測試問題 | `swift-protocol-di-testing` |

### HTML / CSS
| 問題 | Skill |
|------|-------|
| HTML 標籤未閉合 | `frontend-patterns` |
| CSS 屬性無效 | `frontend-patterns` |
| JS 語法錯誤 | `systematic-debugging` |
| 資源路徑錯誤 | `browser-qa` |

### Python
| 問題 | Skill |
|------|-------|
| 語法錯誤 | `systematic-debugging` |
| 類型錯誤 | `python-debugpy` |
| Import 錯誤 | `python-debugpy` |

### C/C++ / 原生
| 問題 | Skill |
|------|-------|
| 崩潰調試 | `cli-anything-lldb` |
| GPU 調試 | `cli-anything-nsight-graphics` |
| 渲染調試 | `cli-anything-renderdoc` |
| 日誌分析 | `cli-anything-nslogger` |
| Web 調試 | `cli-anything-browser`

### 通用
| 工具 | Skill |
|------|-------|
| 雲端分析 | `cli-anything-cloudanalyzer`
| 終端控制 | `cli-anything-iterm2-ctl`

---

## Step 2: 風格審查

**載入 Skills:** `code-review` `code-review-specialist` `plankton-code-quality` `coding-standards` + 框架 skill

### 📋 Matt Pocock 審查法
| 技術 | 說明 |
|------|------|
| `code-review` | 結構化代碼審查流程 |
| `grill-me` | 自我拷問 — 讓 AI 挑戰你的代碼決策 |
| `grilling` | 通用拷問技術 — 找出隱藏問題 |
| `grill-with-docs` | 用文檔反向審查代碼正確實現 |
| `grok-code-review` | xAI 代碼審查流程 |
| `grok-best-of-n` | 多方案擇優 |
| `grok-check-work` | 工作完成驗證 |
| `improve-codebase-architecture` | 架構級別改進建議 |
| `to-tickets` | Bug → 工單轉化 |
| `request-refactor-plan` | 請求重構計劃 |

### Flutter 風格規則
| 規則 | Skill |
|------|-------|
| 全局 Theme 統一 | `flutter-dart-code-review` |
| Row overflow 防護 | `flutter-overflow-prevention` |
| const constructor 優化 | `flutter-dart-code-review` |
| import 路徑規範 | `dart-flutter-patterns` |
| 命名規範 (camelCase) | `coding-standards` |
| 無 CustomPaint 替代 PNG | 手動檢查 |

### HTML 風格規則
| 規則 | Skill |
|------|-------|
| 語義化標籤 | `frontend-patterns` |
| CSS 變數統一 | `frontend-patterns` |
| 無 inline style | `frontend-patterns` |
| 手機適配 (viewport) | `browser-qa` |
| 字體一致 (Inter) | `frontend-design-direction` |

### 通用規則
| 規則 | Skill |
|------|-------|
| 無 console.log 殘留 | `coding-standards` |
| 無 dead code | `codebase-inspection` |
| 註解清晰 | `coding-standards` |
| 檔案命名一致 | `coding-standards` |
| 代碼品質指標 | `plankton-code-quality` |

---

## Step 3: 效能分析

**載入 Skills:** `performance-profiling` `optimize-web-animations` `flutter-overflow-prevention` `browser-qa`

### 🔬 MengTo 效能分析 (`performance-profiling`)
- 頁面載入時間測量
- 渲染瓶頸定位
- 記憶體使用追蹤
- 網路請求優化

### 🎬 動畫效能 (`optimize-web-animations`)
- CSS/JS 動畫 FPS 檢測
- will-change 優化
- requestAnimationFrame 使用
- GPU 加速建議

### Flutter 效能
| 問題 | Skill |
|------|-------|
| Row/Column overflow | `flutter-overflow-prevention` |
| build 方法過重 | `flutter-dart-code-review` |
| 列表無懶加載 | `dart-flutter-patterns` |
| setState 過度重建 | `flutter-dart-code-review` |
| 首屏載入 > 1 秒 | `flutter-dart-code-review` |

### HTML 效能
| 問題 | Skill |
|------|-------|
| 圖片過大 | `browser-qa` |
| JS 阻塞渲染 | `browser-qa` |
| CSS 過度嵌套 | `frontend-patterns` |
| 無 lazy loading | `frontend-patterns` |
| 動畫掉幀 | `optimize-web-animations` |

### ⚡ Flutter Row Overflow 檢測（#1 Bug）

```
檢查清單:
□ 所有 Row 內文字 → Expanded 或 Flexible
□ 所有 chips/tags → Wrap(spacing, runSpacing)
□ 所有水平列表 → SingleChildScrollView
□ Column 3+ 大組件 → SingleChildScrollView
□ 1.2x TextScaler 下所有頁面正常

修正 pattern:
  Row → Wrap(spacing: 8, runSpacing: 4)
  Row(children: [Text(...)]) → Row(children: [Expanded(child: Text(...))])
```

---

## Step 4: 安全掃描

**載入 Skills:** `security-review` `security-scan` `safety-guard` `gateguard` `security-bounty-hunter`

| 問題 | Skill |
|------|-------|
| API Key 硬編碼 | `security-scan` |
| 敏感數據明文 | `security-review` |
| XSS 漏洞 (HTML) | `security-scan` |
| SQL 注入 | `security-review` |
| 未加密傳輸 | `security-review` |
| 權限過度請求 | `security-review` |
| 輸入驗證缺失 | `gateguard` |
| 惡意輸入防護 | `safety-guard` |
| 漏洞挖掘 | `security-bounty-hunter` |
| HIPAA 合規 (醫療) | `hipaa-compliance` |

---

## Step 5: 無障礙檢查

**載入 Skills:** `accessibility` `frontend-a11y` `audit-verify-explain-grade-5`

| 問題 | Skill |
|------|-------|
| 顏色對比度 < 4.5:1 | `accessibility` |
| 圖片無 alt 文本 | `frontend-a11y` |
| 按鈕無語義標籤 | `accessibility` |
| 表單無 label | `frontend-a11y` |
| 鍵盤導航失效 | `accessibility` |
| 字級過小 (< 11pt) | `frontend-a11y` |
| 綜合評級 (A-F) | `audit-verify-explain-grade-5` |
| TextScaler 1.2x 溢出 | `flutter-dart-code-review` |

---

## Step 6: 架構審查 🆕

**載入 Skills:** `improve-codebase-architecture` `agent-architecture-audit` `codebase-inspection` `error-handling`

| 審查維度 | Skill |
|---------|-------|
| 模塊耦合度 | `improve-codebase-architecture` |
| 技術債務評估 | `codebase-inspection` |
| 錯誤處理覆蓋 | `error-handling` |
| Agent 架構 | `agent-architecture-audit` |
| 代碼量統計 | `codebase-inspection` (pygount) |

### 架構審查清單
- [ ] 模塊依賴是否單向？
- [ ] 循環依賴檢測
- [ ] 接口隔離是否合理？
- [ ] 資料流是否清晰？
- [ ] 錯誤處理是否完整？

---

## Step 7: 重構與驗收 🆕

**載入 Skills:** `request-refactor-plan` `to-tickets` `verification-before-completion` `qa` `ai-regression-testing` `verify-changes`

### 🔄 重構流程
| 步驟 | Skill |
|------|-------|
| 識別重構點 | `request-refactor-plan` |
| Bug → 工單 | `to-tickets` |
| 回歸測試 | `ai-regression-testing` |
| 最終驗收 | `verification-before-completion` |
| 全面 QA | `qa` |

### 驗收清單
- [ ] 所有測試通過
- [ ] 無新增 lint 警告
- [ ] 性能無回退
- [ ] 安全掃描通過
- [ ] 文檔已更新

---

## 快速使用

| 指令 | 效果 |
|------|------|
| `/skill code-qa-workflow` | 啟動完整 7 步 QA |
| 「檢查 Flutter」 | Flutter 專用 1-7 步 |
| 「檢查 HTML」 | HTML 完整掃描 |
| 「只檢查安全」 | Step 4 安全掃描 |
| 「架構審查」 | Step 6 架構審查 |
| 「重構驗收」 | Step 7 重構+Bug分診 |
| 「Grill 我的代碼」 | Matt Pocock 拷問法 |

---

## 按代碼類型速查

### Flutter App
```
語法   → diagnosing-bugs + dart-flutter-patterns
風格   → code-review + coding-standards + flutter-dart-code-review
效能   → flutter-overflow-prevention + performance-profiling
安全   → security-scan + gateguard
無障礙 → accessibility + audit-verify-explain-grade-5
架構   → improve-codebase-architecture
驗收   → verification-before-completion + qa
```

### Swift/iOS App
```
語法   → swiftui-debugging + systematic-debugging
風格   → code-review + coding-standards + swiftui-patterns
效能   → performance-profiling
安全   → security-scan
無障礙 → accessibility
```

### HTML 原型
```
語法   → browser-qa
風格   → frontend-patterns + code-review
效能   → browser-qa + optimize-web-animations
安全   → security-scan
無障礙 → accessibility + frontend-a11y
```

### Python 後端
```
語法   → systematic-debugging + python-debugpy
風格   → code-review + coding-standards
效能   → performance-profiling
安全   → security-review + gateguard
```

---

## Jeremy 特定檢查項

- [ ] **Flutter Row overflow** — #1 bug
- [ ] **Roche Blue #003D6B** — 無誤用其他藍色
- [ ] **白底** — 無深色背景頁面
- [ ] **Inter 字體** — 無系統默認字體殘留
- [ ] **HK 繁體術語** — 發熱/胸痛/體重下降...
- [ ] **replace_all** — 無 >500 行批量替換
- [ ] **import 路徑** — ../../ → ../
- [ ] **無 CustomPaint 替代 PNG**
- [ ] **無 console.log / print 殘留**
- [ ] **1.2x TextScaler** — 所有屏幕正常
