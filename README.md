# HBS Case Writer

A Claude Code skill for creating Harvard Business School-style teaching cases on financial market events and investment decisions.

## Overview

This skill transforms real-world financial events into immersive, decision-focused teaching cases following HBS conventions. It's designed for finance professors, case writers, and anyone developing instructional materials for business education.

### Key Features

- **Narrative structure** — Opens at the decision moment with a named protagonist
- **Objective tone** — Third-person, present tense, journalistic style
- **Unresolved ending** — Ends with open questions, never conclusions
- **Data-driven exhibits** — Professional tables and charts with proper sourcing
- **Figure generation** — Publication-quality matplotlib visualizations (300 DPI)

## Installation

### Prerequisites

- [Claude Code](https://github.com/anthropics/claude-code) installed
- Python 3.8+ with matplotlib and pandas (for figure generation)

### Setup

1. Clone this repository:
   ```bash
   git clone https://github.com/franklee16/hbs-case-writer.git
   ```

2. Copy to your Claude skills directory:
   ```bash
   cp -r hbs-case-writer ~/.claude/skills/
   ```

   Or on Windows:
   ```cmd
   xcopy /E /I hbs-case-writer %USERPROFILE%\.claude\skills\hbs-case-writer
   ```

## Usage

Invoke the skill in Claude Code:

```
/hbs-case-writer Write an HBS case about the SVB collapse
```

Or describe the event directly:

```
Create a teaching case on spot Bitcoin ETFs
```

## Skill Structure

```
hbs-case-writer/
├── SKILL.md                      # Main skill instructions for Claude
├── README.md                     # This file
├── scripts/
│   └── case_plots.py            # Figure generation (matplotlib)
├── references/
│   ├── hbs-patterns.md          # Detailed patterns from real HBS cases
│   └── financial-data-sources.md # Where to find financial data
└── assets/
    └── case-template.md         # Ready-to-use case template
```

## Case Structure

Every case follows this architecture:

1. **Title & Header** — Case title, protagonist name/role, date, institution
2. **Opening Hook** — Start at the decision moment; protagonist faces a choice
3. **Background** — Industry context, market conditions, relevant history
4. **The Situation** — Specific events, data, and stakeholders involved
5. **The Decision** — End with open questions; NO resolution

## Figure Generation

Generate professional figures using the included plotting script:

```bash
cd hbs-case-writer/scripts
python case_plots.py
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

### Example: Creating Figures

```python
from case_plots import plot_time_series, plot_pie_chart

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

## Writing Principles

### Narrative Style
- Third-person limited (follow the protagonist)
- Present tense throughout
- Objective, journalistic tone — no judgments or conclusions
- Let facts and data tell the story

### What Makes It a Case (Not an Article)
- Ends with a decision point, never a resolution
- Presents conflicting information or trade-offs
- Reader must analyze, not just absorb
- Avoid teaching explicitly — immerse the reader instead

### The Protagonist
- Name a specific person or team facing the decision
- Give them a role, organization, and stakes
- Show their thought process through action, not introspection

## Data Sources

The skill draws from:
- **Market data** — Yahoo Finance, FRED, Bloomberg
- **Company data** — SEC EDGAR filings, earnings calls
- **News** — WSJ, FT, CNBC, Bloomberg
- **Academic** — SSRN, NBER working papers

See [references/financial-data-sources.md](references/financial-data-sources.md) for a comprehensive list.

## Output Format

The skill produces:
1. **Case document** — Full narrative with exhibits (Markdown format)
2. **Figures** — Professional publication-quality charts (PNG, 300 DPI)
3. **Teaching note** (optional) — Learning objectives, discussion questions, teaching plan

## Case Template

Use the included template to get started quickly:

```
assets/case-template.md
```

## References

- [HBS Case Patterns](references/hbs-patterns.md) — Detailed patterns from real HBS cases
- [Financial Data Sources](references/financial-data-sources.md) — Comprehensive data source guide

## Requirements

For figure generation:
```
matplotlib>=3.5.0
pandas>=1.3.0
numpy>=1.21.0
```

Install with:
```bash
pip install matplotlib pandas numpy
```

## License

MIT License

## Author

Created by Weikai Li, Professor of Finance at City University of Hong Kong.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## Acknowledgments

- Inspired by Harvard Business School case writing methodology
- Built for [Claude Code](https://github.com/anthropics/claude-code)
