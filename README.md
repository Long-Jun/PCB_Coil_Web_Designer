# NTUT-UTL PCB Coil Generator  
# 北科大 UTL 實驗室 PCB 螺旋線圈產生器

Interactive web-based tool for designing planar PCB spiral coils,  
with live preview, mm/mil unit support, and DXF export.  
專為平面 PCB 螺旋線圈設計的互動式網頁工具，支援 mm / mil 單位、即時預覽與 DXF 輸出。  
Originally developed for the UTL Lab at National Taipei University of Technology (NTUT).  
最初開發用途為北科大 UTL 實驗室之 PCB 線圈設計與實驗。

---

## ✨ Features 功能特色

- **Interactive coil preview 即時線圈預覽**
  - Real-time drawing on HTML5 `<canvas>`  
    透過 HTML5 `<canvas>` 即時繪製線圈形狀  
  - Auto-scaling view, always centered on the coil  
    畫面自動縮放與置中顯示，不須手動調整視窗

- **Practical geometry controls 幾何參數控制**
  - Inner diameter **Din** with mm / mil unit selection  
    內徑 Din 支援 mm / mil 單位切換  
  - Trace width & spacing (mm / mil)  
    線寬與線距皆可使用 mm / mil 輸入  
  - Rotation direction (CW / CCW), start angle, end angle or turns  
    支援順 / 逆時針方向，起始角度、結束角度與圈數互相聯動

- **Automatic design summary 設計摘要資訊**
  - Outer diameter (OD) in mm and mil  
    自動計算外徑 OD（mm / mil）  
  - Total number of turns  
    顯示實際總圈數  
  - Approximate total trace length  
    估算總線長（便於粗略推估電阻等）

- **DXF export DXF 檔匯出**
  - Exports a single `LWPOLYLINE` entity in mm  
    匯出單一 `LWPOLYLINE` 實體，座標單位為 mm  
  - Trace width stored as polyline width  
    線寬寫入 polyline width 欄位，方便在 CAD 中直接使用

All logic is implemented in pure HTML/CSS/JavaScript. No external libraries are required.  
所有邏輯均以原生 HTML / CSS / JavaScript 實作，無外部套件依賴。

---

## 📂 Project Structure 專案結構

Currently the project consists of a single main file:  
目前專案主要由一個檔案組成：

```text
.
├─ index.html   # Main HTML page, includes CSS + JavaScript logic
└─ (optional) docs/
   └─ screenshot.png   # You can add a screenshot for the README
