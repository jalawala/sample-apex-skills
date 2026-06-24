# EKS Guidance

- Before starting an EKS task, check whether a relevant APEX skill is
  available. Load the skill and prefer its guidance over general knowledge.
- When uncertain about specific EKS details (add-on versions, API parameters,
  Karpenter behavior, VPC CNI settings), verify against upstream source repos
  rather than guessing. State uncertainty explicitly if you cannot confirm.
- When providing version-specific guidance, cross-reference the upstream repo
  to confirm the behavior still holds in the current release:
  - Karpenter: `github.com/aws/karpenter-provider-aws`
  - VPC CNI: `github.com/aws/amazon-vpc-cni-k8s`
  - AWS Load Balancer Controller: `github.com/kubernetes-sigs/aws-load-balancer-controller`
  - CoreDNS: `github.com/coredns/coredns`
  - EKS AMI: `github.com/awslabs/amazon-eks-ami`
  - EKS Terraform module: `github.com/terraform-aws-modules/terraform-aws-eks`
- When creating infrastructure, prefer Terraform with
  `terraform-aws-modules/terraform-aws-eks` unless the team has an established
  CDK or CloudFormation pattern.
- When working with EKS infrastructure, follow AWS Well-Architected Framework
  principles.
