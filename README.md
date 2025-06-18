# ⚙️ Gensyn Node Setup Guide

> A simple and complete guide to running a Gensyn node | Verified by me ✅  
> By [@zarv](https://twitter.com/zarvxbt) | Early Web3 Contributor

---

## 📌 Prerequisites

- Linux VPS or bare metal (Recommended: Ubuntu 22.04)
- Minimum 4 CPU, 16 GB RAM, 200GB SSD
- Docker & Docker Compose installed

---

## 🛠️ 1. System Update & Docker Install

`bash
sudo apt update && sudo apt upgrade -y
sudo apt install docker.io docker-compose -y
sudo systemctl enable docker && sudo systemctl start docker

git clone https://github.com/gensyn-ai/peer-node.git
cd peer-node
