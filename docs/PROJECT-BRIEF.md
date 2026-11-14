# Project brief

## Purpose

OpenMettle helps people assemble and operate a capable AI experience through a coherent open-source platform. It brings together the model-serving layer, useful tools, memory and context, and browser or IDE harness integrations with clear configuration and practical defaults.

The ambition is to make the surrounding experience associated with leading AI products accessible to self-hosters. Model quality and hardware constraints still matter; OpenMettle must report its tested capabilities honestly.

## Audience

People who want a useful assistant for their household, creative work or development, and want to own the system they run. Setup should be documented for a technically curious person without assuming they are an infrastructure specialist.

## Principles

1. Start with one supported path that is easy to install, verify and recover.
2. Keep advanced options available without making them prerequisites for ordinary use.
3. Prefer coherent workflows over a large collection of disconnected services.
4. Make access, data flow, costs and resource limits understandable.
5. Measure quality as well as latency and throughput.
6. Keep configuration portable and implementation-specific values out of the source tree.
7. Build on existing open-source projects and preserve their identity and licenses.

## Initial milestones

| Milestone | Evidence of completion |
| --- | --- |
| Project foundation | Public profile, contribution routes, repository starter and ownership established |
| Component boundaries | Repository responsibilities and interfaces documented |
| Generalized configuration | One sanitized example configuration passes validation; required overrides documented |
| Supported installation | One documented hardware/software profile installs on a clean system and passes smoke checks |
| Integrated assistant | Browser and one development harness exercise the intended tool, memory and model paths |
| First preview | Versioned artifacts, known limitations, quality results, backup and recovery instructions published |

Milestones are planning targets, not announcements of available features. No release dates are committed.

## Scope decisions to make while porting

- Choose the first supported deployment profile and minimum hardware requirements.
- Decide which services are core and which are optional.
- Define provider interfaces and which local or remote providers are supported initially.
- Define user isolation, tool permissions and data retention behavior.
- Establish a repeatable evaluation set for the intended household and coding tasks.
- Choose component repository names after their boundaries are clear.
