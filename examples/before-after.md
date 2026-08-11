# Before / after: the whole pitch

Use this as the screenshot pair for the launch post.

---

## Before — cold "what's next?"

```text
Here are some suggested next steps:

1. Add more unit tests to improve coverage
2. Improve error handling around the API layer
3. Consider adding monitoring / observability
4. Update the documentation to reflect the new feature
5. Refactor for readability and maintainability
6. Add rate limiting on the new endpoints
7. Handle edge cases more carefully
8. Improve accessibility on the new UI
9. Add TypeScript types where missing
10. Consider caching frequently accessed data
```

Zero citations. Could have been written without opening the repo.

---

## After — `/cooked`

```text
## Verdict
**Still cooking.**
Billing webhook is registered but never called from the checkout success path.

## Scope
12 files since origin/main · against issue #88

## Findings

### BLOCKING
1. `handleStripeWebhook` exported, zero call sites — `src/billing/webhook.ts:14`
   Checkout success never hits the webhook route; paid users stay "pending".

### WILL BITE
1. New env `STRIPE_WEBHOOK_SECRET` missing from `.env.example` — `src/billing/config.ts:9`
   Works locally with shell export; CI and teammates will fail silently.

### LOOSE ENDS
1. `// TODO: retry on 429` left in this diff — `src/billing/client.ts:41`

### NOT DOING
- Full Stripe idempotency rewrite — out of scope for #88; not required to close paid status.

### Spec delta
| Requirement | Status |
|---|---|
| Process Stripe webhook on success | silently dropped |
| Show paid status in UI | partial (`PaidBadge` rendered, state never flips) |
| Email receipt | done |

## Don't start yet
Don't start the admin dashboard redesign — the money path is still open.

## → Next
Wire `handleStripeWebhook` into the checkout success handler · Finish
Done when a successful test payment flips the user to `paid` in the DB.
```

Every line cites a file, a command, or a requirement. One next action.
