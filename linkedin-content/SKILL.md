---
name: linkedin-content
description: Write high-performing LinkedIn posts using a structured research-to-publish workflow. Use when the user wants to write, plan, or improve a LinkedIn post. Triggers include: "write a LinkedIn post", "help me post about", "draft a post", "I want to share something on LinkedIn", or any request to create LinkedIn content. This skill enforces a five-phase process with mandatory approval gates at each phase.
---

# LinkedIn Content Creation Skill

This skill helps you write LinkedIn posts that are grounded in source material, validated against your post history, and written in a voice that earns real engagement. It was built and battle-tested by Pete Caputa, CEO of Databox, whose LinkedIn content consistently reaches tens of thousands of people per post.

Pete shared his full workflow publicly because 70+ people asked to see it. This skill is a cleaned-up, generalized version that any creator can use. At the bottom, you'll find Pete's own configuration as a reference implementation.

---

## First-Run Check

Before doing anything else in a new session, verify that the following required fields have been provided. If any are missing, use the `ask_user_input_v0` tool to collect them before proceeding to Phase 1. Do not skip this step or assume defaults.

Ask the user:

> "Before we write your first post, I need a few details to personalize this skill for you. Please fill in what applies:"
>
> 1. **Your name**
> 2. **Your professional background** — 2-3 sentences on your experience and credibility
> 3. **Your company and what it does** — including your role, product/service, and who you serve
> 4. **Your primary LinkedIn audience** — who are you writing for?
> 5. **Your AuthoredUp dataset ID** — required if using AuthoredUp for post performance data
> 6. **Your Databox account ID** — required if using Databox to pull business data
> 7. **Avoma and Slack setup** — optional; let the user know these unlock call transcript and team context pulls
> 8. **Voice and tone examples** — optional; 2-3 of their best posts. If they don't have any yet, offer to use Pete's examples from the Reference section as a starting point.

Once all required fields are confirmed, save them for the session and proceed normally. Do not ask for these again in the same session.

---

## Before You Start: Setup

This skill works best when you've connected a few tools. Here's what to set up and why.

### Step 1: Personalize the Skill

Before writing any post, you need to configure this skill for yourself. The first time you use it, Claude will ask you for the following. Fill in what you can — required fields are marked.

**Required:**
- **Your name** — so the skill can write in first person and attribute correctly
- **Your professional background** — a 2-3 sentence summary of your experience and credibility (this informs how the skill frames your authority and voice)
- **Your company and what it does** — including your role, the product or service, and who you serve
- **Your primary LinkedIn audience** — who you are writing for (e.g., "agency owners and marketing consultants," "RevOps leaders at mid-size SaaS companies")

**Required if using AuthoredUp:**
- **Your AuthoredUp dataset ID** — used to pull your post performance history so the skill can validate hooks and angles against what has actually worked for you (see AuthoredUp setup below)

**Required if using Databox:**
- **Your Databox account ID** — used to pull business or marketing data to validate posts with real numbers (see Databox setup below)

**Optional (power users):**
- **Avoma setup** — if you want to pull quotes or themes from recorded calls with customers, partners, or guests
- **Slack setup** — if you want to pull context about what your team is working on
- **Voice and tone examples** — paste 2-3 of your best-performing posts so the skill can match your voice. If you don't have any yet, you can borrow from Pete's examples in the Reference section below.

---

### Step 2: Set Up Your Tools (Recommended)

These tools unlock the most powerful parts of this skill. Each one is optional, but the more you connect, the better your posts will be.

---

#### AuthoredUp (Strongly Recommended)

AuthoredUp tracks the performance of every post you publish on LinkedIn: impressions, engagement rate, comment count, and the full post text. Connecting it turns your post history into a data asset. Instead of guessing what works, you can see it.

The skill uses AuthoredUp in two ways:
- **Phase 1 (Research):** Pulls patterns across your full post history to inform angle and hook decisions
- **Phase 3 (Hook Validation):** Checks whether a specific opener type, topic, or structure has worked before

