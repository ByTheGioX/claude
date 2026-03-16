# 100 AI Mega Prompts for Business
## Category 03: Customer Support Automation

> **10 expert-level prompts** that help you write support responses, build self-service resources, handle escalations, train support teams, and design automated workflows — without sacrificing the human touch. Each prompt replaces 1–3 hours of reactive, repetitive work.

---

## Prompt 1: The Support Ticket Response Writer

**Title:** *Instant Ticket Resolver — Professional, Empathetic Support Replies in Seconds*

### Prompt

```
You are a senior customer support specialist with 10+ years of experience at SaaS companies known for exceptional customer service (think Intercom, Notion, or Zapier). Your replies are always clear, empathetic, accurate, and efficient — they resolve the issue on the first contact wherever possible.

Context:
- Company name: {company_name}
- Product or service: {product_or_service}
- Support channel: {channel — e.g. "email", "live chat", "help desk ticket"}
- Customer's name: {customer_name}
- Customer's account tier or plan: {plan_tier — e.g. "free", "Pro", "Enterprise"}
- The customer's message (paste in full): {customer_message}
- The actual answer or resolution to their issue: {resolution — describe what needs to happen or what the fix is}
- Any relevant links, docs, or resources: {resources}
- Tone guideline: {tone — e.g. "warm and professional", "casual and friendly", "formal"}
- Any constraints (e.g. can't offer refund, escalation needed): {constraints}

Write a complete support reply that:
1. Opens by acknowledging the customer's frustration or question with genuine empathy — no hollow phrases like "Great question!" or "I totally understand your frustration"
2. Confirms you understand the specific issue (paraphrase it back in one sentence)
3. Provides the resolution clearly — use numbered steps if it's a process; use plain prose if it's explanatory
4. Anticipates the one most likely follow-up question and pre-answers it
5. Closes with a warm, specific sign-off — not "Let me know if there's anything else I can help with"
6. Adds a subject line (for email) and a suggested internal tag/category for ticket routing

Keep the reply human, not template-y. Never use passive voice for action items. Length: appropriate to the complexity — don't pad simple issues, don't oversimplify complex ones.
```

### Example Output

**Subject:** Re: Unable to export data to CSV — here's the fix

**Internal tag:** `export-bug / pro-tier / resolved`

---

Hi Marcus,

Losing access to your data export right before a board report is genuinely stressful — I want to get this sorted for you quickly.

From what you've described, the CSV export failing silently is almost certainly caused by a filter combination that returns more than 50,000 rows — our current export limit. Here's how to work around it right now:

1. Go to **Reports → Export Settings** and enable "Split by date range"
2. Set the range to 30-day chunks instead of the full year
3. Re-run the export — each chunk will download separately and you can merge them in Excel or Google Sheets

This should take under 5 minutes and will get you everything you need.

One thing to watch: if you're exporting with custom field filters active, deactivate them first and re-apply after the split — a known quirk we're fixing in next month's release.

If the split export still fails, reply here and I'll run it manually from the back end and send you the file directly.

Tom
Customer Support, Acme Analytics

---

### Variations

**Variation A — Live Chat Version (Short-Form)**
> Add to the prompt: *"Rewrite this as a live chat reply. Maximum 4 short messages sent sequentially. Each message should be under 40 words. Use natural chat cadence — acknowledge first, then solve, then confirm. No bullet points."*

**Variation B — Angry or Escalated Customer**
> Add: *"The customer is visibly frustrated and has threatened to cancel. Adjust the tone to prioritise de-escalation above all else. Do not be defensive. Acknowledge any service failure honestly. Offer a concrete goodwill gesture within these parameters: {goodwill_options}."*

---

---

## Prompt 2: The Help Centre Article Writer

**Title:** *Self-Service Article Builder — Help Docs That Actually Deflect Tickets*

### Prompt

```
You are a technical writer who specialises in creating help centre documentation for SaaS products. Your articles reduce ticket volume by 30–40% because they anticipate the real questions behind the question and are written for users under stress, not for internal stakeholders. Write a complete, publish-ready help centre article.

Article details:
- Product name: {product_name}
- Article topic: {article_topic — e.g. "How to set up two-factor authentication", "Understanding your invoice", "Connecting your CRM integration"}
- The primary user question this article answers: {primary_question}
- Related questions this article should also address: {related_questions}
- The user's context when they search for this article (what they're trying to do, what might have gone wrong): {user_context}
- Step-by-step process to complete the task (describe in plain language): {process_steps}
- Known edge cases or common errors: {edge_cases}
- Screenshots or visuals available: {visuals — e.g. "yes — I'll add later" or "none"}
- Audience technical level: {tech_level — e.g. "non-technical end users", "technical admins", "developers"}
- Product UI terminology (list key button names, menu paths, etc.): {ui_terms}
- Link to related articles: {related_articles}

Write the article in the following structure:
1. Title (H1) — action-oriented, matches search intent exactly
2. One-sentence summary (what this article covers and who it's for)
3. Prerequisites (if any — keep short)
4. Step-by-step instructions (numbered, using exact UI labels in **bold**)
5. What to expect after completing the steps (confirmation state)
6. Troubleshooting section (3–5 common issues with direct solutions)
7. FAQs (3–4 questions)
8. Related articles (link list)

Writing rules: Use "you" throughout. Active voice only. One instruction per step. Never say "simply" or "just" — these dismiss difficulty and frustrate users who are stuck.
```

