# AO Job Failure Demo

Playbooks for the Automation Orchestrator **AAP Job Failure - AI Triage and Remediation** demo.

## Playbooks

| File | Job template | Purpose |
|------|----------------|---------|
| `ao-demo-broken-localhost.yml` | **AO Demo \| Broken localhost playbook** | Fails on purpose (`modee` typo instead of `mode`) |
| `ao-demo-fix-localhost.yml` | **AO Demo \| Fix localhost playbook** | Corrected playbook the AI should recommend |
| `forward-job-failure-to-ao.yml` | **AO \| Forward Job Failure** | Posts failed `job_id` to AO webhook `aap-job-failed` |

## Demo flow

1. Launch **AO Demo | Broken localhost playbook** (inventory: localhost).
2. Job fails with Ansible unsupported-parameter error.
3. AAP error notification launches the forwarder (or trigger AO manually with the job ID).
4. AO agent reads stdout via MCP, finds **AO Demo | Fix localhost playbook**.
5. Approve → run fix playbook; Reject → re-run original on failed hosts.

## AAP project

SCM URL: `https://github.com/redawg/ao-job-failure-demo.git`  
Branch: `main`
