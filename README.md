# LLM API Playground

A free playground for testing chat-completion APIs straight from your browser. Paste a key, pick a provider (or paste any OpenAI-compatible URL or cURL command), and test streaming, tool calling, structured output, latency and model availability in one place. No sign-up, no install, no analytics.

**Open it here: https://harshvardhan9084.github.io/llm-api-playground/**

## What you can use it for

- **Check which models your key can use.** Fetch the model list, then run a live probe that sends a tiny request to each model and marks it ✓ working, ⚠ rate-limited or billing issue, ✗ unavailable, or ? error. Pick from the dropdown and go.
- **Compare speed.** Time to first token, total time, tokens per second, token usage, reasoning tokens and cached tokens for every run. A repeat-N benchmark reports min, median, p90, max and mean, and the Runs table exports to CSV.
- **Test API features without writing code.** Streaming, tool/function calling (including sending tool results back), JSON mode, JSON-schema structured output, stop sequences, seed, top_p, penalties, reasoning effort and an `extra_body` field for anything else.
- **Debug requests.** See the exact request and raw response, then copy the request as cURL, Python or JavaScript.
- **Switch providers without losing your chat.** Send the same conversation to different providers and compare answers and speed.
- **Try local models.** Connect Ollama, LM Studio, vLLM or llama.cpp servers on localhost.

## Providers

| Tab | Default base URL |
|---|---|
| Inception (Mercury) | `https://api.inceptionlabs.ai/v1` |
| Google AI Studio (Gemini, OpenAI-compatible endpoint) | `https://generativelanguage.googleapis.com/v1beta/openai` |
| OpenRouter | `https://openrouter.ai/api/v1` |
| Together AI | `https://api.together.xyz/v1` |
| OpenAI | `https://api.openai.com/v1` |
| **Custom** | Detected for you (see below) |

Each tab adapts the interface: parameter names, value ranges, reasoning-effort options and provider-only controls (for example Inception's `diffusing` and `realtime` flags, or OpenRouter's `top_k`, `min_p` and attribution headers).

## Custom provider with auto-detection

On the **Custom** tab, paste any of the following into Smart setup:

- a base URL, even a partial one such as `api.example.com`
- a full endpoint URL such as `…/v1/chat/completions`
- a cURL command copied from a provider's docs
- or just a key with a recognizable prefix

The playground tries the likely `/v1`, `/openai/v1` and `/api/v1` variants, tests Bearer, `x-api-key`, `api-key` and query-string authentication, reads the model list, and checks whether the server wants `max_tokens` or `max_completion_tokens`. A log shows each step, and everything it fills in can be edited under **Advanced**. A dropdown of known endpoints (Groq, Mistral, DeepSeek, xAI, Fireworks, Cerebras, SambaNova, DeepInfra, Hyperbolic, NVIDIA NIM, Perplexity, Moonshot, Cohere, Ollama, LM Studio and more) is included.

## Chat view

Full-screen mode, adjustable text size, rendered Markdown and a status line with the model and timing.

## Privacy and your keys

- Requests go **directly from your browser to the provider** you choose. There is no server in between and no analytics.
- Your keys stay in your browser. Under **Key storage** you can remember them on this device, keep them for the current tab only, or encrypt them with a passphrase. The passphrase cannot be recovered.
- Use the playground only on a device you trust.

## Good to know

- **Some providers block browser requests (CORS).** If that happens you will see a "network or CORS" message. It is the provider's setting, not something the playground can bypass.
- **Ollama:** start it with `OLLAMA_ORIGINS=https://harshvardhan9084.github.io` so the page is allowed to reach it. Safari blocks `http://localhost` from secure pages.
- **Availability probes use your quota.** Each probed model gets a real 16-token request, so keep the "Probe up to" limit low on providers with hundreds of models.
- **If a provider rejects a parameter,** check the raw response and use `extra_body` to adjust the request. Provider APIs change over time.
- Inception's fill-in-the-middle tab is experimental, and with the `diffusing` option streamed text may replace itself instead of appending.

## Feedback

Found a bug or want a provider added? Open an issue in this repository.

## Disclaimer

This project is not affiliated with, endorsed by or sponsored by any provider it can connect to. Product and company names belong to their owners.
