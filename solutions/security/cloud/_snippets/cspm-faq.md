
## CSPM FAQ [_cspm_faq]

Frequently asked questions about the Cloud Security Posture Management (CSPM) integration and features.

**How often is my cloud security posture evaluated?**

Cloud accounts are evaluated when you first deploy the CSPM integration and every 24 hours afterward.

**Can I onboard multiple accounts at one time?**

Yes. Follow the onboarding instructions in the getting started guides for AWS, GCP, or Azure.

**When do newly enrolled cloud accounts appear on the dashboard?**

After you deploy the CSPM integration, it can take up to 10 minutes for resource fetching, evaluation, and data processing before a newly enrolled account appears on the Cloud Security Posture dashboard.

**When do unenrolled cloud accounts disappear from the dashboard?**

Newly unenrolled cloud accounts can take a maximum of 24 hours to disappear from the Cloud Security Posture dashboard.

**Can I install an unlimited number of agentless integrations?**

Each agentless integration deployment counts towards the maximum number of agentless integrations you can have in the same project. When you reach the maximum, you'll see an error message similar to `You have deployed the maximum number of agentless integrations. To continue, remove some or use agent-based deployment.` You won't be able to deploy another agentless integration until you remove an existing one. All [agentless integrations](/solutions/security/get-started/agentless-integrations.md) count towards this limit.


## KSPM FAQ [_kspm_faq]

Frequently asked questions about the Kubernetes Security Posture Management (KSPM) integration and features.

**What versions of Kubernetes are supported?**

For self-managed/vanilla and EKS clusters, Kubernetes version 1.23 is supported.

**Do benchmark rules support multiple Kubernetes deployment types?** Yes. There are different sets of benchmark rules for self-managed and third party-managed deployments. Refer to [Get started with KSPM](/solutions/security/cloud/get-started-with-kspm.md) for more information about setting up each deployment type.

**Can I evaluate the security posture of my Amazon EKS clusters?** Yes. KSPM currently supports the security posture evaluation of Amazon EKS and unmanaged Kubernetes clusters.

**How often is my cluster’s security posture evaluated?** Clusters are evaluated when you deploy a KSPM integration, and every four hours after that.

**When do newly-enrolled clusters appear on the dashboard?** It can take up to 10 minutes for deployment, resource fetching, evaluation, and data processing to complete before a newly-enrolled cluster appears on the dashboard.

**When do unenrolled clusters disappear from the dashboard?** A cluster will disappear as soon as the KSPM integration fetches data while that cluster is not enrolled. The fetch process repeats every four hours, which means a newly unenrolled cluster can take a maximum of four hours to disappear from the dashboard.


## Findings page [_findings_page]

**Are all the findings page current?** Yes. Only the most recent findings appear on the Findings page.

**Can I build custom visualizations and dashboards that incorporate findings data?** Yes. You can use {{kib}}'s custom visualization capabilities with findings data. To learn more, refer to [Dashboards and visualizations](/explore-analyze/dashboards.md).

**Where is Findings data saved?** You can access findings data using the following index patterns:

* **Current findings:** `logs-cloud_security_posture.findings_latest-*`
* **Historical findings:** `logs-cloud_security_posture.findings-*`


## Benchmark rules [_benchmark_rules]

**How often are my resources evaluated against benchmark rules?** Resources are fetched and evaluated against benchmark rules when a security posture management integration is deployed. After that, the CSPM integration evaluates every 24 hours, and the KSPM integration evaluates every four hours.

**Can I configure an integration’s fetch cycle?** No, the fetch cycle’s timing is not configurable.

**Can I contribute to the CSP ruleset?** You can’t directly edit benchmark rules. The rules are defined [in this repository](https://github.com/elastic/csp-security-policies), where you can raise issues with certain rules. They are written in [Rego](https://www.openpolicyagent.org/docs/latest/policy-language/).

**How can I tell which specific version of the CIS benchmarks is in use?** Refer to the `rule.benchmark.name` and `rule.benchmark.version` fields for documents in these datastreams:

* `logs-cloud_security_posture.findings-default`
* `logs-cloud_security_posture.findings_latest-default`
