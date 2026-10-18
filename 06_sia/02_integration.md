# SIA — System Integration

## What Integration Is

Making separate systems (apps, databases, services) work together and share data.

## Integration Approaches

| Approach | How | Pros | Cons |
|----------|-----|------|------|
| Point-to-point | Direct link between two systems | Quick for few systems | Tangled as systems grow (n² links) |
| Hub-and-spoke / ESB | Central bus routes and transforms | Central control | Bus is bottleneck / single failure point |
| API-based | Systems expose REST/SOAP endpoints | Standard, reusable | Needs versioning, security |
| Message-based | Queue/broker (Kafka, RabbitMQ) | Async, decoupled, resilient | Eventual consistency, harder debugging |
| Database integration | Shared DB | Simple | Tight coupling; avoid |
| File transfer | CSV/XML batch | Works with legacy | Delayed, error-prone |

## API Styles

| | REST | SOAP |
|--|------|------|
| Format | JSON (usually) | XML only |
| Transport | HTTP | HTTP, SMTP, others |
| Contract | OpenAPI (optional) | WSDL (strict) |
| Use | Web/mobile APIs | Enterprise, strict contracts |

## Data Formats

```json
{ "orderId": 101, "items": [{ "sku": "A1", "qty": 2 }] }
```

```xml
<order id="101"><item sku="A1" qty="2"/></order>
```

JSON lighter, easier in JS. XML supports schemas, namespaces.

## Synchronous vs Asynchronous

- **Sync** — caller waits for response. Simple; coupled availability.
- **Async** — caller continues; result via callback/message. Resilient; more complex.

## Middleware

Software layer between systems: message brokers, ESB, API gateways, ORMs.

## Integration Concerns

1. **Data mapping/transformation** — field names, formats differ.
2. **Authentication** between systems (API keys, OAuth, mTLS).
3. **Error handling** — retries with backoff, dead-letter queue.
4. **Idempotency** — repeated message must not duplicate effect.
5. **Versioning** — don't break consumers.
6. **Monitoring/logging** — trace requests across systems.

## System Integration Steps

Requirements → identify systems and interfaces → choose approach → design data mapping → build → test (integration + end-to-end) → deploy → monitor.

## Testing Levels

Unit → Integration → System → Acceptance (UAT).

## Gotchas

- Integration failures often come from mismatched data formats and time zones.
- Retrying non-idempotent calls can double-charge/duplicate.
- Secure every interface — integrations widen attack surface.
