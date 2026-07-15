# Competitive Research Subskill

## Purpose
Research competitive intelligence for a specific opportunity, including competitor positioning, battlecards, win/loss analysis, and trap questions.

## Inputs
- Opportunity ID
- Account name
- Known competitors (from Salesforce)
- Industry

## Research Strategy

### 1. Identify Competitors
- Pull known competitors from Salesforce opportunity
- Search mentions in Gong call transcripts
- Check recent wins/losses against similar competitors
- Look for competitor mentions in account Slack threads

### 2. Gather Competitive Intelligence

Search across:
- **Competitive Intelligence Collection** in Glean
- **Battlecards** (Confluence, Drive)
- **Win/Loss Analysis** (Salesforce, Gong)
- **Compete Newsletter** archives
- **#competitive** Slack channel
- **Sales enablement** materials

### 3. Extract Key Information

For each competitor, gather:
- **Positioning** - How they position themselves
- **Strengths** - What they do well
- **Weaknesses** - Where they fall short
- **Pricing model** - How they charge
- **Win strategies** - How we beat them
- **Trap questions** - Questions that expose their weaknesses
- **Landmines** - Areas to avoid
- **Recent activity** - Product launches, messaging changes

### 4. Contextualize for This Opportunity

- Match competitor weaknesses to buyer needs
- Identify which trap questions are most relevant
- Surface recent win stories against these competitors
- Note any account-specific competitive history

## Output Format

Return structured data for each competitor:

```json
{
  "competitor_name": "Competitor Name",
  "in_deal": true/false,
  "positioning": "How they position...",
  "key_strengths": ["Strength 1", "Strength 2"],
  "key_weaknesses": ["Weakness 1", "Weakness 2"],
  "pricing_model": "Description of pricing...",
  "win_strategy": "How to beat them in this deal...",
  "trap_questions": [
    "Question 1 that exposes weakness?",
    "Question 2 that exposes weakness?"
  ],
  "landmines": ["Avoid topic 1", "Avoid topic 2"],
  "recent_intel": "Recent competitive activity...",
  "relevant_wins": [
    {
      "customer": "Customer Name",
      "context": "Similar situation...",
      "outcome": "What happened..."
    }
  ]
}
```

## Search Queries

Use these searches to gather intelligence:

1. **Battlecards**: `[competitor] battlecard win strategy differentiation`
2. **Win/Loss**: `[competitor] won lost deal why app:salescloud`
3. **Recent Intel**: `[competitor] launch announcement updated:past_month`
4. **Trap Questions**: `[competitor] weakness objection gotcha question`
5. **Gong Analysis**: `[competitor] mentioned app:gong in:[account-name]`

## Quality Checks

- ✓ At least 3 competitors researched (or all known competitors)
- ✓ Each competitor has win strategy
- ✓ Trap questions are specific and actionable
- ✓ Recent intel is within last 6 months
- ✓ Win stories are relevant to this industry/use case