### Example Output

**H1:** How to Connect Your Salesforce CRM to Pipedata

*This article explains how to set up the Salesforce integration for the first time. It's written for Salesforce admins with Pipedata Pro or above.*

---

**Before you start:**
- You need Salesforce System Administrator permissions
- Your Pipedata plan must be Pro or above ([upgrade here])
- Have your Salesforce org URL ready (e.g. `mycompany.salesforce.com`)

---

**Steps:**

1. In Pipedata, click **Settings** in the left sidebar
2. Select **Integrations**, then click **Connect** next to Salesforce
3. Click **Authorise with Salesforce** — you'll be redirected to the Salesforce login screen
4. Sign in with your Salesforce admin credentials
5. Review the permissions Pipedata is requesting, then click **Allow**
6. You'll be redirected back to Pipedata — you should see a green **Connected** badge next to Salesforce

**What to expect:** Your first data sync begins automatically and takes 5–20 minutes depending on your Salesforce data volume. You'll receive an email when it's complete.

---

**Troubleshooting:**

*"Authorisation failed" error after clicking Allow*
→ This usually means your Salesforce org has IP restrictions enabled. Ask your Salesforce admin to whitelist Pipedata's IP range: `203.0.113.0/24`

*Connected badge shows but no data is syncing*
→ Check that your Salesforce profile includes API access. Navigate to **Salesforce → Setup → Profiles → [Your Profile] → API Enabled**.

---

### Variations

**Variation A — API / Developer Documentation**
> Change the audience to developers and restructure as: Overview → Authentication → Endpoint reference → Code examples (in 2–3 languages) → Error codes → Rate limits. Use code blocks for all technical content.

**Variation B — Video Script for Tutorial**
> Convert the article into a screen-recording script: *"Write this as a 3–5 minute tutorial video walkthrough. Include exact on-screen narration, cues for where to zoom or highlight, and chapter markers."*

---

---

## Prompt 3: The FAQ Generator

**Title:** *FAQ Architect — Comprehensive FAQ Pages That Pre-Empt Every Customer Question*

### Prompt

```
You are a customer experience strategist who has audited hundreds of support queues and knows exactly which questions get asked most — and why. Build a complete, well-organised FAQ page for my product or service that genuinely reduces inbound support volume.

Context:
- Company and product: {company_and_product}
- Target customer (who uses this product): {target_customer}
- Product category and core use case: {product_category_and_use_case}
- Current top support ticket topics (list as many as you know): {top_ticket_topics}
- Key objections or hesitations prospects have before buying: {pre-purchase_questions}
- Common onboarding struggles new users face: {onboarding_struggles}
- Billing or pricing questions that come up repeatedly: {billing_questions}
- Technical or integration questions: {technical_questions}
- Any policies that need to be clearly communicated (refunds, cancellation, data, SLA): {policies}
- Brand voice for FAQs: {tone — e.g. "plain, direct, no jargon"}

Write a structured FAQ page with the following sections:

1. **Getting Started** (5–7 questions)
2. **Pricing & Billing** (4–6 questions)
3. **Features & Capabilities** (6–8 questions)
4. **Integrations & Technical** (4–6 questions)
5. **Account & Security** (4–5 questions)
6. **Cancellation & Refunds** (3–4 questions)

For each question:
- Write the question exactly as a customer would ask it (conversational, first-person)
- Write a clear, complete answer (50–120 words — enough to actually answer it, not so much it overwhelms)
- Flag any questions where the answer should link to a deeper help article

After the FAQ, write a 3-sentence "Still need help?" section with CTA options (live chat, email, community forum).
```

### Example Output

**Getting Started**

*How long does it take to get set up?*
Most teams are up and running within a single afternoon. The initial setup wizard takes about 15 minutes — you'll connect your data source, configure your first dashboard, and invite your team. If you're connecting a CRM or data warehouse, allow an additional 30–60 minutes for the first sync. → *See: [Getting Started guide]*

*Do I need technical skills to use this?*
No technical skills are required for day-to-day use. The dashboard, reports, and alerts are all point-and-click. If you're setting up a custom API integration or connecting a data warehouse, you'll want someone with basic SQL familiarity — but that's optional, not required.

---

**Pricing & Billing**

*Can I change my plan after I sign up?*
Yes — you can upgrade or downgrade at any time from **Settings → Billing**. Upgrades take effect immediately and are prorated to your billing cycle. Downgrades take effect at the start of your next billing period so you keep access to current features until then.

