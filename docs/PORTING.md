# Porting an existing implementation

Use this checklist for each component moved into OpenMettle. It is a review guide; it does not authorize deleting history or changing someone else's license.

## Establish provenance

- Record the upstream repository, exact source commit, imported paths and relevant license in `UPSTREAM.md`.
- Preserve copyright notices, license files and required notices.
- Distinguish original code from upstream forks or patches. A new project identity does not replace upstream obligations.
- Decide whether to preserve Git history or import a reviewed snapshot. Document the choice.

## Separate installation configuration

- Replace personal hostnames, real domains, usernames, email addresses and absolute paths with configuration keys.
- Replace actual IP addresses, VLANs, disk identifiers, mount points and device paths with examples or discovery logic.
- Identify assumptions about GPU count, VRAM, CPU architecture, operating system, storage layout and network access.
- Keep credentials, certificates, private keys, kubeconfigs, private datasets and runtime state outside source control.
- Document required overrides and validation. Defaults must not silently erase disks or expose a service publicly.

## Review documentation

- Explain the component's purpose and how it connects to the platform.
- Make examples work from a fresh checkout without a maintainer's home directory.
- Use `example.com`, `example.net`, `example.org` or `.invalid` domains where examples need a domain.
- Update relative links, image references, package names, registries, badges and CI URLs.
- Separate installation instructions from historical experiment notes.
- Attribute benchmark results to their exact model, hardware and software configuration.
- Remove private anecdotes and household-specific details while retaining relevant technical limitations.

## Validate the new repository

- Run a credential scan over the intended files and, if preserved, the Git history. If credentials were exposed, rotate them; deleting a file is insufficient.
- Check for remaining installation-specific identifiers using an explicit search list from the source environment.
- Verify configuration rendering and validation without applying it to a live machine.
- Add tests for the actual component and failure modes; repository hygiene checks are only the baseline.
- Exercise the supported installation path, permission boundaries, backups and recovery before describing it as supported.
- Review the repository's license, security reporting, CI permissions and release process before its first public preview.
