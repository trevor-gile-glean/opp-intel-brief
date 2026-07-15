---
name: opp-intel-brief
description: Exhaustive opportunity intelligence brief for Salesforce opportunities with competitive insights, differentiation messaging, stakeholder context, MEDDPICCS gap analysis, customer references, use-case solution mapping, industry intelligence, and actionable deal advancement strategies. Use when a user asks to research an opportunity, prepare for a deal review or customer call, analyze competition, find references, assess deal risk, or recommend next steps for a sales opportunity.
---
# Opportunity Intelligence Brief

**Exhaustive research and intelligence brief for sales opportunities.**

## Overview

The Opportunity Intelligence Brief skill provides Account Executives with a comprehensive, AI-generated intelligence brief for any Salesforce opportunity. It synthesizes actionable insights across competitive intelligence, differentiation messaging, use case-to-solution mapping, industry references, and more, to help move deals forward. 

## What It Does

For a given Salesforce opportunity, this skill:

1. **Gathers comprehensive opportunity context** from Salesforce (account details, contacts, stage, competitors, requirements)
2. **Researches competitive intelligence** across battlecards, win/loss analysis, Gong transcripts, and competitive docs.  Uses `subskills/competitive-research.md` to support competitive intelligence research.
3. **Identifies differentiation messaging** based on the competitive landscape and buyer persona
4. **Maps use cases to solutions** using internal solution briefs, industry decks, and product positioning.  Uses `subskills/solution-mapping.md` to support solution mapping research.
5. **Finds relevant customer references** (similar industry, company size, use cases) and success stories.  Uses `subskills/reference-matching.md` to support customer reference research.
6. **Surfaces industry intelligence** including trends, pain points, and common objections. Uses `subskills/industry-intelligence.md` to support industry intelligence research.
7. **Provides actionable recommendations** for advancing the deal based on current stage and context
8. **Generates a branded HTML artifact** with all insights organized for easy consumption

## Usage

Use this skill when the user wants a deal-specific intelligence brief for a real Salesforce opportunity. Typical triggers include requests to research an opportunity, prepare for a deal review or customer call, understand the competitive landscape, find strong customer references, map pains to Glean use cases, identify risks or blockers, or recommend concrete next steps to move the deal forward.

This skill should also trigger when the user provides a Salesforce opportunity ID or opportunity URL and asks for any combination of competitive intelligence, account research, proof points, stakeholder context, MEDDPICCS gap analysis, or opportunity strategy.

## Customization

The prompt may customize the workflow or output in a few possible ways: 

- If the prompt signals speed or asks for a quick take, produce a lighter-weight brief that prioritizes the most decision-relevant findings.
- If the prompt asks for specific sections such as competition, references, technical validation, industry context, stakeholder strategy, or deal risks, then only research and output those sections.
- If the user includes specific questions, hypotheses, or known deal context, use them to shape what evidence to look for, what sources to prioritize, and how to frame the recommendations.

## Workflow

Follow this workflow in order. Treat each step's output as an input to later steps. Do not jump to synthesis before the grounding steps are complete.

### 1. Classify the request and set research depth

Start by deciding how broad the research should be.

1. Determine whether the request is Quick, Standard, or Deep.
2. Extract any user-specified emphasis areas such as competition, references, technical validation, industry context, stakeholder strategy, or deal risk.
3. Convert the prompt into a research plan that states:
    - the opportunity identifier
    - the target depth
    - the priority sections
    - the sources to emphasize

Output:

- Research plan
- Ordered list of priority questions to answer

### 2. Ground the opportunity in Salesforce

This step is required before all other research.

1. Retrieve the opportunity, account, owner, close date, stage, amount, forecast, competitors, linked contacts, recent activity, and any notes or fields that describe pains, requirements, or next steps.
2. Resolve the minimum set of core entities:
    - opportunity
    - account
    - seller team
    - known stakeholders
    - known competitors
3. Normalize the opportunity into a compact deal snapshot.

Output:

- Deal snapshot
- Initial list of stakeholders
- Initial list of competitors
- Initial list of known pains, requirements, and open questions

Dependency:

- All later steps depend on this snapshot.

### 3. Build the evidence map before deep research

Use the grounded opportunity to decide where evidence is likely to exist.

1. List the most relevant internal sources for this deal:
    - Salesforce activity
    - Gong calls
    - Slack threads
    - Google Drive docs
    - Confluence pages
    - competitive materials
