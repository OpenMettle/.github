# Organization and repository setup

## Organization foundation

- Create OpenMettle as a GitHub Free organization owned by the intended personal account.
- Publish this `.github` repository publicly for the organization profile and shared defaults.
- Publish `repository-template` publicly and enable **Template repository**.
- Enable Discussions in `.github` for project-wide questions.
- Establish a project-controlled private contact address before broad community promotion, then update the code of conduct. Do not publish a maintainer's private email automatically.

The bootstrap script sets the organization display name and description, creates the two repositories, publishes the content and applies the repository settings below. The account owner must create the organization and authorize the CLI or app separately.

## Repository defaults

Use `main`, squash merges and automatic deletion of merged branches. Disable unused wikis. Enable private vulnerability reporting and Dependabot alerts. Keep Actions tokens read-only by default and grant a specific workflow only the permissions it requires.

After the first successful **Repository checks** job, consider a ruleset or branch protection for `main` that prevents force pushes and deletion and requires this check. Choose PR review requirements to fit the maintainer team; a sole maintainer must not be locked out by a mandatory second reviewer who does not exist.

Review each new repository's private reporting and Actions settings; repository templates copy files, not every repository setting.

## What inherits and what is copied

| Material | Mechanism |
| --- | --- |
| Contribution, conduct, security and support guidance | GitHub defaults from the public `.github` repository unless overridden |
| Issue forms and PR template | GitHub defaults unless the target repository defines its own |
| CI, scripts, editor settings and example configuration | Copied when creating from `repository-template` |
| License | Must be present in each repository; never inherited automatically |
| CODEOWNERS, branch rules, secrets and repository settings | Configure explicitly; no automatic inheritance is assumed |

Avoid maintaining duplicate copies of shared guidance unless a component needs different instructions. If you want the guidance included in distributed source archives, copy it intentionally and establish how updates will be maintained.

## Suggested first work items

1. Agree the initial component boundaries and repository names.
2. Inventory upstream licenses and attribution before moving code.
3. Separate site configuration from reusable platform defaults.
4. Define a clean-install acceptance path for one supported profile.
5. Publish reproducible quality and performance evaluation instructions.
6. Document backup, restore and rollback before the first preview release.

No personal repositories need to be transferred or deleted as part of this bootstrap.
