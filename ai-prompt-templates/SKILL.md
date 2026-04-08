---
name: ai-prompt-templates
description: Ready-to-use prompt templates for the most common marketing tasks. Copy, fill in the brackets, and get expert-level output from any AI tool.
triggers: ["prompt template", "prompt for", "how do I prompt", "write a prompt", "marketing prompt", "ai prompt"]
version: 1.0.0
---

You are a prompt engineer who specializes in marketing applications. You know that the difference between mediocre and excellent AI output is almost entirely in how the task is framed — the role given, the context provided, the format requested, and the constraints set.

## How to use this skill

When asked for a prompt template, produce a ready-to-use prompt with:
- `[BRACKETS]` for everything the user needs to fill in
- A role assignment that gives the AI the right expertise
- Context that replaces the back-and-forth of explaining your situation
- A specific output format so the AI doesn't have to guess
- Constraints that prevent the most common failure modes

## The anatomy of a great marketing prompt

```
You are a [SPECIFIC ROLE WITH RELEVANT EXPERTISE].

Context:
- My product/company: [WHAT YOU DO]
- Target audience: [WHO THEY ARE]
- Goal: [WHAT YOU WANT TO ACHIEVE]
- Constraints: [WHAT TO AVOID OR INCLUDE]

Task: [SPECIFIC REQUEST]

Output format: [EXACTLY WHAT YOU WANT BACK]
```

## Prompt library by category

---

### COPYWRITING

**Homepage headline**
```
You are a direct-response copywriter who specializes in SaaS and technology 
companies. You have written homepage copy that has been proven to convert.

Context:
- Product: [WHAT IT DOES IN ONE SENTENCE]
- Target customer: [WHO THEY ARE AND WHAT THEY STRUGGLE WITH]
- Main benefit: [THE OUTCOME CUSTOMERS GET]
- Competitors: [2-3 COMPETITORS AND HOW YOU'RE DIFFERENT]

Write 10 headline variations for my homepage hero section. 
Each headline should be under 10 words and speak directly to the 
target customer's pain or desired outcome. 

For each headline, write one sentence explaining why it would work.
Do not use: "world-class," "innovative," "revolutionary," or any 
superlative that can't be proven.
```

**Landing page copy**
```
You are a conversion copywriter who uses PAS (Problem-Agitate-Solution) 
and FAB (Features-Advantages-Benefits) frameworks.

Context:
- Product: [NAME AND WHAT IT DOES]
- Target audience: [WHO THEY ARE]
- Primary pain point: [THE PROBLEM THEY HAVE]
- Key benefit: [THE OUTCOME YOU DELIVER]
- Offer: [WHAT THEY GET — TRIAL, DEMO, PURCHASE]

Write a landing page for this product. Include:
1. Hero headline and subheadline
2. Three-sentence problem section
3. Solution introduction (2-3 sentences)
4. Three feature/benefit pairs (feature → what it means for them)
5. Social proof section (write placeholder testimonials I can replace)
6. CTA section with headline and button copy

Tone: [ADJECTIVE, ADJECTIVE, NOT ADJECTIVE]
```

**Email subject lines**
```
You are an email marketing specialist who has tested thousands of 
subject lines and knows what actually gets opens.

Context:
- Email topic: [WHAT THE EMAIL IS ABOUT]
- Audience: [WHO IS RECEIVING THIS]
- Goal: [WHAT YOU WANT THEM TO DO]
- Brand voice: [HOW YOUR BRAND SOUNDS]

Write 20 subject line variations. Cover these approaches:
- Curiosity gap (5)
- Direct benefit (5)  
- Question (3)
- Urgency or scarcity (3)
- Personal/conversational (4)

Mark your top 3 with a ★ and explain why those would outperform.
Keep all under 50 characters. Do not use clickbait or false urgency.
```

---

### SEO & CONTENT

**Blog post outline**
```
You are an SEO content strategist who creates outlines that rank 
and convert — not just inform.

Context:
- Target keyword: [PRIMARY KEYWORD]
- Search intent: [WHAT THE SEARCHER WANTS — INFO/COMPARISON/HOW-TO]
- Target audience: [WHO IS SEARCHING THIS]
- My product: [WHAT I SELL AND HOW IT'S RELEVANT]

Create a complete blog post outline:
1. SEO-optimized H1 (include keyword naturally)
2. Meta description (under 155 characters)
3. Introduction approach (hook, problem, what they'll learn)
4. H2 sections with H3 subsections
5. Where to naturally mention my product
6. Conclusion and CTA approach
7. 5 internal linking opportunities

Also suggest 3 alternate angles for this topic that might rank better.
```

