# NTUT-UTL PCB Coil Generator
### 北科大 UTL 實驗室 PCB 螺旋線圈產生器

Interactive web-based tool for designing planar PCB spiral coils, with live preview, mm/mil unit support, and DXF export.
專為平面 PCB 螺旋線圈設計的互動式網頁工具，支援 mm / mil 單位、即時預覽與 DXF 輸出。

Originally developed for the UTL Lab at National Taipei University of Technology (NTUT).
最初開發用途為國立臺北科技大學 UTL 實驗室之 PCB 線圈設計與實驗。

GitHub靜態網址:
https://long-jun.github.io/PCB_Coil_Web_Designer/

---

## ✨ Features 功能特色

### Interactive coil preview 即時線圈預覽
* **Real-time drawing on HTML5 `<canvas>`**
    透過 HTML5 `<canvas>` 即時繪製線圈形狀
* **Auto-scaling view, always centered on the coil**
    畫面自動縮放與置中顯示，不須手動調整視窗

### Practical geometry controls 幾何參數控制
* **Inner diameter Din with mm / mil unit selection**
    內徑 Din 支援 mm / mil 單位切換
* **Trace width & spacing (mm / mil)**
    線寬與線距皆可使用 mm / mil 輸入
* **Rotation direction (CW / CCW), start angle, end angle or turns**
    支援順 / 逆時針方向，起始角度、結束角度與圈數互相聯動

### Automatic design summary 設計摘要資訊
* **Outer diameter (OD) in mm and mil**
    自動計算外徑 OD（mm / mil）
* **Total number of turns**
    顯示實際總圈數
* **Approximate total trace length**
    估算總線長（便於粗略推估電阻等）

### DXF export DXF 檔匯出
* **Exports a single LWPOLYLINE entity in mm**
    匯出單一 LWPOLYLINE 實體，座標單位為 mm
* **Trace width stored as polyline width**
    線寬寫入 polyline width 欄位，方便在 CAD 中直接使用

> All logic is implemented in pure HTML/CSS/JavaScript. No external libraries are required.
> 所有邏輯均以原生 HTML / CSS / JavaScript 實作，無外部套件依賴。

---

## 📂 Project Structure 專案結構

Currently the project consists of a single main file:
目前專案主要由一個檔案組成：

* `index.html`
    * **Main HTML page, includes CSS + JavaScript logic.**
        主視覺、版面配置與 JavaScript 計算程式都寫在這個檔案中。

Optional files you may add:
可以自行新增的選用檔案，例如：

* `docs/screenshot.png`
    * **A screenshot used in this README.**
        用於在 README 中展示工具畫面。

> If you rename the file (e.g., `index.html`), remember to update this description.
> 如果日後更改檔名，記得同步更新 README 說明。

---

## 🚀 Getting Started 開始使用

### 1. Local usage 本機使用

1.  **Clone this repository:**
    下載此專案原始碼：
    ```bash
    git clone [https://github.com/](https://github.com/)Long-Jun/PCB_Coil_Web_Designer.git
    cd PCB_Coil_Web_Designer
    ```

2.  **Open `index.html` with your browser** (Chrome / Edge / Firefox, etc.).
    使用瀏覽器開啟 `index.html`（雙擊檔案或拖曳至瀏覽器視窗即可）。

> 💡 **This project is fully static and works offline.**
> 本工具為純前端靜態網頁，可 **完全離線** 使用。

### 2. GitHub Pages (optional) 在 GitHub Pages 部署（選用）

You can host this tool as an online demo for your lab members:
你可以把它部署成線上版，方便實驗室成員直接使用。

1.  Make the repository public. (將此 repo 設為公開)
2.  Go to **Settings** → **Pages**:
    * Source: **Deploy from a branch**
    * Branch: `main` (or your default branch), Root `/`
3.  GitHub will generate a URL, e.g.:
    `https://<your-account>.github.io/<your-repo-name>/`
4.  Share this URL with your team; they can use the coil generator directly in the browser.
    把這個網址分享給實驗室成員，就能直接在瀏覽器上使用線圈設計工具。

---

## 🧮 Parameter Explanation 參數說明

### Geometry 幾何尺寸

* **Inner diameter Din**
    * Input: numeric value + unit (mm / mil)
        內徑輸入數值與單位（mm 或 mil）
    * Internally converted to mm for further computation.
        程式內部一律轉換成 mm 進行計算。

* **Trace width (Width 線寬)**
    * Input in mm or mil (可使用 mm 或 mil 輸入)
    * Used for both canvas line width and DXF polyline width.
        同時用於畫布線寬與 DXF polyline 的 width 欄位。

* **Spacing (線距)**
    * Input in mm or mil (可使用 mm 或 mil 輸入)
    * Distance between adjacent turns.
        線圈相鄰匝間之間距。

