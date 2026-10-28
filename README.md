# workshop-2026

高雄市 115 年度教保研習：問卷入口與講義下載。

## 網頁與部署

- 網站檔案只放在 `public/`，Wrangler 只上傳此資料夾。
- `public/.assetsignore` 使用允許清單，只發布首頁、講義 PDF 及 QR Code PNG／SVG。
- QR Code 與填答按鈕均指向 `https://forms.gle/DNUr9uyD9woBuZkB8`。
- SVG 適合印刷與放大，PNG 提供一般圖片相容性。
- `GitHub 網頁.zip` 是原始附件，留在根目錄保存，不會上傳網站。

從專案根目錄使用 Cloudflare Workers 靜態資產部署：

```sh
npx wrangler deploy --config wrangler.jsonc
```

Cloudflare Git 自動部署的根目錄為儲存庫根目錄，無須建置步驟，部署命令使用上述命令。不要使用 `wrangler pages deploy .`。

每個公開檔案須小於或等於 25 MiB。目前講義約 4.72 MiB。加入新網站檔案時，同步更新 `.assetsignore` 的允許清單。

`.gitignore` 可避免新安裝檔加入 Git，但不會停止追蹤已提交的檔案，也不會清除歷史。這次檢查的全部 Git 歷史未包含 `GoogleDriveSetup.exe` 或超過 25 MiB 的檔案，不需要重寫歷史。
