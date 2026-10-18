---
name: eumetsat-manage-data-subscriptions
description: List, create, inspect and delete EUMETSAT Data Store subscriptions that deliver new products in a collection.
api: EUMETSAT Data Store Subscription API
generated: 2026-10-18
method: generated
operations:
  - retrieveSubscriptionsUsingGET
  - createNewSubscriptionUsingPOST
  - retrieveSubscriptionUsingGET
  - deleteSubscriptionUsingDELETE
---
# Manage EUMETSAT Data Store subscriptions

Spec: `openapi/eumetsat-data-store-subscription-openapi.yml` (base `https://api.eumetsat.int/data/subscribe/0.0.1`).

1. `retrieveSubscriptionsUsingGET`: list your existing subscriptions so you do not create a duplicate.
2. `createNewSubscriptionUsingPOST`: create a subscription for a collection. Keep the returned `subscriptionId`.
3. `retrieveSubscriptionUsingGET`: confirm the subscription and its settings.
4. `deleteSubscriptionUsingDELETE`: remove it when you no longer need it.

Rules: POST is not idempotent, so list your subscriptions before you retry a create.