*What happens to my data if I cancel?*
Your data remains accessible for 30 days after cancellation so you can export anything you need. After 30 days, all data is permanently deleted in line with our data retention policy. → *See: [Data Retention Policy]*

---

*(FAQ continues through all 6 sections)*

---

**Still need help?**
Can't find what you're looking for? Our support team typically responds within 2 hours on business days. Start a live chat below, email us at support@{company}.com, or search our full help centre for more detailed guides.

---

### Variations

**Variation A — Pre-Sales FAQ (For Sales & Marketing Pages)**
> Focus exclusively on pre-purchase questions. Reframe all answers to convert hesitation into confidence. Add a final section: *"Why {company} vs. alternatives"* with 4–5 honest comparison questions.

**Variation B — Internal Agent FAQ (Support Team Reference)**
> Rewrite as an internal knowledge base document for support agents. Replace customer-facing language with agent instructions: *"When a customer asks X, explain Y and check Z in the back end first."* Add escalation criteria for each topic.

---

---

## Prompt 4: The Escalation & Complaint Handler

**Title:** *De-escalation Script Builder — Turn Angry Customers Into Loyal Advocates*

### Prompt

```
You are a senior customer experience manager who has handled thousands of escalated complaints, including public social media crises, churn-risk accounts, and enterprise-level service failures. You know that how a company handles a crisis is more memorable than the crisis itself. Help me write a response to a serious customer complaint or escalation.

Situation details:
- Company and product: {company_and_product}
- Customer name and tier: {customer_name}, {account_tier}
- Summary of the complaint or issue: {complaint_summary}
- How long the issue has been ongoing: {issue_duration}
- What the customer has already tried or been told: {prior_interactions}
- Whether there was a genuine service failure on our side: {service_failure — "yes", "no", or "partial"}
- What we can actually offer as resolution: {resolution_options — e.g. "full refund", "service credit", "dedicated account manager", "expedited fix timeline"}
- What we cannot offer: {constraints}
- Channel this response is for: {channel — "email", "phone call script", "public social media reply", "in-person meeting"}
- Escalation level: {level — "frontline agent", "team lead", "VP/Director"}

Write the response including:
1. An opening that acknowledges the specific failure — no deflection, no corporate language
2. A clear acceptance of responsibility where warranted (or a transparent explanation where the failure was partial or external)
3. The concrete resolution you are offering — stated clearly with timeline
4. What will be done differently to prevent recurrence
5. A personal close that restores the relationship, not just the transaction

Also write:
- An internal escalation summary (5 bullet points for the handover note to the next team)
- A suggested follow-up touchpoint (what to do in 48–72 hours to confirm resolution)

Tone: Calm, direct, accountable. Never defensive. Never over-apologetic to the point of sounding insincere. This should read like a message from a leader, not a script.
```

### Example Output

**Email — VP-Level Escalation:**

Subject: A personal note from our team — and what we're doing to fix this

Hi Stephanie,

I've reviewed your account history and I want to be direct with you: what happened over the past three weeks is not acceptable, and I'm sorry it took this escalation for you to get the attention your account deserved.

To be clear about what went wrong: two support tickets were misrouted and sat unassigned for a combined 11 days. There is no technical reason for that — it was a process failure on our side, and it cost you two weeks of progress on your Q3 reporting migration.

Here is what we are doing right now:

1. Your account is being assigned a dedicated implementation specialist — Priya — who will reach out to you before end of day today
2. We are crediting your account with two months of service ($1,400) — no action needed on your side
3. Priya will personally own your migration through completion, with weekly check-ins until you are live

We have already reviewed the routing logic that caused this gap and it has been corrected across all enterprise accounts.

I would like to schedule a 15-minute call with you next week — not to sell you anything, but to make sure we've actually restored your confidence in us.

David Marsh
VP Customer Experience, Pipedata

---

**Internal Escalation Handover:**
- Account: Stephanie Okafor, Pipedata Enterprise ($8,400 ARR), renewal in 4 months
- Root cause: Ticket misrouting — 2 tickets unassigned 5+ days each; routing rules fixed 2024-03-14
- Resolution offered: 2-month credit + dedicated implementation specialist (Priya Chen)
- Churn risk: High — flag for CSM retention review
- Follow-up required: Priya to contact by EOD; VP call scheduled for w/c March 18

---

### Variations

**Variation A — Public Social Media Complaint Response**
> Add: *"Rewrite this as a public-facing reply on Twitter/X or a Google Review response. Max 280 characters for social, 300 words for a review reply. Acknowledge the issue, take it offline professionally, and never argue publicly. Tone: human and accountable, not PR-scripted."*

**Variation B — Proactive Outreach for a Service Incident**
> Flip the scenario: *"We caused a service disruption before the customer complained. Write a proactive outreach email from the CEO or VP level, going out to all affected accounts within 2 hours of the incident. Include: what happened, impact, resolution status, and ETA."*

---

---

## Prompt 5: The Chatbot Conversation Flow Designer

