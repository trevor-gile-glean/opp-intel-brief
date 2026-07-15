# Opportunity Intelligence Brief - Quick Usage Guide

## Quick Start

### Basic Usage

```
/opp-intel-brief <salesforce-opportunity-id>
```

**Example:**
```
/opp-intel-brief 006PZ00000LQamxYAD
```

This will generate a comprehensive intelligence brief in ~5 minutes with:
- ✅ Opportunity context and key contacts
- ✅ Competitive intelligence
- ✅ Differentiation messaging  
- ✅ Use case to solution mapping
- ✅ 5-7 relevant customer references
- ✅ Industry intelligence
- ✅ Actionable next steps

## When to Use This Skill

### Perfect For:
- 📞 **Pre-call preparation** - Get up to speed before customer meetings
- 📊 **Deal reviews** - Prepare comprehensive analysis for deal review meetings
- 🎯 **Competitive situations** - Understand how to position against competitors
- 🚀 **Deal acceleration** - Find insights to move stalled deals forward
- 👥 **Account planning** - Strategic planning for key accounts
- 📝 **Executive briefings** - Create executive-ready opportunity summaries

### Best Timing:
- Before important customer calls or demos
- When deal enters new stage (especially 3-4-5)
- After competitive information emerges
- Before QBRs or deal reviews
- When taking over an opportunity from another AE

## Advanced Options

### Research Depth

Control how comprehensive the research is:

```bash
# Quick brief (~2 minutes) - essentials only
/opp-intel-brief 006ABC123 --depth quick

# Standard brief (~5 minutes) - comprehensive [DEFAULT]
/opp-intel-brief 006ABC123 --depth standard

# Deep research (~10-15 minutes) - exhaustive analysis
/opp-intel-brief 006ABC123 --depth deep
```

**Depth Comparison:**

| Feature | Quick | Standard | Deep |
|---------|-------|----------|------|
| Time | ~2 min | ~5 min | ~10-15 min |
| Competitors | Top 2-3 | All known | All + emerging |
| References | 2-3 | 5-7 | 10+ scored |
| Industry Research | Basic | Standard | Comprehensive |
| Use Case Mapping | High-level | Detailed | Exhaustive |
| Recommendations | Basic | Comprehensive | Strategic |

### Focus Areas

Focus on specific intelligence areas:

```bash
# Competitive intelligence only
/opp-intel-brief 006ABC123 --focus competitive

# Customer references only  
/opp-intel-brief 006ABC123 --focus references

# Industry intelligence only
/opp-intel-brief 006ABC123 --focus industry

# Multiple areas
/opp-intel-brief 006ABC123 --focus competitive,references

# Everything [DEFAULT]
/opp-intel-brief 006ABC123 --focus all
```

### Using Salesforce URLs

You can paste the full Salesforce URL instead of just the ID:

```bash
/opp-intel-brief https://glean.lightning.force.com/lightning/r/Opportunity/006PZ00000LQamxYAD/view
```

## Understanding the Output

### The HTML Artifact

The skill generates a **branded HTML artifact** that includes:

#### 1. Executive Summary
- Deal snapshot (account, stage, amount, close date)
- Top 3-5 key insights
- Critical action items

#### 2. Opportunity Context  
- Account overview
- Key contacts and stakeholders
- Current sales activity
- Identified needs and requirements
- Known competitors

#### 3. Competitive Intelligence
- Competitor landscape
- Head-to-head comparisons
- Trap questions to ask
- Win strategies and battlecards
- Recent competitive intel

#### 4. Differentiation Messaging
- Key differentiators for this deal
- Value proposition tailored to buyer
- Proof points and evidence
- Objection handling strategies

#### 5. Use Case & Solution Mapping
- Identified business needs
- Glean solutions mapped to needs
- Implementation approach
- ROI and business case elements

#### 6. Customer References
- Similar customers (industry, size, use case)
- Case studies and success stories
- Reference contacts (if available)
- Industry-specific proof points

#### 7. Industry Intelligence
- Industry trends affecting this buyer
- Common pain points in industry
- Regulatory/compliance considerations
- Industry-specific messaging

#### 8. Next Steps & Recommendations
- Stage-specific action items
- Suggested resources and assets
- Follow-up actions
- Risk mitigation strategies

## Pro Tips

### For Best Results:

1. **Keep Salesforce Updated**
   - Add competitors to the opportunity
   - Document requirements and use cases in notes
   - Keep contacts and stage current
   - Log activities and next steps

2. **Run at Key Milestones**
   - When opportunity enters qualification stage
   - Before important customer meetings
   - When competitive situation emerges
   - Before moving to next stage

3. **Share with Your Team**
   - HTML artifacts have stable URLs
   - Share with SEs, CSMs, leadership
   - Use in deal reviews and planning sessions
   - Reference during team coaching

