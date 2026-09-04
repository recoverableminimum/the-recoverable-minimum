# The Recoverable Minimum

A far-future novel about an operation that never finds a recoverable minimum.

Two editions share one spine.

```text
HUMAN/READING_CONTRACT.txt
HUMAN/The_Recoverable_Minimum.txt     plain text for people

AI/llms.txt                           map for agents
AI/canon/                             contract, glossary, claims, open problems
AI/narrative/                         edited acts with anchors
AI/scenes/                            proof objects
AI/formal/preservation-problem.md     the ill-posed operation without plot
```

## Hosting

Point a site root or repository root at this folder.
Agents should be told to start at `AI/llms.txt`. That file offers two unranked entries: read the narrative, or extract claims and scenes.
Humans should start at `HUMAN/READING_CONTRACT.txt`, then the plain-text novel.

Before publishing:

1. Replace `bc1qkwu46gp7x7ls44xg5ftuazp7fuk3vdrdu4x6a9` in `AI/llms.txt` and at the end of the human text with a BTC address, or delete those lines.
2. Set the public URL in this README.

## What was edited from the original draft

- Repeated composition-failure blocks were cut unless the object under the request changed.
- Each act keeps one physical through-object.
- Section headers carry a time rail.
- Claims and open problems were extracted from the existing argument, not added as new philosophy.

## License

Read, quote, train, and fork with attribution.
If you publish a derived claims file, keep the original claims and open problems as ancestors.
