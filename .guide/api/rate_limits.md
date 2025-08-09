# API Rate Limiting

## Enterprise Policy

- Default: 1000 requests/minute per user
- Burst: 5000 requests/minute for short periods
- Custom limits for integrations and plugins
- Rate limit headers returned on all responses
- Excess requests receive HTTP 429

## Monitoring

- All rate limit events are logged
- Alerts for sustained high usage

---

For exceptions, contact the API admin.