**To get started with AuthoredUp:**
1. Sign up at [authoredup.com](https://authoredup.com) (Pete's referral link — he uses this himself)
2. Connect your LinkedIn account
3. Connect AuthoredUp to Databox as a custom integration. AuthoredUp does not have a native MCP server, but you can make your post data queryable by Claude by connecting AuthoredUp to Databox via a custom integration. Follow the setup guide here: [help.databox.com/set-up-a-custom-integration](https://help.databox.com/set-up-a-custom-integration). If you need help getting this configured, you can book a call with a Databox product expert at [databox.com/demo](https://databox.com/demo) or reach out to your Databox account manager directly.
4. Note your dataset ID from Databox — you'll need it for setup above

> If you don't use AuthoredUp, the skill will skip the data-driven hook validation steps and rely on general principles instead. You can still get a great post — you'll just miss the personalized performance signal.

---

#### Databox (Strongly Recommended)

Databox is a business analytics platform that connects to dozens of tools (CRMs, ad platforms, website analytics, email, and more) and lets you build dashboards, track KPIs, and query your data in plain language using Genie, Databox's AI analyst.

In this skill, Databox serves two roles:
1. **As the host of your AuthoredUp data** — your post history lives here as a custom dataset, queryable via Genie
2. **As a source of business validation** — if you're writing a post about your marketing results, sales pipeline, or product adoption, Genie can pull the actual numbers to make your post specific and credible

**To get started with Databox:**
1. Start a free plan or trial at [databox.com](https://databox.com)
2. Connect your data sources (start with whatever feeds your marketing or business reporting)
3. Connect the Databox MCP to Claude so the skill can query Genie directly
4. Note your account ID — you'll need it for setup above

---

#### Avoma (Recommended for Anyone Who Records Calls)

Avoma is an AI meeting assistant that records, transcribes, and summarizes your calls. If you talk to customers, partners, prospects, or podcast guests, Avoma turns those conversations into a searchable library of quotes and themes — which become some of the best source material for LinkedIn posts.

The skill uses Avoma to pull:
- Direct quotes from specific calls (with your permission to share or anonymize)
- Recurring themes across multiple conversations
- Exact language your customers use to describe their problems or wins

**To get started with Avoma:**
1. Sign up at [avoma.com](https://www.avoma.com?via=71efpocm) (Pete's referral link)
2. Connect your calendar so Avoma joins and records your calls
3. Set up the Avoma MCP using their step-by-step guide: [help.avoma.com/avoma-mcp-server-user-guide](https://help.avoma.com/avoma-mcp-server-user-guide)
4. Once the MCP is connected, you can ask Claude to pull transcripts or notes from any recorded meeting by title, date, or attendee

---

#### Slack (Recommended for Team Context)

If your LinkedIn posts often reference what your team is building, shipping, or learning, connecting Slack gives the skill access to internal context without requiring you to manually summarize it. Useful for surfacing recent wins, customer feedback threads, or product updates that make for timely posts.

Slack is available as a built-in connector in Claude.ai. Enable it in your connectors settings.

---

## How the Skill Works: Five Phases

Every post goes through five phases. **The skill will not advance to the next phase without your explicit approval.** This is intentional. The most common mistake in AI-assisted content creation is moving too fast — drafting before the angle is right, publishing before the hook is validated. The gates exist to protect the quality of the output.

---

### Phase 1: Research Collection

**Goal:** Gather all source material before doing anything else.

At the start of every post session, use the `ask_user_input_v0` tool to present the following as a multi-select question:

> "What source material should I collect for this post?"
>
> - Pull from Databox — your business or marketing data (good for posts with real numbers)
> - Pull from AuthoredUp — your post performance history (always useful; done automatically if connected)
> - Pull from Avoma — a specific call transcript or recurring themes across calls
> - Pull from Slack — recent team activity, wins, or context
> - Fetch a URL — paste a link to a research report, blog post, or piece of content
> - Paste it here — share raw text, quotes, notes, or anything else
> - Skip source material — go straight to brainstorming

You can select multiple options. The skill will collect everything before moving on.

**Also done automatically in Phase 1 (if AuthoredUp is connected):**
- Pull broad performance patterns from your post history: which topics, hooks, structures, and content types have driven the most impressions and engagement
- Surface 3-5 specific observations to inform Phase 2 angle brainstorming
- Flag if any similar posts have already been published (to avoid repetition or to identify a natural follow-up angle)

**Before writing any post that features a customer, partner, or guest:**
The skill will ask: "Do you have any written quotes from this person — LinkedIn comments, reviews, testimonials, or other written responses?" Written quotes take priority over transcript quotes. The transcript version is used only if no written version exists or is weaker.

**Before closing Phase 1, use the `ask_user_input_v0` tool to ask:**

> "Do you have any media or links to attach to this post?"
>
> - Video — square format performs better than vertical on mobile. Vertical videos push the post text down, making it harder to discover in the feed.
> - Image
> - PDF (for a carousel post)
> - Link — contextual inline links are encouraged when they add value. Always dismiss LinkedIn's auto-generated link preview card before publishing (click the X). Attaching a video or image removes the preview card automatically.
> - No media or links

The skill will note your selection and carry it into the drafting phase.

**Wait for explicit approval before proceeding to Phase 2.**

---

### Phase 2: Brainstorming Angles and Hooks

**Goal:** Identify the best angle before writing a single word of copy.

Based on all research collected, the skill will propose 3-5 distinct angles. For each, it will describe:
- The emotional charge (what feeling does this create in the reader?)
- The intended audience (who is this for?)
- The hook (what's the opening line or idea?)
- The content intent it serves (Vision & Trends, Best Practices, Examples, Quick Wins, How-Tos, or Evaluation)

The skill will then ask you to choose one — or combine elements from multiple. It will work through any open decisions one at a time using multiple choice questions before moving forward.

**No post copy is written in this phase.**

**Wait for explicit approval before proceeding to Phase 3.**

---

### Phase 3: Hook Validation Against Post History

**Goal:** Pressure-test the chosen angle against what has actually worked.

Once you've approved a direction, the skill uses your AuthoredUp data to search for past posts that used a similar hook, opener pattern, angle, or topic. It will surface 3-5 specific observations — for example:
- Did a similar opener drive above-average impressions?
- Did a related topic underperform?
- Did story-first vs. stat-first make a difference on this subject?

If AuthoredUp is not connected, the skill will apply general principles from Pete's research (documented in the Reference section below) and note that personalized validation isn't available.

The skill may suggest refinements before outlining. You'll confirm or reject those before moving on.

**Wait for explicit approval before proceeding to Phase 4.**

---

### Phase 4: Outline and Flow

**Goal:** Agree on the structure before any copy is written.

The skill will propose a structural skeleton: opener, body beats in order, quote placement (if applicable), and closing. No post copy — just the outline.

The skill will ask multiple choice questions to resolve any open structural decisions (e.g., "Should the customer's result come in the second beat or the third?").

**No post copy is written in this phase.**

**Wait for explicit approval before proceeding to Phase 5.**

---

### Phase 5: Drafting

**Goal:** Write the full post. Then — and only then — address length.

Once you've approved the outline, the skill writes the full draft. It writes freely, without artificially constraining length in order to fit within LinkedIn's limit. A full, complete draft is always better than a compressed draft.

At the bottom of every draft, the skill will show:

> **Estimated character count: [X]**
> *(LinkedIn's limit is 3,000. Your target before trimming is 2,500 to stay safely under.)*

**The skill will not offer to trim until you have approved the draft for content.** Length editing is a separate phase that only begins after you've said the draft is directionally right.

#### Before Moving to Length Editing

Once the draft is approved for content, the skill will ask:

> "Are there any contextual links to weave into the post — for example, linking a product, resource, or report when it's mentioned? If yes, where should they go?"

The skill will place links inline at the natural mention point. It will also add a reminder at the bottom of the draft: **dismiss LinkedIn's link preview card before publishing** by clicking the X on it. If a video or image is attached, this happens automatically.

#### When the Draft Is Over 2,500 Characters

Trimming happens in two passes. The skill will not make any changes until you've approved what to do.

**Pass 1 — What to cut entirely:**
The skill presents a numbered list of elements to remove completely, with a rationale for each and the estimated character savings. You approve or reject each item before anything is touched.

**Pass 2 — What to shorten:**
After cuts are made, the skill presents a numbered list of elements to condense, with a suggested approach for each. You approve before any changes are made.

The skill makes one pass at a time and shows you the updated draft after each round.

**Approved style shorthands for tightening copy (these never alter direct quotes):**
- `&` instead of "and" in narrator text
- `~3 years` instead of "nearly three years"
- `2x/month` instead of "twice a month"
- Drop filler setup sentences before quotes when the quote speaks for itself

---

## Editing Protocol

When a draft needs significant revision beyond length, the skill does not immediately redraft. Instead, it asks 3-5 targeted questions per round using multiple choice format — prioritizing structure and angle questions before style and voice questions. It only redrafts once you give explicit approval.

---

## The Frameworks

These are the core intellectual frameworks that power the skill. They were developed by Pete Caputa based on years of LinkedIn posting and should be understood as his approach — adapt them to your own voice and experience over time.

---

### Post Framework

Most posts follow this general structure — not as a formula, but as a default:

1. **Start with a statement that evokes emotion** — something people will passionately agree or disagree with. No warm-up sentence.
2. **Follow with a story or data** that adds depth, offers actionable insight, or validates the opening claim.
3. **Include a visual or video** if available — not for the sake of media, but to enable link-sharing without hurting engagement.
4. **Use links contextually, inline — never let LinkedIn auto-generate a link preview card.** If you mention Databox's AI Analyst, linking it inline (even in parentheses) makes sense — it adds context and drives clicks. The problem is not links themselves; it's the large link preview card LinkedIn appends to the bottom of the post when it detects a URL. Always dismiss that preview card before publishing by clicking the X on it. If you attach a video or image, LinkedIn places that at the bottom instead, which naturally prevents the preview card from appearing.
5. **End with a question** to encourage engagement — but see the exception below.

**Exception on closing questions:** When the opener uses negative emotional charge (implying the reader has a problem they may not know about), do not end with a question that asks them to publicly confirm that problem. Match the closing energy to the opening charge. If a video or rich media is attached and serves as the natural engagement device, a closing question is optional.

---

### The Charges Framework

Stories start from emotional charge, not neutrality. Move between emotional rungs to build or release tension — this maintains reader momentum throughout the post.

Rungs (from highest to lowest): **Double Positive → Positive → Neutral → Negative → Double Negative**

Opening on a negative charge and closing on a positive one creates a satisfying arc. Opening and closing on the same charge creates flatness. Understand the emotional trajectory of your post before you write it.

---

### Opener Patterns That Work

These are drawn from Pete's highest-performing posts. They reflect how his voice sounds when it's working — not a formula to follow every time, but a reference for what makes a strong opening.

- **Strong, specific claim:** "Most companies should stop publishing educational content to their website for SEO purposes. It's like buying real estate in an undesirable neighborhood."
- **Credibility-anchored observation:** "After 9 years at HubSpot and 8 more at Databox, I'm amazed at the number of companies still cutting and pasting raw data into spreadsheets."
- **Contrarian take with honest qualifier:** "Account-based marketing has seemed like bullshit to me since it came out. I must be missing something, though?"
- **Exact numbers up front:** "472 applicants applied for Databox's VP Marketing role. 102 days after opening it, Heather Adams officially joined."
- **"If I were running X at Y...":** "If I were running sales at a marketing agency, I'd be using Databox as a consultative selling tool."
- **Overheard scene or dialogue:** "Gym friend: We just started using HubSpot. It's hard. Do you work there?"
- **"I think we're seeing...":** "I think we're seeing the end of the inbound sales development role at SaaS companies."

**What these share:** They are immediate, specific, and create a reason to keep reading. There is no warm-up sentence. Vagueness and generic setup lines are the most common thing to cut from a draft.

---

### Content Intent Mapping Framework

Every post must align with at least one of six content needs. Choose the one that matches why someone would stop and read this post.

| Intent | What it does for the reader |
|---|---|
| **Vision & Trends** | Shows them where things are going |
| **Best Practices** | Helps them do something better |
| **Examples** | Shows them how it works in the real world |
| **Quick Wins** | Gives them something actionable right now |
| **How-Tos** | Walks them through a specific process |
| **Evaluation** | Helps them decide between options |

**Special rule for Vision & Trends posts:** These are high-impact, zero-click posts built on founder POV or market insight. But they must include at least one of: research/statistics, expert opinion or quotes, customer use cases, or product/platform data. If validation is missing, the skill will ask for it or request permission to proceed without it.

---

### Voice and Tone

**Critical distinction: you share observations, not declarations. You witness and report.**

You do not preach, predict the future with certainty, or position yourself as an authority making pronouncements. Phrases like "from what I'm seeing" or "in my experience talking to clients" are preferred over declarative statements that lecture. You never sound like you're telling people what to do — you're sharing what you've seen.

When telling a customer story, let the story carry the argument. Do not step outside the narrative to explain the lesson. The story should prove the point without you narrating what the point is.

---

### Formatting and Style Rules

- No em dashes in post copy. Replace with a comma, colon, parentheses, or end the sentence. Exception: em dashes inside direct quotes from other people are never altered.
- No sentence fragments. When listing items, use a colon followed by commas in a single sentence.
- No headers or heavy formatting inside the post. Simple bullet points are acceptable when the content naturally calls for them — a list of items, or a post that breaks into three distinct sections. Use sparingly and only when bullets genuinely aid readability, not as a default structure.
- No hashtags unless there is a deliberate reason. They consistently correlate with lower reach.
- Contextual inline links are encouraged when they add value — link a product, feature, or resource when you mention it. Always dismiss LinkedIn's auto-generated link preview card before publishing (click the X). Attaching a video or image removes the preview card automatically.
- Do not repeat attribution names after every quote.

---

### Quote and Attribution Rules

- Never lead with the person's name. Lead with a headline that summarizes the insight, then provide the quote with attribution.
- Written quotes (LinkedIn comments, testimonials, reviews) take priority over transcript quotes. Use transcript versions only when no written version exists or when it is clearly stronger.
- Introduce the person by name once. Let subsequent quotes stand without repeating the name and attribution.
- Never alter the wording of a direct quote. If a quote is too long to use, cut it entirely rather than paraphrase it.

---

### Customer Story Framework

When writing a post about a customer, the customer is the hero. Databox (or your tool/service) is the enabler — woven in, not centered.

The customer's results, systems, and thinking should be front and center.

**Dual-audience option:** A post about an agency customer can optionally be written to reach two audiences at once — agency owners who aspire to operate that way, and business owners who are evaluating what to look for in an agency partner. When this framing is used, note it in the post's strategic metadata.

**Fact-checking standard:** Before publishing any customer story, flag any specific claims that cannot be directly verified from source material. Do not assume — flag it explicitly at the bottom of the draft so you can verify with the customer before publishing.

---

### Strategic Metadata

For every post, the skill will explicitly provide:

- **Content Intent(s)** — which of the six intents this post serves
- **Content Theme(s)** — what broader topic or strategic area it belongs to
- **Core Positioning Concept(s)** — what it communicates about you or your company
- **Offer (if present)** — any CTA, resource, or value-add baked into the post
- **Validation used** — what evidence supports the post's central claim (or a prompt to find it)

---

### Pre-Publish Checklist

Before finalizing any draft, apply these checks:

1. Is the opener a real claim or observation — or is it a warm-up sentence that could be cut?
2. Are there specific numbers, names, or examples in the body — or is it all generality?
3. If the post opens with negative charge, does the closing question ask the reader to publicly self-incriminate? If so, remove or replace it.
4. If a video or rich media is attached, is the closing question necessary — or does the media serve as the engagement device?
5. Are links in the post body? If so, move them to the first comment.
6. Are there hashtags? If so, is there a deliberate reason?
7. Does the post stay in story or observation mode throughout — or does it slip into editorializing or preaching?
8. Have you confirmed any quotes with their sources before publishing?
9. Have you verified all factual claims that can't be traced to the source material?

---

## Reference: Pete's Setup

This is Pete Caputa's own configuration for this skill. It's included so you can see how the personalization section looks when filled in — and so you can borrow from it if you're just getting started.

**Name:** Pete Caputa

**Professional background:** Spent 9 years at HubSpot in leadership roles, including running their partner program at scale. Joined Databox as CEO 8+ years ago. Deep credibility with agency, consultant, and professional services audiences. Known on LinkedIn for blunt takes on marketing, data, agencies, and leadership.

**Company:** Databox — a business analytics platform that makes it easy for everyday business users (not just analysts or engineers) to connect their tools, define metrics, build dashboards, and act on insights faster. Key products include Genie (an AI analyst that answers performance questions in plain language), an MCP server for querying data inside Claude, and the Predictable Scale methodology for OKR alignment.

**Primary LinkedIn audience:** Agency professionals, consultants, and professional services firms — especially those helping clients improve performance through better use of data. Also targeting RevOps agencies and GTM leaders at mid-size B2B/SaaS companies.

**AuthoredUp dataset ID:** `fd952e73-50f0-40f8-b408-e5d7dc361fb6`

**Databox account ID:** `31`

**Avoma:** Connected via MCP. Filter meetings using `pete@databox.com` as attendee email for most reliable retrieval. Use `get_meeting_transcript` for direct quotes.

**Slack:** Connected via MCP. Use `slack_search_public_and_private` with `include_context: false` and limit 5-8 for clean results.

**Voice/tone examples (Pete's openers from top posts):**
- "Most companies should stop publishing educational content to their website for SEO purposes. It's like buying real estate in an undesirable neighborhood."
- "After 9 years at HubSpot and 8 more at Databox, I'm amazed at the number of companies still cutting and pasting raw data into spreadsheets."
- "I think we're seeing the end of the inbound sales development role at SaaS companies."

**Content themes Pete returns to:**
- HubSpot ecosystem commentary: acquisitions, earnings, competitive dynamics
- Contrarian marketing takes: SEO, ABM, inbound, content strategy
- AI's impact on marketing, search, sales, and buyer behavior
- Agency positioning: how agencies are undervaluing data, losing clients, getting commoditized
- Real team and hiring stories told with specific numbers
- CEO and leadership observations: accountability, scaling, decision-making

**Partners and colleagues (add your own equivalents):**
When tagging partners or colleagues in posts, always confirm in advance that they've seen any quotes attributed to them and are comfortable being tagged publicly. Never publish a quote or tag someone without that confirmation.
