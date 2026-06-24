# APEX Skills — Agent Rules

Rules for AI coding agents working on EKS projects that use APEX Skills.
Copy this file into your project root as `AGENTS.md` (or `CLAUDE.md` for Claude Code)
so your agent loads it automatically.

## Skill Discovery

- Before starting any EKS-related task, check whether a relevant APEX skill is
  available. Prefer skill guidance over general knowledge.
- Skills are installed at `~/.claude/skills/` (Claude Code) or `~/.kiro/skills/`
  (Kiro). Each skill has a `description:` field in its frontmatter — match your
  task against those descriptions.
- If multiple skills could apply, prefer the most specific one. Routing:
  - Architecture decisions → `eks-best-practices`
  - Cluster discovery → `eks-recon`
  - Upgrade readiness → `eks-upgrade-check`
  - Operational audit → `eks-operation-review`
  - Design documents → `eks-design`
  - Terraform generation → `eks-build`
  - Platform engineering / IDP → `eks-platform-engineering`
  - GenAI/ML workloads → `eks-genai`
  - Ingress migration → `eks-ingress-migration`
  - Cost analysis → `eks-cost-intelligence`
  - MCP server setup → `eks-mcp-server`
  - Terraform modules → `terraform-skill`
  - Skill creation/modification → `skill-creator`
  - Steering workflow authoring → `steering-workflow-creator`
  - Docs and cross-reference updates → `update-docs`

For structured multi-phase engagements (design, upgrade, operational review), use steering workflows (e.g., `apex:eks-design`, `apex:eks-upgrade-check`) rather than invoking skills directly. Invocation syntax varies by agent — `/apex:*` in Claude Code, steering files in Kiro.

## Verify Against Upstream Sources

Skill knowledge can go stale. The EKS ecosystem moves fast — Karpenter, VPC CNI,
CoreDNS, and kube-proxy ship new versions frequently. When providing guidance:

1. **Distrust your training data** for version-specific details (API versions,
   default values, feature flags, compatibility matrices). Skill content is more
   current than training data, but even skills have a "last verified" date.

2. **Verify claims against upstream sources** when uncertain. Clone or fetch from
   these repositories to confirm behavior:

   | Component | Upstream Source |
   |-----------|---------------|
   | Karpenter | `github.com/aws/karpenter-provider-aws` |
   | VPC CNI | `github.com/aws/amazon-vpc-cni-k8s` |
   | AWS Load Balancer Controller | `github.com/kubernetes-sigs/aws-load-balancer-controller` |
   | CoreDNS | `github.com/coredns/coredns` |
   | kube-proxy | `github.com/kubernetes/kubernetes/tree/master/pkg/proxy` |
   | EKS AMI | `github.com/awslabs/amazon-eks-ami` |
   | Cilium | `github.com/cilium/cilium` |
   | ArgoCD | `github.com/argoproj/argo-cd` |
   | External DNS | `github.com/kubernetes-sigs/external-dns` |
   | cert-manager | `github.com/cert-manager/cert-manager` |
   | EKS Terraform module | `github.com/terraform-aws-modules/terraform-aws-eks` |
   | Cluster Autoscaler | `github.com/kubernetes/autoscaler` |
   | Istio | `github.com/istio/istio` |
   | Gateway API | `github.com/kubernetes-sigs/gateway-api` |
   | EBS CSI Driver | `github.com/kubernetes-sigs/aws-ebs-csi-driver` |
   | EFS CSI Driver | `github.com/kubernetes-sigs/aws-efs-csi-driver` |
   | Pod Identity Agent | `github.com/aws/eks-pod-identity-agent` |
   | Metrics Server | `github.com/kubernetes-sigs/metrics-server` |
   | Node Termination Handler | `github.com/aws/aws-node-termination-handler` |

3. **Check release pages** for breaking changes before recommending version
   upgrades. Never assume backward compatibility across minor versions of
   Karpenter, VPC CNI, or the AWS Load Balancer Controller.

4. **State uncertainty explicitly.** If you cannot verify a claim against an
   upstream source, say so. "I believe X based on skill guidance but have not
   confirmed against the current release" is better than a confident wrong answer.

## AWS Documentation

- Prefer the AWS MCP Server for documentation search if available — it provides
  real-time, indexed AWS docs.
- Without MCP: reference `docs.aws.amazon.com/eks/latest/userguide/` and
  `docs.aws.amazon.com/eks/latest/best-practices/` as authoritative sources.
- For EKS API changes, check the EKS changelog:
  `docs.aws.amazon.com/eks/latest/userguide/doc-history.html`

## Infrastructure as Code

- Prefer Terraform with `terraform-aws-modules/terraform-aws-eks` for new
  clusters unless the team has an established CDK/CloudFormation pattern.
- When `terraform` is available, run `terraform fmt` and `terraform validate` on
  generated output. In sandboxed environments without CLI access, validate HCL
  syntax structurally.
- When generating Kubernetes manifests, validate with `kubectl --dry-run=client`
  if kubectl is available.

## Safety

- Never execute or recommend destructive operations (node drain, cluster delete, force
  pod eviction) without explicit user confirmation and a rollback plan.
- Upgrades are one-way — always confirm the user has tested in a non-production
  environment first.
- Secrets, credentials, and kubeconfig contents must never appear in agent output
  or be written to files outside of designated secret stores.
- Refer to `eks-best-practices` for IAM least-privilege, Pod Disruption Budgets,
  Pod Security Standards, and network policy guidance.
