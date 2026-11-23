---
type: Guide
title: Architecture
description: The systems the company runs on, what each is for, and how information moves between them.
tags: [technology]
status: draft
x-owner: /people/roles/cto
---

# Overview

<!-- Every company runs on systems, whether or not it writes software: email
and files, customer records, accounting, the website, and anything it builds
for customers. This page is the map: what each system is for, which role
owns it, and what data it holds. Link each to its
[vendor page](../operations/vendors/index.md); a system the company builds
belongs here too, linked from its product's page. -->

# Diagram

<!-- Replace this example with your own systems. Kept as text, the diagram
changes in the same review as the page, and anyone can see what moved. -->

```d2
direction: right
team: Team
email: Email and files
crm: Customer records
accounting: Accounting
website: Website

team -> email
team -> crm
website -> crm: enquiries
crm -> accounting: invoices
```

# Data

<!-- Where customer and company data is kept, which system is the source of
truth for each kind, and who can reach it (see [access](security/access.md)). -->
