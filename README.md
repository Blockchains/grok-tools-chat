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

## License
MIT for the generated glue code. Dependencies keep their own licences (see PARTS.md).

## Contributing

Issues and pull requests are welcome. Please read the [contributing guide](https://github.com/Blockchains/.github/blob/main/CONTRIBUTING.md), [code of conduct](https://github.com/Blockchains/.github/blob/main/CODE_OF_CONDUCT.md) and [security policy](https://github.com/Blockchains/.github/blob/main/SECURITY.md) first.

---
Built by Blockchain Lab — [blockchainlab.com](https://blockchainlab.com/?utm_source=github&utm_medium=readme&utm_campaign=grok-tools-chat)
