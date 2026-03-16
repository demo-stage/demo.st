# Publishing demo.st to Claude Code Market

[Claude Code Market](https://www.ccmarket.dev/) (ccmarket.dev) is a marketplace for **sub-agents** used with [Claude Code](https://code.claude.com/). Agents are markdown files that guide Claude on when and how to use certain workflows—in our case, deploying to demo.st via MCP tools.

## What we provide

- **Agent repo:** [demo-stage/demo.st-Claude](https://github.com/demo-stage/demo.st-Claude) — agent file `demo-st.md` — Instructions for the “demo.st deploy” agent (when to use demo.st, tool workflow, setup, best practices).
- **MCP server:** demo.st is an **HTTP MCP** server at `https://demo.st/mcp`. Users must add it in Claude Code and set `DEMO_ST_MCP_TOKEN` for reserve/upload/clear/release.

The agent does not replace the MCP server; it tells Claude how to use the demo.st MCP tools once they are configured.

## How to submit

1. **Sign in at Claude Code Market**  
   - Go to [https://www.ccmarket.dev/agents/submit](https://www.ccmarket.dev/agents/submit).  
   - Click **Continue with GitHub** and authorize.

2. **Prepare the agent for download**  
   - The agent lives in a **separate repo:** [demo-stage/demo.st-Claude](https://github.com/demo-stage/demo.st-Claude). Push the contents of the `demo.st-Claude/` folder in this project to that repo so the raw URL works:
     ```bash
     curl -o ~/.claude/agents/demo-st.md "https://raw.githubusercontent.com/demo-stage/demo.st-Claude/main/demo-st.md"
     ```
   - Ensure `demo-st.md` is committed and pushed to the `main` branch of `https://github.com/demo-stage/demo.st-Claude`.

   **Push the agent repo (one-time):** From this project, the `demo.st-Claude/` folder holds the contents for [demo-stage/demo.st-Claude](https://github.com/demo-stage/demo.st-Claude). To populate the empty GitHub repo:
   ```bash
   cd "demo.st-Claude"
   git init
   git remote add origin https://github.com/demo-stage/demo.st-Claude.git
   git add .
   git commit -m "Add demo.st agent for Claude Code Market"
   git branch -M main
   git push -u origin main
   ```

3. **Fill out the submission form**  
   Use the following as a starting point (adjust if the form fields differ):

   | Field | Suggested value |
   |-------|------------------|
   | **Agent name** | demo.st — Deploy Agent |
   | **Short description** | Deploy static sites and demos to demo.st: reserve a subdomain, upload a zip, get a live link like yourproject.demo.st. Uses the demo.st MCP server. |
   | **Category** | Deployment / DevOps (or closest available) |
   | **Installation** | `curl -o ~/.claude/agents/demo-st.md "https://raw.githubusercontent.com/demo-stage/demo.st-Claude/main/demo-st.md"` |
   | **Usage** | "Use the demo-st agent to deploy this project to a live link" or "Publish the build to demo.st with subdomain my-app" |
   | **Prerequisites** | Claude Code with the demo.st MCP server configured and DEMO_ST_MCP_TOKEN set. Sign in at https://demo.st and add MCP URL https://demo.st/mcp with Authorization: Bearer \${env:DEMO_ST_MCP_TOKEN}. |

4. **Submit**  
   Submit the form. The team may review before listing. Once approved, the agent will appear in the marketplace and users can install it and use it with Claude Code (after configuring the demo.st MCP server).

## After submission

- Keep the agent in [demo-stage/demo.st-Claude](https://github.com/demo-stage/demo.st-Claude) in sync with demo.st behavior (new tools or workflow changes).
- If the marketplace allows, add a link to the demo.st docs (https://demo.st, https://demo.st/terms, https://demo.st/privacy) in the agent listing or in the agent file.

## Reference

- **Claude Code Market:** https://www.ccmarket.dev/  
- **Claude Code MCP docs:** https://code.claude.com/docs/en/mcp  
- **demo.st MCP endpoint:** https://demo.st/mcp  
