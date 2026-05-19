# builderbot-mobuk

Slack Canvas agents for the Merchant Onboarding UK (Clearpay) team.

## Agents

| Agent | File | Description |
|-------|------|-------------|
| Fetch Agent | `agents/fetch-agent.md` | Retrieves Trustpilot profile data, domain WHOIS age details, and fulfilment timeframe assessments for a supplied domain or URL. |
| Merchant Onboarding BuilderBot Assistant | `agents/mobassistant-agent.md` | Provides UK Clearpay Merchant Onboarding second-opinion support on verticals, business attributes, risk ratings, policy rules, required reviews, and escalation paths. |

## Usage

1. Copy the contents of the relevant agent file from `/agents/`.
2. Paste it into a Slack Canvas in your channel.
3. Use the trigger/input pattern listed in each agent file.

## Fetch Agent

**File:** `agents/fetch-agent.md`

**Triggers:** `Fetch <domain>` or `Check <URL>`

**Returns:**
- Trustpilot score, review count, rating breakdown where available, and profile link.
- Domain WHOIS registration date, domain age, registrar, and expiry date where available.
- Fulfilment timeframe assessment based on whether the business sells products, services, or both.
- Delivery page status, stated delivery timeframe, bespoke/handmade indicators, estimated fulfilment timeframe, and confidence level.

**Handles edge cases including:**
- No Trustpilot profile found.
- Private or unavailable WHOIS data.
- Invalid URL/domain input.
- Service-based businesses where physical fulfilment is not required.
- Product businesses with no delivery page, using vertical/product-type signals to estimate fulfilment.
- Hybrid businesses, assessing fulfilment for the product side only.

## Merchant Onboarding BuilderBot Assistant

**File:** `agents/mobassistant-agent.md`

**Input:** An onboarding agent's question about a vertical, business attribute, risk rating, eligibility, or policy rule.

**Returns:**
- UK-specific policy determination: Approved, Restricted, or Prohibited.
- Required risk reviews where applicable.
- Key conditions, policy notes, and operational considerations.
- Recommended next steps or escalation path.

**Knowledge base referenced by the agent:**
- UK Risk Onboarding Playbook.
- Global Merchant Category Policy (GMCP) v1.9.
- Master List and Rating of Verticals & Attributes.
- UK SMB Merchant Onboarding Support Channel Context.

**Key guidance covered:**
- UK vertical checks and regional ratings.
- Pricing defaults and approval requirements.
- Business attributes such as dropshipping, pre-orders, delivery timeframes, subscriptions, marketplaces, and foreign entities.
- Common UK prohibited and approved categories.
- Special cases including invasive beauty, pharmacies, eyewear, consumer electronics, ticketing, travel, and services.
- Risk contacts and escalation rules.

## Team

Merchant Onboarding (UK) Clearpay

## License

Internal use only — Block, Inc.
