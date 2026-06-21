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
5. **Analysis Framework** — Information the reader needs to analyze (not the analysis itself)
6. **The Decision** — End with open questions; NO resolution

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

The case is authored in Markdown (`.md`) as the single source of truth, then rendered into the deliverable formats the user requests. **Always ask the user which outputs they want** before generating; do not assume.

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

1. **Research Phase**
   - Identify the key decision and protagonist
   - Gather market data, news, and financials
   - Find academic or analytical context

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
