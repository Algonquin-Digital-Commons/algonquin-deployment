# Algonquin Institution Site-Profile Input Register

> Standard: PSDC-DOC-001
> Document type: governance-standard
> Status: Draft input register; no deployment approval
> Owner: Algonquin deployment maintainers
> Accountable maintainer: RedjiJB until delegation
> Last reviewed: 2026-10-08
> Governing decisions: PSDC ADR-0010, ADR-0012, ADR-0023, ADR-0028, ADR-0031; Algonquin institutional authority

## Purpose and scope

This register collects the public, reviewable decisions needed to turn the
common PSDC architecture into an Algonquin-controlled development or campus
pilot profile. It does **not** claim Algonquin College has approved the
platform, assigned network space, delegated identity authority, or named
operators. It contains no secrets, private keys, internal topology, protected
student data, or production credentials. Sensitive values may be referenced by
an approved external authority record rather than copied into Git.

The first signed institution profile must bind exact common component and
contract versions, site values, policy authority, responsible roles and
rollback. Until then, the safe default for every unresolved row is **no campus
connection and no protected-data workload**. Founder acceptance of a common
PSDC default does not substitute for college network, security, records,
privacy, academic or operations approval.

## Known public facts and authority boundaries

- The institution slug and display name in [`institution.yaml`](../../institution.yaml)
  are `algonquin` and `Algonquin College`.
- The GitHub fork organization is `Algonquin-Digital-Commons`; the common
  upstream organization is `Post-Secondary-Digital-Commons`.
- This repository owns Algonquin deployment bindings. Common product behavior
  and reusable schemas remain in the corresponding PSDC repositories.
- The common [Network Architecture](https://github.com/Post-Secondary-Digital-Commons/psdc-architecture/blob/main/docs/network/Network-Architecture.md),
  [Retention](https://github.com/Post-Secondary-Digital-Commons/psdc-architecture/blob/main/docs/governance/Retention.md),
  [KMS](https://github.com/Post-Secondary-Digital-Commons/psdc-architecture/blob/main/docs/security/KMS.md),
  and [Disaster Recovery](https://github.com/Post-Secondary-Digital-Commons/psdc-architecture/blob/main/docs/architecture/Disaster-Recovery.md)
  state common constraints but leave campus values to institutional authority.

## Required inputs and decision owners

Every entry is **unapproved** until a named institution role records a decision,
evidence source, effective date, expiry or review date, and approval reference.
The roles below are proposed approval functions, not claims that a person or
department has accepted them.

| ID | Required input | Proposed approving function | Evidence before binding | Safe interim state |
|---|---|---|---|---|
| ALG-SITE-001 | Pilot purpose, participating programs, sponsor and permitted data classes | College sponsor + privacy | Written pilot charter and data inventory | Synthetic data only |
| ALG-SITE-002 | Institutional OIDC issuer, account-linking scope and outage owner | Identity authority | Issuer metadata, test realm, role mapping and approval | No campus account connection |
| ALG-SITE-003 | DID/VC issuer and verifier roles, recovery and revocation authority | Identity + records | Credential policy and key-custody review | No institutional credential issuance |
| ALG-SITE-004 | Public and internal DNS zones, delegation and service names | Network/DNS authority | Approved zone allocation and change ticket | No institutional DNS names |
| ALG-SITE-005 | IPv4/IPv6 prefixes, IPAM owner and overlap check | Network/IPAM authority | Reserved prefixes and collision report | No routable campus allocation |
| ALG-SITE-006 | VLAN/VRF, lab uplink, firewall and egress profiles | Network + security | Segmentation design, flow matrix and rollback | Isolated synthetic lab only |
| ALG-SITE-007 | Lab owner-return and non-disruption rules | Lab operations + academic owner | Calendar, consent/notice and reclaim test | No unattended lab enrollment |
| ALG-SITE-008 | Workload trust domain, SPIFFE/SPIRE names and mTLS issuance | PKI + security | Trust-domain approval and certificate lifecycle test | No campus workload identity |
| ALG-SITE-009 | Offline CA root, intermediates, signing and recovery custodians | PKI + security | Ceremony plan, custody separation and recovery exercise | No production certificate issuance |
| ALG-SITE-010 | KMS/HSM roots, envelope keys, rotation, quorum and break-glass | Security + data stewards | Key inventory, recovery and revocation tests | No protected data encryption service |
| ALG-SITE-011 | Per-data-class retention authority, legal holds and disposition | Records + privacy + counsel | Signed retention authority records and deletion/restore tests | Do not store protected classes |
| ALG-SITE-012 | Backup location, encrypted copies, RPO/RTO per service and restore owner | Service owner + operations | Business-impact analysis and restore rehearsal | No production stateful service |
| ALG-SITE-013 | Production/lab capacity inventory and quota envelopes | Infrastructure + lab owner | Authorized census, power/network review and headroom model | No production capacity claim |
| ALG-SITE-014 | Federation peers, gateway transport and trust bundle | Federation + security | Partner agreement, revocation and isolation test | Federation disabled |
| ALG-SITE-015 | Ingress/DDoS owner, incident contacts and escalation | Network + security | Edge design and tested escalation path | No public ingress |
| ALG-SITE-016 | Component/contract compatibility lock and release signatures | Deployment + product maintainers | Pinned release inventory, SBOM and rollback | No release admission |
| ALG-SITE-017 | Finance/credit accounting, settlement and dispute authority | Finance + governance | Non-transferable credit rules and reconciliation exercise | Test ledger only |
| ALG-SITE-018 | Named change, on-call, privacy and incident approvers | College sponsor + operations | RACI and accepted duty roster | Founder cannot self-approve college roles |

## Required profile record and approval workflow

A future site-profile record MUST identify the input ID, chosen value or secure
external reference, environment, classification, decision owner, approving
function, source evidence, effective date, review/expiry, applicable common
contract version, and rollback. The approver MUST be distinct from an
untrusted submitter for high-impact identity, key, network and retention
changes. A missing approval fails closed; a `null`, `TBD`, or unverified
reference is never interpreted as an accepted default.

The workflow is: collect public inputs → request institution review → record
approval and evidence → validate against released common schemas → sign the
environment profile → test in an isolated pilot → rehearse rollback. A
subsequent change must recheck dependent DNS, identity, certificate, network,
data and recovery records rather than editing one value in isolation.

## Maturity, evidence and definition of done

This register is **documented**, not contracted, signed, implemented or
deployed. It is done as an input register when every row has an owner and a
source path for a future decision. A deployable profile requires every
applicable row to be resolved, independently approved where required, checked
against a versioned common schema, signed and backed by isolated test evidence.
Production admission additionally requires recovery, privacy, security,
capacity and incident evidence from the real Algonquin environment.

No deployment automation may treat this document or the public
[`institution.yaml`](../../institution.yaml) as a substitute for those gates.

## Change control and exceptions

Proposed changes use a pull request in this fork and identify affected common
contracts. An exception needs scope, risk, compensating control, institution
approver and expiry; it cannot silently weaken a common safety boundary.
Never commit secrets or private topology to make a validator pass. Where the
institution has not delegated authority, leave the row unresolved and stop the
affected pilot or production action.
