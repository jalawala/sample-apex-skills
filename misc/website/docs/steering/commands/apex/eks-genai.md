---
title: "apex:eks-genai"
description: "Build, train, fine-tune, or serve a generative AI / LLM workload on Amazon EKS — walks the opinionated 6-layer stack (GPU vs Neuron, Karpenter scheduling, vLLM/Ray serving, distributed training, ML storage, GPU/Neuron observability, LiteLLM gateway) with a non-negotiable security baseline and cost levers. Use to design or stand up self-hosted GenAI on EKS."
custom_edit_url: https://github.com/aws-samples/sample-apex-skills/blob/main/steering/commands/apex/eks-genai.md
format: md
---

:::info[Source]
This page is generated from [steering/commands/apex/eks-genai.md](https://github.com/aws-samples/sample-apex-skills/blob/main/steering/commands/apex/eks-genai.md). Edit the source, not this page.
:::

<objective>
Run the APEX GenAI-on-EKS workflow — turn a team's GenAI/LLM workload goals into an opinionated, layer-by-layer Amazon EKS stack recommendation and build path.
</objective>

<execution_context>
@~/.claude/apex-steering/workflows/eks-genai.md
</execution_context>

<process>
Follow the eks-genai workflow end-to-end. Detect the user's mode from their message and route into the matching row of the workflow's "How to Route Requests" table. Use the `eks-genai` skill for the 6-layer stack, the GPU-vs-Neuron decision, the JARK + vLLM + LiteLLM canonical reference, KV-cache tiering, cost levers, and the security baseline. Phases: 1) workload scoping, 2) compute and cluster selection (Layers 1-2), 3) serving/training, storage, observability, gateway (Layers 3-6), 4) security baseline, cost, and build path.
</process>