2. Prioritize sources by expected signal:
    - direct deal evidence first
    - account history second
    - general market or enablement material third
3. Note what each source is expected to answer.

Output:

- Evidence map by source
- Search plan by question

Dependency:

- This determines where to search in Steps 4 through 9.

### 4. Reconstruct account and opportunity history

Establish how the deal got here before interpreting current risk.

1. Build a chronological view of the account relationship leading into the current opportunity.
2. Capture major transitions such as:
    - first engagement
    - evaluation start
    - stage changes
    - stakeholder changes
    - procurement or security involvement
    - shifts in competitive posture
3. Separate account-history facts from opportunity-specific facts.

Output:

- Account historical context
- Draft prospect interaction timeline
- Candidate turning points and narrative arcs

Dependency:

- Stakeholder analysis, risk analysis, and next-step recommendations should use this history.

### 5. Analyze stakeholders and buying process

Do this before writing recommendations or MEDDPICCS gaps.

1. Identify the economic buyer, champion, technical evaluator, blockers, and neutrals.
2. For each stakeholder, capture:
    - role
    - level of engagement
    - stated priorities
    - sentiment
    - evidence of influence
3. Infer the buying process and decision committee only from evidence.
4. Mark missing stakeholder coverage explicitly.
5. Infer org chart relationships from conversations and transcripts. Relationships to create the org chart must be inferred from interactions with the prospect or from notes that we have taken internally.

Output:

- Stakeholder map
- Decision-process hypothesis
- Stakeholder gaps
- Estimated org chart

Dependency:

- MEDDPICCS scoring and action planning depend on this step.

### 6. Assess risks and MEDDPICCS from evidence

Only score what the evidence supports.

1. Evaluate each MEDDPICCS element using direct evidence from the grounded deal and stakeholder analysis.
2. Mark each item green, yellow, or red.
3. For every yellow or red item, state:
    - what is missing
    - why it matters now
    - what evidence would change the score
4. Build a risk list that includes severity, source, and mitigation path.

Output:

- MEDDPICCS scorecard
- Risk register
- List of unresolved deal questions

Dependency:

- Next steps must map back to these gaps and risks.

### 7. Research the company's technology stack

Use the `customer-tech-stack-discovery` skill to research the company's technology stack.  Do not create a separate artifact for the technology stack.  The research will be used when the opportunity intelligence skill create's its artifact.  The goal is to have a full understanding of the technology stack as a reference for the AE when having conversations internally within Glean and externally with the customer.

### 8. Research competitors only after the deal context is clear

Competitive research must be deal-specific, not generic.

1. Start with competitors explicitly named in Salesforce, calls, emails, or Slack.
2. Use `subskills/competitive-research.md` to gather:
    - head-to-head positioning
    - likely objections
    - trap-setting questions
    - win or loss evidence
3. Tie each competitive insight back to:
    - this buyer's priorities
    - this stage of the deal
    - this deal's known risks
4. If no competitor is explicitly named, research only plausible alternatives supported by evidence.

Output:

- Competitor landscape
- Deal-specific differentiation angles
- Trap questions by competitor

Dependency:

- Proof points and messaging should reflect this step.

### 9. Map pains to solutions before selecting proof points

Do not start with generic product pitches.

1. Use the opportunity context, call evidence, and stakeholder priorities to identify the most important buyer pains.
2. Use `subskills/solution-mapping.md` to map each pain to:
    - relevant Glean capability
    - expected business outcome
    - likely persona resonance
3. Keep mappings concrete and buyer-relevant.
4. Exclude solution rows that are not supported by the deal context.

Output:

- Pain → Solution → Outcome mappings
- Ranked list of most relevant use cases

Dependency:

- Reference selection and proof-point selection depend on these ranked use cases.

### 10. Select proof points and customer references

Only select references that strengthen the specific story emerging from Steps 6 through 8.

1. Use `subskills/reference-matching.md` to find customer references that match on:
    - industry
    - company size
    - persona
    - use case
    - deployment context
    - competitive situation
2. Prefer references that support the top-ranked use cases and top deal risks.
3. For each reference, capture:
    - why it matches
    - what proof it provides
    - what claim it should support
4. Build business-case proof points from the strongest available evidence, not from generic claims.

Output:

- Ranked references
- Proof-point set
- Support matrix linking claims to evidence

Dependency:

- Executive summary and one-pager-worthy messaging depend on this set.

### 11. Add industry context only where it sharpens the story

Industry research should support the deal, not distract from it.

1. Use `subskills/industry-intelligence.md` to gather only the trends, pressures, and benchmarks that help explain:
    - why the buyer should act now
    - why the pains matter
    - why the proposed use cases are credible
2. Prefer industry context that strengthens the business case or helps rebut inertia.

Output:

- Industry trends and benchmarks relevant to this deal
- Why-this-matters-now material

Dependency:

- Executive summary and business-case framing depend on this step.

### 12. Synthesize findings into a deal thesis

Do this only after the research branches are complete.

1. Combine the outputs of Steps 4 through 11 into a single view of:
    - why the deal is where it is
    - what is helping
    - what is blocking
    - what message is most likely to move it forward
2. Write the core deal thesis in 3 to 5 sentences.
3. Identify the top 3 to 5 burning issues.
4. For each issue, specify:
    - evidence
    - implication
    - recommended action

Output:

- Deal thesis
- Burning issues
- Message strategy
- Advancement strategy

Dependency:

- The artifact should be assembled from this synthesis, not from raw notes.

### 13. Generate next steps from the gaps, not from generic sales motions

Recommendations must be evidence-linked.

1. Convert the risk register and MEDDPICCS gaps into concrete next steps.
2. Assign each next step:
    - owner
    - objective
    - target timing
    - evidence it is meant to create or validate
3. Prioritize actions that unlock the next stage of the deal.

Output:

- Ordered action plan
- Recommended stakeholder messaging
- Deal advancement playbook

### 14. What to say. What to share. What to do.

Review the opportunity intelligence collected and identify the most significant gaps in terms of the following criteria:

1. What does the prospect need to hear about to convince them to move the deal forward?
2. What does the prospect need to see to convince them to move the deal forward?
3. What is the most important action to take to move the deal forward?

Then: 

1. Research sales enablement material using Glean company search to identify the right things to say.
2. Find the top 7 existing sharable assets (e.g., blog posts, Glean website pages, Glean docs documentation, presentations, one-pagers, roadmaps, etc...) to address what the customer needs to see.

Output:

1. What to say.  The best thing to say and how to say it.
2. What to share.  The top 7 existing sharable assets.
3. What to do.  The best action to take.

### 15. Assemble the artifact last

Do not populate the HTML template until the research is complete enough to support each section.

1. Fill each tab with synthesized content, not raw excerpts.
2. Keep citations close to the claims they support.
3. If a section has weak evidence, say so directly instead of filling it with generic content.
4. If the template is missing a needed section, add a tab that matches the existing visual system.

Output:

- Final branded HTML brief (defined in the Output section below)

## Output

The skill generates a **branded HTML artifact** using the opportunity brief template (`templates/opportunity-brief-template.html`), organized into the following tabbed sections:

### 1. Executive Summary

- Deal snapshot cards (stage, amount, seats, deployment, close date, etc.)
- Visual stage progress bar
- Top 3-5 burning issues with evidence and quotes
    - For each burning issue, provide a small button.  When the user clicks on the button, then redirect them to a Glean Chat with a message pre-filled.  The message must be a detailed prompt that, when run, will provide the most help to the user to move the deal forward.  If "further analysis" is needed, then use a bullseye icon on the button.  If "help me decide" is needed, then use a compass icon.  If "give me the next step" is needed, then use an arrow-right icon.  If "investigate sources" is needed, then use a search-plus icon.
- "Why This Deal Matters Now" compelling reasons

### 2. Stakeholders

- Visual stakeholder map with role-based color coding (Economic Buyer, Champion, Technical Evaluator, Risk/Blocker, Neutral)
- Stakeholder cards with engagement status tags
- Decision process and committee structure
- Add an org chart section at the bottom. Build a compact org chart section.  Make the org chart visual, but only static.  Don't try and make collapsible nodes or anything like that.  The org chart should display name, title, and team.  Use the same color-coding as the stakeholder map to identify the role of each person within the opp.  There doesn't have to be only one person at the top, because we realize that this is an incomplete org chart.

### 3. Competitive Intelligence

- Competitor landscape tags
- Head-to-head comparison table across key dimensions
- Trap-setting questions organized by competitor
- Win data and benchmark statistics

