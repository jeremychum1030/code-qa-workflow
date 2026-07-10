---
name: code-qa-workflow
description: 代碼品質保證工作鏈 — 自動檢測並修正 Flutter/HTML/JS/Python 代碼中的錯誤、風格問題、效能瓶頸、安全漏洞和無障礙缺陷。
version: 1.0.0
---

# 代碼品質保證工作鏈

> `/skill code-qa-workflow` → 自動掃描代碼 → 分類問題 → 逐一修正
> 支援: Flutter / HTML / JavaScript / Python / CSS

---

## 5 步檢測流水線

```
🔍 Step 1: 語法檢查  →  編譯錯誤、import 錯誤、類型錯誤
🎨 Step 2: 風格審查  →  命名規範、代碼結構、設計一致性
⚡ Step 3: 效能分析  →  overflow、渲染效能、載入速度
🔒 Step 4: 安全掃描  →  API 密鑰、敏感數據、注入漏洞
♿ Step 5: 無障礙    →  對比度、標籤、語音朗讀
```

---

## Step 1: 語法檢查

**載入 Skills:** `systematic-debugging` + 對應框架 skill

### Flutter
```
問題 → Skill
─────────────────────────────
import 錯誤        → dart-flutter-patterns
類型不匹配         → flutter-dart-code-review
Widget 樹錯誤      → systematic-debugging
狀態管理 bug       → flutter-dart-code-review
路由錯誤           → dart-flutter-patterns
```

### HTML / CSS
```
問題 → Skill
─────────────────────────────
HTML 標籤未閉合    → frontend-patterns
CSS 屬性無效       → frontend-patterns
JS 語法錯誤        → systematic-debugging
資源路徑錯誤       → browser-qa
```

### Python
```
問題 → Skill
─────────────────────────────
語法錯誤           → systematic-debugging
類型錯誤           → python-debugpy
Import 錯誤         → python-debugpy
```

---

## Step 2: 風格審查

**載入 Skills:** 對應框架 code review + coding-standards

### Flutter 風格規則
| 規則 | 檢查方式 |
|------|---------|
| 全局 Theme 統一代碼 | `flutter-dart-code-review` |
| Row overflow 防護 | 檢查所有 Row → 須 Wrap/Expanded |
| const constructor 優化 | `flutter-dart-code-review` |
| import 路徑規範 (../../ → ../) | `dart-flutter-patterns` |
| 命名規範 (camelCase) | `coding-standards` |
| 無 CustomPaint 替代 PNG | 手動檢查 |

### HTML 風格規則
| 規則 | 檢查方式 |
|------|---------|
| 語義化標籤 | `frontend-patterns` |
| CSS 變數統一 | `frontend-patterns` |
| 無 inline style | `frontend-patterns` |
| 手機適配 (viewport) | `browser-qa` |
| 字體一致 (Inter) | `frontend-design-direction` |

### 通用規則
| 規則 | 檢查方式 |
|------|---------|
| 無 console.log 殘留 | `coding-standards` |
| 無 dead code | `codebase-inspection` |
| 註解清晰 | `coding-standards` |
| 檔案命名一致 | `coding-standards` |

---

## Step 3: 效能分析

**載入 Skills:** 對應效能 skill + `browser-qa`

### Flutter 效能
| 問題 | 檢查方式 |
|------|---------|
| build 方法過重 | `flutter-dart-code-review` |
| 列表無懶加載 | `dart-flutter-patterns` |
| 圖片未緩存 | `dart-flutter-patterns` |
| setState 過度重建 | `flutter-dart-code-review` |
| 首屏載入 > 1 秒 | `flutter-dart-code-review` |

### HTML 效能
| 問題 | 檢查方式 |
|------|---------|
| 圖片過大 | `browser-qa` |
| JS 阻塞渲染 | `browser-qa` |
| CSS 過度嵌套 | `frontend-patterns` |
| 無 lazy loading | `frontend-patterns` |
| Google Font 未預載 | `browser-qa` |

### ⚡ Flutter Row Overflow 檢測（#1 Bug）

```
檢查清單:
□ 所有 Row 內文字 → 確認有 Expanded 或 Flexible
□ 所有 chips/tags → 確認用 Wrap(spacing, runSpacing)
□ 所有水平列表 → 確認用 SingleChildScrollView
□ 1.2x TextScaler 下所有頁面正常

修正 pattern:
  Row → Wrap(spacing: 8, runSpacing: 4)
  Row(children: [Text(...), ...]) → Row(children: [Expanded(child: Text(...)), ...])
```

---

## Step 4: 安全掃描

**載入 Skills:** `security-review` `security-scan` `safety-guard`

| 問題 | 檢查方式 |
|------|---------|
| API Key 硬編碼 | `security-scan` |
| 敏感數據明文 | `security-review` |
| XSS 漏洞 (HTML) | `security-scan` |
| SQL 注入 | `security-review` |
| 未加密傳輸 | `security-review` |
| 權限過度請求 | `security-review` |
| HIPAA 合規 (醫療) | `hipaa-compliance` |

---

## Step 5: 無障礙檢查

**載入 Skills:** `accessibility` `frontend-a11y`

| 問題 | 檢查方式 |
|------|---------|
| 顏色對比度 < 4.5:1 | `accessibility` |
| 圖片無 alt 文本 | `frontend-a11y` |
| 按鈕無語義標籤 | `accessibility` |
| 表單無 label | `frontend-a11y` |
| 鍵盤導航失效 | `accessibility` |
| 字級過小 (< 11pt) | `frontend-a11y` |
| TextScaler 1.2x 溢出 | `flutter-dart-code-review` |

---

## 快速使用

| 指令 | 效果 |
|------|------|
| `/skill code-qa-workflow` | 啟動品質檢查流程 |
| 「檢查 Flutter 代碼」 | Step 1-3 Flutter 專用 |
| 「檢查 HTML」 | Step 1-5 HTML 完整掃描 |
| 「只檢查安全」 | Step 4 安全掃描 |
| 「修復 overflow」 | Row overflow 專項修正 |

---

## 按代碼類型速查

### Flutter App
```
語法 → dart-flutter-patterns + flutter-dart-code-review
風格 → coding-standards + flutter-dart-code-review
效能 → flutter-dart-code-review (重點: Row overflow)
安全 → security-scan
無障礙 → accessibility
```

### HTML 原型
```
語法 → browser-qa
風格 → frontend-patterns + frontend-design-direction
效能 → browser-qa
安全 → security-scan
無障礙 → accessibility + frontend-a11y
```

### Python 後端
```
語法 → systematic-debugging + python-debugpy
風格 → coding-standards
效能 → python-patterns
安全 → security-review
```

---

## Jeremy 特定檢查項

- [ ] **Flutter Row overflow** — #1 bug，每個頁面都要檢查
- [ ] **Roche Blue #003D6B** — 無誤用其他藍色
- [ ] **白底** — 無深色背景頁面
- [ ] **Inter 字體** — 無系統默認字體殘留
- [ ] **HK 繁體術語** — 發熱/胸痛/體重下降...
- [ ] **replace_all** — 無 >500 行的批量替換
- [ ] **import 路徑** — ../../ → ../
- [ ] **無 CustomPaint 替代 PNG**
- [ ] **無 console.log / print 殘留**
- [ ] **1.2x TextScaler** — 所有屏幕正常
