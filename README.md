# LinkedIn Account Checker API — official examples | CheckNumber

This repository documents the CheckNumber LinkedIn Account Checker API integration contract using facts from the expansion manifest.

- Product page: https://checknumber.ai/products/linkedin
- API base URL: `https://api.checknumber.ai`
- Authentication: `X-API-Key`
- API key environment variable: `CHECKNUMBER_API_KEY`
- License: MIT

## Processing model

This is a file-based asynchronous API. Submit an authorized text file, poll the task until `exported`, then download the result URL. It is not a realtime single-identifier endpoint.

```bash
curl -X POST "https://api.checknumber.ai/v1/tasks" -H "X-API-Key: ${CHECKNUMBER_API_KEY}" -F "file=@examples/numbers.txt" -F "task_type=linkedin_phone"
curl -X POST "https://api.checknumber.ai/v1/gettasks" -H "X-API-Key: ${CHECKNUMBER_API_KEY}" -F "task_id=YOUR_TASK_ID"
```

## Products and limits

| Code | Name | Input | Limits | Result fields | Documentation |
| --- | --- | --- | --- | --- | --- |
| `linkedin_phone` | Number Checker | phone | 1000–500000 rows | `number, activated` | [docs](https://docs.checknumber.ai/linkedin-number-checker) |
| `linkedin` | Email Checker | email | 1000–10000000 rows | `email, activated` | [docs](https://docs.checknumber.ai/linkedin-email-checker) |
| `linkedin_profile` | Email Profile Checker | email | 1000–10000000 rows | `email, activated, country, gender, industry, job_title, inferred_salary` | [docs](https://docs.checknumber.ai/linkedin-profile-checker) |

## Response and boundaries

- Treat only an explicit determined result as a positive or negative classification; `undetermined`/`exists=false` is not a negative.
- Authentication keys must come from environment variables or a secret manager; never commit keys or call private/internal endpoints.
- Product prices can change. Check the official pricing page at runtime; this repository intentionally does not hard-code a price.
- Use only identifiers you are authorized to process and follow applicable privacy, platform, and data-protection requirements.

## Runnable examples

Eight self-contained examples are provided under `examples/`: Python, Node.js, Go, Java, C#, PHP, and Shell each implement the full submit → poll → download workflow with HTTP error handling; browser JavaScript submits through a same-origin proxy contract and never contains an API key. Set the server-side API-key environment variable before running them.

## Official resources

- `linkedin_phone`: https://docs.checknumber.ai/linkedin-number-checker
- `linkedin`: https://docs.checknumber.ai/linkedin-email-checker
- `linkedin_profile`: https://docs.checknumber.ai/linkedin-profile-checker
- Pricing: https://checknumber.ai/pricing
- OpenAPI contract: [openapi.yaml](openapi.yaml)

Last reviewed: 2026-08-18.
