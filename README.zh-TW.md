# 實驗代理人 (Experiment Agent)

![Version](https://img.shields.io/badge/version-1.0-blue)
![License](https://img.shields.io/badge/license-CC--BY--NC--4.0-green)

Claude Code 技能：執行、監控、解讀、驗證學術研究實驗。

## 功能

- **執行程式碼實驗** — 執行腳本（Python、R 等），即時監控 stall/crash，收集結果
- **管理人工研究** — 規劃 protocol、檢查 IRB 倫理、追蹤資料收集進度
- **統計解讀** — 解讀 p-value、效果量、信賴區間；檢查 11 種統計謬誤（Simpson's Paradox、存活者偏誤等）
- **驗證重現性** — 重新執行實驗並比對結果

## 為什麼需要

Lu et al.（2026, *Nature*）展示了自主 AI 研究的實驗進度管理器。本技能將同樣的執行與監控能力帶入人類參與的學術工作流程——不承擔全自動化的風險。

## 模式

| 模式 | 功能 |
|------|------|
| `run` | 執行程式碼 + 監控 process |
| `manage` | 規劃 + 追蹤人工研究 |
| `validate` | 統計解讀 + 重現性驗證 |
| `plan` | Socratic 對話設計實驗 |

## 快速開始

1. Clone 本 repo 到你的專案或 `.claude/skills/`
2. 啟動 Claude Code session
3. 試試：「跑我的分析：`Rscript analysis.R`」

## ARS 相容性

本技能可獨立使用，也可選擇性整合 [Academic Research Skills (ARS)](https://github.com/Imbad0202/academic-research-skills)：

- 讀取 ARS Stage 1 輸出（RQ Brief、Methodology Blueprint）預填實驗設計
- 產出符合 Material Passport 的輸出供 ARS Stage 2 使用
- ARS 不需要任何修改——使用者手動銜接

## 安全機制

- 只執行你指定的命令——從不自動生成或修改你的程式碼
- 從不自動重試 crash 的實驗
- 從不接觸原始參與者資料
- 統計解讀是描述性的，不代替你下結論
- 完整清單見 SKILL.md 安全規則

## 授權

CC-BY-NC 4.0

## 作者

吳承翊 (Cheng-I Wu)

---

## 變更紀錄

見 [CHANGELOG.md](CHANGELOG.md)