### Rotation direction 旋轉方向
* **CCW** (counter-clockwise, 逆時針)
* **CW** (clockwise, 順時針)

### Start angle / End angle / Turns 起始角 / 結束角 / 圈數
* **startAngle**: start angle in degrees. 起始角度（度）
* **endAngle**: end angle in degrees. 結束角度（度）
* **turns**: `number of turns = (endAngle - startAngle) / 360`
    圈數 = (結束角度 − 起始角度) / 360

> Changing turns will update endAngle, and vice versa.
> 調整圈數會自動更新結束角度，直接改結束角度也會反推圈數。

**Internally, the tool uses an Archimedean spiral approximation:**
程式內部以阿基米德螺旋線作為幾何近似：
> `pitch = trace width + spacing`
> 螺距 = 線寬 + 線距
> Radius grows linearly with angle. (半徑隨旋轉角度線性增加)

---

## 📁 DXF Export DXF 匯出格式

When you click **"輸出 DXF 檔案"**, the tool generates a DXF file:
按下 **「輸出 DXF 檔案」** 按鈕時，工具會產生一個 DXF 檔案，內容特性如下：

* **DXF version:** AC1009 (AutoCAD R12)
    DXF 版本：AC1009（AutoCAD R12 相容）
* **A single LWPOLYLINE entity:**
    只包含一個 LWPOLYLINE 實體
    * Coordinates in mm (所有座標單位為 mm)
    * Polyline width = trace width (mm) (polyline width 欄位設為線寬)
* **Filename pattern:**
    檔名格式：`coil_din<Din>_<direction>.dxf`
    *Example:* `coil_din10_ccw.dxf`

> If the scale looks incorrect after importing into an ECAD/CAD tool, please check that the unit is interpreted as mm.
> 若匯入 ECAD / CAD 後比例不正，請確認軟體有將座標單位視為 mm。

---

## ⚙️ Implementation Notes 實作細節

* **No external dependencies:** pure HTML + CSS + vanilla JavaScript
    無任何外部 JS / CSS 套件，純原生 HTML / CSS / JavaScript。
* **Canvas:**
    * Internal resolution fixed at 800 x 800
        Canvas 內部解析度固定為 800 × 800
    * CSS uses `width: 100%` + `aspect-ratio: 1/1` to scale responsively
        使用 width: 100% 與 aspect-ratio: 1/1 讓畫布在不同螢幕自適應縮放
* **Point sampling:**
    * `segmentsPerTurn = 72` → 72 segments per turn for a good balance of smoothness and file size.
        每圈切成 72 個線段，在平滑度與 DXF 檔案大小之間取得折衷。
    * You can increase this value for higher resolution (at the cost of larger DXF files).
        若需要更高解析度，可提高此數值，但 DXF 檔案會變大。

---

## 🧪 Limitations & TODO 已知限制與未來可能改進

### Current limitations 目前限制
* **Only supports single-layer planar spiral coils.**
    目前僅支援單層平面螺旋線圈：
    * No multi-layer or stacked coils. (尚未支援多層疊繞設計)
* **No segment-wise variable width.**
    不支援不同區段使用不同線寬。
* **No built-in electrical calculations.**
    尚未內建電感值、Q 值或電阻等電氣參數計算。
* Start / end pads are not drawn as actual pads; only the start point is highlighted.
    起點與終點焊盤目前未以實際 pad 形狀繪出，只以起點標記點顯示。

### Possible future improvements 未來可考慮的改進方向
* Multi-layer coil design support (e.g., top/bottom or stacked layers).
    支援多層、雙面或疊繞線圈設計。
* Inductance and DC resistance estimation.
    加入電感與 DC 電阻的估算功能。
* Export additional formats (e.g., CSV point list, JSON).
    增加輸出 CSV / JSON 等點序列格式。
* UI enhancements (keyboard shortcuts, presets for common coil sizes).
    增加快捷鍵、常用尺寸預設等更友善的操作介面。

---

## 📜 License 授權條款

**Apache-2.0 License**

This project is licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.

本專案採用 **Apache-2.0** 授權條款，詳細內容請參考根目錄下的 LICENSE 檔案。

---

## 🙌 Acknowledgements 致謝

* **NTUT UTL Lab** – original use case: PCB spiral coils for sensing and experimental setups.
    感謝 **國立臺北科技大學 UTL 實驗室** 在感測器與實驗設計上的需求，促成本工具的開發。
* Built originally using a browser-based coding environment (e.g., “Vibe Coding” / v0-style UI).
    本工具最初以瀏覽器端互動式程式設計環境（例如 Vibe Coding 介面）開發，再逐步整理為單一 HTML 檔案形式。

If you find this tool useful or adapt it for your own lab, feel free to open an issue or share feedback.
若你在其他實驗室或專案中使用或修改本工具，歡迎透過 issue 或其他方式回饋使用心得。
