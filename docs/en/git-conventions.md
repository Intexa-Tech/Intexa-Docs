# Git conventions

This document defines how we work with Git to keep a consistent workflow.

---

## Branches

### Main branches

- `main`: production.
- `develop`: development / integration.

### Work branches

- `feature/short-name`: new feature.
- `fix/short-name`: bug fix.

#### Practical rules

- Use lowercase.
- Use hyphens `-` to separate words.
- Names should describe the goal:
  - `feature/user-auth`
  - `feature/payment-webhook`
  - `fix/login-redirect`
  - `fix/order-total-rounding`

---

## Commits

We use a simple format inspired by **Conventional Commits**.

### Types

- `feat:` new functionality.
- `fix:` bug fix.
- `docs:` documentation.
- `refactor:` code improvement (no behavior change).

### Rules

- Short and clear messages.
- Use **present tense**.
- No trailing period.
- Explain the *what* (the *why* can go in the PR description).

### Examples

```text
feat: add user registration endpoint
fix: prevent null pointer on invoice creation
docs: update onboarding steps
refactor: extract order total calculation
```

---

## Recommended flow (summary)

1. Create a branch from `develop`:

```text
git checkout develop
git pull
git checkout -b feature/REPLACE_ME
```

2. Make small and frequent commits.

3. Keep your branch up to date (if applicable):

```text
git fetch
REPLACE_ME
```

4. Open a PR into `develop`.

5. After approval and merge into `develop`, deploying/merging into `main` follows the project release process:

- `REPLACE_ME` (manual / CI/CD / tag / release branch)

---

## Placeholders to customize

- Release strategy: `REPLACE_ME`
- PR rules (min reviewers, required checks, etc.): `REPLACE_ME`
- Additional naming (hotfix, chore, etc. if used): `REPLACE_ME`
