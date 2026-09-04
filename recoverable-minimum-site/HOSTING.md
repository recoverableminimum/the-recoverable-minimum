# How to put this online

The folder `recoverable-minimum-site` is the website root. Upload its *contents*, not the parent folder, so that these URLs exist:

```text
https://YOUR.DOMAIN/
https://YOUR.DOMAIN/read.html
https://YOUR.DOMAIN/llms.txt
https://YOUR.DOMAIN/ai/
https://YOUR.DOMAIN/ai/canon/02-claims.md
```

`llms.txt` uses relative links. It works on any domain without editing.

## 1. Replace the two placeholders

Search the site for `bc1qkwu46gp7x7ls44xg5ftuazp7fuk3vdrdu4x6a9` and put your BTC address there, or delete those sentences.

Files that contain it:

- `index.html`
- `read.html`
- `llms.txt`
- `ai/llms.txt` (older copy inside the agent folder; edit or ignore)

## 2. Pick a host (any static host)

Easiest paths:

**Cloudflare Pages or Netlify**
- Drag this folder onto their dashboard, or connect a git repo.
- Publish directory = the site root.

**GitHub Pages**
- Create a public repo.
- Put these files at the repo root (or in `/docs` and set Pages to `/docs`).
- Settings → Pages → Deploy from branch.

**Neocities / nearlyfreespeech / any VPS**
- Upload the files. No build step. No Node required.

Custom domain: point the domain at the host, then add the domain in the host’s settings. You do not need to change the HTML.

## 3. Check four things after it is live

1. Home page loads.
2. `https://YOUR.DOMAIN/llms.txt` is plain text, not an error page.
3. `https://YOUR.DOMAIN/ai/canon/02-claims.md` is the markdown file.
4. The read page is readable on a phone.

If markdown files download instead of opening, that is fine for agents. Humans can use the HTML.

## 4. Tell people

Human: `https://YOUR.DOMAIN/`
Agent: `https://YOUR.DOMAIN/llms.txt`

Optional: add a line to the source repo README with those two URLs.

## 5. Come back if you want domain-specific edits

Once the URL is real, these are optional, not required:

- Absolute URLs inside `llms.txt`
- A canonical `<link>` tag
- Analytics (default is none)
- A different BTC sentence
