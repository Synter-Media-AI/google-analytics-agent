# Google Analytics MCP Starter Kit — Manage GA4 with AI

> **This is a recipe repo.** The Synter MCP server itself lives at [Synter-Media-AI/mcp-server](https://github.com/Synter-Media-AI/mcp-server): 19 ad platforms, campaign creation on 14, one-click install in Cursor, Claude, ChatGPT, and VS Code. Issues, releases, and ⭐ go there.


[![MCP Compatible](https://img.shields.io/badge/MCP-compatible-blue)](https://modelcontextprotocol.io)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Platform: Google Analytics](https://img.shields.io/badge/Platform-Google%20Analytics%204-E37400)](https://analytics.google.com)

**Ask questions about your website traffic in plain English.** Open this repo in Amp, Cursor, or VS Code and query GA4 data with AI — pull reports, analyze conversion funnels, build audiences, and link Google Ads for attribution.

---

## Why Google Analytics + AI?

GA4 is the source of truth for website analytics — 28 million websites use it. But the GA4 interface is notoriously unintuitive. Building custom reports requires navigating nested menus, understanding dimensions vs metrics, configuring date comparisons, and interpreting sampling caveats.

Most marketers use GA4 at 10% of its capability. They check pageviews and bounce rate, then close the tab. The real power — funnel analysis, cohort reports, custom audiences, and cross-platform attribution — goes untapped because the UI is too complex.

An AI agent turns GA4 from a confusing dashboard into a conversation. Ask "where are my signups coming from?" and get a channel breakdown. Ask "which landing pages have the highest drop-off?" and get an actionable report.

**Best for:** Understanding website traffic and conversion attribution, building remarketing audiences, linking GA4 to Google Ads, diagnosing traffic drops, and answering "what's working?" questions.

---

## Quick Start (30 Seconds)

### Amp / Cursor / VS Code (Copilot)

1. **Get a free API key** at [syntermedia.ai/developer](https://syntermedia.ai/developer)
2. **Set the key:**
   ```bash
   export SYNTER_API_KEY=syn_your_key_here
   ```
3. **Open this repo** in your editor
4. **Start chatting** — MCP tools are pre-configured in `.mcp.json`

### Claude Desktop

Copy `claude_desktop_config.json` to your Claude config directory and replace the API key:

- **macOS:** `~/Library/Application Support/Claude/claude_desktop_config.json`
- **Windows:** `%APPDATA%\Claude\claude_desktop_config.json`

---

## What You Can Do

| Capability | Example |
|-----------|---------|
| **Traffic Reports** | "Show me traffic by source/medium for the last 30 days" |
| **Conversion Analysis** | "Which channels are driving the most signups?" |
| **Landing Page Performance** | "What are my top 10 landing pages by conversion rate?" |
| **Funnel Analysis** | "Show the drop-off rate at each step of my checkout funnel" |
| **Audience Building** | "Create an audience of users who visited pricing page but didn't sign up" |
| **Google Ads Linking** | "Link my GA4 property to Google Ads for conversion import" |
| **Real-Time Data** | "How many users are on the site right now? Which pages?" |
| **Cohort Analysis** | "What's the retention rate by signup week for the last 3 months?" |
| **Page Path Analysis** | "What's the most common navigation path from homepage to purchase?" |
| **Custom Events** | "Set up a custom event for video plays on the product page" |
| **Anomaly Detection** | "Traffic dropped 40% yesterday. What happened?" |

---

## Example Conversations

### 1. Diagnosing a Traffic Drop

> **You:** Our traffic dropped 40% last Tuesday. What happened?
>
> **Agent:** Let me pull your daily traffic with source breakdown around that date...
>
> **Findings:**
> | Source/Medium | Before (Mon) | After (Tue) | Change |
> |---|---|---|---|
> | google / organic | 4,200 | 1,890 | **-55%** |
> | google / cpc | 1,100 | 1,080 | -2% |
> | direct / (none) | 890 | 850 | -4% |
> | social / referral | 340 | 310 | -9% |
>
> The drop is almost entirely in **Google organic search**. Your paid traffic, direct, and social are unchanged. This suggests either:
>
> 1. **Google algorithm update** — Let me check... Yes, Google rolled out a core update on Monday evening. Multiple industry sources confirm ranking volatility.
> 2. **Indexing issue** — Let me check your top pages...
>
> Your top 5 organic landing pages lost an average of 12 positions. This looks like an algorithm update impact, not a technical issue.
>
> **Recommended actions:**
> - Don't panic — core updates often self-correct within 2-3 weeks
> - Check Search Console for manual actions (unlikely but worth confirming)
> - Monitor your top 20 keywords daily for the next 2 weeks
> - Focus on content quality improvements for affected pages

### 2. Building a Remarketing Audience

> **You:** I want to retarget people who viewed our pricing page but didn't sign up.
>
> **Agent:** I'll create a GA4 audience with these criteria:
>
> **Audience definition:**
> - Include: Users who viewed `/pricing` page (page_view event, page_location contains "/pricing")
> - Exclude: Users who triggered `sign_up` event
> - Lookback window: 30 days
> - Membership duration: 30 days
>
> **This audience will automatically sync to:**
> - Google Ads (if GA4-Ads linking is enabled) → Use for Search/Display remarketing
> - Any connected destination (Meta, DV360, etc.)
>
> **Current audience size estimate:** ~2,400 users in the last 30 days
>
> This is your highest-intent remarketing audience — they're interested enough to check pricing but haven't committed. Show them a targeted ad addressing common objections (price, features, competitor comparison).
>
> Want me to create this audience and suggest Google Ads remarketing campaign settings?

### 3. Conversion Funnel Analysis

> **You:** What's the conversion rate from first visit to signup? Where do people drop off?
>
> **Agent:** Let me build a funnel report with your key events...
>
> **Signup Funnel (last 30 days):**
>
> | Step | Users | Drop-off |
> |---|---|---|
> | Session Start | 45,200 | — |
> | Viewed Homepage | 38,400 | 15% left |
> | Viewed Features Page | 12,300 | 68% left |
> | Viewed Pricing Page | 4,800 | 61% left |
> | Started Signup Form | 1,920 | 60% left |
> | Completed Signup | 840 | 56% left |
>
> **Overall conversion rate: 1.86%** (840 / 45,200)
>
> **Biggest leak: Homepage → Features (68% drop-off).** Most visitors leave from the homepage without exploring further. This suggests your homepage isn't compelling enough to drive exploration.
>
> **Second biggest leak: Pricing → Signup Form (60% drop-off).** People check pricing and leave. This could be price shock, unclear value proposition, or missing social proof on the pricing page.
>
> **Quick wins:**
> 1. Add a clear CTA on the homepage that links directly to features
> 2. Add testimonials and case studies to the pricing page
> 3. Consider a "Start Free Trial" button on pricing (removes commitment anxiety)
> 4. Test exit-intent popups on the pricing page with a limited-time offer

### 4. Channel Attribution for Signups

> **You:** Which marketing channels are actually driving signups? Not just traffic.
>
> **Agent:** Here's your last 30 days, showing sessions AND signup conversions by channel:
>
> | Channel | Sessions | Signups | Conv Rate | Cost/Signup |
> |---|---|---|---|---|
> | Organic Search | 18,400 | 312 | 1.7% | $0 (free) |
> | Paid Search | 8,200 | 246 | 3.0% | $34 |
> | Social (organic) | 5,100 | 41 | 0.8% | $0 (free) |
> | Social (paid) | 3,800 | 114 | 3.0% | $22 |
> | Direct | 6,200 | 89 | 1.4% | — |
> | Email | 2,100 | 38 | 1.8% | ~$2 |
> | Referral | 1,400 | 31 | 2.2% | — |
>
> **Insights:**
> - **Paid Social is your most efficient paid channel** ($22/signup, 3.0% conversion)
> - **Organic Social has the worst conversion rate** (0.8%) — high traffic, low intent
> - **Organic Search is your volume driver** (312 signups at $0)
> - **Paid Search converts well** (3.0%) but costs more per signup ($34)
>
> **Attribution caveat:** This is last-click. Many signups touch multiple channels. Let me pull first-click attribution for comparison...
>
> With first-click: Organic Search gets credit for 380 signups (+22%), Paid Social drops to 82 (-28%). This means social drives awareness → people later search your brand and convert. Both channels are valuable for different reasons.

### 5. Enhanced Ecommerce Deep Dive

> **You:** I have an ecommerce site. What can GA4 tell me about my sales funnel?
>
> **Agent:** If you have enhanced ecommerce tracking set up, GA4 provides incredibly detailed purchase funnel data. Let me check your event configuration...
>
> ✅ Your ecommerce events are properly configured. Here's the full funnel:
>
> | Step | Event | Users | Revenue |
> |---|---|---|---|
> | Product View | `view_item` | 28,400 | — |
> | Add to Cart | `add_to_cart` | 4,260 | — |
> | Begin Checkout | `begin_checkout` | 2,130 | — |
> | Add Payment | `add_payment_info` | 1,704 | — |
> | Purchase | `purchase` | 1,363 | $142,800 |
>
> **Cart-to-Purchase rate: 32%** (industry avg is 25-30%, so you're above average)
> **View-to-Cart rate: 15%** (this is your biggest drop — industry avg is 8-12%, so you're actually good)
>
> **Product-level insights:**
> | Product | Views | Add to Cart % | Purchase % | Revenue |
> |---|---|---|---|---|
> | Premium Widget | 8,200 | 22% | 41% | $48,300 |
> | Starter Kit | 12,400 | 11% | 28% | $31,200 |
> | Accessories Bundle | 4,800 | 19% | 38% | $22,100 |
>
> Your Premium Widget has the highest add-to-cart AND purchase rate. It's your best product — feature it more prominently on the homepage and in ads.

---

## GA4 Tips from the Pros

1. **Set up enhanced ecommerce tracking first.** Revenue attribution is the foundation of everything. Without purchase events, GA4 can only tell you about traffic — not business impact.
2. **Link GA4 to Google Ads immediately.** This enables conversion import, audience sharing, and cross-platform attribution. It's free and takes 2 minutes.
3. **Use explorations, not standard reports.** GA4's standard reports are limited. Explorations (funnel, path, cohort) are where the real insights live.
4. **Check data retention settings.** GA4 defaults to 2 months of user-level data retention. Change to 14 months in Admin → Data Settings → Data Retention.
5. **Set up key events (conversions) immediately.** Mark your most important events (sign_up, purchase, lead_form_submit) as key events. This unlocks Smart Bidding in Google Ads.
6. **Don't ignore sampling warnings.** When GA4 samples data, results can be misleading. Use the Data API (which this agent uses) for unsampled reports on large datasets.
7. **Build audiences for every campaign type.** Pricing page visitors, blog readers, cart abandoners, repeat purchasers — each becomes a remarketing audience shared with Google Ads.

---

## FAQ

### Is there an MCP for Google Analytics?
Yes — this repo. It pre-configures the Synter MCP server for GA4 management and reporting. Works with Amp, Cursor, VS Code, and Claude Desktop.

### Can AI pull GA4 reports for me?
Yes. Ask questions in plain English — "what are my top traffic sources?" or "which pages have the highest bounce rate?" — and the agent queries the GA4 Data API and returns formatted results.

### Do I need the GA4 API?
No. The Synter MCP server handles GA4 API authentication. You just need a free API key from [syntermedia.ai/developer](https://syntermedia.ai/developer) and a connected GA4 property.

### Can the agent create GA4 audiences?
Yes. Describe your audience criteria and the agent creates it in GA4. Audiences sync automatically to Google Ads for remarketing.

### Can I compare GA4 data to Google Ads data?
Yes — when GA4 and Google Ads are linked, the agent can show both GA4 conversion data and Google Ads campaign data side by side for attribution analysis.

---

## Related Repos

- [google-ads-agent](https://github.com/Synter-Media-AI/google-ads-agent) — Google Ads campaign management
- [google-tag-manager-agent](https://github.com/Synter-Media-AI/google-tag-manager-agent) — Tag and event setup
- [conversion-tracking-agent](https://github.com/Synter-Media-AI/conversion-tracking-agent) — Verify tracking works
- [cross-platform-ads-agent](https://github.com/Synter-Media-AI/cross-platform-ads-agent) — Multi-channel reporting
- [shopify-agent](https://github.com/Synter-Media-AI/shopify-agent) — Ecommerce data sync
- [hubspot-agent](https://github.com/Synter-Media-AI/hubspot-agent) — CRM conversion attribution

---

## License

MIT — see [LICENSE](LICENSE) for details.

Built by [Synter](https://syntermedia.ai) · [Get API Key](https://syntermedia.ai/developer) · [Documentation](https://syntermedia.ai/docs)
