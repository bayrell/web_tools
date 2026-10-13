Требуется разработать web_search и web_fetch. Провайдеры добавить в реестр и выбирать случайно. Провайдеры могут добавляться.

Создать setup.py и библиотеку для python web_tools.

Ollama:

Web search API
Performs a web search for a single query and returns relevant results.
​
Request
POST https://ollama.com/api/web_search
- query (string, required): the search query string
- max_results (integer, optional): maximum results to return (default 5, max 10)
​
Response
Returns an object containing:
- results (array): array of search result objects, each containing:
  - title (string): the title of the web page
  - url (string): the URL of the web page
  - content (string): relevant content snippet from the web page

```
curl https://ollama.com/api/web_search \
  --header "Authorization: Bearer $OLLAMA_API_KEY" \
	-d '{
	  "query":"AI news"
	}'
```

Firecrawl:
```
curl -X POST https://api.firecrawl.dev/v2/search \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer fc-YOUR_API_KEY" \
  -d '{
    "query": "AI news",
    "sources": ["web", "alexandria"],
    "limit": 10
  }'
```

Response:
```
{
  "success": true,
  "data": {
    "web": [
      {
        "url": "",
        "title": "",
        "description": "",
        "position": 1
      },
  }
}
```

Include domains:

```
curl -X POST https://api.firecrawl.dev/v2/search \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer fc-YOUR_API_KEY" \
  -d '{
    "query": "AI news",
    "includeDomains": ["arxiv.org"],
    "limit": 10
  }'
```

Fetch url:

```
curl "https://r.jina.ai/<url>"
```

Возвращает markdown

Пример:
```
curl https://r.jina.ai/https://baylang.com/
```