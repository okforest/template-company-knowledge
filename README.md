# {{company_name}} Knowledge

What {{company_name}} is and how it operates: its products, market, revenue
operations, people, operations, finance, and legal. Written for people joining
the company and for the AI assistants that work with it.

The knowledge is an [Open Knowledge Format (OKF)](https://github.com/open-knowledge-format/open-knowledge-format/blob/main/SPEC.md)
bundle in [`okf/`](okf/index.md): one markdown file per concept, with YAML
frontmatter. Start at [`okf/index.md`](okf/index.md), which declares the OKF
version it follows (`okf_version`).

## Using this template

<!-- Delete this section once setup is done. -->

This repository is the [OKForest](https://www.okforest.ai) company knowledge
template. Start your own copy with GitHub's **Use this template › Create a new
repository** (it should be private), or from a terminal:

```sh
npx giget gh:okforest/template-company-knowledge acme-knowledge
```

### Setup checklist

- [ ] Replace `{{company_name}}` with your company's name, and
      `{{password_manager}}` with the password manager you use, everywhere.
      `npx okforest validate okf` warns about each one left in a page.
- [ ] Add yourself (and anyone else) in `okf/people/team/` with
      `npx okforest new Person people/team/<name>.md --root okf`.
- [ ] Set `x-held-by` and `x-state` on each role in `okf/people/roles/`. One
      person can hold several roles (`x-state: interim`). Delete roles nobody
      needs, and reassign the pages they owned.
- [ ] Fill in `okf/company/overview.md`, then the rest of `okf/company/`.
- [ ] Delete starter pages that don't apply, and their lines in `index.md`.
- [ ] Replace the entry in `okf/log.md` with today's date.
- [ ] In the repository's settings, require the **Scan and Validate** check
      before merging to `main`.
- [ ] Delete `LICENSE`: it covers the template, not your company's knowledge.
- [ ] Delete this section.

### Or ask an AI agent to do it

Open the new repository in Claude Code (or another coding agent) and give it
this prompt:

```text
This repository was just created from the OKForest company knowledge
template. Set it up for our company, following AGENTS.md:

1. Ask me for the company's name and the password manager we use, then
   replace every {{company_name}} and {{password_manager}} in the repository.
2. Ask me who works here, their job titles, and which roles each person
   holds. Create a Person page for each in okf/people/team/ and set x-held-by
   and x-state on the roles. Suggest removing roles nobody holds or needs.
3. Interview me to fill in okf/company/overview.md, mission.md, vision.md,
   and values.md. Leave anything I don't know as a draft.
4. Read our website, if we have one, and draft
   okf/company/brand/messaging.md and okf/products/ from it, citing it in
   sources. Ask before treating anything as final.
5. Work through the rest of the setup checklist in README.md, run
   npx okforest validate okf until it reports no errors, and show me what
   changed.
```

### Contributing to the template

Improvements are welcome as pull requests to
[okforest/template-company-knowledge](https://github.com/okforest/template-company-knowledge).
Keep it general: no company-specific content. The template is licensed
[MIT-0](LICENSE), so copies need not keep the license or credit it.

## Layout

| Path | What it holds |
|---|---|
| `okf/company/` | Who we are: overview, mission, vision, values, history, brand, glossary |
| `okf/products/` | What we sell: each product's overview, pricing, and roadmap |
| `okf/market/` | Who we serve and compete with: ideal customer, personas, competitors |
| `okf/revenue/` | Marketing, sales, and customer support |
| `okf/people/` | Roles, team, org chart, onboarding |
| `okf/operations/` | Vendors, meeting cadence, and operating policies |
| `okf/finance/` | Budgets, billing, accounting |
| `okf/legal/` | Contracts, intellectual property, compliance |
| `okf/.okforest/` | OKForest settings, and each type's schema and template |
| `AGENTS.md` | Instructions for AI agents editing this repository |
| `.github/` | CI (secret scan and validation on every pull request) and Dependabot |

## Working with it

```sh
# Add a page from its type's template
npx okforest new Vendor operations/vendors/acme-cloud.md --root okf \
  --title "Acme Cloud" --description "Hosts our production systems."

# Check the bundle
npx okforest validate okf

# List the types, tags, and fields in use
npx okforest inventory okf
```

The starter pages are drafts (`status: draft`): fill them in, remove the
guidance comments, and mark them `stable`. Never commit secrets: see the
[secrets policy](okf/operations/secrets-policy.md).