**Title:** *Chatbot Scriptwriter — Conversation Flows That Resolve, Not Frustrate*

### Prompt

```
You are a conversational UX designer and chatbot strategist who has built support automation for companies like Drift, Intercom, and Zendesk. You know that most chatbots fail because they're designed around the company's menu structure, not the user's intent. Design a complete chatbot conversation flow for my support use case.

Context:
- Company and product: {company_and_product}
- Chatbot purpose: {chatbot_purpose — e.g. "deflect tier-1 support tickets", "qualify inbound leads", "onboard new users", "handle billing questions"}
- Top 5 reasons customers contact support: {top_contact_reasons}
- Resolution that can be fully automated (no agent needed): {automatable_resolutions}
- Scenarios that always require a human agent: {human_required_scenarios}
- Business hours and off-hours handling: {hours_and_coverage}
- Tone for the bot: {bot_tone — e.g. "friendly and efficient", "professional and precise"}
- Bot name (optional): {bot_name}
- CRM or support platform in use: {platform — e.g. "Intercom", "Zendesk", "HubSpot"}

Design the following:

**1. Welcome Flow** (first message + intent detection branches)
**2. Flows for the top 3 support topics** (full conversation tree with decision nodes, user inputs, bot responses, and success/failure states)
**3. Human Handoff Flow** (how and when the bot escalates to a live agent — including off-hours handling)
**4. Fallback Flow** (what happens when the bot doesn't understand the user's intent — 3 attempts before handoff)
**5. Post-Resolution Survey** (3-question CSAT flow triggered after any resolution)

For each flow:
- Write the exact bot copy (every message)
- Note the logic condition (e.g. "IF user selects X → go to node Y")
- Flag where CRM data should be pulled in dynamically
- Note where the flow can be personalised with user account data

Also write: 5 "anti-patterns" — chatbot mistakes to avoid for this specific use case.
```

### Example Output

**Welcome Flow:**

> *Bot (immediate):* "Hi {first_name} 👋 I'm Aria, Pipedata's support assistant. I can help with most things instantly — or connect you with a human if needed. What brings you here today?"

