Day 48 — Compare & Decide Builder

What I Built

I built Compare & Decide Builder, an interactive decision-support application for comparing AI coding assistants.

The application compares Cursor, GitHub Copilot, Windsurf, and Claude Code across five criteria:

Cost

Features

Ease of Use

Availability

Performance

Instead of presenting one fixed “best” choice, the application lets users adjust criterion weights and updates the ranking dynamically.

Purpose

The purpose of the application is to help students and developers choose an AI coding assistant based on their own priorities.

The application demonstrates:

Weighted decision scoring

Transparent comparison

Real-world sourced information

Visible citations

Editorial-synthesis flags

Research methodology

Live ranking updates

Decision Being Compared

Which AI coding assistant actually fits how a developer works?

The four options are:

Cursor

GitHub Copilot

Windsurf

Claude Code

The application is designed for students and developers choosing their next AI coding tool.

Options Compared

Cursor

AI-native VS Code fork · Anysphere

Criterion

Score

Cost

5/10

Features

9/10

Ease of Use

8/10

Availability

6/10

Performance

7/10

GitHub Copilot

Plugin for any IDE · Microsoft/GitHub

Criterion

Score

Cost

8/10

Features

6/10

Ease of Use

9/10

Availability

10/10

Performance

5/10

Windsurf

Agentic IDE · Cognition AI

Criterion

Score

Cost

6/10

Features

7/10

Ease of Use

7/10

Availability

5/10

Performance

6/10

Claude Code

Terminal-native coding agent · Anthropic

Criterion

Score

Cost

3/10

Features

8/10

Ease of Use

5/10

Availability

4/10

Performance

10/10

Decision Criteria

Cost

Lower monthly price for a solo developer receives a higher score.

Features

Measures the breadth of agentic, multi-file, and model capabilities.

Ease of Use

Considers setup friction, learning curve, and editor familiarity.

Availability

Considers platform/IDE reach, free-tier access, and availability signals.

Performance

Uses reported benchmark information, context-window information, and performance reporting where available.

Data Sources

The HTML application contains a dedicated Sources Panel listing the citations used for the comparison.

The sources include:

LowCode Agency — Cursor pricing

eesel — Cursor pricing

CloudZero — GitHub Copilot pricing

Nocode MBA — GitHub Copilot pricing

CloudZero — Windsurf pricing

K-Antenna — Windsurf pricing

SSD Nodes — Claude Code pricing

Claudify — Claude Code pricing

NXCode — Cursor vs Claude Code vs GitHub Copilot

Kanerika — GitHub Copilot vs Claude Code vs Cursor vs Windsurf

Browse AI — GitHub Copilot vs Cursor vs Windsurf

Gil Ricardo — Cursor vs Claude Code vs Windsurf vs Copilot

Fundesk — AI Coding Agents Compared

Modern Data Tools — Windsurf pricing

DevTools Review — Windsurf pricing

LushBinary — AI Coding Agents comparison

Each source entry in the application contains its title, domain, URL, and verification date.

Initial Ranking

The default Balanced preset uses:

Criterion

Weight

Cost

20%

Features

20%

Ease of Use

20%

Availability

20%

Performance

20%

Using these weights, the application's weighted calculation produces:

Rank

Tool

Weighted Score

1

GitHub Copilot

7.60 / 10

2

Cursor

7.00 / 10

3

Windsurf

6.20 / 10

4

Claude Code

6.00 / 10

These are calculated scores from the application's stored criterion scores, not scores directly published by the cited sources.

Criteria Weights

The application allows each criterion to be adjusted from 0 to 50.

Available presets:

Balanced

Budget student

Power / performance

Team lead

Balanced

Cost 20 · Features 20 · Ease of Use 20 · Availability 20 · Performance 20

Budget Student

Cost 45 · Features 10 · Ease of Use 25 · Availability 15 · Performance 5

Power / Performance

Cost 10 · Features 30 · Ease of Use 10 · Availability 15 · Performance 35

Team Lead

Cost 15 · Features 20 · Ease of Use 15 · Availability 35 · Performance 15

The application also includes a Reset to balanced button.

Weight Adjustment Experiment

The application recalculates rankings whenever a criterion slider changes.

Initial Weights

The default configuration is:

20 / 20 / 20 / 20 / 20

Changed Weights

