# The Idea Collection

Self Caring Co. daily self-care idea app, hosted on GitHub Pages and powered by Notion via Cloudflare Worker.

## Architecture

```
Notion Database → Cloudflare Worker → GitHub Pages App
```

- **Notion** — content bank, edit ideas here
- **Cloudflare Worker** — `idea-collection-api.dholmes127.workers.dev` — fetches and transforms Notion data
- **GitHub Pages** — hosts the app at `dholmes127.github.io/selfcaring-idea-collection`

## Deploying the Worker

1. Go to [dash.cloudflare.com](https://dash.cloudflare.com)
2. Workers & Pages → Create → Worker
3. Name it `idea-collection-api`
4. Paste the contents of `worker.js`
5. Deploy

## Updating ideas

1. Edit content in Notion (body copy, PS, energy tags)
2. Never change the App ID column
3. The app picks up changes within 1 hour (Worker cache TTL)
4. To force an immediate refresh, go to the Worker in Cloudflare → Caching → Purge Cache

## Adding new ideas to Notion

1. Create a new page in the database
2. Fill in: Title, Category, Body, PS (optional), Energy (multi-select), App ID (unique slug e.g. `my-new-idea`), Status = Ready
3. Live within 1 hour

## Embedding in WordPress

Add this to your protected page via a Divi Code module:

```html
<iframe 
  src="https://dholmes127.github.io/selfcaring-idea-collection" 
  width="100%" 
  height="800px" 
  frameborder="0"
  style="border:none;">
</iframe>
```
