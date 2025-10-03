# Upvert API Documentation

## Warmly Orchestration webhook API

### Send webhook payload

Send orchestration webhook payload to show popup(s)

**Endpoint:** `POST /api/v3/warmoffers/webhook`

## Authentication

All API requests require a valid API key in the `x-upvert-api-key` header. Contact Upvert to obtain your API key.

**Headers:**

- `x-upvert-api-key`: Your Upvert API key (required)

**Example Request:**

```bash
curl -X POST \
  -H "Content-Type: application/json" \
  -H "x-upvert-api-key: pk_<YOUR_PK>" \
  # Send real webhook payload
  -d '{"hello": "world"}' \
  https://app.warmoffers.ai/api/v3/warmoffers/webhook
```

**Payload:**

Payload **must** include normal [Contact webhook payload](https://help.warmly.ai/articles/7839413626-setting-up-webhooks#website-visit-contact-webhook-example-10)

```json
{
  "Signal": "Website Visit Contact",
  "Orchestration Name": "Webhook Integration",
  "Webhook Sent At": "2025-08-25T15:11:55.835Z",

  // ... All other Contact webhook fields

  // Additional fields only for Upvert
  someUniqueEndUserIdentifierAvailableInBrowser: 'asdf',
  popupIds: [1, 2, 3],
}
```

**Success Response (200):**

```json
{"success": true}
```

**Error Responses:**

**401 - Missing API Key:**

```json
{
  "error": "Missing Upvert API Key. Add x-upvert-api-key header to the request"
}
```

**401 - Invalid API Key:**

```json
{
  "error": "Upvert API Key is incorrect. Add the correct x-upvert-api-key header to the request"
}
```
