# WalkTrack GPS 第一版

## 使用方式（Samsung S23 Ultra / Chrome）

1. 將此資料夾所有檔案上傳至支援 HTTPS 的靜態網站，例如 GitHub Pages、Netlify 或 Cloudflare Pages。請保持檔名與相對位置不變。
2. 使用手機 Chrome 開啟部署後的 `https://...` 網址，允許「位置資訊」權限。
3. Chrome 選單 →「加到主畫面」或「安裝應用程式」。
4. 到戶外等待 GPS 定位後，點「開始」，運動結束點「結束並儲存」。
5. 在「歷史紀錄」查看地圖、匯出 GPX；在「每週統計」查看最近七天紀錄。

## GitHub Pages 部署

1. 建立公開 GitHub repository，例如 `walktrack`。
2. 將 `index.html`、`app.js`、`sw.js`、`manifest.webmanifest`、`icon.svg` 上傳至 repository 根目錄。
3. Settings → Pages → Build and deployment → Deploy from a branch → `main` / `(root)` → Save。
4. 等候部署完成，開啟 `https://你的帳號.github.io/walktrack/`。

## 本機測試（電腦）

在專案資料夾執行 `python -m http.server 8000`，電腦瀏覽器開啟 `http://localhost:8000`。手機若透過電腦 LAN IP 連線，因不是 HTTPS，GPS 通常無法使用。

## 重要限制

- Android Chrome/PWA 在螢幕關閉、切到背景或被系統省電管理時，不保證繼續收到定位更新。此網頁版**不具備可靠背景 GPS 紀錄能力**。如需鎖屏持續追蹤，建議後續製作原生 Android App，使用前景服務與適當權限。
- 運動資料存在瀏覽器 localStorage，不會自動同步或上傳。清除網站資料、更換手機、無痕模式可能遺失資料，請定期匯出 GPX。
- GPS 過濾精度差於 50m、移動少於 3m 及瞬間速度超過 8m/s 的定位點。GPS 仍可能漂移；距離與速度僅供參考。
- 熱量是簡化距離估算：走路約 0.55 kcal/kg/km，慢跑約 1.03 kcal/kg/km，非醫療或專業運動測量。
- Leaflet CSS/JS 及 OpenStreetMap 圖磚需網路連線；目前未包含離線地圖。
- OpenStreetMap 官方圖磚有使用政策，請勿大量批次下載或預先快取地圖圖磚。正式大量使用應改用合規圖磚供應商。
- GPX 匯出包含精確 GPS 座標，分享前請注意住家與工作地點隱私。
