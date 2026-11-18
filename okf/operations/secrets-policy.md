---
type: Policy
title: Secrets policy
description: Secrets never go in this repository; it records where they are kept.
tags: [operations]
status: draft
owner: /people/roles/coo
# effective: 2027-01-31
applies_to: [everyone, contractors, ai-agents]
---

# Policy

This repository is read by the whole team and by AI assistants, and git keeps
every version of every file. So it records **where** a secret is kept, never
the secret itself.

Never write these anywhere in the repository, including drafts:

- passwords, passphrases, and recovery codes
- API keys, access tokens, and private keys
- bank account and routing numbers, and payment card numbers
- anyone's government ID number

Instead, give the location, in a `credentials` field or in the text:
`{{password_manager}} › <vault> › <item>`.

These are not secrets and may be recorded: the company's tax ID, registration
numbers, and registered address, and anything else that appears on invoices,
contracts, or the website.

Personal data stays out too: no home addresses, personal phone numbers, pay,
performance reviews, or health information. Work names, job titles, and
roles are fine.

# Why

Anything committed to git stays in its history even after it's deleted, and
everyone with access to the repository, and every AI assistant reading it,
can see it.

# Enforcement

Every pull request runs a secret scan (`.github/workflows/ci.yaml`),
and the type schemas reject frontmatter fields with names like `password` or
`api_key`.

# If a secret is committed

Rotate it first: change the password or revoke the key where it was issued.
Then remove it from the repository, delete the logs of any CI run that may
have printed it (they outlive the commit), and tell the owner of this policy.
