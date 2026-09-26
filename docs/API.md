# Proposed frontend API contract

Status: proposed for teammate agreement. There were no backend models in the repository. Canonical current frontend schemas: `frontend/types/huddle.ts`. Change those schemas and `frontend/lib/api.ts` together once backend models exist.

## Endpoints

| Method | Path                    | Request JSON            | Response                                      |
| ------ | ----------------------- | ----------------------- | --------------------------------------------- |
| POST   | `/huddles`              | `{ "question": "..." }` | Complete Huddle object, status `ready`        |
| POST   | `/huddles/:id/request`  | `{}`                    | Updated Huddle, status `pending`              |
| POST   | `/huddles/:id/response` | `{ "response": "..." }` | Updated Huddle, status `complete`, with brief |

The initial prototype expects synchronous responses, not polling or streaming. Errors must use non-2xx status codes. There is a 12-second timeout. Errors remain visible; demo results never silently replace a failed live response. A creation error offers an explicitly labeled demo switch. Preserve input after failed operations.

## Huddle response shape

```json
{
  "id": "huddle-123",
  "createdAt": "2026-09-25T12:00:00Z",
  "status": "ready",
  "demo": false,
  "question": {
    "specialty": "Oncology",
    "condition": "Breast cancer",
    "topic": "Treatment sequencing",
    "intent": "Evidence review",
    "question": "Original question preserved verbatim"
  },
  "sources": [],
  "expert": null,
  "response": null,
  "brief": null
}
```

Source fields: `id`, `title`, `publisher`, `type`, `date` (display string), `snippet`, `url` (HTTPS), `verified` (boolean). `verified` means the source link was checked, not that clinical correctness is certified. Keep descriptive snippets distinct from quoted passages. Do not invent publication dates.

Expert fields: `id`, `name`, `initials`, `specialty`, `expertise` (string array), `match` (number 0–100), `demo` (boolean). The score measures routing relevance, never clinical correctness.

Brief fields: `evidence` (string array), `takeaways` (string array), `uncertainty` (string), `synthesisLabel` (string). Expert text remains in `response` and is not merged into evidence.

## Enable development integration

Copy `frontend/.env.example` to `frontend/.env.local`:

```dotenv
NEXT_PUBLIC_API_MODE=live
NEXT_PUBLIC_API_URL=http://localhost:8000
```

Restart the frontend after changing environment variables. The backend must allow the frontend development origin through CORS. `NEXT_PUBLIC_*` values are public browser configuration: never put API keys in them. This adapter currently sends no authentication credentials. Add secure authentication with the backend teammate before using any private or real information. Use HTTPS for remote services.

Graph data remains synthetic in live mode and is labeled accordingly. Voice is transcribed by the browser, not sent as audio to these endpoints. Real expert routing, retrieval, asynchronous jobs, source-level synthesis citations, and persistence are backend work still to be agreed.