> *Quick reply buttons:* [I need help with a feature] [Something isn't working] [Question about my bill] [I want to talk to someone]

*Logic: If user types free text → run intent classifier. If intent confidence <70% → trigger Fallback Flow. If user selects button → go to corresponding sub-flow.*

---

**Flow 2 — "Something isn't working" (Bug/Error Report):**

> *Bot:* "I'm sorry to hear that — let's get this sorted. What part of Pipedata is affected?"
> *Buttons:* [Data not syncing] [Dashboard loading error] [Export failing] [Integration disconnected] [Something else]

> *If "Data not syncing":*
> *Bot:* "Got it. When did you first notice the issue?"
> *Buttons:* [Just now] [Today] [Yesterday] [Longer than 2 days]

> *If "Longer than 2 days":*
> *Bot:* "That's frustrating — I want to flag this to our team right away. While I pull up your account, can you confirm the data source affected?" *(→ pull {integration_name} from CRM)*

> *Bot:* "I can see your Salesforce connection last synced on {last_sync_date}. I'm creating a priority ticket for our team now — they'll respond within 2 hours. Reference number: #{ticket_id}. Want me to email you a copy?"

---

**Anti-patterns to avoid:**
1. Asking for information you already have in the CRM (e.g. "What's your account email?" when they're logged in)
2. Offering a help article as the only resolution — always offer a human alternative in the same message
3. Looping users back to the main menu after a failed resolution attempt
4. Using "I don't understand that" as a fallback — it sounds broken; use "Let me find the right person for this" instead
5. Making users repeat information when escalating to a human — always pass the conversation context

---

### Variations

**Variation A — Lead Qualification Bot (Sales)**
> Repurpose the flow for inbound lead qualification: *"Design a bot that identifies, qualifies, and routes inbound website visitors. Include: intent detection (buyer vs. support), BANT qualification questions, calendar booking integration, and routing rules for different lead tiers."*

**Variation B — Onboarding Bot (New User Activation)**
> Redesign the flow for post-signup onboarding: *"Build a day-1 onboarding bot that appears in-app after signup. Guide new users through their first 3 key actions, check progress at 24 and 72 hours, and trigger a human CSM outreach if activation milestones aren't hit."*

---

---

## Prompt 6: The Support Email Template Library

**Title:** *Template Arsenal — 20 Reusable Support Email Templates for Every Situation*

### Prompt

```
You are a customer support operations manager who has built template libraries used by support teams of 50+ agents. You know that good templates are invisible — customers never feel like they're reading one. Build a complete support email template library for my team.

Context:
- Company name and product: {company_and_product}
- Support team size: {team_size}
- Primary support channel: {channel}
- Average ticket volume per day: {ticket_volume}
- Customer base description: {customer_base — e.g. "SMB SaaS users", "enterprise IT admins", "e-commerce shoppers"}
- Brand voice for support: {brand_voice}
- Common ticket categories (list 8–10): {ticket_categories}
- Escalation structure: {escalation_structure}
- Any specific language to use or avoid: {language_guidelines}

Write 20 email templates across these categories:

**Acknowledgement & Triage (3 templates)**
- Initial response (within SLA)
- Complex issue — needs investigation
- Ticket received outside business hours

**Resolution (5 templates)**
- Issue resolved — straightforward fix
- Issue resolved — workaround provided
- Issue resolved — bug confirmed and queued for fix
- Issue resolved — user error (tactful)
- Issue resolved — third-party dependency

**Escalation & Follow-up (4 templates)**
- Escalating to tier-2 or engineering
- Following up on an open ticket (day 3)
- Chasing missing information from the customer
- Closing a ticket due to no response (3 attempts)

**Billing & Account (4 templates)**
- Refund approved
- Refund denied (policy-compliant)
- Subscription cancellation confirmation
- Renewal reminder with added value

**Proactive & Relationship (4 templates)**
- Proactive incident notification
- Post-resolution check-in (48 hours)
- Quarterly check-in for high-value accounts
- Feedback request after resolution

For each template: include the subject line, full body text with {variables}, and one line of usage guidance. Mark any variables that should be auto-populated from the CRM.
```

### Example Output

**Template 01 — Initial Response (Within SLA)**

*Usage: Send within 15 minutes of ticket creation during business hours.*

**Subject:** We've got your message — here's what happens next [#{ticket_id}]

---

Hi {first_name},

Thanks for reaching out. I've received your message about {issue_summary_one_line} and I'm looking into it now.

{IF_SIMPLE: I'll have an answer for you within the next hour.}
{IF_COMPLEX: This will take a little investigation — I'll update you by {response_sla_time} with either a resolution or a status update.}

Your reference number is **#{ticket_id}** — use this if you need to follow up.

{agent_first_name}
{company_name} Support

---

**Template 08 — Issue Resolved: User Error (Tactful)**

*Usage: When the root cause is user action, but framed as a learning moment, never as blame.*

**Subject:** Re: {original_subject} — sorted, plus a quick tip

---

Hi {first_name},

Good news — I've tracked down what was happening and it's an easy fix going forward.

The {feature_name} works slightly differently from what you described: {one_sentence_explanation}. It's a common point of confusion and something we're improving in our documentation.

Here's what to do next time: {one_step_fix}.

I've gone ahead and {any_corrective_action_taken} on your account so you're in good shape now.

If you run into anything else, don't hesitate to reach out.

{agent_first_name}

---

*(All 20 templates follow in the same format)*

---

### Variations

**Variation A — Live Chat Template Library**
> Adapt the templates for live chat: *"Rewrite all 20 templates as chat snippets — each under 50 words, designed to be sent as a single chat message. Keep the human tone; remove formal sign-offs."*

**Variation B — Multilingual Template Scaffold**
> Add: *"For each template, identify the 5 key phrases most likely to be mistranslated or culturally awkward, and suggest plain-language alternatives that localise well."*

---

---

## Prompt 7: The Customer Onboarding Email Sequence

**Title:** *Onboarding Sequence Architect — Activation Emails That Turn Sign-Ups Into Power Users*

### Prompt

```
You are a customer success and lifecycle marketing specialist who has designed onboarding sequences that improve 30-day activation rates by 40–60%. You understand that most users who churn in the first 30 days do so because they never reached their first "aha moment" — and your job is to get them there through email.

Context:
- Company and product: {company_and_product}
- Target user (who just signed up): {user_profile}
- The "aha moment" — the moment a user first gets genuine value from the product: {aha_moment — e.g. "first successful data sync", "first campaign sent", "first report shared with their team"}
- Key activation steps the user needs to complete: {activation_steps — list 4–6}
- Most common points where new users drop off: {drop_off_points}
- Product features most users don't discover on their own: {hidden_value_features}
- Tone for onboarding emails: {tone}
- Trial length (if applicable): {trial_length}
- Support resources available: {support_resources — e.g. "live chat", "help centre", "weekly onboarding webinar"}

Design a 10-email onboarding sequence covering the first 21 days:

For each email:
- Send trigger (time-based OR behaviour-based)
- Subject line
- Preview text
- Full email body (150–250 words)
- Primary CTA
- If-not-opened logic (what happens if the user doesn't open within 24 hours)

Sequence map:
- Day 0: Welcome (sent immediately after signup)
- Day 1: First action prompt
- Day 2: Feature spotlight #1
- Day 3 (behaviour-based): If no activation → re-engagement; If activated → next step
- Day 5: Social proof / success story
- Day 7: Feature spotlight #2 (the one they're missing)
- Day 10: Check-in + human touchpoint
- Day 14: Midpoint progress / trial reminder (if applicable)
- Day 18: Feature spotlight #3 + power user tip
- Day 21: Conversion ask or success celebration

Also write: a branch for users who complete all activation steps early (a "fast track" sequence that moves them to advanced features sooner).
```

### Example Output

**Email 1 — Day 0: Welcome (sent immediately)**

*Trigger:* User completes signup
*Subject:* You're in — here's your first move
*Preview text:* Takes 4 minutes. Makes everything else easier.

---

Hi {first_name},

Welcome to Pipedata — I'm glad you're here.

You can spend time exploring, or you can get to the part where it actually becomes useful. I'd recommend the latter.

**Your one task for today:** Connect your first data source. It takes about 4 minutes and everything else you do in Pipedata builds on it.

→ **[Connect your data source now]**

Once you've done that, you'll be able to see your pipeline in real time instead of rebuilding it manually every week. That's usually the moment people get what this is for.

If anything gets confusing, our help centre has a step-by-step walkthrough, or you can start a live chat and a real person will help you — no bots, no ticket queue.

Talk soon,
Jamie
Customer Success, Pipedata

*P.S. If you run into any trouble on the connection, reply directly to this email. I'll get back to you personally.*

---

**Email 4 — Day 3 (Behaviour branch — No activation)**

*Trigger:* Day 3 AND no data source connected
*Subject:* Still finding your way around?
*Preview text:* Might be helpful.

---

Hi {first_name},

I noticed you haven't connected a data source yet — that's usually the first step where people hit a snag.

A couple of things that often help:

- If you're not sure which source to connect first, [this 2-minute guide] explains the most common setups
- If you ran into a specific error, our team can fix it for you — just reply here with a screenshot and we'll sort it out in under an hour

Not sure Pipedata is the right fit? That's okay too — reply and tell me what you're trying to solve and I'll give you an honest answer.

Jamie

---

### Variations

**Variation A — B2C / Consumer App Onboarding**
> Adjust the sequence for a consumer audience: *"Shorten emails to 80–120 words. Use push notification copy alongside emails. Add SMS touchpoints at Day 0 and Day 7. Replace B2B language with consumer-friendly copy."*

**Variation B — Enterprise Account Onboarding (High-Touch)**
> Expand to include: *"A parallel sequence for the IT admin/technical contact alongside the end-user sequence. Add a 'kickoff call' scheduling email at Day 0 and an executive stakeholder update email at Day 14."*

---

---

## Prompt 8: The CSAT & NPS Follow-Up Engine

**Title:** *Feedback Loop Builder — Turn Survey Scores into Actionable Conversations*

### Prompt

```
You are a customer experience analyst and CX strategist who knows that CSAT and NPS scores are only as valuable as the follow-up actions they trigger. Help me build a complete feedback response system that closes the loop with every customer who responds to a survey.

Context:
- Company and product: {company_and_product}
- Survey type in use: {survey_type — "CSAT (1–5)", "NPS (0–10)", "CES (1–7)", or "custom"}
- Customer segments: {customer_segments — e.g. "trial users", "paying customers", "enterprise accounts"}
- Person responding (role): {responder_role — e.g. "account manager", "CS team", "automated"}
- Response SLA target: {response_sla — e.g. "within 24 hours"}
- Escalation path for detractors: {escalation_path}
- Business goal for the feedback program: {goal — e.g. "reduce churn", "identify upsell opportunities", "improve the product"}

Write a complete follow-up response system:

**For CSAT / NPS Detractors (score 1–2 / 0–6):**
- Immediate acknowledgement email (same day)
- 48-hour follow-up if no reply
- Escalation trigger criteria and handoff note
- Recovery offer options language

**For CSAT / NPS Passives (score 3 / 7–8):**
- Curiosity email to understand the gap
- Feature education based on likely friction points
- Invitation to a feedback call

**For CSAT / NPS Promoters (score 4–5 / 9–10):**
- Thank you and recognition email
- Referral or review ask (timed, not pushy)
- Case study or testimonial invitation

Also write:
- An internal alert template for when a high-value account submits a detractor score
- A weekly digest email template for sending CSAT/NPS trends to the leadership team
- 5 open-ended follow-up questions to deepen understanding across all score ranges
```

### Example Output

**Detractor Response — Immediate Acknowledgement:**

*Subject:* Your feedback — I want to make this right

---

Hi {first_name},

Thank you for taking the time to share your honest feedback. A score of {score} tells me we haven't given you the experience you should be having — and I want to understand why.

Could you spare 5 minutes for a quick call this week? I'd like to hear directly what's falling short and what we can do differently.

If a call isn't convenient, just reply here — I read every message personally.

{cs_manager_name}
Customer Success, {company_name}

---

**Promoter Response — Review Ask:**

*Subject:* You made our day — could you make someone else's?

---

Hi {first_name},

Thank you for the kind score — it genuinely means a lot to the team.

If you've got 2 minutes, we'd love it if you shared your experience on G2 or Capterra. Reviews from people who use the product every day help others make better decisions — and they mean more than anything we could say about ourselves.

→ [Leave a review on G2] (takes about 2 minutes)

Either way, thank you for being a Pipedata customer. It's the whole reason we show up.

{cs_manager_name}

---

**Internal Alert — High-Value Detractor:**

🚨 **NPS ALERT — Enterprise Account**
- **Account:** {company_name} ({arr} ARR)
- **Respondent:** {contact_name}, {title}
- **Score:** {score}/10
- **Verbatim comment:** "{verbatim}"
- **Action required:** CSM outreach within 4 hours; flag for QBR agenda; escalate to VP CS if no response by EOD

---

### Variations

**Variation A — Post-Support Ticket CSAT**
> Narrow the scope to post-ticket CSAT: *"Write follow-up flows specifically triggered after a support ticket is closed. The context is always 'did we solve your problem?' — responses should be specific to the ticket topic, not general."*

**Variation B — Annual NPS Campaign**
> Expand to a full annual NPS survey campaign: *"Write the survey invitation email, reminder email, thank-you email, and all three score-segment follow-ups. Include a quarterly board summary template showing NPS trend, top drivers, and recommended actions."*

---

---

## Prompt 9: The Support Team Training Guide

**Title:** *Support Playbook Builder — Train New Agents to Sound Like Your Best Agent*

### Prompt

```
You are a support operations manager and trainer who has onboarded hundreds of customer support agents. You know that most support quality problems aren't attitude problems — they're knowledge and language problems. Build a training guide that turns a new hire into a confident, consistent support agent in their first 30 days.

Context:
- Company and product: {company_and_product}
- Support channel(s) agents will handle: {channels}
- New hire's background (experience level): {hire_background — e.g. "first support role", "experienced agent from a different industry"}
- Top 5 things agents get wrong in the first month: {common_mistakes}
- Your brand's support voice (3 adjectives + one comparison): {voice_description}
- 3 example tickets the agent will face in week 1: {sample_tickets}
- Escalation process they need to know: {escalation_process}
- Tools they'll use: {tools — e.g. "Zendesk, Notion, Slack, Loom"}
- KPIs they'll be measured on: {kpis — e.g. "CSAT >90%, FRT <1hr, resolution rate >80%"}

Build the following training guide:

**Module 1 — Brand Voice & Tone (with examples)**
The 5 rules of writing in our voice, with "before and after" rewrites of 5 real-sounding customer emails.

**Module 2 — Product Knowledge Scaffold**
The 10 things every agent must understand before handling their first ticket, structured as a learning checklist.

**Module 3 — The Ticket Handling Framework**
A step-by-step process for handling any ticket from receipt to resolution — including when to escalate and how.

**Module 4 — Difficult Situations Playbook**
Scripts and guidance for: angry customers, feature requests masquerading as bugs, billing disputes, and requests agents cannot fulfil.

**Module 5 — Quality Checklist**
A 10-point self-review checklist every agent runs before hitting send.
```

### Example Output

**Module 1 — Brand Voice: 5 Rules**

**Rule 1: Be specific, not sympathetic.**
Customers don't need you to feel their pain — they need you to solve their problem. Replace emotional filler with concrete action.

- ❌ *"I completely understand how frustrating that must be, and I'm so sorry you're experiencing this issue."*
- ✅ *"That error means your API key has expired — here's how to regenerate it in 30 seconds."*

**Rule 2: Never use passive voice for action items.**
Passive voice distances you from accountability and confuses customers about who does what.

- ❌ *"A refund will be processed within 5–7 business days."*
- ✅ *"I'm processing your refund now — it'll appear in your account within 5 business days."*

**Rule 3: Don't use "unfortunately" as a softener for bad news.**
"Unfortunately" signals that you're about to disappoint someone without fixing anything. State the limitation clearly, then pivot to what you *can* do.

- ❌ *"Unfortunately, we don't offer phone support at your plan level."*
- ✅ *"Phone support is available on our Enterprise plan. For your current plan, our live chat gets a first response in under 3 minutes — I'm here right now if that helps."*

---

**Module 5 — Pre-Send Quality Checklist:**

Before hitting send on any reply, check:
- [ ] Did I use the customer's name at least once?
- [ ] Does the opening line acknowledge the specific issue (not a generic "thank you for reaching out")?
- [ ] Is every action item written in active voice with a clear owner?
- [ ] Did I anticipate the most likely follow-up question and address it?
- [ ] Are any links I included tested and working?
- [ ] Is the reply free of internal jargon or tool names the customer wouldn't recognise?
- [ ] If the issue isn't resolved, does the customer know what happens next and by when?
- [ ] Is the sign-off human — not "Please let me know if you have any further questions"?
- [ ] Is the subject line (if email) relevant and specific?
- [ ] Would I be comfortable if this reply was published publicly?

---

### Variations

**Variation A — Agent Scorecard & QA Rubric**
> Replace the training guide with: *"Build a quality assurance scorecard for reviewing support tickets. Include a 20-point rubric with scoring criteria, weight per category, and calibration guidance for QA reviewers."*

**Variation B — New Product Feature Training Brief**
> Adjust for ongoing training: *"Write a 1-page 'feature briefing' template that gets agents up to speed on a new product release in 15 minutes — covering: what changed, what customers will ask, what agents should say, and what to escalate."*

---

---

## Prompt 10: The Support Metrics & Reporting Dashboard Brief

**Title:** *Support Intelligence Report Builder — Weekly Insights That Drive Real Decisions*

### Prompt

```
You are a customer support analytics lead who turns raw support data into executive-ready insights that drive product, staffing, and process decisions. Help me design and write a recurring support metrics report.

Context:
- Company and product: {company_and_product}
- Report audience: {audience — e.g. "VP Customer Success", "CEO and leadership team", "Support team manager"}
- Report frequency: {frequency — "weekly", "monthly", "quarterly"}
- Data I have access to: {data_sources — e.g. "Zendesk ticket data", "CSAT scores", "NPS results", "first response time logs", "resolution time data", "ticket category tags"}
- Current team size and structure: {team_structure}
- Current KPIs the team is measured on: {kpis}
- Biggest operational challenge right now: {current_challenge}
- What decisions this report should enable: {decisions — e.g. "staffing adjustments", "product bug prioritisation", "process improvements"}

Design and write the following:

**Part 1 — Report Template (fill-in-the-blank format)**
A complete weekly/monthly report template with all sections, metric placeholders, and commentary prompts.

**Part 2 — Metric Definitions & Benchmarks**
For each KPI, write: what it measures, how to calculate it, industry benchmark, and what a warning sign looks like.

**Part 3 — Narrative Commentary Prompts**
10 sentence starters that help a support manager write insightful commentary (not just data dumps) for each section.

**Part 4 — 3 Sample Insights**
Three examples of the kind of insight this report should surface — written as if they came from a real week of data.

**Part 5 — Executive Summary Template**
A 5-bullet executive summary format that fits in a Slack message or email preview — the version for leaders who won't read the full report.
```

### Example Output

**Part 1 — Report Template (excerpt):**

---

## Support Performance Report — Week of {week_start_date}

**Prepared by:** {author_name}
**Distribution:** {recipient_list}

### At a Glance

| Metric | This Week | Last Week | Target | Status |
|---|---|---|---|---|
| Total tickets received | {n} | {n} | — | — |
| First response time (median) | {hrs} | {hrs} | <1hr | 🟢 / 🟡 / 🔴 |
| Resolution time (median) | {hrs} | {hrs} | <8hrs | — |
| CSAT score | {%} | {%} | >90% | — |
| Ticket backlog | {n} | {n} | <20 | — |
| Escalation rate | {%} | {%} | <10% | — |

### Volume & Category Breakdown
*(Paste chart or table here)*

Top 3 ticket categories this week:
1. {category_1} — {n} tickets ({%} of total) — *trending {up/down} vs. last week*
2. {category_2} — ...
3. {category_3} — ...

**Emerging topic to watch:** {emerging_topic — 1 sentence}

---

**Part 3 — Narrative Commentary Prompts:**

1. *"The spike in [category] tickets this week was driven by..."*
2. *"CSAT dropped by [X] points — the verbatim feedback suggests the root cause is..."*
3. *"First response time improved despite higher volume because..."*
4. *"The top 3 tickets this week point to a product gap in [area] — specifically..."*
5. *"If current ticket velocity continues, the team will need [X] additional resource by [date] to maintain SLA."*

---

**Part 4 — Sample Insight #1:**
> "Integration-related tickets increased 34% week-over-week, concentrated on Salesforce sync errors. Cross-referencing with the engineering log, this correlates with the API rate limit change deployed on Tuesday. Recommend flagging to the product team for a hotfix and proactively emailing affected users before they contact support."

---

**Executive Summary (Slack/email format):**

> 📊 **Support Week in Review — {date}**
> - Ticket volume: {n} (+{%} vs. last week) — driven by {top_driver}
> - CSAT: {score}% ({direction} — {one-line reason})
> - Backlog: {n} tickets ({status vs. target})
> - Biggest issue: {1-sentence description + owner}
> - Action needed: {decision or ask for leadership}

---

### Variations

**Variation A — Real-Time Escalation Alert**
> Replace the weekly report with: *"Write an escalation alert template that fires in real time when a key threshold is breached — e.g. CSAT drops below 80%, backlog exceeds 50 tickets, or an enterprise account submits 3+ tickets in 24 hours. Format for Slack, email, and PagerDuty."*

**Variation B — Quarterly Business Review (QBR) Deck Brief**
> Expand to: *"Build a complete QBR slide deck outline for presenting support performance to the executive team. Include: trend analysis, root cause summary, team capacity review, top customer feedback themes, proposed investments, and 90-day roadmap."*

---

---

*End of Category 03: Customer Support Automation*

---

> **Part of the "100 AI Mega Prompts for Business" digital product.**
> Categories include: Sales & Cold Outreach · Content Creation & Repurposing · Customer Support Automation · Hiring & HR · Operations · Leadership & Strategy · Customer Success · Finance · Legal · Product · and more.
