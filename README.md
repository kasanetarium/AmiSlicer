> ⚠️ **Alpha Release (v0.01)** — This software is in early development.  
> ⚠️ **アルファ版 (v0.01)** — 本ソフトウェアは開発段階のアルファ版です。

---

## Overview

AmiSlicer is a **generative slicer** that converts STL models into G-code with sinusoidal perimeter deformation.  
It creates unique woven-like surface structures by alternating phase between layers.

---

## 概要

AmiSlicerは、STLモデルの外周にサイン波変形を加えたG-codeを生成する実験的スライサーです。  
層ごとに位相を反転させることで、編み込まれたような構造を生成します。

---

## Features / 主な機能

- STL slicing / STLスライス
- Sinusoidal perimeter modulation / 外周へのサイン波変形
- Alternating phase between layers / レイヤー間の位相反転（アミアミ構造）
- Optional Z-direction modulation / Z方向の波変形
- Self-intersection detection and correction / 自己交差検出・修正
- 2D / 3D preview / 2D・3Dプレビュー
- G-code export / G-code出力
- JSON-based settings / 設定の保存・読み込み

---

## Concept

This tool does **not aim for optimization or strength improvement**.  
Instead, it explores:

> **Structure as expression**

---

## コンセプト

本ツールは強度最適化などを目的としたものではなく、  
**構造そのものを表現として扱うこと**を目的としています。

---

## Getting Started / 基本の流れ

1. Open STL  
2. Adjust orientation  
3. Configure printer settings  
4. Configure wave parameters  
5. Preview (2D / 3D)  
6. Fix self-intersections if needed  
7. Export G-code  
8. Print  

---

## Documentation / 詳細マニュアル

- English Manual: [docs/manual_en.md](docs/manual_en.md)
- 日本語マニュアル: [docs/manual_ja.md](docs/manual_ja.md)

---

## ⚠️ Safety Notice / 安全に関する注意

- This software is experimental and may contain unexpected behavior.  
- Generated G-code controls heaters and motors — use with caution.  
- Always monitor your printer during operation.  
- Perform test prints before actual use.  
- The author is not responsible for any damage caused by this software.  

---

## License

MIT License

---

<p align="center">
<strong>AmiSlicer v0.01 Alpha</strong><br>
Author / 製作者: Yosuke Hori / kasanetarium
</p>
