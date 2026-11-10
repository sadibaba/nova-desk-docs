# Security Policy and Incident Response

## Contact

Report suspected vulnerabilities to `support@nova-desk.online`.

Use the public safety form at `/legal/report` for content, user, copyright,
or non-sensitive bug reports. Do not include credentials, private keys, or
unnecessary personal data in a report.

A machine-readable disclosure file is available at
`/.well-known/security.txt`.

## Scope and safe harbour

Good-faith research is welcome when it:

- avoids accessing, modifying, or deleting another person's data;
- avoids disrupting the service, other users, or shared infrastructure;
- uses the minimum testing necessary to demonstrate the issue;
- does not publish details before a reasonable remediation window;
- does not use social engineering, phishing, or physical intrusion.

Do not test against third-party providers, real user accounts, or production
data without written permission. NovaDesk does not currently operate a paid
bug bounty.

## Response targets

- Acknowledge a report within 3 business days.
- Provide an initial assessment or status update within 10 business days.
- Coordinate disclosure after a fix is available and affected users have had a
  reasonable opportunity to act.

## Incident response plan (internal)

### 1. Preparation

- Maintain an owner and a backup incident lead.
- Keep an inventory of providers, credentials, data stores, and data flows.
- Confirm how to rotate JWT, session, database, Cloudinary, email, OAuth, AI,
  and infrastructure credentials.
- Keep an offline contact list for legal and hosting support.
- Review access logs and backup restoration at least quarterly.

### 2. Detection and triage

- Record the reporter, time, affected systems, and initial evidence.
- Classify severity: critical, high, medium, or low.
- Open an incident channel and restrict discussion to the response team.
- Preserve logs and evidence before changing systems where practical.

### 3. Containment

- Revoke compromised tokens and rotate affected credentials.
- Disable affected integrations or endpoints if necessary.
- Isolate affected hosts or storage buckets.
- Prevent further data loss without destroying evidence.

### 4. Assessment

- Identify what data, users, and systems were affected.
- Determine whether personal data was accessed, altered, disclosed, or lost.
- Check legal, contractual, and regulatory notification duties.
- Record decisions and the reasoning behind them.

### 5. Notification

- Notify affected users without undue delay when required and useful.
- Notify regulators or law enforcement where legally required.
- Provide a plain-language description, likely impact, steps taken, and
  recommended user actions. Do not speculate beyond verified facts.

### 6. Recovery

- Deploy the fix and verify that the attack path is closed.
- Restore from a known-good backup if integrity is uncertain.
- Monitor for recurrence and confirm normal service behaviour.
- Rotate any credentials that may have been exposed.

### 7. Post-incident review

- Write a blameless postmortem with a timeline, root cause, impact, and
  corrective actions.
- Assign owners and deadlines for each action.
- Update this plan, tests, and monitoring.

### 8. Breach notification checklist

- Who was affected, and how many?
- What categories of data were involved?
- When did the incident begin and when was it contained?
- Was data encrypted at rest or in transit? NovaDesk is not end-to-end
  encrypted.
- What harm is reasonably likely?
- What have users been advised to do?
- Which regulator, court, or law-enforcement contact applies?
- Who approves the public statement?

## Current platform controls

- Render is the auth/user/data authority; the VM is IDE-only.
- IDE containers run as a non-root user with dropped capabilities, no Docker
  socket, resource limits and a private per-user network.
- Registration is restricted to `@gmail.com`; disposable domains are rejected.
- Secrets belong in platform environment variables, never in Git or docs.
- Cloudinary is required for durable images; Render local disk is ephemeral.
- The VM is a single point of failure for the IDE; login remains available
  without it.

## Known limitation

NovaDesk is not end-to-end encrypted. Operators may be able to access stored
content. Do not store highly sensitive information on the platform.
