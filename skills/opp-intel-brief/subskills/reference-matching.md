# Customer Reference Matching Subskill

## Purpose
Find and rank customer references that are most relevant to the target opportunity based on industry, company size, use cases, and business context.

## Inputs
- Account name
- Industry
- Company size (employee count, revenue)
- Identified use cases
- Geographic region
- Specific requirements or pain points

## Research Strategy

### 1. Build Target Profile

Extract key matching criteria:
- **Industry** - Primary industry vertical
- **Sub-industry** - More specific categorization
- **Company size** - Employee range, revenue band
- **Use cases** - Specific problems being solved
- **Persona** - Who is buying (IT, Engineering, Sales, etc.)
- **Tech stack** - Known technologies they use
- **Buying triggers** - What prompted evaluation

### 2. Search for Customer References

Search across:
- **Customer case studies** (website, Drive, Confluence)
- **Customer success stories** 
- **Reference lists** and reference sheets
- **Salesforce won opportunities** with similar profiles
- **Customer testimonials** and quotes
- **Industry-specific customer decks**
- **#customer-success** Slack channel

### 3. Score and Rank References

Score each reference based on match quality:

**Critical matches** (30 points each):
- Same industry vertical
- Similar company size (within 2x)
- Same primary use case

**Strong matches** (20 points each):
- Adjacent industry
- Same buyer persona
- Same competitive displacement

**Good matches** (10 points each):
- Same geographic region
- Similar tech stack
- Similar business model

**Bonus factors** (5 points each):
- Recent win (last 6 months)
- Executive testimonial available
- Video case study available
- Reference willing to speak
- ROI metrics documented

### 4. Enrich Reference Data

For top-ranked references, gather:
- Company overview and metrics
- Use cases implemented
- Business outcomes achieved
- ROI and time-to-value
- Quote or testimonial
- Contact for reference call (if available)
- Case study link
- Competitive displacement story

### 5. Categorize by Use Type

Organize references by:
- **Call references** - Willing to speak with prospects
- **Written case studies** - Public or internal docs
- **Logo/name only** - Can mention as customer
- **Industry proof points** - For presentations
- **Technical validation** - For technical buyers

## Output Format

Return ranked list of references:

```json
{
  "references": [
    {
      "company_name": "Reference Company",
      "match_score": 85,
      "industry": "Financial Services",
      "size": "5,000 employees",
      "use_cases": ["Use case 1", "Use case 2"],
      "outcomes": {
        "roi": "40% reduction in time to find information",
        "time_to_value": "4 weeks",
        "adoption": "90% DAU"
      },
      "quote": "Glean has transformed...",
      "quote_attribution": "CTO, Reference Company",
      "case_study_url": "https://...",
      "reference_type": "call_reference",
      "contact_available": true,
      "competitive_win": "Displaced Microsoft Search",
      "why_relevant": [
        "Same industry",
        "Similar size",
        "Same use case"
      ]
    }
  ]
}
```

## Search Queries

Use these searches to find references:

1. **Industry**: `customer case study [industry] success story`
2. **Use Case**: `[use case] implementation customer testimonial`
3. **Competitive**: `displaced [competitor] customer win`
4. **Size**: `enterprise large company [industry] customer`
5. **Recent**: `customer case study updated:past_6_months`
6. **References**: `reference sheet customer list [industry]`

## Quality Checks

- ✓ At least 5-7 references for standard depth
- ✓ At least 10+ references for deep research
- ✓ Top 3 references have match score > 70
- ✓ Each reference has clear relevance explanation
- ✓ Mix of reference types (calls, case studies, logos)
- ✓ At least 1-2 from same industry
- ✓ Outcomes/ROI documented where available
- ✓ No outdated references (>2 years old) unless exceptional

## Prioritization Logic

When presenting references, prioritize:

1. **Perfect match** - Same industry + size + use case
2. **Industry leader** - Well-known company in target industry
3. **Recent win** - Closed in last 6 months
4. **Call reference** - Customer willing to speak
5. **Competitive displacement** - Won against known competitor
6. **Strong outcomes** - Documented ROI and metrics
7. **Similar journey** - Same buying triggers and challenges