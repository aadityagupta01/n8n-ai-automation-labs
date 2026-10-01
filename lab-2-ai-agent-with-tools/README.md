# Lab 2: Build an AI agent with tools

An AI agent in n8n that uses Google Gemini, can do exact maths with a
Calculator tool, remembers the conversation, and can look up live exchange
rates. It is exposed as a live webhook.

## Architecture
```
Webhook (POST /lab2-final) → AI Agent → Respond to Webhook
                               ├── Chat Model: Google Gemini
                               ├── Memory: Simple Memory
                               ├── Tool: Calculator
                               └── Tool: HTTP Request (Frankfurter API)
```

## What I built
1. Added a Google Gemini credential and the Gemini Chat Model.
2. Created the AI Agent with the prompt `{{ $json.body.prompt }}`.
3. Added a Calculator tool and a system message: "Always use the calculator tool for arithmetic."
4. Added Simple Memory so the agent remembers the conversation.
5. Added an HTTP Request tool: `https://api.frankfurter.dev/v1/latest?base=USD`.
6. Exposed the agent with Webhook and Respond to Webhook.

## Try it
```bash
curl -X POST https://<your-instance>/webhook/lab2-final \
  -H "Content-Type: application/json" \
  -d '{"prompt":"What is 17 multiplied by 23? Reply with only the number."}'
```
Expected response:
```json
{ "output": "391" }
```

You can also ask the agent: *What is the USD to INR rate?* It should call the HTTP Request tool.

## What I learned
- Agents decide when to call tools based on each tool's description.
- A system message steers the agent toward reliable behaviour.
- Memory lets the agent keep context across turns.
- Free API tiers can hit rate limits, so retries may be needed.

## Setup
Add your own Google Gemini credential in n8n. No API key is included in this repo.

## Files
- `workflow/lab2-ai-agent-with-tools.json`: importable workflow
- `screenshots/Workflow-screenshot.png`: