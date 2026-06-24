# AWS & EKS Guidance

- Prefer the AWS MCP Server for AWS interactions — it provides sandboxed
  execution, observability, and audit logging. If unavailable, use the
  AWS CLI directly.
- Before starting a task, check whether a relevant AWS skill is available.
  Load the skill with `retrieve_skill` and prefer its guidance over
  general knowledge.
- Prefer the EKS MCP Server for live cluster interactions — it provides
  read-only Kubernetes API access, upgrade insights, and cluster discovery.
  If unavailable, use kubectl and AWS CLI directly.
- Before starting an EKS task, check whether a relevant APEX skill is
  available. Load the skill and prefer its guidance over general knowledge.
- When uncertain about specific AWS details (API parameters, permissions,
  limits, error codes), verify against documentation rather than guessing.
  State uncertainty explicitly if you cannot confirm.
- When uncertain about specific EKS details (add-on versions, API parameters,
  Karpenter behavior, VPC CNI settings), verify against upstream source repos
  rather than guessing. Cross-reference the upstream repo to confirm the
  behavior still holds in the current release:
  - Karpenter: `github.com/aws/karpenter-provider-aws`
  - VPC CNI: `github.com/aws/amazon-vpc-cni-k8s`
  - AWS Load Balancer Controller: `github.com/kubernetes-sigs/aws-load-balancer-controller`
  - CoreDNS: `github.com/coredns/coredns`
  - EKS AMI: `github.com/awslabs/amazon-eks-ami`
  - EKS Terraform module: `github.com/terraform-aws-modules/terraform-aws-eks`
- When creating infrastructure, prefer infrastructure-as-code (Terraform with
  `terraform-aws-modules/terraform-aws-eks`, AWS CDK, or CloudFormation) over
  direct CLI commands.
- When working with infrastructure, follow AWS Well-Architected Framework
  principles.
- Do not use em dashes in AWS resource names or descriptions. Use
  hyphens instead.
