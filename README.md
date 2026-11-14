# Awesome-Disaster-Recovery-Orchestration-Testing

# Top Disaster Recovery Orchestration & Testing Ecosystem

**Curated List of SaaS Platforms & Open-Source GitHub Projects**  
*Focused on Recovery Orchestration, Automated Failover & DR Drill Validation*  
**Last updated: March 2026**

This repository tracks notable **SaaS platforms** and **open-source projects** for **Disaster Recovery Orchestration & Testing**. These tools help organizations automate failover, orchestrate recovery runbooks, and—critically—**prove** that DR actually works through scheduled drills, measured RTO/RPO, and evidence-based validation.

**Examples** include Veeam Disaster Recovery Orchestrator, Zerto, Azure Site Recovery, AWS Elastic Disaster Recovery, Druva, and open-source alternatives like Stronghold, Kanister, and Krkn (the category leaders).

**Open-source emphasis**: This section highlights every major active project for self-hosted DR orchestration, open-source chaos engineering, and community-driven recovery validation—ideal for organizations seeking to move beyond vendor promises to measured, enforceable recovery proof. The open-source landscape has matured: **Stronghold** turns DR into testable contracts with MET/VIOLATED/UNKNOWN verdicts , **Kanister** provides blueprint-based application recovery on Kubernetes , and **Krkn** enables chaos-driven DR validation .

Contributions welcome! Open an PR to add/update entries. Keep descriptions factual and link to official sites.

