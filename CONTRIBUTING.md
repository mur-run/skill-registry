# Publishing a skill

1. Author + validate:
   ```
   mur skill new my-skill
   mur skill validate my-skill/skill.yaml
   ```
2. Publish:
   ```
   mur skill publish my-skill/skill.yaml
   ```
   This signs the manifest with your offline key (`~/.mur/publisher-identity.key`, auto-generated on first use), forks this repo, adds `skills/<name>/versions/<version>.yaml`, and opens a PR.
3. A maintainer reviews the PR (your GitHub identity is your publisher identity). CI validates: signature present + valid, security scan clean, name/version match the path, and the committed `index.yaml` is authoritative.
4. On merge, CI regenerates `index.yaml`.

Bump `version` for every change — published versions are immutable.
