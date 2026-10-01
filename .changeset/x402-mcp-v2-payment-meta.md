---
"agents": patch
---

Fix `withX402().paidTool` never seeing a payment sent with MCP SDK v2. The tool handler read the payment token from `extra._meta`, which only exists in SDK v1; v2 passes the request on `extra.mcpReq`, so every call was answered with `PAYMENT_REQUIRED`. Read `extra.mcpReq._meta` first and keep the v1 path (and the header fallbacks) working.
