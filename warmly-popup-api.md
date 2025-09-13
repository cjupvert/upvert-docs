# Upvert API Documentation

## Warmly Integration API

### Get Popups for Organization

Retrieve all popups for a specific Warmly organization.

**Endpoint:** `GET /api/v3/warmoffers/popups/{warmlyOrgId}`

## Authentication

All API requests require a valid API key in the `x-upvert-api-key` header. Contact Upvert to obtain your API key.

**Headers:**

- `x-upvert-api-key`: Your Upvert API key (required)

**Example Request:**

```bash
curl -X GET "https://app.warmoffers.ai/api/v3/warmoffers/popups/org_12345" \
  -H "x-upvert-api-key: pk_<YOUR_PK>"
```

**Success Response (200):**

```json
{
  "popups": [
    {
      "popup_id": 1,
      "popup_name": "Test Popup 1"
    },
    {
      "popup_id": 2,
      "popup_name": "Test Popup 2"
    },
    {
      "popup_id": 3,
      "popup_name": "Test Popup 3"
    }
  ]
}
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

**Note:** The endpoint is currently returning test data while Upvert adds Warmly org id's to our user base
