# ck-api

堅果中學公告擷取 API。

這個 Repo 可以大致分成三個部分：

- `main.py` – REST API。使用 `uvicorn` 和 `fastapi`。
- `discovery/*` – 資料探索。
- `ckapi/*` – 可使用的模組。

你可以下載這個 Repo，並自己試試：

```sh
git clone https://github.com/AWeirdDev/ck-api
```

```python
from ckapi import CkClient

client = CkClient()

news = await client.get_news()
```

## REST API
```http
GET http://localhost:8000/news
```

**Parameters**:
- `n` – Optional. Number of items.
- `page` – Optional. Page #.
- `text` – Optional. Text filter.

## 如何找到這些資料
首先，如果直接以 HTML 提取資料的話，內容並沒有被顯示，因此可能是利用 Javascript。
從開發者工具的 Network 頁籤可以發現一些 XHR 請求，主要包括 SVG 圖示、 `single` 和 `find`。

***

# DISCLAIMER

THE SOLE PURPOSE OF THIS REPOSITORY IS TO PROVE THE POSSIBILITY OF UTILIZING MODERN TOOLS FOR FETCHING DATA, AND IS FOR EDUCATIONAL PURPOSES ONLY.
AS STATED IN THE `robots.txt` FILE IN THE OFFICIAL SITE:

```yml
User-agent: *
Allow: /nss/
Allow: /public/
Allow: /uploads/
Allow: /sitemap/
Sitemap: https://www.ck.tp.edu.tw/sitemap.xml
```

...ANY USER AGENT IS ALLOWED, AND THE SITES THIS PROGRAM VISITS IS ALWAYS UNDER THE SCOPE OF `/nss/`.
AS OF THE VERSION OF `robots.txt` FOUND ON 2025-08-30, THE BEHAVIORS OF THIS PROGRAM DO NOT VIOLATE THE ROBOTS TEXT.
[VIEW ON WAYBACK MACHINE (INTERNET ARCHIVE)](https://web.archive.org/web/20250830100619/https://www.ck.tp.edu.tw/robots.txt).

**EDUCATIONAL PURPOSES ONLY.** **EDUCATIONAL PURPOSES ONLY.** **EDUCATIONAL PURPOSES ONLY.** 