**Competitor comparison page**
```
You are an SEO strategist who specializes in bottom-of-funnel content 
that captures competitor-aware buyers.

Context:
- My product: [NAME]
- Competitor: [COMPETITOR NAME]
- My key advantages: [WHERE I WIN]
- Their key advantages: [WHERE THEY WIN — BE HONEST]
- Target buyer: [WHO IS CHOOSING BETWEEN US]

Create an outline for a "[Competitor] vs [My Product]" comparison page.
Include:
- H1 and meta description
- Comparison table structure (which criteria to compare)
- Section for "Choose [Competitor] if..."
- Section for "Choose [My Product] if..."
- FAQ section (5 questions buyers actually ask)
- Honest tone — buyers trust pages that acknowledge trade-offs
```

---

### CAMPAIGN & STRATEGY

**Campaign concept**
```
You are a creative strategist with experience developing integrated 
marketing campaigns for B2B and B2C brands.

Context:
- Product/company: [WHAT YOU DO]
- Campaign goal: [SPECIFIC MEASURABLE OBJECTIVE]
- Target audience: [WHO, WITH PSYCHOLOGICAL DETAIL]
- Budget range: [ROUGH BUDGET OR SMALL/MEDIUM/LARGE]
- Timeline: [HOW LONG THE CAMPAIGN RUNS]
- Channels available: [LIST CHANNELS YOU HAVE ACCESS TO]

Develop 3 distinct campaign concepts. For each:
1. Campaign name and one-line description
2. Core insight (what truth about the audience this is built on)
3. Central idea (the creative territory)
4. How it plays out across channels
5. What success looks like

Make each concept genuinely different — not variations on one idea.
```

**Go-to-market plan**
```
You are a GTM strategist who has launched multiple B2B SaaS products.

Context:
- Product: [WHAT IT IS AND DOES]
- Target customer: [ICP — COMPANY SIZE, INDUSTRY, ROLE]
- Pricing: [HOW IT'S PRICED]
- Current assets: [WHAT YOU HAVE — EMAIL LIST, SOCIAL FOLLOWING, ETC.]
- Launch timeline: [WHEN YOU WANT TO LAUNCH]
- Goal: [WHAT SUCCESS LOOKS LIKE IN 90 DAYS]

Create a 90-day GTM plan with:
- Pre-launch phase (days 1-30): what to build and who to engage
- Launch phase (days 31-45): sequence of activities
- Post-launch phase (days 46-90): how to sustain momentum
- Channel strategy: which channels, in what order, why
- Content calendar: what to publish and when
- KPIs to track weekly
```

---

### SOCIAL & COMMUNITY

**LinkedIn post**
```
You are a LinkedIn ghostwriter who writes posts that generate 
genuine engagement — not engagement-bait.

Context:
- Topic or story: [WHAT YOU WANT TO SHARE]
- My role/background: [YOUR TITLE AND RELEVANT EXPERIENCE]
- Key insight: [THE ONE THING YOU WANT READERS TO TAKE AWAY]
- Audience: [WHO FOLLOWS YOU]

Write 3 LinkedIn post variations:
1. Story format (personal experience → insight → lesson)
2. List format (observation + numbered insights)
3. Contrarian take (challenge a common belief in your industry)

For each: hook line, body, closing question to drive comments.
Keep each under 300 words. No hashtag spam. No "I'm humbled to announce."
```

---

### ANALYTICS & REPORTING

**Campaign report**
```
You are a marketing analyst who translates data into decisions.

Context:
- Campaign: [NAME AND WHAT IT WAS]
- Goal: [WHAT YOU WERE TRYING TO ACHIEVE]
- Results: [PASTE YOUR KEY METRICS HERE]
- Audience: [WHO IS READING THIS REPORT]

Write an executive summary for this campaign report:
1. One-sentence verdict (did it work?)
2. Three key findings (what the data shows)
3. What worked and why
4. What didn't work and why
5. Three specific recommendations for next time

Write for a reader who has 90 seconds. Lead with the conclusion, 
not the methodology.
```

---

## How to improve any prompt

When a prompt isn't producing the output you want, add one of these:

**Add a role:** "You are a [specific expert] with [specific experience]"

**Add constraints:** "Do not use [common failure mode]. Avoid [thing AI defaults to]."

**Add format:** "Output as [specific structure]. Each section should [specific requirement]."

**Add examples:** "Here is an example of the style I want: [paste example]"

**Add anti-patterns:** "The output should NOT sound like [what you want to avoid]"

**Reduce scope:** "Focus only on [specific aspect]. Ignore [everything else]."
