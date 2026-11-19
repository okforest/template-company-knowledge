# AGENTS.md

<!-- From the OKForest company knowledge template. Make it yours: add how your
company works with this repository, and remove anything that doesn't apply. -->

{{company_name}} Knowledge: what the company is and how it operates, as an
[OKF v0.3](https://github.com/open-knowledge-format/open-knowledge-format)
bundle in `okf/`, managed with [OKForest](https://www.okforest.ai). People
read it to learn the company; AI assistants use it to answer questions about
it. Write for both.

Everything outside `okf/` (this file, `README.md`, `.github/`,
`.betterleaks.toml`) is repository setup, not knowledge. Commands below run
from the repository root.

## A fresh copy of the template

If the placeholder `company_name` in double curly braces still appears in this
repository, it is a new copy of the template that hasn't been set up yet. Follow the setup checklist in
`README.md`, and ask a person for anything it needs (names, roles, the
password manager) rather than guessing.

## Before you finish

- `npx okforest validate okf` must report no errors. Fix warnings you
  introduced. `npx okforest rule <rule>` explains any finding.
- Pull requests run a secret scan and the same validation
  (`.github/workflows/ci.yaml`). The scan checks the whole git history, so a
  secret must never be committed, even briefly.

## Writing concepts

- One concept per file, in the folder for its area (`company/`, `products/`,
  `market/`, `revenue/`, `people/`, `operations/`, `finance/`, `legal/`). File
  and folder names are lowercase slugs: `ideal-customer-profile.md`.
- Start new pages from their type's template:
  `npx okforest new <Type> <path> --root okf --title "…" --description "…"`.
  The path is inside `okf/`, e.g. `operations/vendors/acme-cloud.md`.
- Use only the types defined in `okf/.okforest/types/`, spelled exactly
  (`Vendor`, not `vendor`). If none fits, add a schema and template in the
  same change and say why. Check `npx okforest inventory okf` before adding a
  type or tag, to reuse an existing one.
- Every concept has a `title` and a one-sentence `description`. New or
  unreviewed pages are `status: draft`.
- Fields OKF doesn't define start with `x-` (`x-owner`), so a later OKF
  version can't give them another meaning. Name a new field the same way,
  and add it to its type's schema and template in the same change.
- Link with standard markdown links, using absolute paths from the bundle
  root (`okf/`): `[ideal customer profile](/market/ideal-customer-profile.md)`.
- `index.md` and `log.md` are reserved names in every folder. Keep each
  folder's `index.md` up to date when you add, rename, or remove a page, and
  give a new folder its own `index.md`, listed in its parent's. Record notable
  changes in `okf/log.md` under a `## YYYY-MM-DD` heading, newest first.

## Accuracy

- Don't invent facts. If something is unknown, leave the guidance comment in
  place and ask, rather than filling it in with a guess.
- When content comes from a document or site, cite it in `sources` and use
  footnotes in the body.
- When you write content, set `generated: { by: <agent>/<version>, at: <time> }`.
  Never add a `verified` entry for a person (`human:…`); only that person
  can do that.
- `Statement` pages (mission, vision, values, messaging, positioning) are
  exact wording: quote them verbatim, and change them only when asked to.
  `Guide` pages are explanation and may be paraphrased.

## Roles and ownership

- `x-owner`, `x-reports-to`, and `x-approved-by` point to a Role page:
  `x-owner: /people/roles/cfo`. Never put a person's name there, so
  ownership stays correct when people change roles.
- A role is a function (CEO, CFO, CMO…). A person has an `x-job-title` on
  their page in `people/team/`, and one person may hold many roles.
- Who holds a role is recorded only on the Role page (`x-held-by`). Don't
  also list roles on the Person page.
- Only create a role that owns something: it is the `x-owner` of at least
  one page, or has responsibilities no existing role covers. When a role no
  longer owns anything, propose removing it.

## Secrets and personal data

Follow the [secrets policy](okf/operations/secrets-policy.md). In short:

- **Never write:** passwords, API keys, tokens, private keys, recovery codes,
  bank account or routing numbers, card numbers, or anyone's government ID
  number.
- **Instead,** record where a secret is kept, in the `x-credentials` field:
  `x-credentials: "{{password_manager}} › <vault> › <item>"`.
- **Allowed:** the company's tax ID, registration numbers, registered address,
  and other facts that appear on public or customer-facing documents.
- **Keep personal data out:** no home addresses, personal phone numbers, pay,
  performance reviews, or health information. Work names, job titles, and
  roles are fine.
- If you find a secret already in the repository, don't just delete it: it
  stays in the git history. Tell a person so it can be rotated.
