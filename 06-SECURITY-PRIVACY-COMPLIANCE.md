# 06 - Security, Privacy, and Compliance

## Security posture

NovaDesk has a real security foundation, but it is not a hardened enterprise
platform.

### Implemented

- bcrypt/bcryptjs password hashing
- JWT access and refresh tokens
- refresh-token storage and revocation
- account lockout after repeated failures
- active-account checks on every authenticated request
- server-side role and ownership checks
- token-protected owner bootstrap
- active Admin record plus clearance checks
- owner-only admin management
- owner cannot be demoted or suspended through normal admin endpoints
- rate limiting on auth and API groups
- helmet security headers
- CORS allowlist
- upload MIME restrictions and size limits
- private local storage for new storage files
- report intake with rate limiting
- audit logging
- legal and safety pages
- security.txt and incident plan

### Not implemented or incomplete

- end-to-end encryption
- MFA enforcement
- hardware-key support
- full CSRF design for cookie flows
- malware scanning of uploads
- comprehensive ownership tests
- secret rotation automation
- production secret manager
- centralized audit retention policy
- data export UI
- automated account deletion verification
- vulnerability disclosure SLA tooling
- dependency patching process
- full transitive licence audit
- backup encryption verification

## The E2EE warning

NovaDesk is not end-to-end encrypted. The service and its operators may be able
to access stored content. Users must not store:

- passwords
- private keys
- recovery codes
- financial records
- medical records
- identity documents
- confidential client data
- regulated personal data

This warning appears on the landing page, privacy page, security page, report
form, and storage UI.

## Owner and admin security model

```text
owner bootstrap:
  OWNER_EMAIL
  OWNER_SETUP_TOKEN
  verified account
  no existing active owner
  timing-safe token compare
  token revocation after setup

requireAdmin:
  valid access token
  active user
  active Admin record
  clearance >= 2
  role admin or owner

requireOwner:
  valid access token
  active user
  active Admin record with isOwner
  role owner
```

Rules:

- A matching email alone never grants owner.
- A local role value never grants server access.
- A suspended or deleted user cannot continue using an old token.
- Deleting a user cleans up tokens, memberships, notifications, settings, and
  admin record.
- Only the owner can create, demote, suspend, or delete other admins.
- Team deletion is permanent and cascades selected team records.

These rules need regression tests before beta.

## Privacy position

Data categories:

- account details
- content and uploaded media
- technical logs
- usage and security events
- reports and moderation records
- integration tokens and provider data

The public Privacy Policy covers purpose, sharing, retention, rights, cookies,
and contact. It is an operational template, not legal advice.

## Third-party processors

Potential processors:

- hosting and database provider
- Cloudinary / custom media provider
- email provider (Resend/SMTP)
- Google OAuth
- GitHub OAuth / GitHub App
- AI provider
- Redis / Upstash
- Coder (optional)
- CrazyGames (optional)
- SearXNG (optional)

Each needs a current data-processing review before a commercial launch.

## Legal document status

The public legal centre includes:

- Terms of Service
- Privacy Policy
- Acceptable Use and Community Guidelines
- Report and Takedown Process
- Cookie Notice
- Copyright and DMCA Policy
- Data Retention and Deletion Policy
- Security and Incident Response
- Third-Party Licences and Notices

Status: useful product documentation, **not a lawyer-reviewed compliance
package**. Before launch:

1. Have a qualified lawyer review the terms, privacy, copyright, and retention
   language.
2. Confirm the governing law and jurisdiction.
3. Confirm the copyright agent and takedown address.
4. Confirm PECA and local regulatory obligations.
5. Confirm data-processing agreements with providers.
6. Add a data export and account deletion workflow.
7. Document breach notification timelines and authorities.
8. Publish a monitored security and privacy contact.

## Security contact

- The current company contact is `novadesk120@gmail.com`.
- `/.well-known/security.txt` is the machine-readable disclosure file.
- `SECURITY.md` is the internal plan.
- The public legal pages use `novadesk120@gmail.com` as the contact.

Update these if a dedicated domain email is created later.

## Incident response summary

The internal plan in `SECURITY.md` covers:

1. preparation
2. detection and triage
3. containment
4. assessment
5. notification
6. recovery
7. post-incident review
8. breach notification checklist

The public security page intentionally publishes only the summary.

## Compliance checklist

- [ ] Lawyer-reviewed terms and privacy
- [ ] Data processing register
- [ ] Data export flow
- [ ] Account deletion flow
- [ ] Retention job
- [ ] Backup restore test
- [ ] Breach notification contacts
- [ ] Security contact monitored
- [ ] Dependency and licence audit
- [ ] Upload malware scanning
- [ ] Accessibility review
- [ ] Age and child-safety review
- [ ] Copyright agent process
- [ ] PECA/legal request process
