# Prompt Formula Library (Pack A v0.1)

這是一個 **單頁（index.html）+ prompts.json** 的 Prompt Builder：
- 選模板 / 填變數 → 一鍵 Copy → 貼到 ChatGPT / Gemini / 任何 LLM
- Local-first：你匯入的 prompts.json 會存在瀏覽器 localStorage（不需要後端）

## 檔案
- `index.html`：單頁 UI（搜尋、Pack 篩選、變數填空、Copy、匯入/匯出）
- `prompts.json`：模板資料（目前只有 Pack A：8 個核心公式）

## 本地測試
直接雙擊 `index.html` 開啟即可（大多瀏覽器可正常讀取 prompts.json）。
若遇到瀏覽器阻擋 fetch（少數情況），用任意本地伺服器：
- VS Code: Live Server
- 或 Python:
  - `python -m http.server 8000`
  - 然後開 `http://localhost:8000`

## 部署到 GitHub Pages（免費）
1. 新建 repo（或 fork）
2. 把 `index.html` 與 `prompts.json` 放在 repo 根目錄
3. GitHub → Settings → Pages → Branch 選 `main` / `/root` → Save
4. 等 1–2 分鐘，會得到 Pages 網址

## 如何新增模板（最簡單）
打開 `prompts.json`：
- `prompts` 是陣列，每個元素是一條模板
- `template` 內可用 `{{variable}}` 變數
- `variables` 用來定義 UI 的輸入欄位

建議做法：
- 先把 Pack A 拍成 EP.01–EP.08
- 每集新增 1 條模板（Pack B/C/D 之後再加）

## JSON 格式（摘要）
```json
{
  "meta": { "name": "...", "version": "v0.1", "pack": "A" },
  "prompts": [
    {
      "id": "A-GAF",
      "pack": "A",
      "title": "...",
      "teaser": "...",
      "tags": ["..."],
      "variables": [{"key":"topic","label":"主題","placeholder":"..."}],
      "template": "..."
    }
  ]
}
```

## 注意
- 這個工具只負責生成 Prompt，不會直接生成圖片/影片檔案。
- 圖像/影片工具通常也接受提示詞：把 Builder 產出的 prompt 貼進去即可。