The application supports changing individual weights with sliders and selecting the four predefined presets.

Ranking Before

With the Balanced configuration:

GitHub Copilot → Cursor → Windsurf → Claude Code

Ranking After

The HTML code supports live ranking changes, but it does not store a user's manual post-adjustment result. Therefore, the exact final ranking after a manual adjustment should be added here only after completing the actual test.

Sources Panel

The application includes a collapsible Sources panel titled:

Every citation used to build this comparison

Each source entry displays:

Associated tool

Source title

Domain

Verification date

Clickable source URL

This makes the research behind the comparison visible.

How This Was Researched

The application includes a collapsible How this was researched panel.

Scoring Approach

Each tool receives a 1–10 score for every criterion.

The methodology explains that:

Cost scores are anchored to real monthly pricing.

Performance scores use reported SWE-bench Verified results and context-window information where available.

Features, ease of use, and availability include Claude's editorial synthesis of cited information.

Editorial-synthesis values are clearly flagged in the comparison table.

Cost

Pricing was cross-checked across two independent write-ups per tool.

The methodology also notes that credit- or token-metered billing can make the published monthly figure a floor rather than a hard ceiling for heavy users.

Performance

SWE-bench Verified is used as the main shared benchmark where available.

The application notes that comparable benchmark figures were not available for every tool, so qualitative reporting was not converted into invented numerical benchmarks.

Conflicting Sources

Windsurf Pro Pricing

Some sources still listed Windsurf Pro at the former $15/month price.

The application uses $20/month, based on later sources reporting a pricing change in March 2026.

The older price is treated as outdated.

GitHub Copilot Billing

Sources differed on how Copilot's listed prices should be interpreted.

The application uses the more recent interpretation that the listed prices represent monthly credit allowances rather than simply unlimited usage ceilings.

Estimates and Calculated Values

The application distinguishes sourced information from editorial synthesis.

The HTML marks some Ease of Use, Availability, and Performance values as editorial synthesis.

The weighted ranking is a calculated result produced by the application's JavaScript scoring formula.

The application states that no data point was invented to fill a research gap.

Final Ranking

The ranking depends on the selected weights.

With the default Balanced configuration:

GitHub Copilot — 7.60 / 10

Cursor — 7.00 / 10

Windsurf — 6.20 / 10

Claude Code — 6.00 / 10

This should not be interpreted as a universal ranking because users can change the importance of each criterion.

Key Learning

The main lesson from the application is that there is not necessarily one universally “best” tool.

The best choice can change depending on what the user values most.

Weighted decision scoring makes those priorities visible and allows the recommendation to adapt to them.

Transparency

Transparency is a central part of the application.

It exposes:

Individual criterion scores

Supporting factual descriptions

Editorial-synthesis labels

Source links

Verification dates

Research methodology

Conflict explanations

Weighted-score calculations

A pricing and benchmark disclaimer

The application also recommends checking vendor pricing directly before making a purchase decision because pricing and model versions can change.

My Experience

Building this project showed how research, data modeling, scoring logic, and interface design can work together in one application.

The most interesting feature is the live ranking system. Instead of displaying only a predetermined winner, the application lets users change what matters to them and see the ranking respond.

The Sources and How This Was Researched panels also make the reasoning easier to inspect.

Biggest Insight

There is not always one universally “best” tool. The best choice depends on what the user values most.

A weighted decision model makes those priorities visible and turns a simple comparison into a more structured decision process.

What I Learned

How to structure a multi-criteria decision model.

How weighted scoring can personalize rankings.

Why real-world data needs traceable sources.

Why estimates and editorial judgments should be labeled.

Why conflicting sources should be surfaced instead of hidden.

How interactive controls can turn a static comparison into a decision-support system.

How transparency can make an AI-generated application more trustworthy.

Screenshots

Add the actual screenshots from the completed application here.

Recommended screenshots:

Main comparison dashboard

Balanced ranking

Adjusted criteria weights

Updated ranking after the weight change

Sources panel

How This Was Researched panel

Technical Notes

The application is a single HTML file using:

HTML

CSS

Vanilla JavaScript

It includes:

Responsive layout

Interactive weight sliders

Preset weighting modes

Live ranking updates

Full comparison table

Sources panel

Research methodology panel

Expand/collapse interactions

Loading state

Error fallback

Mobile responsive behavior

Project Folder
