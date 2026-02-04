# ♟️ 棋弈江湖 - 專業象棋對戰平台

<div align="center">

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Platform](https://img.shields.io/badge/platform-Web%20%7C%20PWA-green.svg)
![AI](https://img.shields.io/badge/AI-Pikafish-orange.svg)

**一個功能完整、開源的象棋學習與對弈平台**

[🎮 立即體驗](https://android-xiangqi-offline.netlify.app/) | [📖 完整文檔](#功能介紹) | [🐛 問題回報](填入你的Google表單連結)

</div>

---

## ✨ 核心特色

- 🤖 **本地 AI 引擎** - 基於 Pikafish 的強大 AI 對戰與分析
- 📸 **全平台唯一開源棋盤識別** - 支援實體棋盤、線上截圖雙模式
- ⚖️ **智能棋規判定** - 自動識別將殺、困斃、長將、長捉等複雜局面
- 🧠 **專業覆盤分析** - 深度剖析每一步棋的優劣
- 📚 **7300+ 題庫資源** - 涵蓋開局、殘局、江湖、古譜等
- 💾 **完全離線可用** - PWA 技術，無網路也能暢玩
- 🎨 **自訂化體驗** - 多種棋盤與棋子風格

---

## 🚀 快速開始

### 線上體驗
直接訪問：https://android-xiangqi-offline.netlify.app/

### 本地運行
```bash
# Clone 專案
git clone https://github.com/dffge552/xiangqi-pwa-offline.git

# 進入目錄
cd xiangqi-pwa-offline

# 安裝依賴（如果有的話，根據你的專案調整）
npm install

# 啟動開發伺服器
npm start
```

---

## 📸 象棋棋盤識別系統（開源亮點）

### 🌟 全平台唯一開源實現

本專案提供**完整開源**的象棋棋盤識別解決方案，包含訓練好的模型與完整程式碼，你可以：

- ✅ 直接使用於你的專案（請標註原作者）
- ✅ 重新訓練模型以提升準確度
- ✅ 修改適配不同棋種或應用場景
- ✅ 學習 AI 視覺識別的實作方式

### 📦 模型檔案

| 模型 | 用途 | 檔案 |
|------|------|------|
| 線上棋盤偵測 | 定位棋子位置 | `online_xiangqi_piece_detector.onnx` |
| 線上棋子分類 | 識別棋子類型 | `online_xiangqi_classifier.onnx` |
| 實體棋盤識別 | 實體棋盤整合識別 | `Entity_chess_recognition_model.onnx` |

### 🔧 兩種識別模式

#### 1️⃣ 實體棋盤識別
- 支援木質、紙質等各類實體棋盤
- 自動透視校正（拍攝角度容錯）
- 智能座標映射技術
- ⚠️ 最佳支援淺色系棋子

#### 2️⃣ 線上截圖識別  
- 針對數位化棋盤優化
- 雙模型架構：Detection + Classification
- 自動識別紅黑陣營
- 無需透視校正

### 🎯 使用範例

```javascript
// 範例：如何整合識別功能（偽代碼）
const recognizer = new ChessRecognizer();

// 上傳照片
recognizer.uploadImage(imageFile);

// 標註四角與中兵（用於定位校正）
recognizer.markCorners([topLeft, topRight, bottomRight, bottomLeft]);
recognizer.markCenterPawn(centerPosition);

// 執行識別
const fenCode = await recognizer.recognize();
console.log(fenCode); // 輸出 FEN 格式棋盤
```

> 💡 詳細 API 使用說明請參考專案原始碼

---

## 🎮 功能介紹

### 對戰模式
- ♟️ **雙人對戰** - 本地或線上對弈
- 🤖 **AI 對戰** - 多難度等級挑戰（PC & Android）
- ⏱️ **棋鐘功能** - 仿真正式比賽計時

### 學習工具
- 🧠 **覆盤分析** - AI 深度分析每一步（僅 PC）
- 📊 **AI 分析** - 即時最佳走法建議（PC & Android）
- 📚 **開局殘局庫** - 7300+ 精選題庫
  - 象棋定式（~200 題）
  - 江湖殘局（366 題）
  - 疑難雜症（183 題）
  - 基本殺法、古局練習等

### 輔助功能
- 🔄 **悔棋** - 一鍵退回上一步
- 💾 **儲存/載入局面** - 保存精彩對局
- ⚙️ **自訂棋盤** - 創建任意合法局面
- 🎨 **個性化設定** - 5 種棋盤 + 5 種棋子風格

### 智能判定
- ✅ 自動識別將殺、困斃
- ✅ 無過河子判和
- ✅ 循環局面自動判和
- ✅ 長捉/長將智能判定
- 📜 採用《中華民國象棋規則-113年修訂版》
- 🎯 大部分局面都能準確自動判定

> ⚠️ 注意：遇無法自動判定或判定錯誤的情況，請棋手依照官方規則自行裁定勝負

---

## 🍎 平台支援

| 功能 | Windows/Mac/Linux | Android | iOS |
|------|-------------------|---------|-----|
| 雙人對戰 | ✅ | ✅ | ✅ |
| 棋鐘功能 | ✅ | ✅ | ✅ |
| AI 對戰 | ✅ | ✅ | ❌* |
| AI 分析 | ✅ | ✅ | ❌* |
| 覆盤分析 | ✅ | ❌** | ❌* |
| 拍照識別 | ✅ | ✅ | ✅ |

\* iOS 限制：WebAssembly 本地運算受限  
** 手機 CPU 運算能力不足

---

## 🐟 AI 引擎

本專案採用 **[皮卡魚 (Pikafish)](https://pikafish.org/)** 作為 AI 核心：

- 🔓 開源免費的象棋引擎
- ⚡ 持續更新優化，棋力強勁
- 🚀 支援多線程並行計算
- 📖 廣泛應用於象棋教學

相關資源：
- [皮卡魚在線分析平台](https://pikafish.org/)
- [皮卡魚官網](https://pikafish.org/)

---

## 📋 技術棧

- **前端框架**: [填入你使用的框架，如 React/Vue/原生 JS]
- **AI 引擎**: Pikafish (WebAssembly)
- **視覺識別**: ONNX Runtime (自訓練模型)
- **PWA**: Service Worker + Workbox
- **儲存**: LocalStorage / IndexedDB

---

## 📖 詳細文檔

- [📸 拍照識別完整使用說明](./docs/photo-recognition.md)
- [📚 開局殘局庫使用指南](./docs/opening-endgame.md)
- [⚙️ 遊戲設定與功能說明](./docs/game-settings.md)
- [🤖 AI 功能使用技巧](./docs/ai-features.md)

---

## 🎯 開發緣起

> 大家好，我是一名目前就讀高二的學生。開發「棋弈江湖」源自於學校功課的要求，但更源於對象棋的熱愛。
> 
> 市面上的象棋軟體要不是功能過於複雜，就是缺少現代化介面。因此我結合程式設計專長，打造這個既專業又親切的平台。
> 
> 本專案核心目的是**提升棋士棋力**，透過 AI 分析、覆盤功能、多樣化對戰模式，讓每位使用者都能持續進步，期盼培養出更多優秀象棋人才，為台灣象棋界爭光！

---

## 🤝 貢獻指南

歡迎各種形式的貢獻！

### 如何貢獻
1. Fork 本專案
2. 創建你的特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交你的修改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 開啟 Pull Request

### 特別歡迎
- 🧠 **AI 模型改進** - 提升識別準確度
- 🌍 **多語言支援** - 翻譯介面文字
- 🎨 **UI/UX 優化** - 提升使用體驗
- 📚 **題庫擴充** - 新增更多練習題
- 🐛 **Bug 修復** - 回報與修復問題

---

## 📝 授權條款

本專案採用 [MIT License](LICENSE) 授權。

**這意味著你可以：**
- ✅ 商業使用
- ✅ 修改原始碼
- ✅ 分發
- ✅ 私人使用
- ✅ **複製到其他地方使用**

**唯一要求：**
- ⭐ **必須標註原作者名稱**
- 📄 保留原始版權聲明

### 引用範例
```
本專案使用了「棋弈江湖」的棋盤識別系統
原作者：dffge552
來源：https://github.com/dffge552/xiangqi-pwa-offline
```

---

## 🙏 致謝

### 題庫來源
- [从寬象棋 YouTube 頻道](https://youtube.com/@从宽象棋) - 江湖殘局與疑難雜症

### 推薦學習資源
- [棋弈江湖官方頻道](填入你的頻道)
- [从寬象棋](https://youtube.com/@从宽象棋)
- [象棋王子](填入連結)
- [板牙象棋](填入連結)
- 更多資源請見[遊戲內說明](#)

---

## 📞 聯絡方式

- 🐛 [問題回報表單](填入你的 Google 表單)
- 📧 Email: [你的信箱]
- 🌐 線上體驗: https://android-xiangqi-offline.netlify.app/

---

## 🌟 Star History

如果這個專案對你有幫助，請給個 ⭐ Star 支持！

[![Star History Chart](https://api.star-history.com/svg?repos=dffge552/xiangqi-pwa-offline&type=Date)](https://star-history.com/#dffge552/xiangqi-pwa-offline&Date)

---

<div align="center">

**用心打造 · 開源分享 · 共同進步**

Made with ❤️ by [dffge552](https://github.com/dffge552)

</div>
