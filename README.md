<div align="center">

<img src="assets/cover.png" alt="RevenueCat through HeyMetra's MCP server" width="100%">

# RevenueCat &times; HeyMetra

**MRR, active subscriptions and trials as they stand right now.**

Your subscription revenue lives in RevenueCat. What you paid to get those subscribers does not. Ask about both in the same sentence.

[![MCP Registry](https://img.shields.io/badge/MCP_Registry-com.heymetra%2Fheymetra-1f6feb)](https://registry.modelcontextprotocol.io/v0/servers/com.heymetra%2Fheymetra/versions)
[![Transport](https://img.shields.io/badge/transport-Streamable_HTTP-444)](https://modelcontextprotocol.io/)
[![Auth](https://img.shields.io/badge/auth-OAuth_2.1-444)](https://heymetra.com/security/)
[![Connector page](https://img.shields.io/badge/heymetra.com-revenuecat-1f6feb)](https://heymetra.com/connectors/revenuecat/)

```
https://mcp.heymetra.com/mcp
```

</div>

---

## Ask it things like

> What is our MRR right now?

> How many subscriptions are active at this moment?

> How many trials are running right now?

> Can I see the same figures in EUR instead of USD?

> How did MRR move month by month this year?

No dashboard, no export, no query language. You ask in the assistant you already use and the answer comes back with the account it came from.

## Connect RevenueCat

**1. Create a V2 secret key in the project's settings**

RevenueCat dashboard → your project → Settings → API keys → New. Name it, choose V2 as the version, and give it read permissions.

> V2 is not optional here: a V1 key cannot read the project and its figures, however its permissions are set.

**2. Choose what the key may read and change**

Project configuration read, so the key can list the projects it may see; and charts metrics read, which is where MRR, revenue and every chart come from. A key with read permissions only cannot change anything in RevenueCat. To let your assistant propose changes too, give customer information read and write (granting a customer an entitlement for a set time, or taking back one you granted) and project configuration read and write (attaching a product to an entitlement, creating an offering). Each change waits for your approval.

**3. Copy the key and paste it into HeyMetra**

It starts with sk_. Choose RevenueCat on the Connections screen and paste it. It is stored encrypted and never shown again.

> A key that starts with appl_, goog_ or amzn_ is a PUBLIC SDK key, the one an app ships with. It cannot read anything and is not a secret.

**4. Pick the project**

One key can see several projects, and a RevenueCat project is usually one app. HeyMetra lists what the key can reach and one connection is one project.

**5. Add HeyMetra to the assistant you use**

Claude, ChatGPT, Grok, Perplexity, Claude Code, Codex, Cursor or Antigravity. Your RevenueCat project answers there once it connects.

The same steps are on the docs page: [RevenueCat setup guide](https://heymetra.com/docs/revenuecat/).

## Then add HeyMetra to your assistant

Add HeyMetra once and it is there in every conversation. The address is the same everywhere:

```
https://mcp.heymetra.com/mcp
```

### One command

```bash
npx add-mcp https://mcp.heymetra.com/mcp
```

[`add-mcp`](https://www.npmjs.com/package/add-mcp) is a third-party installer that writes the configuration for Claude Code, Codex, Cursor, Antigravity, VS Code and seventeen other agents. It infers the name from the address, so the server lands as `heymetra`. Run against this endpoint before it was written here.

### Or by hand

<details>
<summary><b>Claude</b> — Settings → Customize → Connectors → Add custom connector</summary>

Paste the address above into Settings → Customize → Connectors → Add custom connector.

_On Team and Enterprise plans, an owner adds the connector for the whole organization under Organization settings → Connectors, and each member then connects to it._

Full walkthrough: [heymetra.com/mcp/claude/](https://heymetra.com/mcp/claude/)
</details>

<details>
<summary><b>ChatGPT</b> — chatgpt.com/plugins → + → Add custom MCP server</summary>

Paste the address above into chatgpt.com/plugins → + → Add custom MCP server.

_Add it on chatgpt.com in a browser, because the mobile app cannot add one. Every ChatGPT plan can, Free included. In a Business, Enterprise or Edu workspace, an admin or owner decides whether members can add custom MCP servers. ChatGPT needs the full address, including /mcp at the end._

Full walkthrough: [heymetra.com/mcp/chatgpt/](https://heymetra.com/mcp/chatgpt/)
</details>

<details>
<summary><b>Grok</b> — grok.com/connectors → New Connector → Custom</summary>

Paste the address above into grok.com/connectors → New Connector → Custom.

_On Grok Business and Enterprise, a team admin has to provision the connector in xAI's cloud console before members can use it._

Full walkthrough: [heymetra.com/mcp/grok/](https://heymetra.com/mcp/grok/)
</details>

<details>
<summary><b>Perplexity</b> — Plugins → Add custom → Connector → Add MCP connector → Remote</summary>

Paste the address above into Plugins → Add custom → Connector → Add MCP connector → Remote.

_In an organization, members can add a custom connector only after an admin turns on Allow members to add custom connectors, which is off by default._

Full walkthrough: [heymetra.com/mcp/perplexity/](https://heymetra.com/mcp/perplexity/)
</details>

<details>
<summary><b>Claude Code</b> — claude mcp add --transport http</summary>

```bash
claude mcp add --transport http heymetra https://mcp.heymetra.com/mcp
```

_You can also add the server to a .mcp.json file at the project root. Run /mcp in a session to sign in and to check that it connected._

Full walkthrough: [heymetra.com/mcp/claude-code/](https://heymetra.com/mcp/claude-code/)
</details>

<details>
<summary><b>Codex</b> — ~/.codex/config.toml</summary>

```toml
[mcp_servers.heymetra]
url = "https://mcp.heymetra.com/mcp"
```

_Codex reads the server from an [mcp_servers.<name>] section in config.toml, and you sign in with codex mcp login <name>._

Full walkthrough: [heymetra.com/mcp/codex/](https://heymetra.com/mcp/codex/)
</details>

<details>
<summary><b>Cursor</b> — ~/.cursor/mcp.json, or .cursor/mcp.json in a project</summary>

```json
{
  "mcpServers": {
    "heymetra": { "url": "https://mcp.heymetra.com/mcp" }
  }
}
```

_Cursor signs in to HeyMetra without a client ID or secret, so the server entry needs no auth block._

Full walkthrough: [heymetra.com/mcp/cursor/](https://heymetra.com/mcp/cursor/)
</details>

<details>
<summary><b>Antigravity</b> — ~/.gemini/config/mcp_config.json, or .agents/mcp_config.json in a project</summary>

```json
{
  "mcpServers": {
    "heymetra": { "serverUrl": "https://mcp.heymetra.com/mcp" }
  }
}
```

_Antigravity's documented key for the address is serverUrl, though it also accepts url._

Full walkthrough: [heymetra.com/mcp/antigravity/](https://heymetra.com/mcp/antigravity/)
</details>

## What it may and may not touch

Propose a change to this account. Nothing is sent until you approve it, and HeyMetra cannot undo it afterwards.

Permissions are switched on per connection, and one you leave off is a tool your assistant never sees.

| Permission | What it covers | Changes anything? |
|---|---|---|
| **Full account access** | Lets your assistant read anything in this account to answer your questions. The figures are the provider's own, not ones HeyMetra has checked. It can also propose changes: none is applied until you approve it, and HeyMetra cannot undo one afterwards. | Yes — every change waits for your approval |

<details>
<summary>What each permission lets an assistant do, in full</summary>

- Ask anything about this account and get the answer from its live data. Reads only, and the figures are the provider's own rather than ones HeyMetra has checked.
- Propose a change to this account. Nothing is sent until you approve it, and HeyMetra cannot undo it afterwards.
</details>

Anything that would change something comes back as a proposal you approve, inside bounds that live in code rather than in a prompt: ±50% on a budget, 5 campaigns per action and 20 changes a rolling day, and an approval that expires after 30 minutes. [How that works](https://heymetra.com/security/).

## When something goes wrong

<details>
<summary>The key saves and no projects are offered.</summary>

**Why:** The key has no read permission on projects, so it can authenticate and see nothing.

**Fix:** Edit the key in RevenueCat and grant read on projects, then reconnect.

</details>

<details>
<summary>The project connects but the overview reports no metrics.</summary>

**Why:** Either the charts and metrics permission is missing, or the project genuinely has no transactions yet. RevenueCat answers both the same way.

**Fix:** Compare against the project's own Overview page in the RevenueCat dashboard. Figures there and none here is a permission; nothing in either is a new project.

</details>

<details>
<summary>Saving fails and the key was copied correctly.</summary>

**Why:** Usually a V1 key. It is a valid RevenueCat key, and it cannot read what this connector needs.

**Fix:** Create a new key and choose V2 as the version.

</details>

## What HeyMetra reads from RevenueCat

Connect with a V2 secret key from the RevenueCat project. One key can see several projects, and each project you pick becomes its own connection. Then ask your assistant about MRR, revenue, active subscriptions and trials, churn and conversion, as they stand now or day by day from RevenueCat's own charts, and about the project's products, entitlements, offerings and customers. When you connect, you choose whether your assistant may also propose changes, and every change it proposes waits for your approval.

<details>
<summary>About RevenueCat</summary>

RevenueCat manages in-app subscriptions and reports the revenue behind them (MRR, trials, conversions, churn, and LTV) across iOS, Android, and web in one place. It’s the system of record for mobile subscription revenue.
</details>

## One connection, not seven

The reason to read RevenueCat through HeyMetra rather than through a server that only knows RevenueCat is everything else it can answer in the same breath:

**Ads** — [Google Ads](https://github.com/zeisoft/google-ads-mcp)

**Analytics** — [Google Analytics 4](https://github.com/zeisoft/google-analytics-4-mcp) · [Google Search Console](https://github.com/zeisoft/google-search-console-mcp) · [PostHog](https://github.com/zeisoft/posthog-mcp)

**Ecommerce** — [Trendyol](https://github.com/zeisoft/trendyol-mcp) · [n11](https://github.com/zeisoft/n11-mcp) · [Çiçeksepeti](https://github.com/zeisoft/ciceksepeti-mcp) · [Amazon Seller Central](https://github.com/zeisoft/amazon-seller-central-mcp) · [ikas](https://github.com/zeisoft/ikas-mcp) · [WooCommerce](https://github.com/zeisoft/woocommerce-mcp)

**Revenue & CRM** — [Stripe](https://github.com/zeisoft/stripe-mcp) · [Zoho CRM](https://github.com/zeisoft/zoho-crm-mcp) · [Zoho SalesIQ](https://github.com/zeisoft/zoho-salesiq-mcp) · [Zoho Marketing Automation](https://github.com/zeisoft/zoho-marketing-automation-mcp)

**Mobile** — [AppsFlyer](https://github.com/zeisoft/appsflyer-mcp) · **RevenueCat** · [Adapty](https://github.com/zeisoft/adapty-mcp) · [App Store Connect](https://github.com/zeisoft/app-store-connect-mcp)

**Work** — [Jira](https://github.com/zeisoft/jira-mcp)

**Channels** — [Slack](https://github.com/zeisoft/slack-mcp) · [Telegram](https://github.com/zeisoft/telegram-mcp)

The full catalogue is at [heymetra.com/connectors/](https://heymetra.com/connectors/).

## Links

- [RevenueCat connector page](https://heymetra.com/connectors/revenuecat/)
- [RevenueCat setup guide](https://heymetra.com/docs/revenuecat/)
- [HeyMetra](https://heymetra.com/) — what the product is
- [Setup for every assistant](https://heymetra.com/mcp/)
- [Security and limits](https://heymetra.com/security/)
- [Pricing](https://heymetra.com/pricing/)
- [HeyMetra's own repository](https://github.com/zeisoft/heymetra-mcp)

---

<sub>Built by <a href="https://zeisoft.com">Zeisoft</a>, who make HeyMetra. Not affiliated with RevenueCat. This README is generated from HeyMetra's live connector catalogue and refreshed daily; corrections are welcome as issues.</sub>
