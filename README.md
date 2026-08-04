# Reverse Aging Engineering

一份給自己用的居家訓練計畫, 做成單一 HTML 檔案, 可以直接加到 iPhone 主畫面, 打開時像一個獨立 APP, 沒有網址列.

## Demo

https://allenintaipei.github.io/reverse-aging-plan/plan.html

## 這是不是一個正規的 PWA

目前的做法, 是 iOS Safari 專用的 web app meta tag (apple-mobile-web-app-capable 等) , 讓加入主畫面後用 Safari 引擎全螢幕開啟. 還沒有 manifest.json, 也沒有 Service Worker, 所以現況是:

在 iPhone Safari, 加入主畫面後的開啟體驗, 等同一個獨立 APP.

在 Android Chrome 或桌面瀏覽器, 目前不會跳出安裝提示, 也還沒有離線快取能力.

若之後想做成能被 Chrome, Edge 正式辨識並安裝的完整 PWA, 需要補上 manifest.json 與 Service Worker, 詳見下方 Roadmap.

## 目前已經實作的部分

已加入 apple-mobile-web-app-capable, 讓主畫面圖示以全螢幕獨立視窗開啟, 沒有 Safari 網址列.

已設定 apple-mobile-web-app-status-bar-style, 控制系統狀態列的顯示樣式.

已設定 apple-mobile-web-app-title, 決定主畫面圖示下方顯示的名稱.

已內嵌 SVG 格式的 apple-touch-icon, 不需要額外的圖片檔案.

已支援 prefers-color-scheme, 依系統設定自動切換淺色與深色主題.

已使用 env(safe-area-inset-*), 避免內容被瀏海或 Home 指示條遮住.

已設定 viewport-fit=cover, 讓版面可以延伸到安全區域邊緣.

## 如何加到 iPhone 主畫面

用 Safari 打開上方 Demo 連結.

點畫面下方的分享按鈕.

選加入主畫面.

之後從主畫面圖示開啟, 就會是全螢幕獨立視窗.

## 專案結構

plan.html 是唯一需要部署的檔案, 訓練計畫內容與所有 PWA 相關設定都寫在同一個檔案裡.

plan.md 是原始的 Markdown 版本, 作為內容來源保存.

## 部署方式

使用 GitHub Pages, 從 master 分支的根目錄直接發布. 每次 push 到 master, GitHub Pages 大約 30 到 60 秒後會自動重新部署, 不需要重新加入主畫面.

## Roadmap

補上 manifest.json, 定義 name, icons, start_url, display, theme_color, background_color, 讓 Android Chrome 等其他瀏覽器也能正確辨識為可安裝的 PWA.

加入 Service Worker, 快取靜態資源, 支援離線開啟.

把內嵌 SVG icon 換成正式的 PNG 圖檔, 目前 apple-touch-icon 對舊版 iOS 的相容性不完全穩定.
