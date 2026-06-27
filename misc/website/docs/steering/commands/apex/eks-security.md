---
title: "apex:eks-security"
description: "Harden an Amazon EKS cluster or prepare it for a compliance audit — walks the discovery-driven 7-layer security stack (OS/AMI, identity, workload, image, runtime, audit, compliance accelerators), the compliance-regime scope (HIPAA/PCI/FedRAMP/GDPR/SOC2/ISO), the AWS-canonical baseline, and a 30/60/90 hardening roadmap. Use to design or harden EKS security for regulated workloads."
custom_edit_url: https://github.com/aws-samples/sample-apex-skills/blob/main/steering/commands/apex/eks-security.md
format: md
---

:::info[Source]
This page is generated from [steering/commands/apex/eks-security.md](https://github.com/aws-samples/sample-apex-skills/blob/main/steering/commands/apex/eks-security.md). Edit the source, not this page.
:::

<objective>
Run the APEX EKS security & compliance workflow — turn a team's compliance regime, workload sensitivity, and OS/AMI constraints into an opinionated, layer-by-layer Amazon EKS hardening recommendation and audit-prep roadmap.
</objective>

<execution_context>
@~/.claude/apex-steering/workflows/eks-security.md
</execution_context>

<process>
Follow the eks-security workflow end-to-end. Ask the required discovery questions FIRST (compliance regime, workload sensitivity, OS/AMI strategy, audit timeline, topology, skill, ops-overhead tolerance, current baseline) — do not recommend a stack before they are answered. Use the `eks-security` skill for the 7-layer stack, the compliance-regime scope view, the non-negotiable security baseline, and the 30/60/90 roadmap. Always include the compliance-status disclaimer (defer to the live AWS Services in Scope page) and never call IRSA "legacy", promise "HIPAA-compliant", or conflate FedRAMP Moderate/High or FIPS 140-2/140-3. Phases: 1) discovery, 2) compliance-regime position, 3) top-level stack recommendation, 4) layer-by-layer guidance with shared-responsibility split, 5) 30/60/90 roadmap, 6) security baseline + gotchas + escalation.
</process>
