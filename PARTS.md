# Integration parts used by Grok Tools Chat

Composed by [grokhack.com /forge](https://grokhack.com/forge) from [Blockchains/grokhack-index](https://github.com/Blockchains/grokhack-index) (index generated 2026-10-04T14:56:15Z).

**Idea:** A chat assistant that can look up GitHub repos and do maths with tools

**Archetype:** `chat` · **Capabilities detected:** streaming, tool_calling

## Runtime dependency (installed, pinned to the indexed fork commit)

- `@ai-sdk/xai` 5.0.14 from [Blockchains/ai](https://github.com/Blockchains/ai/tree/08d7f0a75e1466d28c3b71c2be4c0d89d552acf9/packages/xai) (upstream vercel/ai, licence Apache-2.0)

Default model `grok-4.7` (newest model live on the composer's xAI account via `GET /v1/models`; preference grok-4.7, then grok-4.5). Newest general `grok-N.M` model referenced in the index: [Blockchains/xai-sdk-python@1d9e1df](https://github.com/Blockchains/xai-sdk-python/tree/1d9e1dffc9a0521ede0e6bc7f2b906177b940d34). Override with `XAI_MODEL` (digest) or the model picker (chat, live list from `GET /v1/language-models`).

## Reference implementations consulted (not copied; links pinned to the indexed commit)

- [Blockchains/pi `packages/ai/src/api/openai-completions.ts` L1603-1626](https://github.com/Blockchains/pi/blob/83692682f095528f8b71652ddacff7075e36e893/packages/ai/src/api/openai-completions.ts#L1603-L1626) · MIT · 112367 stars · capabilities: anthropic_compatible, openai_compatible, reasoning, streaming, structured_output, tool_calling, vision
- [Blockchains/OmniRoute `src/shared/constants/featureFlagDefinitions.ts` L944-967](https://github.com/Blockchains/OmniRoute/blob/23a11484862b3bb589a55e85b00e4ac53ffeb234/src/shared/constants/featureFlagDefinitions.ts#L944-L967) · MIT · 72848 stars · capabilities: mcp, streaming, structured_output, tool_calling
- [Blockchains/anything-llm `server/utils/agents/aibitat/providers/ai-provider.js` L371-394](https://github.com/Blockchains/anything-llm/blob/feb04ca0a57cda6d0b3a69c62578f0af44d388fc/server/utils/agents/aibitat/providers/ai-provider.js#L371-L394) · MIT · 66708 stars · capabilities: anthropic_compatible, openai_compatible, streaming, tool_calling, vision
- [Blockchains/opencodex `src/web-search/xai-executor.ts` L1-21](https://github.com/Blockchains/opencodex/blob/249462bf570555aad103957025eea96f7489c7eb/src/web-search/xai-executor.ts#L1-L21) · MIT · 16907 stars · capabilities: live_search, streaming, structured_output, tool_calling
- [Blockchains/xai-sdk-ts `src/types.ts` L479-502](https://github.com/Blockchains/xai-sdk-ts/blob/0092a5f7f313ed092ea1326ae147c22981165e82/src/types.ts#L479-L502) · Apache-2.0 · 51 stars · capabilities: image_generation, live_search, streaming, structured_output, tool_calling, vision, voice_realtime
- [Blockchains/opencode `packages/opencode/src/provider/provider.ts` L154-177](https://github.com/Blockchains/opencode/blob/907b3bc518fa48e90e8ec24dd327d13eee71c36c/packages/opencode/src/provider/provider.ts#L154-L177) · MIT · 211703 stars · capabilities: anthropic_compatible, openai_compatible, reasoning, streaming, structured_output
