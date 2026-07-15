# Industry Intelligence Subskill

## Purpose
Research industry-specific trends, pain points, buying patterns, and intelligence to inform opportunity strategy and messaging.

## Inputs
- Industry vertical
- Sub-industry or segment
- Company size bracket
- Geographic region

## Research Strategy

### 1. Identify Industry Context

Determine:
- **Primary industry** - Main vertical (e.g., Financial Services)
- **Sub-industry** - Specific segment (e.g., Investment Banking)
- **Industry maturity** - Emerging, growth, mature, declining
- **Regulatory environment** - Key compliance requirements
- **Market dynamics** - Competitive landscape, consolidation

### 2. Research Industry Trends

Search for:
- **Industry reports** and analyst coverage
- **Industry-specific Glean content** (decks, briefs, webinars)
- **News and announcements** from industry leaders
- **Technology adoption patterns** in the industry
- **Pain points** commonly cited
- **Buying committee structure** typical in industry
- **Budget cycles** and procurement patterns

Sources:
- Industry solution decks and presentations
- Customer case studies from same industry
- Industry analyst reports (Gartner, Forrester)
- Industry news and trade publications
- Conference presentations and keynotes
- #industry-[name] Slack channels if they exist

### 3. Extract Industry Pain Points

Common pain point categories:
- **Regulatory/Compliance** - Industry-specific requirements
- **Speed/Efficiency** - Time-to-market pressures
- **Risk Management** - Security, data governance
- **Customer Experience** - Service quality, personalization
- **Operational Efficiency** - Cost reduction, automation
- **Innovation** - Digital transformation, competitive advantage
- **Talent** - Hiring, retention, skills gaps

### 4. Identify Industry-Specific Use Cases

Map how this industry uses Glean:
- Primary use cases deployed
- Common deployment patterns
- Integration priorities
- Adoption best practices
- Success metrics tracked

### 5. Find Industry Proof Points

Gather:
- **Customer logos** from this industry
- **Case studies** with industry peers
- **Testimonials** from industry leaders
- **Industry awards** or recognition
- **Analyst validation** for industry
- **ROI metrics** specific to industry

### 6. Research Buying Patterns

Understand:
- **Typical deal size** for this industry
- **Sales cycle length** average
- **Key decision makers** and influencers
- **Evaluation criteria** most important
- **Budget timing** and approval processes
- **Vendor consolidation** trends

## Output Format

Return structured industry intelligence:

```json
{
  "industry": "Financial Services",
  "sub_industry": "Investment Banking",
  "industry_overview": {
    "market_size": "Description of market...",
    "key_trends": [
      "Digital transformation acceleration",
      "Regulatory compliance complexity increasing",
      "Remote work adoption"
    ],
    "challenges": [
      "Data scattered across legacy systems",
      "Compliance and audit requirements",
      "Knowledge retention with turnover"
    ]
  },
  "glean_in_industry": {
    "customer_count": 15,
    "sample_customers": ["Bank A", "Bank B", "Investment Firm C"],
    "primary_use_cases": [
      "Compliance and audit trail",
      "Deal research and analysis",
      "Client intelligence"
    ],
    "typical_deployment": "Glean Hosted with SSO",
    "common_integrations": ["Bloomberg", "FactSet", "Salesforce", "Microsoft 365"]
  },
  "pain_points": [
    {
      "pain_point": "Information spread across 20+ systems including Bloomberg, FactSet, internal databases",
      "impact": "Analysts waste 40% of time searching for information",
      "glean_solution": "Universal search and AI answers across all systems",
      "proof": "Goldman Sachs reduced search time by 65%"
    }
  ],
  "buying_patterns": {
    "typical_deal_size": "$250K-$500K ARR",
    "avg_sales_cycle": "6-9 months",
    "key_decision_makers": ["CTO", "Head of Technology", "CDO"],
    "evaluation_criteria": [
      "Security and compliance",
      "Integration with financial data sources",
      "ROI and productivity metrics"
    ],
    "procurement_process": "Formal RFP common, legal review required"
  },
  "regulatory_considerations": [
    "SOC 2 Type II required",
    "FINRA compliance for communications",
    "Data residency requirements"
  ],
  "competitive_landscape": {
    "common_competitors": ["Microsoft", "Google", "Coveo"],
    "industry_specific_competitors": ["AlphaSense", "Bloomberg Search"],
    "why_they_switch": "Need AI-powered search across proprietary + external data"
  },
  "messaging_hooks": [
    "Find critical deal intelligence in seconds, not hours",
    "Compliance-ready search with complete audit trails",
    "Onboard new analysts 3x faster with institutional knowledge"
  ],
  "proof_points": [
    {
      "customer": "Major Investment Bank",
      "outcome": "65% reduction in research time",
      "quote": "Glean has become essential for our analysts"
    }
  ],
  "suggested_assets": [
    {
      "type": "Industry Deck",
      "title": "Glean for Financial Services",
      "url": "https://..."
    }
  ]
}
```

## Search Queries

Use these searches for industry research:

1. **Industry Content**: `[industry] solution deck presentation customer`
2. **Pain Points**: `[industry] challenges pain points problems`
3. **Customers**: `[industry] customer case study success story`
4. **Trends**: `[industry] trends outlook forecast updated:past_6_months`
5. **Compliance**: `[industry] compliance regulatory requirements`
6. **Competition**: `[industry] competitive landscape alternatives`
7. **ROI**: `[industry] ROI metrics outcomes benefits`

## Quality Checks

- ✓ Industry overview is accurate and current
- ✓ Pain points are specific to this industry (not generic)
- ✓ At least 3-5 customer examples from industry
- ✓ Buying patterns reflect recent data
- ✓ Regulatory considerations are complete
- ✓ Messaging hooks are differentiated
- ✓ Proof points include metrics
- ✓ Assets are industry-specific (not generic sales content)

## Industry Vertical Coverage

Prioritize research for these key industries:
- Financial Services (Banking, Investment, Insurance)
- Technology & Software
- Healthcare & Life Sciences
- Manufacturing & Industrial
- Retail & Consumer Goods
- Professional Services
- Media & Entertainment
- Education
- Government & Public Sector
- Energy & Utilities

## Competitive Context by Industry

Different industries have different competitive dynamics:
- **Tech companies** - Often evaluate GitHub Copilot, Google Cloud AI
- **Financial services** - Consider Bloomberg Search, AlphaSense
- **Healthcare** - Evaluate Epic integration, compliance-focused tools
- **Manufacturing** - Consider PLM system integration
- **Retail** - Focus on customer data platforms

## Integration with Other Subskills

- **Competitive Research** - Add industry-specific competitive context
- **Reference Matching** - Prioritize same-industry references
- **Solution Mapping** - Tailor solutions to industry needs
- **Opportunity Context** - Validate industry assumptions