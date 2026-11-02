# Upload to GitHub

The repository-ready files are already arranged at the archive root.

```bash
git init
git add .
git commit -m "Publish SAP Reverse Engineer Agent and Skill V8.7.2"
git branch -M main
git remote add origin https://github.com/naruepan2/SAP-Reverse-Engineer-Agent-and-Skill-for-VS-Code.git
git push -u origin main
```

If `origin` already exists:

```bash
git remote set-url origin https://github.com/naruepan2/SAP-Reverse-Engineer-Agent-and-Skill-for-VS-Code.git
git push -u origin main
```

Authentication is handled by the user's local Git credential manager or GitHub CLI. No credentials are stored in this package.