4. **Re-run as Deal Evolves**
   - Refresh when new information emerges
   - Update after competitive changes
   - Re-analyze after stage changes
   - Get fresh intel before close

5. **Combine with Other Skills**
   - Use `/ae-weekly-brief` for pipeline view
   - Use `/account-research` for deeper account intel
   - Use `/competitive-analysis` for competitive deep-dives

### Time Management:

- **Morning prep**: Run `quick` depth for today's calls
- **Weekly planning**: Run `standard` depth for key deals
- **Deal reviews**: Run `deep` depth the day before
- **Emergency prep**: Run `quick` depth for unexpected meetings

## Common Scenarios

### Scenario 1: New Opportunity Handoff
**Situation**: Taking over an opportunity from another AE

```bash
/opp-intel-brief 006ABC123 --depth deep
```

**Why**: Get comprehensive understanding of account history, competitive landscape, and deal context.

---

### Scenario 2: Competitive Threat
**Situation**: Prospect mentions they're evaluating a competitor

```bash
/opp-intel-brief 006ABC123 --focus competitive --depth standard
```

**Why**: Quickly get battlecard, trap questions, and win strategies for that competitor.

---

### Scenario 3: Stuck Deal
**Situation**: Deal has been in same stage for 3+ weeks

```bash
/opp-intel-brief 006ABC123 --depth deep
```

**Why**: Find new angles, compelling references, and strategies to re-engage buyer.

---

### Scenario 4: Last-Minute Call Prep
**Situation**: Unexpected call with customer in 30 minutes

```bash
/opp-intel-brief 006ABC123 --depth quick
```

**Why**: Get essential competitive intel, key differentiators, and 2-3 good references fast.

---

### Scenario 5: Executive Sponsor Engagement
**Situation**: Need to engage CXO or economic buyer

```bash
/opp-intel-brief 006ABC123 --depth deep --focus industry,references
```

**Why**: Get industry trends, executive-level messaging, and peer company references.

---

### Scenario 6: Technical Evaluation
**Situation**: Moving into technical/POC stage

```bash
/opp-intel-brief 006ABC123 --focus technical
```

**Why**: Map technical requirements to Glean capabilities and find technical references.

## What the Skill Does NOT Do

This skill is for **opportunity intelligence**, not:

- ❌ **Account planning** - Use `/account-research` for deep account analysis
- ❌ **Pipeline forecasting** - Use `/ae-weekly-brief` for pipeline management
- ❌ **Proposal generation** - Use Glean Assistant to draft proposals
- ❌ **ROI calculation** - Use Glean ROI calculator or ask Glean Assistant
- ❌ **Live Salesforce updates** - Does not write back to Salesforce
- ❌ **Gong call analysis** - Does not analyze specific calls (but uses Gong data)

## Troubleshooting

### "Opportunity not found"
- ✓ Check the opportunity ID is correct
- ✓ Ensure you have access to this opportunity in Salesforce
- ✓ Verify opportunity hasn't been deleted

### "No competitive intelligence found"
- ✓ Add competitors to Salesforce opportunity
- ✓ Check if there are Gong calls mentioning competitors
- ✓ Try running with `--depth deep` for broader search

### "Few references found"
- ✓ Industry might be new for Glean
- ✓ Try adjacent industries (e.g., "Financial Services" → "Banking")
- ✓ Check if reference content exists in Glean

### "Taking too long"
- ✓ Deep research can take 10-15 minutes
- ✓ Try `--depth standard` or `--depth quick`
- ✓ Focus on specific areas with `--focus`

### "HTML looks wrong"
- ✓ Refresh the browser
- ✓ Try opening in different browser
- ✓ Report issue to #sales-enablement

## Getting Help

- **Slack**: #sales-enablement
- **Email**: sales-ops@glean.com
- **Documentation**: https://docs.glean.com/skills/opp-intel-brief
- **Report Issues**: Glean feedback or GitHub

## Examples from Real Usage

### Example 1: Enterprise Deal Prep
```
/opp-intel-brief 006XYZ789 --depth deep
```
*Used before $500K+ deal review. Found 3 perfect references in same industry, trap questions for incumbent competitor, and uncovered compliance requirement we hadn't addressed. Deal closed 2 weeks later.*

### Example 2: Competitive Displacement
```
/opp-intel-brief 006ABC456 --focus competitive --depth standard
```
*Prospect was leaning toward Microsoft. Skill surfaced recent competitive win in same industry with similar requirements. Used trap questions in next call. Prospect scheduled POC next day.*

### Example 3: New AE Onboarding
```
/opp-intel-brief 006DEF123 --depth deep
```
*New AE taking over 8 opportunities. Ran skill on each to understand context, competitive situation, and next steps. Ramped up in 1 week instead of 3-4.*

---

**Version**: 1.0.0  
**Last Updated**: 2026-06-02  
**Maintained by**: Glean Skills Team