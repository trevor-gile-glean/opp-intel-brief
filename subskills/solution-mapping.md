# Solution Mapping Subskill

## Purpose

Map identified customer needs and use cases to specific Glean solutions, features, and value propositions.

## Inputs

- Account name and industry
- Identified needs from Salesforce/discovery
- Buyer persona and department
- Known pain points
- Current tools/stack

## Research Strategy

### 1. Extract Use Cases from Opportunity

Sources to check:

- Salesforce opportunity notes and requirements
- Gong call transcripts for this account
- Discovery emails and documents
- Slack conversations about the account
- RFP/RFI documents if available

Common use case patterns:

- **Knowledge Management** - Finding information, reducing search time
- **Onboarding** - New hire ramp, tribal knowledge
- **Productivity** - Reducing context switching, app consolidation  
- **Customer Support** - Agent productivity, case resolution
- **Sales Enablement** - Competitive intel, account research
- **Engineering** - Code search, technical documentation
- **Compliance** - Audit trails, data governance
- **Analytics** - Business intelligence, data analysis

### 2. Research Glean Solutions

Search for solution content:

- **Solution briefs** and one-pagers
- **Industry decks** specific to their vertical
- **Departmental outcomes** presentations
- **Product positioning** docs
- **Use case** documentation
- **ROI calculators** and business case templates
- **Demo flows** and screenshots

Tips that you should definitely use:

- Find departmental and industry solutions within the go/solutions space
- Find enablement material to understand best practices associated with mapping use cases to Glean plays: people, process, platform.

### 3. Map Needs to Glean Capabilities

Create mappings showing:

- **Customer need** - What they're trying to solve
- **Glean solution** - Specific product capabilities
- **Features** - Relevant Glean features
- **Differentiation** - Why Glean vs. alternatives
- **Outcomes** - Expected business results
- **Proof** - Customer examples with similar needs

### 4. Build Implementation Narrative

For each major use case:

- **Current state** - How they do it today
- **Pain points** - What's not working
- **Glean approach** - How Glean solves it
- **Implementation** - How it gets deployed
- **Adoption** - How users start using it
- **Success metrics** - How to measure value

### 5. Create Business Case Elements

Gather supporting materials:

- **ROI metrics** from similar customers
- **Time savings** calculations
- **Cost avoidance** from tool consolidation
- **Productivity gains** measured
- **Risk mitigation** value (compliance, security)

## Output Format

Return structured solution mapping:

```json
{
  "use_cases": [
    {
      "use_case_name": "Knowledge Management",
      "priority": "high",
      "buyer_pain_points": [
        "Employees waste 2+ hours/day searching for information",
        "Knowledge scattered across 15+ tools",
        "New hires take 3-6 months to ramp"
      ],
      "glean_solution": {
        "primary_capabilities": [
          "Universal search across all apps",
          "AI-powered answers from company knowledge",
          "Personalized results based on role and permissions"
        ],
        "key_features": [
          "Semantic search",
          "Knowledge graph",
          "Assistant with enterprise grounding",
          "150+ app connectors"
        ],
        "differentiation": [
          "Only solution with true universal search",
          "AI answers grounded in permissions-aware context",
          "Personal graph for role-based results"
        ]
      },
      "expected_outcomes": {
        "quantitative": [
          "50% reduction in time spent searching",
          "3x faster new hire ramp time",
          "40% increase in knowledge reuse"
        ],
        "qualitative": [
          "Improved employee satisfaction",
          "Better cross-team collaboration",
          "Reduced tribal knowledge risk"
        ]
      },
      "proof_points": [
        {
          "customer": "Similar Company",
          "industry": "Their Industry",
          "metric": "65% reduction in search time",
          "quote": "Glean has become our single source of truth"
        }
      ],
      "implementation_approach": {
        "phase_1": "Deploy search across core apps (Slack, Drive, Confluence)",
        "phase_2": "Enable AI Assistant and agents",
        "phase_3": "Expand to additional data sources"
      },
      "supporting_assets": [
        {
          "type": "Solution Brief",
          "title": "Glean for Knowledge Management",
          "url": "https://..."
        },
        {
          "type": "Customer Story",
          "title": "How Acme Corp Transformed Knowledge Sharing",
          "url": "https://..."
        }
      ]
    }
  ],
  "recommended_demo_flow": [
    "Show universal search across their key apps",
    "Demonstrate AI answers with source citations",
    "Highlight role-based personalization"
  ],
  "technical_requirements": {
    "integrations_needed": ["Google Workspace", "Slack", "Salesforce"],
    "deployment_model": "Glean Hosted",
    "security_considerations": ["SSO with Okta", "SOC 2 compliance"]
  }
}
```

## Search Queries

Use these searches to build solution mappings:

1. **Solution Content**: `[use case] solution brief value proposition`
2. **Industry Specific**: `[industry] use case deck presentation`
3. **Departmental**: `[department] outcomes benefits ROI`
4. **Competitive**: `[use case] vs [competitor] differentiation`
5. **Proof Points**: `[use case] customer success metrics`
6. **Technical**: `[integration] setup requirements documentation`

## Quality Checks

- ✓ All identified use cases mapped to Glean solutions
- ✓ Each solution has clear differentiation vs. alternatives
- ✓ Business outcomes are specific and measurable
- ✓ At least 1-2 proof points per major use case
- ✓ Implementation approach is realistic and phased
- ✓ Supporting assets are current and relevant
- ✓ Technical requirements are documented
- ✓ Demo flow addresses buyer pain points

## Value Messaging Framework

For each solution, articulate:

1. **Problem** - Current pain in customer's words
2. **Impact** - Business cost of the problem
3. **Solution** - How Glean solves it specifically
4. **Proof** - Evidence it works (customer examples)
5. **Differentiation** - Why Glean vs. alternatives
6. **Next Steps** - Path to value realization

## Integration with Other Subskills

- **Competitive Research** - Use to strengthen differentiation
- **Reference Matching** - Pull proof points from references
- **Industry Intelligence** - Contextualize with industry trends

&nbsp;