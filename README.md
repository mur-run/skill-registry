# MUR skill registry

The catalog that `mur agent skill registry-add <agent> <name>` (and `mur skill install <name>`) install from.

- `index.yaml` — generated catalog. **Do NOT hand-edit** — CI regenerates it from `skills/`.
- `skills/<name>/versions/<semver>.yaml` — a signed skill manifest (one file per version; versions are immutable once published).
- `publishers/` — published public keys. The MUR-official key is `mur.pub`; its fingerprint is pinned in the MUR client, so skills it signs install as **Trusted**.

## Trust model

Every skill is signed (DSSE / Ed25519) by its publisher's **offline** key. On install the MUR client verifies the signature **and** a content hash, and **fails closed**. The official publisher key is pinned in the client; other publishers are **trust-on-first-use**. CI here holds **no** signing key — it only validates.

See [CONTRIBUTING.md](CONTRIBUTING.md) to publish a skill.
