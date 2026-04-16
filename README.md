# AmiSlicer

> ⚠️ **Alpha Release (v0.01)** — This software is in early development.  
> ⚠️ **アルファ版 (v0.01)** — 本ソフトウェアは開発段階のアルファ版です。

---

## Overview

AmiSlicer is a **generative slicer** that converts STL models into G-code with sinusoidal perimeter deformation.  
It creates unique woven-like surface structures by alternating phase between layers.

<img src="docs/img/soroban_git.jpg" width="25%" alt="soroban">

---

## 概要

AmiSlicerは、STLモデルの外周にサイン波変形を加えたG-codeを生成する実験的スライサーです。  
層ごとに位相を反転させることで、編み込まれたような構造を生成します。

<img src="docs/UI_git.jpg" width="50%" alt="UI">

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

本ツールは強度最適化などを目的としたものではなく、  
**構造そのものを表現として扱うこと**を目的としています。

---

## Getting Started / 基本の流れ

1. Open an STL file  
2. Adjust the model orientation  
3. Configure machine and print settings  
4. Configure wave parameters  
5. Check the result in 2D / 3D preview  
6. Fix self-intersections if necessary  
7. Export G-code  
8. Print on your 3D printer  


1. STLを読み込む  
2. モデルの向きを調整する  
3. 3Dプリンタ設定と印刷設定を入力する  
4. 波のパラメータを設定する  
5. 2D / 3Dプレビューで確認する  
6. 必要に応じて自己交差を修正する  
7. G-codeを保存する  
8. 3Dプリンタで造形する  

---

## Documentation / 詳細マニュアル

- English Manual: [docs/manual_en.md](docs/manual_en.md)
- 日本語マニュアル: [docs/manual_ja.md](docs/manual_ja.md)

---

## ⚠️ Notes / 注意事項

- Shapes with branching cross-sections are not supported.
- Shapes with internal structures that produce multiple contours in a slice, such as donut-like geometry, are not supported.
- To create stable woven structures, parameters such as nozzle temperature, print speed, and extrusion amount must be carefully adjusted according to the target geometry, nozzle diameter, filament material, and the environment where the 3D printer is installed.


- 枝分かれするような形状（断面が複数になる形状）には対応していません。
- 内側にも構造がある形状（ドーナツのような形状）には対応していません。
- 編み込まれた形状を作るには、製作したい造形物の形状、ノズル径、フィラメント材料、3Dプリンタが設置されている環境に合わせて、ノズル温度、ワーク速度、押し出し量などのパラメータを細かく調整する必要があります。

---

## ⚠️ Safety Notice / 安全に関する注意

- This software is experimental and may contain unexpected behavior or bugs.
- This software generates G-code that controls 3D printer heaters and motors. Please use it with caution.
- Do not leave your 3D printer unattended while printing.
- When using this software for the first time, perform a test print to confirm that temperature and motion are correct.
- After printing, make sure that the nozzle and heat bed have cooled down properly and that the print has finished safely.
- The author is not responsible for any damage or loss caused by the use of this software.


- 本ソフトウェアは実験的なソフトウェアであり、予期しない動作やバグを含む可能性があります。
- 本ソフトウェアは3Dプリンタのヒーターやモーターを制御するG-codeを生成します。十分注意して使用してください。
- 印刷中は3Dプリンタから離れないでください。
- 初めて使用する際は、温度や動作が正しいことを確認するため、必ずテスト印刷を行ってください。
- 印刷後は、ノズルやヒートベッドが十分に冷えており、安全に印刷が完了していることを確認してください。
- 本ソフトウェアの使用によって生じた損害や損失について、作者は責任を負いません。

---

## 📄 License

MIT License

---

<p align="center">
<strong>AmiSlicer v0.01 Alpha</strong><br>
Author / 製作者: Yosuke Hori / kasanetarium
</p>
