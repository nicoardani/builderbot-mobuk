# builderbot-mobuk

Slack Canvas agents for the Merchant Onboarding UK (Clearpay) team — including Fetch (Trustpilot, WHOIS, Fulfilment), Handover Generator, and more.

## Agents

| Agent | File | Description |
|-------|------|-------------|
| Fetch Agent | `agents/fetch-agent.md` | Trustpilot, Domain WHOIS & Fulfilment Timeframe checks |
| Handover Generator | `agents/handover-generator.md` | Auto-generates handover docs from JIRA (AMO project) |

## Usage

1. Copy the contents of the relevant agent file from `/agents/`
2. Paste into a Slack Canvas in your channel
3. Use the trigger commands listed in each agent

## Fetch Agent

Trigger: `Fetch <domain>` or `Check <URL>`

Returns:
- 📊 Trustpilot score, reviews & profile link
- 🌐 Domain WHOIS age, registrar & expiry
- 📦 Fulfilment timeframe assessment

## Handover Generator Agent

Trigger: `Handover <person name>` or `Handover me`

Returns:
- Categorised list of open AMO tickets (Priority / Monitor / Low Urgency)
- Key context and deadlines for each ticket
- Linked directly to JIRA tickets

## Team

Merchant Onboarding (UK) Clearpay

## License

Internal use only — Block, Inc.
