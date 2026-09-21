# Agent instructions

This repository holds a Rust tool that enriches paperless-ngx documents using a local LLM.

## Documentation

Documentation for this system lives in **Outline**, at
<https://docs.homelab.internal>. It is the documentation tool for this homelab
— not a README, not a comment in a manifest, not a task record.

**Any change to how something behaves must be documented there as part of the
change, not afterwards.** That means: a new application or integration, a
changed authentication or data path, a new operational constraint, or a failure
you diagnosed. Write the runbook while the details are still fresh; one written
from a real incident is worth several written from imagination.

**What stays in git.** Manifests, Terraform, scripts, task records and
migration history — anything versioned alongside the code it describes. Outline
links to those files rather than restating them. Two copies of one truth drift
apart, which has already happened here more than once, so a page that pastes a
manifest inline is a page that will be wrong within a month.

**What goes in Outline.** Runbooks, architecture narrative and diagrams, the
reasoning behind decisions someone will later question, and guides for people
who use these applications rather than operate them.

**Credentials never appear in a page.** Name the secret and give its path —
`kv/tooling/rustfs` — never its value. To show that two values match, compare
the first ten characters of a SHA-256 fingerprint. Check any logs or error
output you paste for the same reason.

Agents authenticate with the token at `kv/tooling/outline`, exported by
`just secrets-env` as `OUTLINE_API_TOKEN`. It is scoped to reading and writing
documents and cannot administer the workspace. If an action is refused, that is
deliberate — do not work around it or request an admin token.

Before creating a page, search for an existing one; updating the right page
beats adding a second on the same subject. The conventions in full are in
Outline under **Working Agreements → How we document**.
