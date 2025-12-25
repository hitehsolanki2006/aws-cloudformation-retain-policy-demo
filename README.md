# 🛡️ Protecting Production Infrastructure from Accidental CloudFormation Deletion

Accidentally deleting critical infrastructure is not a beginner mistake —  
it’s a **real production risk** faced by engineers working with AWS CloudFormation in shared or live environments.

This repository documents a **real-world, practical workflow** to prevent that exact failure mode using native CloudFormation safeguards.

---

## 🚨 Why This Matters (The Real Problem)

By default, AWS CloudFormation tightly couples **stack lifecycle** with **resource lifecycle**.

That means:
- Delete the stack → delete the infrastructure
- No confirmation per resource
- No undo
- No safety net

In production or shared AWS accounts, this can lead to:
- EC2 termination
- Data loss
- Downtime
- Incident response escalations

This project exists to demonstrate how to **break that destructive coupling safely**.

---

## 🎯 What This Repository Demonstrates

This is NOT a theoretical example.

This repository shows a **real, tested workflow**:

1. Create a normal CloudFormation stack
2. Allow infrastructure to be created normally
3. Update the same stack to add retention policies
4. Delete the stack intentionally
5. Infrastructure remains alive and operational

This mirrors **how retention is applied in real organizations**, not toy demos.

---

## 🧠 Core Concept: Retention Policies

Two CloudFormation properties fundamentally change how infrastructure behaves:

```yaml
DeletionPolicy: Retain
UpdateReplacePolicy: Retain
