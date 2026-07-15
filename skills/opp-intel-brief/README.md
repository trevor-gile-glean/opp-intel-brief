# Opportunity Intelligence Brief Skill - Development Notes

## Overview

This skill provides comprehensive intelligence briefs for Salesforce opportunities, helping AEs move deals forward with competitive insights, differentiation messaging, use case mapping, and industry intelligence.

## Architecture

### Core Components

1. **SKILL.md** - Primary skill definition and documentation
2. **templates/opportunity-brief.html** - Branded HTML output template
3. **subskills/** - Modular research components
   - `competitive-research.md` - Competitive intelligence gathering
   - `reference-matching.md` - Customer reference identification
   - `solution-mapping.md` - Use case to solution mapping
   - `industry-intelligence.md` - Industry trends and insights

### Subskill Pattern

Each subskill is a self-contained research module with:
- Clear purpose and inputs
- Defined research strategy
- Structured output format
- Quality checks
- Search query patterns

The main skill orchestrates these subskills to build a comprehensive brief.

## Implementation Strategy

### Phase 1: Core Orchestration
1. Parse opportunity ID from user input
2. Fetch opportunity data from Salesforce (via Glean search)
3. Invoke each subskill in parallel for efficiency
4. Synthesize results into unified data structure

### Phase 2: Data Gathering
Each subskill executes independently:
- **Competitive Research** - Searches battlecards, win/loss, Gong transcripts
- **Reference Matching** - Scores and ranks customer references
- **Solution Mapping** - Maps needs to Glean capabilities
- **Industry Intelligence** - Researches industry trends and proof points

### Phase 3: Synthesis & Output
1. Combine all subskill outputs
2. Generate executive summary with top insights
3. Create actionable recommendations based on stage
4. Render HTML using template with Glean branding
5. Return as HTML artifact in Glean

## Glean Capabilities Leveraged

### Data Access
- **Salesforce Connector** - Opportunity, account, contact data
- **Enterprise Search** - Cross-app content discovery
- **Knowledge Graph** - Entity relationships and reasoning
- **Gong Integration** - Call transcript analysis

### AI & Processing
- **Agent Sandbox** - Complex analysis and data processing
- **Glean Chat** - Intelligent synthesis and summarization
- **Canvas** - HTML artifact creation and rendering

### Output
- **HTML Artifacts** - Rich, interactive, shareable briefs
- **Stable URLs** - Easy sharing with team
- **Permission-aware** - Respects data access controls

## Branding

### Colors
- Primary Blue: `#343CED`
- Bright Green: `#D8FD49`
- Oatmeal: `#F6F3EB`
- Black: `#000000`
- White: `#FFFFFF`

### Typography
- Primary: PolySans
- Fallback: DM Sans
- Monospace: SF Mono, Monaco, Consolas

### Visual Style
- Clean, spacious layouts
- Bold but controlled color use
- Strong contrast for accessibility
- Glean logo/wordmark in header

## Research Depth Levels

### Quick (~2 minutes)
- Essential opportunity context
- Top 2-3 competitors only
- Key differentiators
- 2-3 customer references
- Basic recommendations

### Standard (~5 minutes)
- Full opportunity context
- Comprehensive competitive analysis (all known competitors)
- Detailed differentiation messaging
- 5-7 customer references
- Complete use case mapping
- Industry overview
- Stage-specific recommendations

### Deep (~10-15 minutes)
- Exhaustive cross-source research
- Multi-competitor deep analysis with trap questions
- Persona-specific messaging variants
- 10+ scored and ranked references
- Detailed industry deep-dive with trends
- Custom ROI/business case elements
- Historical pattern analysis
- Risk mitigation strategies

## Data Flow

```
User Input (Opportunity ID)
    ↓
Parse & Validate
    ↓
Fetch Salesforce Data
    ↓
Parallel Subskill Execution
    ├── Competitive Research
    ├── Reference Matching
    ├── Solution Mapping
    └── Industry Intelligence
    ↓
Synthesize Results
    ↓
Generate Executive Summary
    ↓
Create Recommendations
    ↓
Render HTML Template
    ↓
Return HTML Artifact
```

## Quality Assurance

### Data Quality Checks
- ✓ Opportunity data is complete and current
- ✓ All known competitors researched
- ✓ References are relevant and current (<2 years)
- ✓ Industry intelligence is up-to-date (<6 months)
- ✓ Sources are cited and accessible

### Output Quality Checks
- ✓ Executive summary is concise and actionable
- ✓ Insights are specific to this opportunity
- ✓ Recommendations match current stage
- ✓ All sections are populated
- ✓ HTML renders correctly
- ✓ Branding is consistent

### Performance Checks
- ✓ Quick depth completes in <3 minutes
- ✓ Standard depth completes in <7 minutes
- ✓ Deep depth completes in <20 minutes
- ✓ Subskills run in parallel when possible

## Testing Scenarios

### Test Case 1: Early Stage Opportunity
- Opportunity in "Discovery" stage
- Multiple competitors identified
- Use cases not fully defined
- Expected: Focus on competitive positioning and use case discovery

### Test Case 2: Late Stage Opportunity
- Opportunity in "Negotiation" stage
- Clear requirements documented
- Single competitor in deal
- Expected: Focus on closing strategies and proof points

### Test Case 3: Competitive Displacement
- Replacing incumbent solution
- Technical requirements defined
- Security/compliance concerns
- Expected: Strong competitive analysis and reference matching

### Test Case 4: New Industry
- First deal in this industry vertical
- Unknown competitive landscape
- Need industry validation
- Expected: Deep industry research and similar-industry references

## Future Enhancements

### v1.1 - Enhanced Intelligence
- [ ] Integration with LinkedIn for contact insights
- [ ] Gong conversation analysis for account sentiment
- [ ] Historical deal pattern matching
- [ ] Win probability scoring

### v1.2 - Collaboration Features
- [ ] Team collaboration on briefs
- [ ] Commenting and annotations
- [ ] Version history
- [ ] Export to PDF/PowerPoint

### v1.3 - Automation
- [ ] Scheduled brief updates
- [ ] Alert on competitive intelligence changes
- [ ] Automatic refresh on stage changes
- [ ] Integration with Salesforce workflows

## Related Skills

This skill complements:
- `/ae-weekly-brief` - Pipeline-level intelligence
- `/account-research` - Deeper account analysis
- `/competitive-analysis` - Standalone competitive research
- `/customer-reference-finder` - Reference discovery

## Development Guidelines

### Adding New Subskills
1. Create `subskills/[name].md` with standardized format
2. Define clear inputs, outputs, and research strategy
3. Include search query patterns
4. Add quality checks
5. Document integration points

### Modifying HTML Template
1. Maintain Glean brand guidelines
2. Test responsive behavior
3. Ensure accessibility (AA contrast)
4. Validate HTML structure
5. Test with various data shapes

### Performance Optimization
1. Run subskills in parallel when possible
2. Cache frequently accessed data
3. Limit search result counts appropriately
4. Use targeted queries vs. broad searches
5. Implement progressive enhancement

## Troubleshooting

### Common Issues

**Issue**: Salesforce data not found
- **Check**: Valid opportunity ID format
- **Check**: User has Salesforce permissions
- **Solution**: Verify ID and retry

**Issue**: No competitors found
- **Check**: Competitors field in Salesforce
- **Check**: Gong transcripts for mentions
- **Solution**: Broaden search queries

**Issue**: Few/no references found
- **Check**: Industry match criteria
- **Check**: Reference content in Glean
- **Solution**: Relax matching criteria

**Issue**: Slow performance
- **Check**: Search query complexity
- **Check**: Number of parallel requests
- **Solution**: Optimize queries, adjust depth

## Support & Feedback

- **Slack**: #sales-enablement
- **Email**: sales-ops@glean.com
- **Issues**: Log in GitHub or Glean feedback
- **Documentation**: https://docs.glean.com/skills/opp-intel-brief

---

**Last Updated**: 2026-06-02
**Version**: 1.0.0
**Author**: Glean Skills Team