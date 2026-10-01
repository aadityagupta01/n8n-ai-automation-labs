# n8n AI Automation Labs

Hands-on labs from my n8n learning journey. Each lab includes the exported
workflow, screenshots and notes on what I built and learned.

## Labs

| Lab | What it covers | Folder |
|-----|----------------|--------|
| Lab 1 | First workflow: Edit Fields, expressions, live webhook | [lab-1-first-workflow](./lab-1-first-workflow) |
| Lab 2 | AI agent with Gemini, Calculator, Memory, HTTP tool, live webhook | [lab-2-ai-agent-with-tools](./lab-2-ai-agent-with-tools) |

## How to use the workflows
1. In n8n, create a new workflow.
2. Click **⋯ → Import → From file** and choose a `.json` file from a lab's `workflow/` folder.
3. Re-create any credentials (for example Google Gemini) with your own API key.
4. Publish the workflow to activate its webhook.

## Tools
n8n Cloud, Google Gemini, Frankfurter exchange-rate API.

## Security note
No API keys are stored in this repo. Credentials must be added in your own n8n instance.