### 4. Technology Stack

Use the output from the technology stack research skill to build a visually appealing representation with styles consistent with other sections in the opportunity intelligence briefing.

### 5. Proof Points (formerly Differentiation Messaging)

- Crown jewel proof point (e.g., internal customer success story)
- Usage metrics grid (adoption, ROI, time saved)
- Business case model with multi-pillar ROI
- Methodology and validation notes

### 6. Use Case & Solution Mapping

- Three-column use case rows: Pain → Glean Solution → Outcome
- Color-coded cells (red pain, blue solution, green outcome)
- Persona-specific context
- Benchmark data integration
- Multi-select checkbox (one box per row) so that a user can pick which use cases are most relevant. The default if is for each checkbox to be toggled on.  Do not create select all or clear all buttons.
- A button with the text "Generate one-pager".  When clicked, the button runs a Glean Chat (by running a /chat?message= constructed link) that generates a personalized one-pager from the selected use cases.  The link includes a message value that will generate asks Glean Chat to generate an HTML artifact based on the use case tab and the use cases that the user has selected.

### 7. Customer References & Social Proof

- Reference cards sorted by relevance (industry, vertical, use case match)
- Key metrics and statistics per reference
- Reference relationship strength indicators
- Action items for reference activation

### 8. Risks & MEDDPICCS

- Risk radar grid with severity color coding (high=red, medium=yellow, low=blue)
- Mitigation strategies per risk
- MEDDPICCS scorecard with traffic-light scoring (green/yellow/red dots)
- Show an overall MEDDPICCS score by adding up each item (green = 2 pts, yellow = 1 pts, red = 0 pts). e.g., 13 out of 18
- Gap analysis

### 9. Next Steps

- Numbered action items with owners and target dates
- Sequential step flow with priority indicators
- Recommended messaging for key stakeholders
- Deal advancement playbook
- A separate section that makes it explicit:
    - What to say
    - What to share
    - What to do

### 10. Prospect Interaction Timeline

- Weekly summary of prospect interactions
- Sequential flow in reverse chronological order
- Sentiment analysis over time.  Use green up arrow for improving sentiment.  Use flat yellow arrow for stable sentiment.  Use red down arrow for declining sentiment.
- Identifies key discovery items, decision points, and strategic directions.
- Provides inline citations to source data (e.g., gong, slack, email, gdrive, etc...)

### 11. Account Historical Context

- Full research of the account's historical context leading up to the opportunity
- Sentiment analysis over time
- Key transition points in the relationship to understand historical context.
- Key external feedback and decisions
- Key internal tactics and strategies

### 12. Data Sources

- Complete listing of data sources (e.g., Gong calls, Salesforce records, Gdrive docs, Slack threads, etc...) used to generate the brief.
- Organized by data source and then listed in reverse chronological order.

## Supporting Files

- Read `/components/action-buttons.md` for guidance about how to create working action-oriented buttons in the output.

## Template Structure

The skill uses `templates/opportunity-brief-template.html` which provides:

- Professional responsive design with theme support (light/dark)
- Make the header compact.  It should communicate the top-level points without using much page real-estate.
- Tabbed navigation for easy section access
- Reusable component styles (cards, grids, tables, tags)
- Print-optimized layout
- PDF export capability
- Glean brand styling with CSS variables
- If the skill asks for a tabbed section that is not defined in the template, then create a new tab with similar formatting.

## Data Sources

The skill searches across:

- **Salesforce** - Opportunity, account, contact, and activity data
- **Competitive Intelligence** - Battlecards, competitive analysis, win/loss data
- **Gong** - Call transcripts and competitive mentions
- **Slack** - #competitive, #sales, #customer-success channels
- **Google Drive** - Case studies, pitch decks, solution briefs, industry decks
- **Confluence** - Product docs, positioning, technical content
- **Knowledge Graph** - Relationship mapping between accounts, opportunities, and people

## Research Depth

Unless the user specifies otherwise, always complete deep and exhaustive research.

- Exhaustive research across all data sources
- Full opportunity context
- Comprehensive multi-competitor analysis with trap questions
- Detailed differentiation messaging with people, process, platform mapping
- Persona-specific messaging
- 10+ customer references with detailed matching
- Industry deep-dive with trends and benchmarks
- Use case and JTBD mapping
- Custom ROI/business case elements
- Historical win/loss patterns for similar deals

