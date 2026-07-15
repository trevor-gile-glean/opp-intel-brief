# Action buttons

Use this component when the output artifact should include clickable buttons that launch either Glean Assistant or a specific Glean Agent.

Keep the pattern simple:

- For Glean Assistant actions, use a `button` tag with an `onclick` handler that calls `sendPrompt`. This runs the action inside the chat associated with the canvas instead of opening a separate tab.
- For Glean Agent actions, use a normal anchor tag styled as a button (this pattern does not change).
- Build any destination URL (for Agent buttons) on the server side when possible.
- URL-encode the full prompt before inserting it into an Agent link.
- Make the visible button label short. Put the detailed instruction in the prompt, not in the label.

## 1. Run Glean Assistant

Use Glean Assistant when the button should run an action inside the chat associated with the canvas and prefill a message.

Instead of a normal anchor tag, use a `button` tag with an `onclick` handler that calls `sendPrompt`. This sends the message to the chat tied to the canvas rather than opening a separate tab.

`sendPrompt` function:

```js
function sendPrompt(actionId, displayLabel, context) {
  if (!window.GleanBridge || !window.GleanBridge.postMessage) return;
  window.GleanBridge.postMessage({
    actionId: actionId,
    type: 'glean-send-message',
    metadata: { displayLabel: displayLabel, context: context }
  });
}
```

HTML pattern:

```html
<button class="action-btn" onclick="sendPrompt('action-id', 'Short display label', 'Full prompt context that tells Assistant exactly what to do, including account, opportunity, stage, competitors, and the issue tied to this button.')">
  Investigate sources
</button>
```

Example usage:

```html
<button class="action-btn" onclick="sendPrompt('lenovo-decision-path', 'Help me decide the best wedge', 'Review the Lenovo CTO Led AI Transformation opportunity and recommend the best wedge to win next: CTO platform layer, Sales and Marketing proving ground, TPM horizontal workflow, or Finance. Explain why and update the artifact after answering.')">Decide</button>
```

`sendPrompt` arguments:

- `actionId`: a stable identifier for the action this button triggers.
- `displayLabel`: short text shown in chat for what the user asked.
- `context`: the full instruction to send to Assistant. Treat this like the prompt below.

Use this for actions such as:

- further analysis
- help me decide
- give me the next step
- investigate sources
- generate a one-pager from selected evidence

Prompt guidance:

- Write the prompt as if the user has already asked the question in chat.
- Include the account name, opportunity name, stage, competitors, and the exact issue the button is tied to.
- Tell Assistant what output to produce.
- Ask for an artifact when the output should be reusable or shareable.
- If the button comes from a specific section of the artifact, pass the section context directly in the prompt.

Example prompt:

```text
Analyze the competitive risk for the Acme opportunity. Focus on Microsoft Copilot and Glean differentiation. Use the evidence already surfaced in this opportunity brief. Produce a concise HTML artifact with risks, proof points, objection handling, and the next best action for the AE.
```

## 2. Run a Glean Agent

Use a Glean Agent when the action should open a specific agent instead of general Assistant chat.

URL pattern:

```text
https://app.glean.com/chat/agents/{AGENT_ID}?message={URL_ENCODED_PROMPT}
```

HTML pattern:

```html
<a class="action-button" href="https://app.glean.com/chat/agents/${agentId}?message=${encodedPrompt}" target="_blank" rel="noopener noreferrer">
  Run Rocky
</a>
```

Use this when:

- the team already has a purpose-built agent
- the workflow should stay inside a governed agent experience
- the button should route into a known agent with strong instructions and tools

Requirements:

- Use a real published agent ID.
- Only render the button if the agent ID is known.
- Keep the message narrowly scoped to the job that agent should do.
- Do not assume the agent shares the same context as the artifact unless you put that context into the message.

Example prompt:

```text
Use this opportunity brief to prepare a deal review for Acme. Focus on blockers, MEDDPICCS gaps, competitive pressure, and the next two actions the AE should take this week.
```

## 3. Helper pattern

Use a small helper when building buttons in the HTML artifact.

For Glean Assistant buttons, include the `sendPrompt` function in the artifact and call it from each button's `onclick`:

```js
function sendPrompt(actionId, displayLabel, context) {
  if (!window.GleanBridge || !window.GleanBridge.postMessage) return;
  window.GleanBridge.postMessage({
    actionId: actionId,
    type: 'glean-send-message',
    metadata: { displayLabel: displayLabel, context: context }
  });
}
```

For Glean Agent buttons, build the URL as before:

```js
function buildAgentUrl(agentId, prompt) {
  return `/chat/agents/${agentId}?message=${encodeURIComponent(prompt)}`;
}
```

## 4. Suggested button metadata

Each button should have:

- label: short text shown to the user
- icon: optional icon name already supported by the artifact
- type: `assistant` or `agent`
- For `assistant`: an `actionId`, a `displayLabel`, and the `context` (full instruction) passed to `sendPrompt`
- For `agent`: an `agentId` and the `prompt` to prefill

Example shape:

```js
{
  label: 'Help me decide',
  icon: 'compass',
  type: 'assistant',
  actionId: 'help-me-decide',
  displayLabel: 'Help me decide',
  context: 'Review the opportunity strategy for Acme and recommend the best next step based on the evidence in this brief.'
}
```

```js
{
  label: 'Run Rocky',
  icon: 'agent',
  type: 'agent',
  agentId: 'YOUR_AGENT_ID',
  prompt: 'Prepare a focused opp review for Acme using the context from this brief.'
}
```

## 5. UX guidance

- Prefer one strong button per decision point instead of a cluster of vague buttons.
- Make the label action-oriented.
- Keep icon choice semantically consistent across the artifact.
- If the button depends on selected rows or filters, assemble the prompt from the current state before building the URL.
- If no agent ID is available, fall back to an Assistant button.

## 6. Recommendation for this skill

For `opp-intel-brief`:

- Use Assistant buttons for burning issues, source investigation, next-step generation, and one-pager creation.
- Use Agent buttons only when there is a known GTM or deal-strategy agent with a stable published ID.
- Prefer prompts that name the opportunity, account, stage, competitor, and the exact artifact section that produced the button.

&nbsp;