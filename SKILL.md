---
name: hbs-case-writer
description: Create Harvard Business School-style case studies on financial market events, products, or investment decisions. Use when the user wants to write a teaching case about a financial event, market phenomenon, investment product, or corporate decision. Triggers on requests like "write a case about X", "create an HBS case on Y", or "develop a teaching case for Z". Outputs immersive, decision-focused narratives with supporting exhibits and teaching notes.
---

# HBS Case Writer

Write Harvard Business School-style teaching cases on financial market events and investment decisions.

## Case Structure

Every case follows this architecture:

1. **Title & Header** — Case title, protagonist name/role, date, institution
2. **Opening Hook** — Start at the decision moment; protagonist faces a choice
3. **Background** — Industry context, market conditions, relevant history
4. **The Situation** — Specific events, data, and stakeholders involved
5. **Analysis Framework** — The apparatus the reader needs to analyze (not the analysis itself). See [Analysis Framework](#analysis-framework) below for the full specification; valuation/decision cases must carry a real framework, not just headline multiples.
6. **The Decision** — End with open questions; NO resolution

## Angle Selection (Confirm Before You Research)

Every topic can become several *different* cases depending on the angle. **Ask the user which angle they want before you research or draft** (use `AskUserQuestion`), and do not default to valuation. The most common framing mistake is to collapse genuinely different case archetypes into valuation-flavored investor decisions. Offer a menu of distinct angles and let the user pick.

Present these standard angles (the `Other` option is supplied automatically, so do not add one):

| Angle | What the case is about | Typical protagonist | Typical framework |
|-------|------------------------|---------------------|-------------------|
| **Valuation** | Price a company, asset, or deal; set a target price or buy/sell/hold/underwrite call | Sell-side analyst, growth investor, banker | DCF build, comps, precedents, a "what must the buyer believe" lever table, sensitivity, triangulation |
| **Investment decision-making** | How to act on a signal, position, or allocation, including forecasting and market-efficiency judgments | Portfolio manager, allocator, macro strategist | A decision-relevant apparatus (for example a calibration or efficiency lens, a risk-return tradeoff, portfolio impact), not necessarily a DCF |
| **Financial product analysis** | Analyze a novel instrument's mechanics, economics, risks, and users; decide whether to use, launch, underwrite, or regulate it | Product lead, risk officer, structurer, buy-side user | How-it-works mechanics, payoff and P&L decomposition, risk scenarios, user and market fit |
| **Industry / market background** | A primer on industry structure, competitive dynamics, or a market event as decision context | Strategist, analyst, new entrant | Structure and conduct, value chain, competitive forces, where value accrues |
| **Corporate strategy & capital allocation** | A company facing a strategic decision (raise capital, M&A, enter or exit a market, restructure, allocate across projects) | CEO, CFO, head of corp dev, board | Strategic options matrix, capital-allocation hierarchy, deal math, scenario analysis |
| **Risk & crisis management** | A firm under pressure making decisions in a run, blowup, or liquidity event | CEO, CRO, treasurer, risk officer | Exposure mapping, liquidity and run dynamics, stress scenarios, deciding under uncertainty |

**Why this matters (worked example).** For *Polymarket*, the headline facts (a company repricing from about $1B to $15B on near-zero revenue) invite a valuation case. But the user may instead want an **investment decision-making** case on forecasting and market efficiency: whether a portfolio manager should act on prediction-market signals. These are different cases with different protagonists and different frameworks. Ask, do not assume.

The angle dictates the protagonist, the framework, and the exhibits (see [Protagonist and Decision Depth](#protagonist-and-decision-depth) and [Analysis Framework](#analysis-framework)). Confirm the angle at the very start; confirm output formats later (see [Output Formats](#output-formats)).

## Writing Principles

### Narrative Style
- Third-person limited (follow the protagonist)
- Present tense throughout
- Objective, journalistic tone — no judgments or conclusions
- Let facts and data tell the story
- Quote real sources when available

### What Makes It a Case (Not an Article)
- Ends with a decision point, never a resolution
- Presents conflicting information or trade-offs
- Reader must analyze, not just absorb
- Avoid teaching explicitly — immerse the reader instead
- Include just enough context; let exhibits carry data

### The Protagonist
- Name a specific person or team facing the decision
- Give them a role, organization, and stakes
- Show their thought process through action, not introspection
- They don't have to be heroic — real people with real constraints

### Protagonist and Decision Depth
The best cases pair a decision that has **genuine analytical structure** with a protagonist whose role **demands** that analysis. Favor:
- A **price target with a defensible framework**, or an explicit **buy / hold / sell / underwrite / allocate** call — decisions the reader can recompute.
- Protagonists whose job is the analysis: a **sell-side analyst setting a target price, a portfolio manager sizing a position, an allocator deciding inclusion, a banker pricing an offering, a risk officer sizing exposure**. These roles force the case to carry a framework (see Analysis Framework).

A **retail investor deciding sell-vs-hold after a pop** is permissible but is the **weakest** decision shape: it rarely requires a framework and collapses to a behavioral call. If you use it, justify *why* (e.g., the case's purpose is market-microstructure or investor-behavior, not valuation) and still equip the reader with a framework to judge the hold. Avoid "should she sell or hold?" as the *sole* decision when a richer analytical decision is available on the same facts — that usually means the protagonist was chosen for color rather than for stakes.

When in doubt, ask: *could a competent reader produce a different defensible answer from the same case?* If the decision is so under-structured that any answer is as good as another, raise the decision's analytical stakes.

## Data & Exhibits

### Required Elements
- Financial data tables (performance, valuations, market data)
- Charts where visual data tells the story better
- Timeline of key events
- Competitive landscape or peer comparisons

### Exhibit Standards
- Source all data (Bloomberg, SEC filings, company reports, etc.)
- Use clean, professional formatting
- Exhibit titles should be descriptive
- Number exhibits sequentially

### Quantitative Discipline
Numbers are the load-bearing structure of a finance case. Hold them to these rules:

1. **Separate offer-price from trading-price valuation.** An IPO has (at least) two valuations: the offer price and the first-day/week trading price. State which multiple you are computing and against which share count. Never write "~100x revenue near $2T" without saying whether that is at offer or at market — the two can differ by a third. Show both when the gap is part of the story.
2. **Reconcile share count before any market-cap claim.** Float, shares outstanding, and fully-diluted differ. Pick one basis, name it, and use it consistently in every market-cap statement; state the basis in the exhibit.
3. **Flag unverified intraday prints.** A specific intraday high/low cited to no exchange feed or timestamp is a fabrication risk. Source it to the exchange or a data vendor with a timestamp, or soften it to a range and label it "unverified" in the text. Do not present a scraped price as fact.
4. **Triangulate valuations for any valuation case.** Show at least two independent estimates (fundamental, secondary-market, precedent, prediction-market) beside the offer/trading price. A single multiple in isolation is not a valuation.
5. **Attribute peaks and records to the right day.** "First-day high," "first-week close," and "all-time intraday" are different things; do not blur them. Cite the day.
6. **Show your basis for growth/margin claims.** "33% growth" must be traceable to two specific revenue figures with their fiscal years; a "net loss" must say GAAP and sit beside any adjusted/EBITDA figure so the reader sees both sides of the P&L.

## Primary-Document Coverage

For any case about a specific company, offering, or transaction, locate and read the **primary disclosure document** — the S-1 / prospectus for an IPO or debt deal, the 10-K / 20-F for an operating company, the DEF 14A for governance and pay, the merger proxy for M&A, the 8-K for the triggering event. News and sell-side notes are **secondary**; they orient you but never replace the filing.

From the primary document, enumerate — explicitly, in your research notes — **all** of the following that exist, not just the ones that fit your first hypothesis:

1. **Business segments** — every reportable segment and every operating segment named in the business description, with each segment's revenue and (where given) operating income.
2. **TAM / market-size breakdown** — every addressable-market figure the issuer states, broken out by segment or geography, and the share each represents.
3. **Use of proceeds** — every named use, in the issuer's own words and order. Note what is *not* named.
4. **Risk factors** — the full set, grouped; flag the idiosyncratic ones (founder/key-person dependency, related-party, milestone-gated pay, regulatory, concentration).
5. **Key-person / founder compensation and award structure** — equity awards, tranche and milestone mechanics, audited grant-date values, and any "considered improbable" auditor notes.
6. **Related-party transactions** — anything between the issuer and founders, affiliates, or control persons.
7. **Share-count basis** — float, shares outstanding, and fully-diluted (options, RSUs, convertibles, tranche awards), stated separately.

Then run a **disclosure-economics scan**: skim the document for term-family frequencies and for what the issuer *emphasizes versus what it buries*. (Example: count AI-family vs. Mars-family terms in a SpaceX prospectus; note whether the use-of-proceeds names the headline theme or omits it.) The largest gap between the marketing narrative and the disclosure text is usually your sharpest case angle.

**Coverage test before you outline:** Can you name every material segment, the largest three risk factors, the CEO's pay mechanics, and the share-count basis? If you cannot, you have not read the document closely enough to write the case. A case that omits a material segment because the writer never enumerated segments is a defective case, not a stylistic choice — the reviewer's Pass 5 will flag it as HIGH.

## Analysis Framework

The Analysis Framework section (Case Structure item 5) is the spine of the case. It gives the reader the *tools* to reach a view; it does not reach the view for them. **The framework must match the angle the user chose** (see [Angle Selection](#angle-selection-confirm-before-you-research)): a valuation or buy/sell/hold case carries the build below, while an investment-decision, product-analysis, industry, strategy, or risk/crisis case carries the angle-appropriate apparatus instead (for example a calibration or efficiency lens, a payoff-and-risk decomposition, or an exposure map). Whatever the angle, the framework must let a competent reader recompute a defensible answer. For a **valuation, capital-allocation, or buy/sell/hold** case, the framework must include, as exhibits or clearly labeled tables, as many of the following as the decision demands:

- **A valuation build**, not just a headline multiple. A segment-level DCF (revenue path, margin path, terminal value, discount rate) or a defensible proxy (comps-derived range, precedent transactions) — with the inputs shown so the reader can flex them.
- **Comps and precedents** — peer multiples and precedent-transaction multiples, each sourced.
- **A "what must the buyer believe" lever table** — hold the framework at base case, solve each lever individually for the market price. This isolates *which* assumption the price is betting on (e.g., a discount-rate revision inside its evidence band vs. a revenue assumption many multiples beyond the TAM).
- **Sensitivity / scenario structure** — at minimum a base/bull/bear or a one-variable sensitivity on the load-bearing assumption(s).
- **Real-options or contingent-claim framing** *when the value is dominated by optionalities* — milestone-gated businesses, staged investments, abandonment options. Name the option, the gate, and the rough magnitude; cite the method (Myers, McDonald–Siegel, Longstaff–Schwartz) only if the case is methods-oriented.
- **Triangulation across independent estimates** — fundamental ranges, secondary-market / private-round prices, prediction-market prints, and the offer/trading price, shown together so the reader can see where the market sits relative to fundamental value.

**Thin vs. adequate.** A framework that quotes only a revenue multiple (e.g., "~100x revenue") and a price chart is **thin** and fails this requirement. An adequate framework lets a reader re-derive a defensible value range and identify the single assumption the price is most sensitive to. For a non-valuation case (e.g., a narrative risk event), the framework may be lighter, but it must still surface the decision-relevant structure (who is exposed, by how much, through what channel).

## Figure Generation

Use the plotting script to create professional figures:

```bash
python scripts/case_plots.py
```

### Available Plot Types

| Function | Use Case | Example |
|----------|----------|---------|
| `plot_time_series` | Trends over time | Stock prices, deposits, rates |
| `plot_bar_chart` | Comparisons | Revenue by segment, market share |
| `plot_stacked_bar` | Composition | Asset allocation, cost breakdown |
| `plot_pie_chart` | Proportions | Deposit composition, market share |
| `plot_dual_axis` | Two metrics | Price and volume, rates and deposits |
| `plot_comparison_bars` | Peer comparison | SVB vs competitors |

### Figure Style

All figures use professional HBS-style formatting:
- Clean white background with subtle grid
- Bold titles and axis labels
- Professional color palette
- High DPI (300) for print quality
- No top/right spines

### Creating Figures

When writing a case, generate figures by:

1. **Identify key data** — What numbers tell the story?
2. **Choose plot type** — Time series for trends, bars for comparisons, pie for proportions
3. **Run the script** — Modify `case_plots.py` with your data
4. **Save to case folder** — Output to `{case_folder}/figures/`

### Example: SVB Case Figures

```python
# Figure 1: Deposit Growth
plot_time_series(
    dates=dates,
    values=deposits,
    title='SVB Total Deposits (2018-2022)',
    ylabel='Deposits ($ Billions)',
    filename='exhibit_deposits.png',
    show_values=True
)

# Figure 2: Uninsured Deposits
plot_pie_chart(
    labels=['Uninsured (>$250K)', 'Insured (<$250K)'],
    values=[94, 6],
    title='SVB Deposit Insurance Status',
    filename='exhibit_uninsured.png',
    colors=['#d62728', '#2ca02c']
)
```

## Financial Data Collection

When building a case, gather:

1. **Market Data** — Prices, volumes, volatility, correlations (Yahoo Finance, FRED, Bloomberg)
2. **Company Data** — Financial statements, SEC filings, earnings calls, investor presentations
3. **News & Analysis** — WSJ, FT, Bloomberg, CNBC coverage of the event
4. **Academic Context** — Relevant research papers on the topic
5. **Regulatory Context** — SEC actions, Fed statements, regulatory changes

Use web search tools to find current data. Document all sources for exhibits.

## Output Formats

The case is authored in Markdown (`.md`) as the single source of truth, then rendered into the deliverable formats the user requests. **Confirm two things with the user, in this order: (1) the angle** ([Angle Selection](#angle-selection-confirm-before-you-research), asked first), **and (2) the output formats** (asked before generating; do not assume).

### 1. Word Document (primary, default)
Convert the authored `.md` to `.docx` using the `md-to-docx` skill (or `docx` skill for richer layout). This is the standard HBS case deliverable.

- Keep the same case folder as the `.md` (e.g. `Case bank/SVB Collapse/SVB_Case.docx`)
- Exhibits/figures embed inline after their referencing text
- Optionally also export a `.pdf` via pandoc

### 2. Beamer Teaching Slides (optional)
On request, generate a companion LaTeX Beamer deck from the **same material** as the case. The deck is for leading the class discussion, not a re-telling — it surfaces the hook, key exhibits, and the open decision questions.

- Start from [slide-template.tex](assets/slide-template.tex) (Metropolis style, compiles with `xelatex`)
- One slide per major case section; one slide per key exhibit
- Close with the decision questions and discussion prompts from the teaching note
- Save as `{case_folder}/{Case_Name}_Slides.tex` and compile to PDF
- If the user has a preferred Beamer style (e.g. the `beamer-slides-teaching` skill), match it instead

**When to offer:** After the Word document is drafted, ask: "Would you also like a Beamer teaching deck from this material?" Only build it if yes — do not auto-generate.

### Output Decision Flow
```
Case drafted (.md) + figures
        │
        ├── Word (.docx) ─── default, always offer
        ├── PDF (.pdf)  ─── optional, via pandoc
        └── Beamer (.tex → .pdf) ─── optional, ask first
```

### Teaching Note (Optional)
Create when the case is complete:
- Learning objectives (2-4 specific takeaways)
- Discussion questions (3-5 questions to guide class)
- Suggested teaching plan (how to structure the discussion)
- Key analysis points (what students should identify)

## Workflow

When given a financial event/product:

0. **Angle Selection (ask first):** Before researching, ask the user which angle to pursue, using the taxonomy in [Angle Selection](#angle-selection-confirm-before-you-research). Do not default to valuation, and do not collapse the options into valuation-flavored investor decisions. The angle dictates the protagonist, framework, and exhibits. Confirm the output formats at the same time or immediately after (see [Output Formats](#output-formats)).

1. **Research Phase**
   1. **Orient with news** — Understand the narrative, the players, the key dates. (Secondary sources only; do not anchor here.)
   2. **Anchor on the primary document** — Read the S-1 / 10-K / proxy / 8-K and run the [Primary-Document Coverage](#primary-document-coverage) enumeration (segments, TAM, use of proceeds, risk factors, comp/award structure, related parties, share-count basis).
   3. **Hunt for a non-obvious angle** — Before settling on a protagonist and decision, search the primary document for a *defensible* angle that is not the headline narrative. Ask:
      - *Disclosure-economics irony*: where does the issuer's emphasis diverge from its actual capital allocation?
      - *Repricing-of-risk framing*: is the market debate really about cash flows, or about the price of risk / the discount rate?
      - *Optionality*: is most of the value in contingent, milestone-gated upside rather than the base business?
      - *Flow vs. fundamental*: is the price being set by mechanical flows (index inclusion, seasoning rules) rather than by views?
   4. **Choose the protagonist and decision to fit the angle:** Honor the angle the user confirmed in Phase 0. Pick a role whose job demands the analysis the angle requires (see [Protagonist and Decision Depth](#protagonist-and-decision-depth)). The angle should dictate the protagonist, not the other way around.
   5. **Gather market data and academic context** — Prices, comps, precedents, and any rigorous secondary analysis (working papers, valuation decks). A rigorous *external* analysis is a source to engage with, not a template to copy — use it to pressure-test your own framework and as a coverage checklist (what segments/frameworks does it surface that your case must at least acknowledge?).

2. **Outline Phase**
   - Map the narrative arc
   - Identify required exhibits
   - Determine the decision point

3. **Writing Phase**
   - Draft sections in order (hook → background → situation → decision)
   - Create exhibits with sourced data
   - Write teaching note if requested

4. **Output Phase**
   - Confirm with the user which formats they want (Word default; Beamer optional)
   - Render the `.md` to the chosen formats (see Output Formats)

5. **Review & Revise Phase**
   - Hand the drafted case to the `case-reviewer` agent (see Case Review & Revision below)
   - The reviewer critiques the case, verifies facts and references, and returns a scored report
   - Apply the revisions, then re-render the affected outputs
   - One review-revise round by default; loop again if the user requests or the score is below threshold

## Case Review & Revision

Every drafted case goes through a review pass before it is considered final. This follows the project's worker-critic separation of powers: **the `case-reviewer` agent only critiques and verifies — it never rewrites. The HBS Case Writer applies the fixes.**

### The Reviewer's Job
The `case-reviewer` agent (`.claude/agents/case-reviewer.md`) produces a scored report against the rubric in [case-review-rubric.md](references/case-review-rubric.md). It checks:

- **HBS style fidelity** — narrative voice, unresolved decision, no hindsight, exhibits carry data
- **Fact verification** — spot-checks numbers, dates, names, and quotes against primary/credible sources via web search
- **Reference & source integrity** — every exhibit sourced, sources resolve, no fabricated citations
- **Pedagogical soundness** — clear decision point, conflicting information present, teaching note aligned
- **Decision-relevant coverage** — every material segment from the primary filing appears; valuation cases carry a real framework (build/comps/lever/sensitivity), not just headline multiples; use-of-proceeds, TAM, key-person pay, and share-count basis are faithfully represented

### The Revise Loop
```
Drafted case (.md + exhibits)
        │
        ▼
  case-reviewer → scored report (0-100) + issue list with severity
        │
        ├── score >= 85 and no HIGH issues → done
        │
        └── otherwise → HBS Case Writer applies fixes
                │
                ▼
          (re-render outputs) → optional second review round
```

- Score starts at 100; deductions per the rubric
- HIGH severity issues (fabricated facts, missing sources, broken decision point) block delivery
- Max 2 review-revise rounds before surfacing remaining issues to the user
- The reviewer's findings are saved alongside the case as `{Case_Name}_review.md`

## References

- [hbs-patterns.md](references/hbs-patterns.md) — Detailed patterns from real HBS cases
- [financial-data-sources.md](references/financial-data-sources.md) — Where to find financial data
- [case-review-rubric.md](references/case-review-rubric.md) — Scoring rubric used by the `case-reviewer` agent
- [slide-template.tex](assets/slide-template.tex) — Beamer teaching deck template
- `case-reviewer` agent (`.claude/agents/case-reviewer.md`) — Reviews and verifies a drafted case
