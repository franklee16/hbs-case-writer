# HBS Case Patterns

Patterns observed from Harvard Business School investment cases.

## Opening Structures

### The Decision Moment Hook
Start the case with the protagonist at the moment of decision:

> "In January 2021, Gabe Plotkin, founder of Melvin Capital, faced a growing short position in GameStop that had turned against him. As the stock price surged, he had to decide whether to cover the position and realize losses, or hold firm and risk even greater losses."

**Pattern elements:**
- Specific date
- Named protagonist with role
- Clear decision statement
- Stakes implied

**Decision depth.** Not all decisions make equally good cases. A protagonist choosing a price target with a segment DCF behind it generates more analytical texture than a retail investor deciding whether to lock in a gain. Match the decision's analytical demands to the protagonist's role — favor decisions the reader can recompute (price target, buy/hold/sell, underwrite, allocate) over purely behavioral calls.

### The Question Hook
Open with a question the reader will grapple with:

> "Was gold a good portfolio diversifier? The question had taken on new urgency after gold's remarkable run during the financial crisis."

## Section Patterns

### Background Sections
Provide context without solving the problem:

**Industry Background:**
- Define the market/industry
- Key players and competitive dynamics
- Recent trends or disruptions
- Regulatory environment if relevant

**Protagonist Background:**
- Who they are (organization, role)
- Their investment philosophy or approach
- Why they're facing this decision
- Relevant constraints (mandate, investors, risk limits)

### Data Presentation
Let exhibits carry the numbers:

- Tables show performance, valuations, financials
- Charts show trends, correlations, comparisons
- Text describes what the data means, not just the numbers
- Source everything: "As shown in Exhibit 3, the fund had returned..."

### The Unresolved Ending
End with questions, not answers:

> "Plotkin weighed his options. Should he cover now and accept the losses? Was the squeeze sustainable? What would happen to his fund—and his reputation—if he was wrong?"

## Tone Patterns

### Objective Voice
❌ "GameStop was clearly overvalued"
✅ "GameStop traded at 50x revenue, a multiple far exceeding traditional retailers"

### Present Tense Narrative
❌ "The fund had lost money"
✅ "The fund loses money"

### Avoiding Hindsight
Since cases are written after events, maintain the uncertainty that existed at the time:

❌ "The market would soon crash"
✅ "Some analysts warned of a bubble, while others saw room for further gains"

## Exhibit Patterns

### Performance Tables
```
Exhibit 1: Fund Performance (2018-2020)

                     2018    2019    2020
Returns (%)          12.4    18.2    -5.3
Benchmark (%)        8.2     15.1    7.4
Alpha (%)            4.2     3.1    -12.7

Source: Fund documents
```

### Market Data
```
Exhibit 2: GameStop Stock Price and Volume

Date        Price ($)    Volume (M)    Short Interest (%)
Dec 1       16.56        2.1           72.0
Dec 15      18.84        3.4           71.2
Jan 4       17.87        4.2           70.8
Jan 13      31.40        17.5          68.4
Jan 19      39.12        58.2          61.0

Source: Bloomberg
```

### Timeline Exhibit
```
Exhibit 3: Key Events Timeline

January 11, 2021    —  Cohen appointed to GameStop board
January 13, 2021    —  Stock price surges 57%
January 19, 2021    —  Citron Research publishes short report
January 22, 2021    —  Trading volume exceeds 197 million shares
January 25, 2021    —  Melvin Capital covers short position

Source: Company filings, news reports
```

### Valuation-Framework Exhibits
For a valuation or buy/sell/hold case, expect to carry framework exhibits — they present the *apparatus* the reader will use, not the conclusion:

- **Segment valuation build** — one row per segment: base-year revenue, terminal revenue, terminal margin, present value; plus net cash. Sum to an equity value and per-share figure.
- **"What must the buyer believe" lever table** — "To justify the $X price, this lever must move from base to Y," one row per lever, with each lever's evidence range beside it (so the reader sees which assumption the price is actually betting on).
- **Estimate triangulation** — fundamental (Morningstar/Damodaran-style), secondary-market/private-round, precedent, prediction-market, offer price, and trading price, in one table, so the reader sees where the market sits relative to fundamental value.
- **Physical-unit translation** (when powerful) — implied revenue restated as launches/day, subscribers, GW of compute, beside today's actual figure. This makes abstract multiples concrete for students.

Example (illustrative, SpaceX IPO 2026):
```
Exhibit: What $1.77T Must Believe (one lever at a time, others at base)

Lever                       Base     Implied by $1.77T   Assessment
Starlink terminal margin    60%      137%                no feasible value
xAI 2036 revenue            $160B    $640B               above supported range
Launch 2036 revenue         $40B     $266B               above supported range
Discount rate               8.25%    6.86%               inside estimation error

Source: segment build calibrated to published valuations (Damodaran, ARK, Morningstar)
```
These are framework exhibits: they let the reader re-derive a value range and locate the single load-bearing assumption, rather than handing over a headline multiple.

## Teaching Note Patterns

### Learning Objectives
Write 2-4 specific, actionable objectives:

1. Understand the mechanics of short selling and short squeezes
2. Analyze the role of retail investors and social media in modern markets
3. Evaluate risk management practices in hedge funds
4. Discuss market efficiency in the context of meme stocks

### Discussion Questions
Open-ended questions that require analysis:

1. What drove the GameStop short squeeze?
2. Was this a market failure or market functioning as designed?
3. How should Melvin Capital have managed this risk differently?
4. What are the implications for hedge fund risk management?

### Teaching Plan
Structure the 80-minute class:

- **Opening (5 min)** — Cold call on the decision
- **Background (15 min)** — Short selling mechanics, GameStop's situation
- **Analysis (25 min)** — What happened, why it happened
- **Discussion (20 min)** — Implications for markets and regulation
- **Closing (15 min)** — Synthesis and key takeaways
