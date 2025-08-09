# Authentication & Authorization

## Supported Methods

- JWT (JSON Web Token) for all API endpoints
- OAuth2 for SSO and third-party integrations
- SAML/LDAP for enterprise directory integration

## Flows

- Login: User submits credentials, receives JWT
- Token refresh: Short-lived tokens, refresh endpoint
- Role-based access: All endpoints check user roles/permissions

## Security

- All tokens are signed and encrypted
- Secrets managed via enterprise vault (e.g., HashiCorp Vault)
- All auth events are logged for audit

---

For SSO setup, see `integration_enterprise.md`.
