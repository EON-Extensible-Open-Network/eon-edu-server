# eon-edu-server

The **institution server** for EON Edu: material distribution, institution catalogue,
roles and identity, school tools.

[![Status](https://img.shields.io/badge/status-Faz%203%20·%20scaffold-6b7280)](https://github.com/EON-Extensible-Open-Network/eon-docs/blob/main/plan/eon-plan.md)
[![License](https://img.shields.io/badge/license-AGPL--3.0--or--later-3b82f6)](LICENSE)

---

## Every institution runs its own

A school, a provincial directorate, or a ministry runs this on its own infrastructure. Data
stays with the institution and in the country (madde 24).

The consequence that matters legally: **the institution is the data controller**, and this
project is a software supplier and data processor (madde 29, Rol C). No student data reaches
us — there is no "our server" for it to reach. If a hosted service is ever offered, that
role changes and the plan says so explicitly rather than letting it drift.

## Why AGPL, when the client is GPL

The copyleft has teeth where software is offered as a network service. A vendor should not be
able to run a closed derivative of this server for schools (madde 33).

There is **no module exception here**, unlike the client repositories — the extension point
argument does not apply to a server.

## Status

**Scaffold — Faz 3.** Implementation is gated behind the Faz L1 checklist (madde 30): legal
entity, legal review, hosting obligations, moderators, transparency reporting. The gate exists
so that enthusiasm cannot open it early.

## Planned scope

**Material distribution (madde 25).** Primary path is plain **HTTPS range-request download**
from the institution server. This is the simplification that matters: because the server is
always a source anyway, HTTP alone removes private torrents, peer coordination, tracker
operation, and peer-to-peer IP visibility — along with the data-protection documentation each
of those would require. Peer distribution stays an off-by-default accelerator for
bandwidth-constrained schools, restricted to the local network, and only for
institution-signed packages.

**Institution catalogue (madde 27c).** There is no marketplace. Official and approved sources
are listed in a catalogue the institution signs; nothing else can be added.

**Roles and identity (madde 17, 18, 21).** Roles are scoped ("teacher at school X") and
enforced server-side — a permission is never merely a hidden button. Nobody picks their own
role: a principal is verified manually, invites teachers, who add students by class code.
Identity providers plug in over OIDC. **No Turkish national ID number is stored**; the
provider verifies, and only "verified" plus an opaque id arrives.

**School tools (madde 20).** Attendance, homework lists, submission, grade portal. Grades
export to CSV/XLSX. Integration with e-Okul happens **only** through an official API with
official permission — never screen scraping.

**Notices (madde 12h).** The takedown process runs at school level too, with a reporting
channel and a ticket trail.

## Not in the pilot

Chat. Matrix plus LiveKit is a product-sized operational burden on its own — server, media
store, federation, retention, moderation — and it collides with the oversight requirement in
madde 23: you cannot honestly claim school oversight of direct messages while end-to-end
encryption is on. The pilot ships a one-way announcement feed and comments on material, which
is what a pilot actually needs (madde 19).

## Deployment

Single command, for a school with no dedicated IT staff (madde 24): containers plus a
compose file, an install guide, a backup and restore procedure, an upgrade procedure. See
[`deploy/`](deploy/).

If the deployment needs a systems administrator, it has failed its target user.

## Data protection

- No student data leaves the institution's server.
- No national ID numbers stored (madde 21).
- Retention and deletion schedules per data type; breach notification procedure (madde 31).
- A data protection impact assessment is produced and shared with the institution — not
  optional, because children's data is processed.
- No telemetry, compiled out entirely (madde 36).

## Related

[eon-stream-app](https://github.com/EON-Extensible-Open-Network/eon-stream-app) — the Edu client build ·
[eon-stream-spec](https://github.com/EON-Extensible-Open-Network/eon-stream-spec) ·
[eon-docs](https://github.com/EON-Extensible-Open-Network/eon-docs)

## License

[AGPL-3.0-or-later](LICENSE).
