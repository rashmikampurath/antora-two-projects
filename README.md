# antora-two-projects

Two Antora websites from shared AsciiDoc:

| Site | Playbook | Content |
| --- | --- | --- |
| Full docs | `playbook-full.yml` | Module A **and** Module B |
| Module B only | `playbook-b.yml` | Module B |

Antora generates one site per **playbook**. Each of Module A and Module B is an Antora **component** (a folder with `antora.yml`). That is what lets the second playbook omit Module A entirely.

```
content/
  module-a/          ← component "module-a" (full site only)
  module-b/          ← component "module-b" (both sites)
playbook-full.yml    → build/site-full
playbook-b.yml       → build/site-b
```

## Prerequisites

- Node.js 18+ (this repo includes `.nvmrc` for Node 20; run `nvm use` in the project folder)

## Setup

```bash
npm install
```

## Build

```bash
npm run build          # both sites
npm run build:full     # A + B → build/site-full
npm run build:b        # B only → build/site-b
```

## Preview

```bash
npm run preview:full   # http://localhost:5000
npm run preview:b      # http://localhost:5001
```

Run these in a second terminal after a build. The full site starts on Module A; the B-only site starts on Module B. On the full site you should see both components in the UI; on the B-only site you should see only Module B.
