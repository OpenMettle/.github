# Security policy

## Reporting a vulnerability

Do not publish exploit details, credentials or private data in an issue or discussion.

Use **Security → Advisories → Report a vulnerability** in the affected repository. If that repository has not enabled private reporting, use the central private reporting form at:

https://github.com/OpenMettle/.github/security/advisories/new

If neither form is available, open an issue containing only **Private security contact requested**. Do not include vulnerability details; a maintainer must arrange a private channel first.

Include the affected repository and commit or release, impact, prerequisites, sanitized reproduction steps and any proposed mitigation. Use synthetic data and describe permission boundaries. Testing must be limited to systems you own or are authorized to assess.

## Supported versions

OpenMettle is in early development and currently has no stable supported release. Each component should publish a support policy when it begins making releases. Maintainers will assess reports on a best-effort basis; no response-time or patch-time guarantee is currently offered.

## Operational boundaries

Examples should default to private network exposure. Review authentication, authorization and tool permissions before making a service available to other people. Treat model-generated commands, retrieved documents and tool output as untrusted input. Keep backups and recovery credentials outside the system they protect.

The repository hygiene check is a limited preventative check, not a full secret scanner or security audit. If a real credential is committed, revoke or rotate it even if the file is subsequently removed.
