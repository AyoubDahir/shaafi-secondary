# shaafi-secondary

GitOps (ArgoCD) for the shaafi ERPNext **secondary/DR site** HA cluster (K3s).

Deliberately decoupled from `AyoubDahir/shaafi` (the live production repo) — see
`erpnext-gitops/apps/*.yaml` comments for why. Reuses the same custom ERPNext image
(`ghcr.io/ayoubdahir/shaafi-custom`) the production repo builds; this repo has no
build pipeline of its own, only deployment manifests.
