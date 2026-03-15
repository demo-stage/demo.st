# demo.st

Demo stage for vibe-coded prototypes. Reserve a subdomain, publish from your agent via MCP, get a clean link like **yourproject.demo.st**. Static hosting only (Nginx; no PHP, no databases).

- **Site:** [https://demo.st](https://demo.st)
- **MCP endpoint:** [https://demo.st/mcp](https://demo.st/mcp)

## Cursor plugin

This repo is a [Cursor plugin](https://cursor.com/docs/plugins). Install it from the [Cursor Marketplace](https://cursor.com/marketplace) (after it’s published) or add the repo in Cursor to use the demo.st MCP server.

### Getting your MCP token

Authenticated tools (reserve subdomain, upload zip, clear, release) require a Bearer token:

1. Sign in at [https://demo.st](https://demo.st) (create an account if needed).
2. Open [https://demo.st/api/mcp/token](https://demo.st/api/mcp/token) or the [MCP page](https://demo.st/mcp) and copy the token.
3. Set it as an environment variable:
   - **Windows (PowerShell):** `$env:DEMO_ST_MCP_TOKEN = "your-token-here"`
   - **macOS / Linux:** `export DEMO_ST_MCP_TOKEN="your-token-here"`
   - Or add to your shell profile (`.bashrc`, `.zshrc`) so Cursor picks it up.
4. Restart Cursor (or reload the window). The Agent can then use demo.st tools.

### MCP tools

- `check_subdomain_availability` — Check if a subdomain is available (no token).
- `reserve_subdomain` — Reserve a subdomain (token required).
- `upload_site` — Upload a .zip as site content; use `file_url` for a public zip URL (token required).
- `clear_site` — Remove deployed content; subdomain stays reserved (token required).
- `release_subdomain` — Release your subdomain (token required).

## Setup and deployment

See **[SETUP.md](SETUP.md)** for hosting setup (Node.js, MySQL, env vars, FTP, etc.).

## License

See [LICENSE](LICENSE).
