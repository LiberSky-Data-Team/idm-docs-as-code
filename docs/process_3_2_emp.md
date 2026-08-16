---
title: 次期IDM基盤構築業務
subtitle: 3.2 社員属性・兼務計算 (Lv2)
version: 第1.0版
author: XXXX株式会社
date: 2026年8月16日
---

**改訂履歴**

| 版数 | 種別 | 変更内容 | 改訂ページ | 変更日 | 担当者 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1.0 | 初版 | 新規作成 | 全 | 2026/08/16 | 山田 |
# 3.2 社員属性・兼務計算 (Lv2)
[📄 PDF版をダウンロード](downloads/process_3_2_emp.pdf){ .md-button .md-button--primary target="_blank" }
[📝 Word版をダウンロード](downloads/process_3_2_emp.docx){ .md-button }


## 概要
Bronze層の社員CSVをクレンジングし、兼務ルールを適用してSilver層の社員マスタを生成します。

## データフロー (Mermaid)
```mermaid
flowchart LR
    classDef bronze fill:#e1d5e7,stroke:#9673a6;
    classDef silver fill:#fff2cc,stroke:#d79b00;

    IN[["Bronze: 社員CSV"]]:::bronze
    PROC(("兼務上限<br>チェック"))
    OUT[("Silver: 社員マスタ")]:::silver

    IN --> PROC --> OUT
```

## ビジネスロジック
1. **名寄せ処理**: `Person_ID` をキーに同一人物を統合する。
2. **兼務上限エラー**: 兼務企業数が5社を超えた場合、エラーとする。
