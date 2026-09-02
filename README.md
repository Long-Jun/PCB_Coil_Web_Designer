# NTUT-UTL PCB Coil Generator

<details open>
<summary><strong>English</strong></summary>

Interactive browser-based tool for designing planar PCB spiral coils with live preview, mm/mil unit support, and DXF export.

**Online tool:**  
https://long-jun.github.io/PCB_Coil_Web_Designer/

Originally developed for the UTL Lab at National Taipei University of Technology (NTUT).

---

## Features

- Real-time planar spiral coil preview using HTML5 Canvas
- Automatic scaling and centered preview
- Inner diameter, trace width, and spacing controls
- mm / mil unit support
- CW / CCW winding direction
- Start angle, end angle, and turn-count controls
- Automatic outer-diameter and approximate trace-length calculation
- DXF export for CAD / ECAD workflows
- Pure HTML / CSS / JavaScript
- Fully static and usable through GitHub Pages or locally

---

## Quick Start

### Online

Open the web tool directly:

https://long-jun.github.io/PCB_Coil_Web_Designer/

No installation is required.

### Local

```bash
git clone https://github.com/Long-Jun/PCB_Coil_Web_Designer.git
cd PCB_Coil_Web_Designer
```

Then open `index.html` in Chrome, Edge, Firefox, or another modern browser.

---

## Design Parameters

### Inner Diameter

Defines the inner diameter of the planar spiral coil.

Supported units:

- mm
- mil

### Trace Width

Defines the PCB conductor width.

Supported units:

- mm
- mil

### Spacing

Defines the gap between adjacent turns.

Supported units:

- mm
- mil

### Rotation Direction

- `CW` — clockwise
- `CCW` — counter-clockwise

### Start Angle / End Angle / Turns

The basic relationship is:

```text
turns = (endAngle - startAngle) / 360
```

Changing the number of turns updates the end angle, and changing the end angle updates the calculated turn count.

The geometry uses an Archimedean spiral approximation:

```text
pitch = trace width + spacing
```

---

## Design Summary

The tool automatically reports:

- Outer diameter
- Total number of turns
- Approximate total trace length

These values are intended for rapid PCB-coil design and preliminary engineering estimates.

---

## DXF Export

The generated DXF can be imported into common CAD / ECAD software.

Key characteristics:

- Coordinates are exported in millimeters
- Trace width is stored in the polyline width
- Suitable for further PCB-layout or mechanical-CAD processing

If the imported geometry appears at the wrong scale, verify that the destination software interprets the DXF coordinates as millimeters.

---

## Project Structure

```text
PCB_Coil_Web_Designer/
├── index.html
├── README.md
├── README.zh-TW.md
└── LICENSE
```

The main interface, styling, and JavaScript logic are contained in `index.html`.

---

## Limitations

The current version is primarily intended for single-layer planar spiral coils.

Current limitations include:

- No multilayer or stacked-coil generator
- No segment-wise variable trace width
- No built-in inductance, Q-factor, or DC-resistance solver
- Start and end pads are not generated as complete PCB pad geometries

---

## GitHub Pages

This repository can be deployed directly as a static website.

1. Open **Settings → Pages**
2. Select **Deploy from a branch**
3. Select the `main` branch
4. Select `/ (root)`
5. Save the configuration

The project will then be available at:

https://long-jun.github.io/PCB_Coil_Web_Designer/

---

## License

This project is licensed under the **Apache License 2.0**.

See [LICENSE](./LICENSE) for details.

---

## Acknowledgements

Originally developed for PCB coil design and experimental work in the **UTL Lab, National Taipei University of Technology (NTUT)**.

Feedback, issues, and improvements are welcome through GitHub Issues.

</details>

<details>
<summary><strong>繁體中文</strong></summary>

北科大UTL實驗室使用的平面PCB螺旋線圈設計工具，可直接在瀏覽器中調整線圈幾何參數、即時預覽，並輸出DXF。

**線上工具：**  
https://long-jun.github.io/PCB_Coil_Web_Designer/

最初開發用途為國立臺北科技大學UTL實驗室之PCB線圈設計與實驗。

---

## 功能特色

- 使用HTML5 Canvas即時預覽平面螺旋線圈
- 畫面自動縮放並保持線圈置中
- 可設定內徑、線寬與線距
- 支援mm / mil單位
- 支援CW / CCW旋轉方向
- 可設定起始角、結束角與圈數
- 自動計算外徑與近似總線長
- 可輸出DXF供CAD / ECAD後續使用
- 使用純HTML / CSS / JavaScript
- 可直接透過GitHub Pages使用，也可離線開啟

---

## 快速開始

### 線上使用

直接開啟：

https://long-jun.github.io/PCB_Coil_Web_Designer/

不需要安裝任何軟體。

### 本機使用

```bash
git clone https://github.com/Long-Jun/PCB_Coil_Web_Designer.git
cd PCB_Coil_Web_Designer
```

接著使用Chrome、Edge、Firefox或其他現代瀏覽器開啟`index.html`。

---

## 設計參數

### Inner Diameter

設定平面螺旋線圈的內徑。

支援單位：

- mm
- mil

### Trace Width

設定PCB導線寬度。

支援單位：

- mm
- mil

### Spacing

設定相鄰線圈匝之間的距離。

支援單位：

- mm
- mil

### Rotation Direction

- `CW`：順時針
- `CCW`：逆時針

### Start Angle / End Angle / Turns

基本關係為：

```text
turns = (endAngle - startAngle) / 360
```

調整圈數時會更新結束角度；修改結束角度時也會重新計算圈數。

程式內部使用阿基米德螺旋線作為幾何近似：

```text
pitch = trace width + spacing
```

---

## 設計摘要

工具會自動顯示：

- 外徑
- 總圈數
- 近似總線長

適合用於快速設計PCB線圈與初步工程估算。

---

## DXF輸出

產生的DXF可匯入常見CAD / ECAD軟體。

主要特性：

- 座標單位為mm
- 線寬寫入polyline width
- 可繼續用於PCB Layout或機構CAD處理

若匯入後比例不正確，請確認目標軟體將DXF座標單位解讀為mm。

---

## 專案結構

```text
PCB_Coil_Web_Designer/
├── index.html
├── README.md
├── README.zh-TW.md
└── LICENSE
```

主要介面、CSS與JavaScript邏輯皆位於`index.html`。

---

## 已知限制

目前版本主要針對單層平面螺旋線圈：

- 尚未支援多層或堆疊線圈
- 尚未支援不同區段使用不同線寬
- 尚未內建電感值、Q值與DC電阻求解
- 起點與終點尚未產生完整PCB Pad幾何

---

## GitHub Pages部署

1. 進入**Settings → Pages**
2. 選擇**Deploy from a branch**
3. Branch選擇`main`
4. Folder選擇`/ (root)`
5. 儲存設定

完成後即可使用：

https://long-jun.github.io/PCB_Coil_Web_Designer/

---

## 授權

本專案採用**Apache License 2.0**。

詳細內容請參考[LICENSE](./LICENSE)。

---

## 致謝

本工具最初因應**國立臺北科技大學UTL實驗室**之PCB線圈設計與實驗需求開發。

若發現問題或有改進建議，歡迎透過GitHub Issues回饋。

</details>
