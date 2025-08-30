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

From this section, I'm tired of translating things over and over, so I'll just write in English lol.

## REST API
```http
GET http://localhost:8000/news
```

**Parameters**:
- `n` – Optional. Number of items.
- `page` – Optional. Page #.
- `text` – Optional. Text filter.

## How?
There's this [CK app](https://apps.apple.com/app/id6608961910) made by our beloved senpai uwu

...but bro just hasn't been updating it for 11+ months, and the "latest news" feature ain't working, and I ain't happy about this shi. So, I just decided to make my own *fetcher*.

First, I fetched the HTML only and attempted to select the data rows in raw HTML. It didn't work.

Turns out, they were using a super advanced technology called Vue and the data was fetched in the browser at runtime. Hell nawh.

Network tab time!

I picked XHR as the filter, and the requests are mostly SVG icons, the path `/single` and `/find`.

The first path I tried to reverse engineer was `/find`, which looked pretty much like some kind of message filter?

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
