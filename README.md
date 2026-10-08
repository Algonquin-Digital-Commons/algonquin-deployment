# Algonquin PSDC Deployment

This independent repository is Algonquin College's thin fork of the PSDC
institution deployment template.

## Owned here

- approved Algonquin branding and public URLs;
- signed deployment-manifest source and release metadata;
- environment composition and pinned Commons component versions;
- Algonquin identity, academic and campus adapter configuration;
- local policy overlays, federation peers and moderation configuration;
- OpenTofu roots, Ansible inventories and environment runbooks; and
- deployment-specific tests, evidence and rollback records.

## Never stored here

- reusable Commons product source;
- institutional secrets, private keys or production credentials;
- copied shared schemas; or
- modifications that should be contributed to an owning PSDC repository.

This repository consumes signed releases from the independent `psdc-*`
repositories. Its compatibility lock must identify exact component and contract
versions before any environment is deployed.

The [institution site-profile input register](docs/governance/Institution-Site-Profile-Input-Register.md)
shows which campus values and authority approvals are still missing. Nothing in
that register authorizes a pilot or production deployment.

An [illustrative Algonquin compute manifest](examples/compute/README.md)
shows institution-specific example values without putting them in the Common
conformance fixtures. It is synthetic and is not deployment authorization.
