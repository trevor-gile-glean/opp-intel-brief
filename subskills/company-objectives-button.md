# Company Objectives Button Subskill

## Purpose
Add a "+ Company Objectives" action button to the interactive opportunity intelligence brief. When clicked, the button asks Assistant to research and append a "Company Objectives" tab to the brief that covers the prospect's business model, primary objectives, challenges, and strategic pressures for the current year.

## When to use
Include this button in the generated HTML artifact whenever the brief could benefit from a deeper view of the prospect's business priorities. It is an on-demand, additive action, so the base brief is generated first and the button lets the AE expand it later.

## Mechanics
Follow `components/action-buttons.md` for the mechanics of adding an action button to the interactive HTML page. This is a Glean Assistant action, so use the `button` tag with an `onclick` handler that calls `sendPrompt`, exactly as described in section 1 of that component. Do not open a separate tab or use an Agent link unless a known published agent ID is available.

Button metadata:
- label: `+ Company Objectives`
- type: `assistant`
- actionId: `company-objectives`
- displayLabel: `Add Company Objectives tab`
- context: the full prompt below

Keep the visible label short (`+ Company Objectives`) and put the full instruction in the `context` argument passed to `sendPrompt`.

## Prompt the button runs
Pass the following as the `context` argument to `sendPrompt`:

```text
Add a "Company Objectives" tab to the opportunity intelligence brief. The tab must include:
- Section 1: The prospect's likely business model and how it's positioned within its industry.
- Section 2: The prospect's likely primary business objectives for this year
- Section 3: The prospect's likely biggest challenges or risks this year
- Section 4: Any major strategic initiatives, leadership priorities, or market pressures shaping those objectives

Use the following guidelines:
- Use company search first and then external search. Systematically reprocess gong calls with this new task in mind. Use external research to fill in missing pieces.
- Focus on the current year
- Prioritize recent, credible sources such as earnings calls, annual reports, investor presentations, leadership interviews, press releases, company blogs, and reputable news coverage
- If the company is private and hard information is limited, infer likely objectives and challenges from recent announcements, hiring patterns, product launches, funding news, partnerships, and industry context
- Separate confirmed facts from reasonable inference
- Do not guess when there is no support
- Keep the output practical and easy to skim
- Include inline citations and explanations for how the intelligence was estimated, including the confidence level of the estimates.

For any sources referenced, add them to the Data Sources tab.
```

## Output
A single "+ Company Objectives" Assistant button rendered in the brief that, when clicked, prefills the chat tied to the canvas with the prompt above and produces a new "Company Objectives" tab plus updated Data Sources entries.
