# builderbot-mobuk

Slack Canvas agents for the Merchant Onboarding UK (Clearpay) team.

## Agents

| Agent | File | Description |
|-------|------|-------------|
| Fetch Agent | `agents/fetch-agent.md` | Retrieves Trustpilot profile data, domain WHOIS age details, and fulfilment timeframe assessments for a supplied domain or URL. |
| Merchant Onboarding BuilderBot Assistant | `agents/mobassistant-agent.md` | Provides UK Clearpay Merchant Onboarding second-opinion support on verticals, business attributes, risk ratings, policy rules, required reviews, and escalation paths. |
| Rolling Reserve Calculator | `agents/rolling-reserve-calculator.md` | Extracts delivery/fulfilment breakdowns from merchant response images and calculates rolling reserve days, holding percentage, and admin portal reason code. |

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

## Rolling Reserve Calculator

**File:** `agents/rolling-reserve-calculator.md`

**Input:** An image of a merchant response containing delivery/fulfilment tier breakdowns. Optional separate GMV or Afterpay share-of-checkout values can be supplied if they are not visible in the image.

**Returns only:**
- Rolling Reserve Days.
- Rolling Reserve Holding %.
- Admin Portal Reason Code.

**Key calculation behaviour:**
- Validates that delivery tier shares total exactly 100% before calculating.
- Uses the upper bound for fulfilment ranges, such as `14-30 days` becoming `30 days`.
- Defaults to product merchant rules unless told the merchant is services-based.
- Defaults to Total GMV `100,000` and Afterpay SOC `13%` when those values are not visible or provided.
- Rounds reserve days up to the nearest 5-day increment.
- Rounds holding percentage up to the nearest 5% increment.
- Selects the admin portal reason code based on the share of orders outside 14 days, or uses category-specific codes when specified.

## Team

Merchant Onboarding (UK) Clearpay

## License

Internal use only — Block, Inc.
