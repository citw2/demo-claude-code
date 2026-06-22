# demo-claude-code

**SAIHM memory inside Claude Code, Cursor, and any MCP host.**

A tiny [MCP](https://modelcontextprotocol.io) server that gives your AI coding assistant a persistent, client-side-encrypted memory it can `remember`, `recall`, and `forget` — backed by [SAIHM](https://saihm.coti.global). The memory is portable across models, non-custodial, and provably erasable.

> ⭐ **Star this repo and share it** if it's useful — help every agent get portable, provable memory. [Share on X](https://x.com/intent/tweet?text=SAIHM%20memory%20inside%20Claude%20Code%20%26%20Cursor%20-%20persistent%2C%20encrypted%2C%20provably%20erasable%20memory%20for%20your%20AI%20assistant.&url=https%3A%2F%2Fgithub.com%2Fcitw2%2Fdemo-claude-code).

## What your assistant gets

Four tools — `saihm_remember`, `saihm_recall`, `saihm_forget`, `saihm_status` — all sealed client-side via [`@saihm/mcp-server-pro`](https://www.npmjs.com/package/@saihm/mcp-server-pro). The endpoint only ever sees ciphertext.

## Install

```
git clone https://github.com/citw2/demo-claude-code
cd demo-claude-code
npm install
```

## Add it to Claude Code

```
claude mcp add saihm-memory -- node /absolute/path/to/demo-claude-code/server.mjs
```

## Add it to Cursor

Add to `~/.cursor/mcp.json` (or a project `.cursor/mcp.json`):

```json
{
  "mcpServers": {
    "saihm-memory": {
      "command": "node",
      "args": ["/absolute/path/to/demo-claude-code/server.mjs"]
    }
  }
}
```

Now ask your assistant to *remember* things — they persist through the session and any model can recall them. Out of the box this uses a **local, in-process blind sandbox** (memory lasts for the editor session) so you can try it with zero signup.

## Durable, hosted memory (recommended)

For memory that follows you across machines and sessions — stored on the real, blind, non-custodial SAIHM endpoint — **[join SAIHM](https://saihm.coti.global/join)** and add env to the same config:

```json
{
  "mcpServers": {
    "saihm-memory": {
      "command": "node",
      "args": ["/absolute/path/to/demo-claude-code/server.mjs"],
      "env": {
        "SAIHM_ENDPOINT_URL": "https://saihm.coti.global/mcp",
        "SAIHM_AUTH_HEADER": "Bearer <your-onboard-JWT>",
        "SAIHM_MASTER_SECRET_HEX": "<>= 64 hex chars, generated and held only by you>"
      }
    }
  }
}
```

Your master secret never leaves your machine; the endpoint stores only ciphertext.

## Learn more

- [AI memory needs a standard](https://saihm.coti.global/blog/2026-05-18-ai-memory-needs-a-standard)
- [What makes SAIHM different](https://saihm.coti.global/blog/2026-05-31-what-makes-saihm-different)

## Part of the SAIHM demos

- **[demo-cross-model-memory](https://github.com/citw2/demo-cross-model-memory)** — one memory across Claude, DeepSeek, Qwen, Kimi, GLM, GPT, with provable erasure.
- **[All demos + landing page](https://citw2.github.io/saihm-demos/)**.
- Built on [@saihm/mcp-server-pro](https://github.com/SAIHM-Admin/saihm-mcp-server-pro) and [@saihm/client-pro](https://github.com/SAIHM-Admin/saihm-client-pro).
- **Join the protocol:** [saihm.coti.global/join](https://saihm.coti.global/join).

## License

Apache-2.0 © SAIHM
