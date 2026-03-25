# stevenoc-mac/standards

Engineering standards, templates, and AI agent conventions for all projects.

## What's here

- `AGENTS.md` - Universal rules for AI agents working on any project
- `templates/` - Project starter templates (Next.js + Neon, Python API, etc.)
- `ci-templates/` - Reusable GitHub Actions workflows
- `scripts/` - Bootstrap scripts for new projects

## How to use

### For AI agents
Read `AGENTS.md` before touching any project in this org. These rules apply universally.

### For new projects
1. Copy the relevant template from `templates/`
2. Copy CI workflows from `ci-templates/` into `.github/workflows/`
3. Create a project-level `AGENTS.md` that references this repo and adds project specifics

### Standards hierarchy
```
stevenoc-mac/standards/AGENTS.md   <- universal rules
  └── your-project/AGENTS.md       <- project-specific additions
```

Project rules inherit from and extend (never override) universal standards.
