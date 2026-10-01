# Lab 1: Your first n8n workflow

A workflow that takes an amount, adds 18% and returns the total through a live webhook.

## What I built
1. **Webhook (POST):** receives data at `/webhook/lab1-final`.
2. **Edit Fields (Set):** computes `total = amount × 1.18`, rounded to 2 decimals.
3. **Respond to Webhook:** returns `{"total": ...}` as JSON.

Earlier in the lab I also practised an **HTTP Request** node (Frankfurter exchange-rate API)
and an **If** node (route to TRUE when the rate is above 50). Those were removed
before the final webhook version.

## Key expression
```
{{ Math.round($json.body.amount * 1.18 * 100) / 100 }}
```
Webhook data arrives under `body`, so the field is `$json.body.amount`.

## Try it
```bash
curl -X POST https://<your-instance>/webhook/lab1-final \
  -H "Content-Type: application/json" \
  -d '{"customer":"Ada","amount":42,"country":"IN"}'
```
Expected response:
```json
{ "total": 49.56 }
```

## What I learned
- Test URLs and production URLs are different, and only the production URL works after publishing.
- Webhook payloads arrive under `$json.body`.
- Expressions only preview correctly when the input data matches.

## Files
- `workflow/lab1-total-calculator.json`: importable workflow
- `screenshots/`: canvas and verification screenshots