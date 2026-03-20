# GitHub Repository Setup Guide

Quick guide to set up your PrivacyLayer repository for community contributions.

## 1. Create Labels

Go to: https://github.com/ANAVHEOBA/PrivacyLayer/labels

Click "New label" and create these:

| Label | Color | Description |
|-------|-------|-------------|
| `circuits` | `#0052CC` | Noir circuit work |
| `contracts` | `#D93F0B` | Soroban contract work |
| `sdk` | `#FBCA04` | TypeScript SDK work |
| `frontend` | `#1D76DB` | UI/UX work |
| `documentation` | `#0E8A16` | Docs and guides |
| `testing` | `#5319E7` | Test coverage |
| `security` | `#B60205` | Security-related |
| `bounty` | `#7057FF` | Has USDC reward |
| `good first issue` | `#7057FF` | Beginner-friendly |
| `help wanted` | `#008672` | Looking for contributors |
| `enhancement` | `#A2EEEF` | New feature |
| `bug` | `#D73A4A` | Something broken |
| `priority: high` | `#B60205` | Urgent |
| `priority: medium` | `#FBCA04` | Important |
| `priority: low` | `#0E8A16` | Nice to have |

## 2. Enable Issue Templates

The issue templates are already created in `.github/ISSUE_TEMPLATE/`:
- `bug_report.md`
- `feature_request.md`
- `bounty_task.md`

These will automatically appear when users create new issues.

## 3. Create Initial Issues

Use the suggestions in `INITIAL_ISSUES.md` to create your first batch of issues:

1. Go to: https://github.com/ANAVHEOBA/PrivacyLayer/issues/new/choose
2. Select "Bounty Task" template
3. Fill in the details from `INITIAL_ISSUES.md`
4. Add appropriate labels
5. Submit

Start with 5-10 issues to get momentum, then add more as needed.

## 4. Set Up Project Board (Optional)

Create a project board to track progress:

1. Go to: https://github.com/ANAVHEOBA/PrivacyLayer/projects
2. Click "New project"
3. Choose "Board" template
4. Create columns:
   - 📋 Backlog
   - 🏗️ In Progress
   - 👀 In Review
   - ✅ Done

Link issues to the board as they're created.

## 5. Add CONTRIBUTING.md

Create a `CONTRIBUTING.md` file with:
- Code of conduct
- How to claim issues
- Development setup
- PR guidelines
- Testing requirements
- Code style guide

## 6. Set Up Branch Protection

Go to: Settings → Branches → Add rule

For `main` branch:
- ✅ Require pull request reviews before merging
- ✅ Require status checks to pass before merging
- ✅ Require branches to be up to date before merging

## 7. Enable Discussions (Optional)

Go to: Settings → General → Features → Discussions

Use for:
- Q&A
- Ideas and brainstorming
- Announcements
- General community chat

## 8. Add Repository Description

Go to: Repository main page → About (gear icon)

Add:
- Description: "First ZK-proof shielded pool on Stellar Soroban using Protocol 25's BN254 and Poseidon primitives"
- Website: (your dApp URL when deployed)
- Topics: `stellar`, `soroban`, `zero-knowledge`, `privacy`, `noir`, `zk-snarks`, `blockchain`, `rust`, `typescript`

## 9. Create Milestones

Go to: https://github.com/ANAVHEOBA/PrivacyLayer/milestones

Create milestones for major releases:
- `v0.1.0 - Core Circuits & Contracts` (current)
- `v0.2.0 - SDK & Testing`
- `v0.3.0 - Frontend & Deployment`
- `v1.0.0 - Mainnet Ready`

Assign issues to milestones to track progress.

## 10. Set Up GitHub Actions (Optional)

Create `.github/workflows/ci.yml` for automated testing:

```yaml
name: CI

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  test-circuits:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Install Noir
        run: |
          curl -L https://raw.githubusercontent.com/noir-lang/noirup/refs/heads/main/install | bash
          noirup
      - name: Test circuits
        run: |
          cd circuits/commitment && nargo test
          cd ../withdraw && nargo test
          cd ../merkle && nargo test

  test-contracts:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Install Rust
        uses: actions-rs/toolchain@v1
        with:
          toolchain: stable
          target: wasm32-unknown-unknown
      - name: Run tests
        run: cd contracts && cargo test
```

## Quick Start Checklist

- [ ] Create labels
- [ ] Verify issue templates work
- [ ] Create 5-10 initial issues from `INITIAL_ISSUES.md`
- [ ] Add repository description and topics
- [ ] Create milestones
- [ ] Set up branch protection
- [ ] Create `CONTRIBUTING.md`
- [ ] (Optional) Set up project board
- [ ] (Optional) Enable discussions
- [ ] (Optional) Set up GitHub Actions

## Next Steps

1. Announce the project on:
   - Stellar Discord
   - Twitter/X
   - Reddit (r/Stellar)
   - Noir Discord

2. Tag issues with `good first issue` to attract new contributors

3. Respond quickly to issue comments and PRs to build momentum

4. Update `INITIAL_ISSUES.md` as you create issues to track what's been posted
