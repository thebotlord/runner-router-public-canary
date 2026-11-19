# Public runner fallback canary

This repository contains only this notice and a harmless runner-identity workflow.
It contains no product source code, credentials, secrets, external actions, or checkout step.

The first attempt deliberately requests an extra unavailable runner label. No Blacksmith
runner can execute it. After a ten-minute queue timeout, an isolated local controller
uses the production router's unchanged selection and retry policy to cancel the
unstarted attempt and rerun it on the free standard GitHub ubuntu-24.04 runner.

This verifies a controlled Blacksmith-unavailable to GitHub execution path. It does
not simulate a real Blacksmith billing outage or alter production router state.
No artifacts, caches, dependencies, or paid runners are used.