## Example Use Cases

### Pre-Call Preparation

Get a comprehensive brief before a customer call to understand competitive landscape, prepare messaging, and identify relevant references.

### Deal Review Prep

Generate an exhaustive analysis before a deal review to identify risks, surface winning strategies, and prepare advancement plans.

### Competitive Displacement

Focus specifically on competitive intelligence when displacing an incumbent solution.

### New Account Research

Research industry context and find compelling references when entering a new account.

## Tips for Best Results

1. **Ensure Salesforce data is current** - The skill pulls from Salesforce, so accurate data produces better insights
2. **Use competitor fields** - Add known competitors to the Salesforce opportunity
3. **Document requirements** - Add use cases and requirements to opportunity notes
4. **Run before key meetings** - Generate briefs 24-48 hours before important calls
5. **Share with team** - HTML artifacts have stable URLs for easy sharing
6. **Refresh as needed** - Re-run the skill as the deal progresses

## Working with the Template

The skill populates the HTML template by replacing template variables with researched content:

### Key Template Variables

**Header & Metadata:**

- `{{CUSTOMER_NAME}}`, `{{CUSTOMER_ICON}}` - Customer branding
- `{{OWNER_NAME}}`, `{{REPORT_DATE}}` - Report metadata
- `{{STAGE_SUMMARY}}` - Current deal stage and forecast category

**Stage Progress:**

- `{{STAGE_1_LABEL}}` through `{{STAGE_5_LABEL}}` - Custom stage names
- `{{STAGE_PROGRESS_HTML}}` - Stage indicator HTML (done/current/pending)

**Content Sections:**

- `{{SNAPSHOT_CARDS}}` - Deal metrics as grid cards
- `{{BURNING_ISSUES_HTML}}` - Top issues with quotes and evidence
- `{{WHY_NOW_BULLETS}}` - Compelling reasons bullets
- `{{STAKEHOLDER_CARDS}}` - Stakeholder map entries
- `{{COMPETITIVE_ROWS}}` - Competitor comparison table rows
- `{{TRAP_QUESTIONS_HTML}}` - Trap questions by competitor
- `{{PROOF_METRICS}}` - Proof point statistics grid
- `{{ROI_MODEL_HTML}}` - Business case pillars and calculations
- `{{USECASE_ROWS}}` - Use case pain/solution/outcome rows
- `{{REFERENCE_CARDS}}` - Customer reference cards
- `{{RISK_ITEMS}}` - Risk grid with severity and mitigation
- `{{MEDDPICCS_ITEMS}}` - MEDDPICCS scorecard grid
- `{{NEXT_STEPS_ITEMS}}` - Action list with owners and dates
- `{{RECOMMENDED_MESSAGING}}` - Executive pitch messaging

### Template Components

The template provides reusable styled components:

**Cards & Grids:**

- `.snapshot-card` - Metric cards with label/value/sub structure
- `.card` - General content cards with title and body
- `.stakeholder-card` - Role-based colored stakeholder entries
- `.ref-card` - Customer reference cards
- `.medd-item` - MEDDPICCS scorecard items

**Visual Elements:**

- `.stage-bar` with `.stage-step` - Progress visualization
- `.tag` with color variants - Status and category tags
- `.quote-block` - Pull quotes with attribution
- `.risk-item` with severity levels - Risk cards
- `.score-dot` - Traffic light indicators

**Tables:**

- `.compete-table` - Competitive comparison matrix
- `.usecase-row` - Three-column use case layout

**Action Items:**

- `.step-list` / `.step-item` - Numbered action steps

### Customization

To customize the template for different organizations:

1. Update CSS variables in `:root` for brand colors
2. Modify `--artifact-primary-brand` for accent color
3. Adjust stage labels for custom sales process
4. Add/remove tabs based on required sections

## Technical Details

### Glean Capabilities Used

- **Salesforce Connector** - Opportunity and account grounding
- **Knowledge Graph** - Entity and relationship reasoning
- **Enterprise Search** - Cross-source content retrieval
- **Agent Sandbox** - Complex data analysis and synthesis
- **Canvas & HTML Artifacts** - Branded output generation using templates

### Template Files

- **Template**: `templates/opportunity-brief-template.html` - Master template with variables
- **Example**: `templates/opportunity-brief-example.html` - Fully populated Sony/Bungie example
- Both use identical styling and component structure

&nbsp;