# PACMAN

# Parameter Safeguard

パラメータ変更作業の入力ミスをゼロにするための、業務用ブラウザツール。  
1文字の誤入力が重大インシデントにつながる現場課題を、自作ツールで解決した。

[![HTML](https://img.shields.io/badge/HTML-Single_File-E34F26?style=for-the-badge&logo=html5)](https://developer.mozilla.org/ja/docs/Web/HTML)
[![JavaScript](https://img.shields.io/badge/JavaScript-Vanilla-F7DF1E?style=for-the-badge&logo=javascript)](https://developer.mozilla.org/ja/docs/Web/JavaScript)
[![GitHub Pages](https://img.shields.io/badge/GitHub_Pages-Deployed-222222?style=for-the-badge&logo=github)](https://pages.github.com/)

**Live Demo (v13 - ロックあり):** https://amamiya-works.github.io/PACMAN/pacman-v13.html  
**Live Demo (v13-Lite - 制限なし):** https://amamiya-works.github.io/PACMAN/pacman-v13-lite.html  
**Live Demo (v13-Offline - オフライン対応):** https://amamiya-works.github.io/PACMAN/pacman-v13-offline.html

---

## 概要

システムのパラメータ変更作業では、1文字の全角混入や誤入力が担当者の重大なミスにつながる。  
既存のツールや手順書では防ぎきれないこの課題に対し、入力の可視化・物理ブロック・証跡保存を一体化したブラウザツールを自作した。

インストール不要・単一HTMLファイルで動作するため、環境を選ばず即日導入できる。

---

## 主要機能

- **文字ボックス表示:** パラメータ文字列を1文字ずつ番号付きボックスで表示・編集。視認性を高め、桁ズレ・脱字を防止する。
- **全角混入の物理ブロック:** 全角文字の混入をリアルタイム検知し、コピーを物理的にブロック。誤ったパラメータが次工程へ渡ることを防ぐ。
- **変更箇所の視覚化:** 編集された文字を黄色ハイライトで表示し、変更前後の差分を一目で把握できる。
- **作業証跡の保存:** 作業内容を画像としてクリップボードに保存。証跡提出・レビューに即対応できる。

---

## バージョン構成

| バージョン                | 特徴                         | 用途                                 |
| :------------------------ | :--------------------------- | :----------------------------------- |
| `pacman-v13.html`         | 推奨画面サイズ未満でロック   | 本番業務・正式運用向け               |
| `pacman-v13-lite.html`    | 警告バナー表示のみ・制限なし | デモ確認・小画面での検証向け         |
| `pacman-v13-offline.html` | ロックあり・外部CDN不要      | インターネット非接続環境での運用向け |

---

## 技術的な設計判断

### なぜ大画面（1280×600px以上）を前提にしたか

「スクロールさせない」ことが設計の中心にある。

画面内に収まらない情報は、作業者の認知負荷を高め、見落としを生む。  
パラメータ変更という高集中を要する作業において、スクロールはミスの温床になりうる。  
大画面を前提とすることで「画面に収まる情報量 = ミスが減る」という設計意図を担保した。

### 文字ボックスのサイズ設計

WCAG（Webアクセシビリティ標準）の推奨タッチターゲット20pxに安全係数1.5を掛けた30pxを最小サイズとして保証している。  
視認性と操作性を両立させるための数値根拠を持った設計。

### 単一HTMLファイル構成

インストール・環境構築を不要にすることで、導入コストをゼロにした。  
ブラウザさえあれば即日利用できる構成は、現場展開のしやすさを最優先した判断。

---

## 使い方

1. HTMLファイルをブラウザで開く
2. パラメータ文字列を入力欄に貼り付ける
3. 文字ボックスで内容を確認・編集する
4. 全角混入がある場合はリアルタイムで警告が表示される
5. 作業完了後、証跡画像をクリップボードに保存する

---

## AI活用について

設計・開発フェーズで LLM（主に Claude）を以下の用途で使用した。

| 用途           | 具体的な内容                                         |
| :------------- | :--------------------------------------------------- |
| 設計レビュー   | 文字ボックスのサイズ設計・画面サイズ制約の根拠整理   |
| 実装調査       | クリップボードへの画像保存APIの実装パターン確認      |
| コードレビュー | 全角検知ロジックの精度向上と誤検知パターンの洗い出し |

コードの自動生成には留まらず、意思決定の高速化と見落としの防止が主な活用目的。  
実装・動作確認はすべて自分で実施している。

---

## ファイル構成

```
PACMAN/
├── pacman-v13.html         # ロックあり・本番運用版
├── pacman-v13-lite.html    # 警告のみ・制限なし版
└── pacman-v13-offline.html # ロックあり・html2canvasインライン埋め込み・オフライン対応版
```

---

## English Summary

# PACMAN — Parameter Safeguard

A browser-based tool that eliminates input errors in parameter change operations.  
A single mistyped character can trigger a critical incident. PACMAN was built to prevent that.

[![HTML](https://img.shields.io/badge/HTML-Single_File-E34F26?style=for-the-badge&logo=html5)](https://developer.mozilla.org/en-US/docs/Web/HTML)
[![JavaScript](https://img.shields.io/badge/JavaScript-Vanilla-F7DF1E?style=for-the-badge&logo=javascript)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![GitHub Pages](https://img.shields.io/badge/GitHub_Pages-Deployed-222222?style=for-the-badge&logo=github)](https://pages.github.com/)

**Live Demo (v13 - with lock):** https://amamiya-works.github.io/PACMAN/pacman-v13.html  
**Live Demo (v13-Lite - no restrictions):** https://amamiya-works.github.io/PACMAN/pacman-v13-lite.html  
**Live Demo (v13-Offline - no CDN required):** https://amamiya-works.github.io/PACMAN/pacman-v13-offline.html

---

## Overview

Renders each character in a numbered box for precise visual verification, physically blocks full-width input before it reaches the next process, and exports an audit trail image to the clipboard.

No installation required. Runs as a single HTML file in any environment.

---

## Key Design Decisions

- **No scrolling by design.** Requires 1280×600px+ display. Information outside the viewport increases cognitive load and introduces oversight risk.
- **30px minimum character box size.** WCAG 20px touch target recommendation × 1.5 safety factor. Standards-referenced, not arbitrary.
- **Single-file architecture.** Zero setup. Any machine with a browser can run it immediately.
