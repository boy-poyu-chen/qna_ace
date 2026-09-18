# 每日快問快答遊戲 (QnA ACE)

健康挑戰「每日快問快答」原型 — 每日 10 題是非題，答對累積行動值，答錯即結束。

## 線上瀏覽

https://boy-poyu-chen.github.io/qna_ace/

## 檔案說明

| 檔案 | 說明 |
| --- | --- |
| `index.html` | 打包後可直接開啟的單檔原型（GitHub Pages 服務的就是這支） |
| `快問快答健康挑戰.dc.html` | Claude Design 原始檔，需搭配 `support.js` 與 `_ds/` |
| `support.js` | Design container 執行環境 |
| `ios-frame.jsx` | iOS 外框元件 |
| `_ds/` | Ant Design Pro design system（CSS／bundle／manifest） |
| `.nojekyll` | 讓 GitHub Pages 不要過濾 `_` 與 `.` 開頭的路徑 |

## 本機預覽

```sh
python3 -m http.server 8000
# 開 http://localhost:8000/index.html
```

`index.html` 會從 unpkg.com 載入 React、從 Google Fonts 載入字型，需要網路連線。