## Table of Contents
- [SaaS/Hosted Platforms](#saas-products)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

## SaaS/Hosted Platforms

| Product | Description | Pricing (Starting) | Free Tier / Trial Limits |
|---------|-------------|-------------------|--------------------------|
| **[Veeam Disaster Recovery Orchestrator](https://www.veeam.com/)** | One-click orchestration plans with automated testing, isolated test labs, and compliance-ready documentation for VMware and Azure recovery. | Quote-only (enterprise contract) | No free tier; trial via sales |
| **[Zerto](https://www.zerto.com/)** | Continuous data replication with journal-based recovery and multi-VM failover orchestration. Enables non-disruptive DR testing. | Quote-only (per-VM subscription) | Trial via sales; no self-serve free tier |
| **[Azure Site Recovery](https://azure.microsoft.com/en-us/products/site-recovery)** | Recovery plans with ordered VM groups and Azure Automation runbook integration. Pay for Azure resources consumed; the service itself is billed per protected instance. | Consumption-based (per protected VM) | No permanent free tier; Azure free account credits apply |
| **[AWS Elastic Disaster Recovery](https://aws.amazon.com/disaster-recovery/)** | Continuous replication with point-in-time recovery and automated drill execution for EC2 and on-premises workloads. | Pay for underlying AWS resources (staging area, replication) | No free tier for DRS itself; AWS Free Tier applies to some resources |
| **[Druva](https://www.druva.com/)** | Cloud-native backup and DR with automated recovery orchestration and cyber recovery runbooks. Includes MDDR for threat monitoring of backups. | Quote-only (per TB/month after deduplication) | No free tier; trial via sales |
| **[Commvault Disaster Recovery](https://www.commvault.com/)** | Enterprise DR orchestration with cleanroom recovery and immutable backups. | Quote-only (enterprise contract) | No free tier; trial via sales |
| **[Cohesity SiteContinuity](https://www.cohesity.com/)** | Integrated backup and automated DR with policy-driven failover and failback orchestration. | Quote-only (enterprise contract) | No free tier; trial via sales |

## Open-Source GitHub Projects

| Project | Star Badge | Description |
|---------|------------|-------------|
| **[Stronghold](https://github.com/mehdi-arfaoui/Stronghold)** | [![Stars](https://img.shields.io/github/stars/mehdi-arfaoui/Stronghold?style=social&color=white)](https://github.com/mehdi-arfaoui/Stronghold/stargazers) | **The most rigorous open-source DR validation framework.** Turns recovery into **testable contracts**: declare RTO/RPO/evidence requirements per service, then Stronghold reads AWS state and returns **MET, VIOLATED, or UNKNOWN** verdicts. **UNKNOWN is not a bug**—it identifies exactly which recovery claim lacks proof. Features: AWS discovery across 16 services into a dependency graph, **39 DR validation rules** across 6 categories (backup, redundancy, failover, detection, recovery, replication), **SPOF detection**, **scenario coverage analysis** (AZ failure, region failure, data corruption), and **DRP generation** as executable YAML runbooks. Evidence maturity levels: **tested > declared > observed > inferred**. CI/CD integration with `stronghold contracts validate --ci` . **Best for teams that need to prove DR, not just claim it.** |
| **[Kanister](https://github.com/kanisterio/kanister)** | [![Stars](https://img.shields.io/github/stars/kanisterio/kanister?style=social&color=white)](https://github.com/kanisterio/kanister/stargazers) | **Blueprint-based application-level DR for Kubernetes.** ~872 stars. Defines backup/restore/recovery procedures as **YAML blueprints** with application-specific quiescing (PostgreSQL, MongoDB, MySQL, Cassandra). **Cross-cluster restore** supported. Integrates with ArgoCD for GitOps. Backends: S3, GCS, Azure Blob, any S3-compatible. **Trade-off**: blueprints require YAML expertise and have no deduplication/encryption (backend-dependent) . **Best for Kubernetes teams needing app-consistent DR procedures.** |
| **[Krkn](https://github.com/krkn-chaos/krkn)** | [![Stars](https://img.shields.io/github/stars/krkn-chaos/krkn?style=social&color=white)](https://github.com/krkn-chaos/krkn/stargazers) | **Chaos engineering for DR validation.** Formerly Kraken. Runs controlled failure scenarios (node kill, pod kill, time chaos, network chaos) against Kubernetes/OpenShift to **prove failover works**. Four interfaces: `krknctl` CLI (recommended), `krkn-hub` container images for CI/CD, Krkn Dashboard (web UI), and standalone Python for full control. **Run external to the cluster**—running inside may be disruptive to itself . **Best for teams wanting to actively break things to validate DR.** |
| **[Ramen](https://github.com/RamenDR/ramen)** | [![Stars](https://img.shields.io/github/stars/RamenDR/ramen?style=social&color=white)](https://github.com/RamenDR/ramen/stargazers) | **Kubernetes DR orchestration for multi-cluster environments.** `ramenctl` CLI validates DR clusters and protected applications, generating **HTML reports** with pass/warning/problem counts. Manages and troubleshoots the complex multi-cluster DR environment (at least 3 connected clusters). Used to implement `odf dr` (OpenShift Data Foundation DR). Apache 2.0 . **Best for OpenShift/ODF DR environments needing validation tooling.** |
| **[K8up](https://github.com/k8up-io/k8up)** | [![Stars](https://img.shields.io/github/stars/k8up-io/k8up?style=social&color=white)](https://github.com/k8up-io/k8up/stargazers) | **Kubernetes-native backup operator built on Restic.** ~961 stars. CRD interface (Backup, Schedule, Restore, Check, Prune). **Client-side encryption and deduplication** inherited from Restic. Pre/post hooks for application consistency. Works on Kubernetes and OpenShift. **No cross-cluster restore** . **Best for teams wanting Restic's proven engine with Kubernetes-native scheduling.** |
| **[Stash](https://github.com/stashed/stash)** | [![Stars](https://img.shields.io/github/stars/stashed/stash?style=social&color=white)](https://github.com/stashed/stash/stargazers) | **Kubernetes backup with database plugins and volume snapshots.** ~1,407 stars (most starred in this category). Built-in plugins for **PostgreSQL, MySQL, MongoDB, MariaDB, Redis, Elasticsearch**. Sidecar injection for consistent backups. **Cross-cluster restore is Enterprise-only** . **Best for teams needing built-in database backup plugins.** |

### Additional Strong Open-Source Options

| Project | Star Badge | Description |
|---------|------------|-------------|
| **[multicloud-disaster-recovery](https://github.com/bukx/multicloud-disaster-recovery)** | [![Stars](https://img.shields.io/github/stars/bukx/multicloud-disaster-recovery?style=social&color=white)](https://github.com/bukx/multicloud-disaster-recovery/stargazers) | **Reference architecture for cross-cloud DR drills.** AWS as primary, Azure and GCP as standby. Terraform (AWS/Azure) + Pulumi (GCP) + Ansible hardening + Python failover scripts with `--dry-run`. Route 53 for traffic steering, Datadog for centralized monitoring. **Demonstrates multi-cloud DR planning beyond diagrams** . **Best as a template for teams building cross-cloud DR drills.** |
| **[ramenctl](https://github.com/ramendr/ramenctl)** | [![Stars](https://img.shields.io/github/stars/ramendr/ramenctl?style=social&color=white)](https://github.com/ramendr/ramenctl/stargazers) | CLI companion to Ramen. Validates DR clusters (`ramenctl validate clusters`) and protected applications (`ramenctl validate application`) with HTML report output. Apache 2.0 . |

**Frameworks for building custom systems**: Combine **Stronghold** for evidence-based DR contract validation with AWS discovery and SPOF detection , **Krkn** for active chaos-driven failover testing , and **Kanister** for application-consistent Kubernetes recovery blueprints —creating a proof-oriented DR stack. For simpler Kubernetes backup, **K8up** (Restic-based, encrypted) or **Stash** (database plugins) provide the backup foundation.

## How to Contribute

1. Fork the repo.
2. Add/edit entries in `README.md` (follow existing format).
3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.
4. Submit PR with a short explanation.

Star the repo if you find it useful!

## Disclaimer

- This is a **community-curated** list — not exhaustive and not an endorsement.
- DR orchestration platforms execute failover and recovery operations that can affect production availability; **always run drills in isolated test environments first** and validate failback procedures before relying on any tool for real incidents.
- **DR testing discipline matters more than tooling.** A proper DR test program includes **tabletop exercises (quarterly)**, **component failover tests**, and **full regional failover drills** with measured RTO/RPO and documented evidence . **Open-source tools enable this discipline without vendor lock-in**: Stronghold explicitly treats **UNKNOWN verdicts as actionable**—they identify exactly which recovery claim lacks proof . Krkn lets you **deliberately break things** to validate failover . **Beware the "backup succeeded" trap**: as the backup orchestrator comparison notes, "the backup command exited zero" and "the backup is restorable" are different claims—automated checks don't replace occasional manual restore drills under stress . Validate RTO/RPO claims against **tested evidence**, not configuration.

---

**Made for SREs, platform engineers, and organizations building provable disaster recovery.**  
Let's make DR orchestration and testing more open, evidence-based, and verifiable.
