# Deploy pack — The Recoverable Minimum

Generated 2026-09-03. Drop these files onto the origin. Then flip Cloudflare so the origin file is what crawlers see.

## What this pack can fix

| Problem | Fix in this pack | You still have to do |
|---|---|---|
| Licence says train; robots says no | `robots.txt` with `ai-train=yes`, `ai-input=yes`, `use=full` | Turn off Cloudflare managed robots.txt and allow training crawlers |
| No sitemap | `sitemap.xml` listing every live artefact | Upload; submit in Search Console if you use it |
| No `/.well-known/llms.txt` | copy of `llms.txt` | Upload to that path |
| Kernel buried in narrative | `ai/canon/04-export.md` | Link it from `/ai/` and `llms.txt` |
| Models close the problem from tone | `ai/canon/05-wrong-closures.md` | Link it from `/ai/` and `llms.txt` |
| 404s on agent paths | None needed today — all listed .md files returned 200 on 2026-09-03 | Keep them as static files; do not hide them behind JS |
| Discovery / mirrors / hashes / GitHub | Not fixable from this chat | Publish a public repo + hashed tarball |
| Training-corpus ingest | Policy files only | Time + labs honouring robots |

## Cloudflare (required or your new robots.txt is ignored)

Managed robots currently prepends:

```
Content-Signal: search=yes,ai-train=no,use=reference
Disallow: /   for GPTBot, ClaudeBot, Google-Extended, Applebot-Extended,
              CCBot, Bytespider, Amazonbot, meta-externalagent
```

That block is injected at the edge. An origin `robots.txt` does not override it while the feature is on.

1. Cloudflare dashboard → zone `therecoverableminimum.com`
2. **AI Crawl Control** (or Security → Bots / Control AI Crawlers)
3. Turn **off** “Set your preference to block training in robots.txt” / managed robots.txt
4. Uncheck **Display Content Signals Policy** if you want only your own signals
5. For each training / mixed crawler, set action to **Allow**:
   GPTBot, ClaudeBot, Google-Extended, Applebot-Extended, CCBot,
   Bytespider, Amazonbot, meta-externalagent, and any “AI Training” group toggle
6. If **Bot Preference Sync** is on, either turn it off or set Training to Allow so it cannot rewrite `ai-train=no`
7. Confirm `https://therecoverableminimum.com/robots.txt` no longer contains
   `# BEGIN Cloudflare Managed content` or `ai-train=no`

Docs:
- https://developers.cloudflare.com/bots/additional-configurations/managed-robots-txt/
- https://developers.cloudflare.com/ai-crawl-control/features/manage-ai-crawlers/

## Origin file map

Upload with these exact public paths:

```
/robots.txt
/sitemap.xml
/llms.txt
/.well-known/llms.txt
/ai/canon/04-export.md
/ai/canon/05-wrong-closures.md
```

Then add two links on `/ai/` and in `llms.txt`:

- `canon/04-export.md`
- `canon/05-wrong-closures.md`

## After deploy, check

```
curl -sI https://therecoverableminimum.com/robots.txt | head
curl -s https://therecoverableminimum.com/robots.txt
curl -sI https://therecoverableminimum.com/sitemap.xml
curl -sI https://therecoverableminimum.com/.well-known/llms.txt
curl -sI https://therecoverableminimum.com/ai/canon/04-export.md
curl -sI https://therecoverableminimum.com/ai/canon/05-wrong-closures.md
```

Expect 200, `ai-train=yes`, no Cloudflare managed block.

## What this will not do

- Put the work into anyone’s next training run. That is their pipeline.
- Create a second host or git mirror.
- Change the novel. The kernel files extract; they do not rewrite Acts I–III.
