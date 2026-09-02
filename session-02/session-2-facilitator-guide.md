# Session 2 facilitator guide

## Learning objective

Students should leave able to turn a conversational LLM task into a controlled workflow: a clear prompt, a structured output, validation, and human review.

## Suggested three-hour flow

| Segment | Time | What students do |
|---|---:|---|
| Reconnect and framing | 10 min | Recall embeddings; contrast a vector similarity workflow with a generative-model workflow. |
| Prompt engineering | 45 min | Improve a vague research prompt with task, context, constraints, examples, and an output contract. |
| Limitations and controls | 25 min | Identify hallucination, ambiguity, staleness, injection, and non-determinism; define a control for each. |
| Break | 10 min | — |
| n8n live build | 50 min | Create the policy-signal triage workflow with Google Sheets and a structured output parser. |
| Agent discussion | 20 min | Compare predictable workflows with bounded agents; define tool permissions and stop conditions. |
| Generative model Colab | 45 min | Run GapGPT or Ollama on the same 25-post sample; inspect result rows. |
| Closing comparison | 15 min | Discuss model disagreement and where human review belongs. |

## Materials

- ai-foundations-workshop-session-2.html
- session-2-n8n-live-demo-guide.md
- generative-text-classification-session-2-colab.ipynb
- telegram_policy_radar_4topics_fa.csv

## n8n recommendation

Use Google Sheets only for the live demonstration because it makes every input and output visible. Start with five posts and a Manual Trigger. Keep an Input tab and a Review tab.

The core flow is:

    Manual Trigger → Google Sheets → Loop Over Items → LLM or AI Agent
    → Structured Output Parser → IF (needs_review) → Google Sheets

Use the exact same prompt and four labels in n8n and Colab. This helps students see that the research design is portable across interfaces.

## Colab recommendation

Default to GapGPT for a quicker class run. Have students run only 25 posts. Use the Windows Ollama guide for the local Gemma 3:4b practice. Treat the Ollama-in-Colab route as an optional demonstration: downloading and running Gemma 3 can be slow on a free Colab runtime.

For a genuine local-model demonstration, use the Ollama installation on your own Windows machine rather than Colab.

## What not to claim

- Do not call the labels accurate without a validated gold standard.
- Do not treat model confidence as calibrated probability.
- Do not treat a valid JSON response as a correct research conclusion.
- Do not give a demo agent unrestricted browser, email, publishing, or deletion permissions.

## Closing question

Ask each group: “Which part of this system should be automated, which part should be assisted, and which part must remain a human decision?”
