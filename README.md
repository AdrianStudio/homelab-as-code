![Proxmox](https://img.shields.io/badge/Proxmox-9.1-E57000?logo=proxmox&logoColor=white)
![K3s](https://img.shields.io/badge/K3s-Kubernetes-FFC61C?logo=k3s&logoColor=white)
![Terraform](https://img.shields.io/badge/Terraform-IaC-7B42BC?logo=terraform&logoColor=white)
![Ansible](https://img.shields.io/badge/Ansible-Config-EE0000?logo=ansible&logoColor=white)
![ArgoCD](https://img.shields.io/badge/ArgoCD-GitOps-EF7B4D?logo=argo&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-CI-2088FF?logo=githubactions&logoColor=white)

# homelab-as-code

Source code for my entire homelab. Everything needed to build, configure and deploy the infrastructure from scratch.

Three layers, one repo:

- **Infrastructure** — Terraform creates VMs and LXCs on Proxmox
- **Configuration** — Ansible prepares the machines (packages, SSH, hardening)
- **Services** — Helm charts and manifests deploy apps on K3s via ArgoCD

---

## Hardware

| Node | Role | Specs |
|------|------|-------|
| EliteDesk 600 G2 | Proxmox master | i5-6500, 16GB RAM, 480GB SSD + 240GB SSD + 6TB HDD |
| ProDesk 400 G3 #1 | Proxmox worker | i5-7500T, 8GB RAM, 500GB HDD |
| ProDesk 400 G3 #2 | Proxmox worker | i5-7500T, 8GB RAM, 500GB HDD |

---

## Network

| Range | Purpose |
|-------|---------|
| 192.168.1.10x | Proxmox nodes |
| 192.168.1.11x | Infrastructure VMs |
| 192.168.1.12x | K3s cluster |
| 192.168.1.20x | Services (LXC) |

---

## Structure

```

homelab-as-code/
├── infra/proxmox/         # Terraform modules for Proxmox VMs/LXCs
├── ansible/
│   ├── inventory/         # Host definitions
│   └── playbooks/         # Base setup, hardening, K3s install
├── k8s/                   # Helm charts and manifests (created per service)
├── .github/workflows/     # CI pipelines
├── .gitignore
└── README.md

```

---

## Author

Adrian Tamargo — [GitHub](https://github.com/AdrianStudio) · [LinkedIn](https://linkedin.com/in/adrian-daniel-tamargo-miller-35a017355)
