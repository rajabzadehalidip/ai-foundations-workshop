# Session 2 n8n live demo: policy-signal triage

## Purpose

Show that the same text-classification task from the Python/Colab exercise can be built visually in n8n with very little code.

The workflow reads a Persian news post, asks an LLM to return a structured classification, and writes the result to a research log. Start with a manual trigger so the class can observe every step.

## Recommended node sequence

1. **Manual Trigger** — starts a test run.
2. **Google Sheets: Get row(s)** — read a small sheet containing student_id, month, and text_fa. Use 5–10 rows for the live demo.
3. **Loop Over Items** — process one post at a time so each result remains traceable.
4. **AI Agent** or **Basic LLM Chain** — connect an approved chat model.
5. **Structured Output Parser** — require fields label, confidence, rationale, evidence, and needs_review.
6. **IF** — send needs_review = true to a Review sheet tab.
7. **Google Sheets: Append or Update Row** — store the structured result.

Optional after the demonstration: replace Manual Trigger with a Schedule Trigger, RSS Feed Trigger, or Webhook.

## Prompt

Use this as the system message or the main instruction in the LLM node:

    You classify Persian news posts for a digital-market research team.
    Use only the text of the post. Do not add outside facts.
    Choose one label from REG, AI, COMP, TELCO.
    Set needs_review to true when evidence is weak or two labels genuinely fit.
    Keep rationale to one sentence. Evidence must be a short excerpt from the post.
    Return only the requested JSON object.

Add the current item’s text field to the user message:

    Classify this post:
    {{$json.text_fa}}

## JSON schema

Put this schema in the Structured Output Parser:

    {
      "type": "object",
      "properties": {
        "label": {"type": "string", "enum": ["REG", "AI", "COMP", "TELCO"]},
        "confidence": {"type": "number", "minimum": 0, "maximum": 1},
        "rationale": {"type": "string"},
        "evidence": {"type": "string"},
        "needs_review": {"type": "boolean"}
      },
      "required": ["label", "confidence", "rationale", "evidence", "needs_review"],
      "additionalProperties": false
    }

## Demonstration moves

1. Run one clear AI or TELCO item and show the output fields.
2. Run an ambiguous item and show it travelling through the review route.
3. Open Google Sheets and show that the source text, model output, and timestamp are all visible.
4. Edit one category definition or the prompt, run again, and show why prompt versions must be logged.

## Teaching point

This is a workflow with an LLM step. It is not automatically an agent.

To demonstrate an agent, replace the simple LLM node with an AI Agent and give it only specific tools, such as reading an approved sheet and adding a reviewed row. Do not give the demonstration agent permission to publish, delete, email, or browse freely.

## Before class

- Prepare a Google Sheet with a small copy of the first 10 dataset rows.
- Configure model credentials in n8n ahead of time.
- Test the output parser and the IF condition.
- Make a Review tab in the Sheet.
- Keep the full dataset in Colab; n8n is for showing the visual no-code workflow.
