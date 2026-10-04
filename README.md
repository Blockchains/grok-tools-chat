# Grok Tools Chat

A chat assistant that can look up GitHub repos and do maths with tools

**Live:** https://blockchains.github.io/grok-tools-chat/ · composed by [grokhack-forge](https://github.com/Blockchains/grokhack-forge) · parts: [PARTS.md](PARTS.md) · manifest: [forge.json](forge.json)

- Archetype: `chat` · capabilities: streaming, tool_calling
- Grok via Vercel AI SDK `@ai-sdk/xai` (browser, bring-your-own key; the key only goes to api.x.ai)
- Default model `grok-4.7`

## Keys
If api.x.ai answers 403 because the xAI account is out of credits or over its spending limit, the app shows an **xAI credits needed** notice; outputs are never faked.

Visitors paste their own xAI API key in the page. CI runs an end-to-end request against api.x.ai: with the `XAI_API_KEY` repository secret it checks a live answer, without it it checks that api.x.ai rejects the unauthenticated call (needs key).

## Run locally
```bash
npm ci && npm run build && npm test && npm run e2e
```
Never commit keys; use `.env` (git-ignored) or repository secrets.

<!-- blocks:start -->
## Use as a building block

> **For AI agents and builders:** read [`AGENTS.md`](AGENTS.md) (setup, commands, structure, rules), [`llms.txt`](llms.txt) (doc map) and the machine-readable [`blocks.json`](blocks.json) ([schema](https://github.com/Blockchains/.github/blob/main/docs/BLOCKS-SCHEMA.md)). How all Blockchains blocks fit together: **[Build with Blocks](https://github.com/Blockchains/.github/blob/main/docs/BUILD-WITH-BLOCKS.md)** · org catalogue: [https://blockchains.github.io/blocks.json](https://blockchains.github.io/blocks.json).

**What it exports**

| Export | Type | Install / access |
|---|---|---|
| `live app` | web | `https://blockchains.github.io/grok-tools-chat/` |
| `forge.json / PARTS.md` | file | `composition manifest: archetype, capabilities, SDK part + commit, default model` |
| `src/grok.ts` | file | `src/grok.ts` |
| `src/tools.ts` | file | `src/tools.ts` |

`src/grok.ts` exports: `chat`, `listModels`, `describeError`, `isCreditsError`, `CREDITS_NOTICE`, `XAI_BASE_URL`

`src/tools.ts` exports: `localTools`, `calculate`, `nowIn`, `githubRepo`

**Minimal example** (this exact tool addition built and passed tests on 2026-10-04 in a freshly composed chat app)

```ts
// src/tools.ts: add a blockchain data tool (npm i github:Blockchains/blockchainlab-sdk)
import { BlockchainLab } from 'blockchainlab-sdk'
const bl = new BlockchainLab()
export const localTools = {
  stablecoin: tool({
    description: 'Stablecoin price vs peg and circulating supply by symbol.',
    inputSchema: z.object({ symbol: z.string().describe('e.g. USDC') }),
    execute: async ({ symbol }) => ({ results: [await bl.stablecoin(symbol)].filter(Boolean) }),
  }),
  // …calculate, current_time, github_repo
}
```

**Inputs → outputs**

- In: `XAI_API_KEY` (secret/env or pasted in the page)
- Out: `Grok output` (web page)

**Composes with**

- [Blockchains/grokhack-forge](https://github.com/Blockchains/grokhack-forge): the composer that generated it; re-compose for variants
- [Blockchains/grokhack-index](https://github.com/Blockchains/grokhack-index): where its SDK part and reference snippets come from
- [Blockchains/blockchainlab-sdk](https://github.com/Blockchains/blockchainlab-sdk): add blockchain data as tools (chat) or inputs (digest)

**Versioning & stability:** `reference`. Generated reference app; versions of the Grok SDK are pinned in package-lock/requirements and recorded in forge.json.
<!-- blocks:end -->

## License
MIT for the generated glue code. Dependencies keep their own licences (see PARTS.md).

## Contributing

Issues and pull requests are welcome. Please read the [contributing guide](https://github.com/Blockchains/.github/blob/main/CONTRIBUTING.md), [code of conduct](https://github.com/Blockchains/.github/blob/main/CODE_OF_CONDUCT.md) and [security policy](https://github.com/Blockchains/.github/blob/main/SECURITY.md) first.

---
Built by Blockchain Lab — [blockchainlab.com](https://blockchainlab.com/?utm_source=github&utm_medium=readme&utm_campaign=grok-tools-chat)
