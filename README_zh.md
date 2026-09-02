# NTUT-UTL PCB Coil Generator

[English](./README.md) | **繁體中文**


北科大UTL實驗室使用的平面PCB螺旋線圈設計工具，可直接在瀏覽器中調整線圈幾何參數、即時預覽，並輸出DXF。

## 📚 簡介

本專案提供一套輕量化的瀏覽器端PCB平面螺旋線圈設計流程，可快速設定線圈幾何、即時檢查結果，並輸出DXF供後續CAD / ECAD使用。

**線上工具：**  
https://long-jun.github.io/PCB_Coil_Web_Designer/

最初開發用途為國立臺北科技大學UTL實驗室之PCB線圈設計與實驗。

---

## ✨ 功能特色

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

## 🚀 快速開始

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

## 🧭 設計參數

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

## 📊 設計摘要

工具會自動顯示：

- 外徑
- 總圈數
- 近似總線長

適合用於快速設計PCB線圈與初步工程估算。

---

## 📁 DXF輸出

產生的DXF可匯入常見CAD / ECAD軟體。

主要特性：

- 座標單位為mm
- 線寬寫入polyline width
- 可繼續用於PCB Layout或機構CAD處理

若匯入後比例不正確，請確認目標軟體將DXF座標單位解讀為mm。

---

## 🗂️ 專案結構

```text
PCB_Coil_Web_Designer/
├── index.html
├── README.md
├── README.zh-TW.md
└── LICENSE
```

主要介面、CSS與JavaScript邏輯皆位於`index.html`。

---

## ⚠️ 已知限制

目前版本主要針對單層平面螺旋線圈：

- 尚未支援多層或堆疊線圈
- 尚未支援不同區段使用不同線寬
- 尚未內建電感值、Q值與DC電阻求解
- 起點與終點尚未產生完整PCB Pad幾何

---

## 🌐 GitHub Pages部署

1. 進入**Settings → Pages**
2. 選擇**Deploy from a branch**
3. Branch選擇`main`
4. Folder選擇`/ (root)`
5. 儲存設定

完成後即可使用：

https://long-jun.github.io/PCB_Coil_Web_Designer/

---

## 📜 授權

本專案採用**Apache License 2.0**。

詳細內容請參考[LICENSE](./LICENSE)。

---

## 🙌 致謝

本工具最初因應**國立臺北科技大學UTL實驗室**之PCB線圈設計與實驗需求開發。

若發現問題或有改進建議，歡迎透過GitHub Issues回饋。
