# Public runner fallback canary

This repository contains only this notice and one harmless runner-identity workflow.
It contains no product source code, credentials, secrets, dependencies, external
actions, checkout step, cache, or artifact upload. Workflow token permissions are empty.

The live Cloudflare dispatcher test queues the workflow on its dedicated hold label.
The deployed dispatcher receives GitHub's signed webhook, enforces its ten-minute
queue timeout, cancels only an unstarted job, confirms completed cancellation,
persists one retry claim, and changes only CI_ROUTER_PUBLIC_CANARY to ubuntu-24.04.
The same run must finish on attempt 2 using a standard free GitHub-hosted runner.
No local controller cancels, changes runner variables, or reruns this test.

This is a controlled unavailable-provider test. Blacksmith is disabled for this
public-only profile, and private organization compute credit remains independently
guarded. The public eligibility proof is bound to this repository ID; its org
variable must select this repository alone. No billing settings are changed.

Earlier local-policy canaries are retained as historical runs; those did not test
Cloudflare's full dispatch path. A first label experiment ran harmlessly within
Blacksmith's existing free allowance and was never retried.
