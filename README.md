# Hi, I'm Tanay Thakare 👋

Final-year AI & Data Science student (B.E., 2027) aiming for a **Junior Cloud Security Validation Engineer** role.

I build tools that **attack containers on purpose**, check whether eBPF runtime sensors actually detect each attack, and **block a release** when they don't, across AWS and Azure.

## 🛡️ Featured projects

### 🚦 [Sensor Release Gate](https://github.com/TanayThakare-sov/sensor-release-gate)
A release-gate pipeline that installs an eBPF sensor on **4 Linux environments** (Ubuntu 22.04/24.04, Amazon Linux 2023, Azure) and blocks the release if any install, detection, observability or overhead check fails.
- Detection checks for `execve`, `openat` and `connect`, plus CPU/memory overhead under a **1,500-process load** with a **25% regression limit** against a stored baseline
- AWS and Azure test matrix provisioned with **Terraform** (SSH locked to operator IP, IMDSv2, encrypted volumes)
- Sensor deployed as a **Kubernetes DaemonSet** with health probes, **21 unit tests**, a GitHub Actions gate workflow and a provisioned **Grafana** dashboard
`Python · eBPF · Terraform · AWS · Azure · Kubernetes · Grafana · GitHub Actions`

### 📊 [eBPF Detection Coverage Scorecard](https://github.com/TanayThakare-sov/ebpf-detection-coverage-scorecard)
Runs **MITRE ATT&CK-mapped** attack techniques inside a container and reports which ones a custom eBPF sensor (and optionally **Falco**) detected or missed.
- Per-run token and log-offset method so a detection only counts if *that run's* attack caused it, which prevents false passes
- Techniques defined in **YAML**, so adding one needs no code change
- Honest scorecard with a deliberate known gap (custom sensor: **4 of 5 techniques, 80%**), run through both `docker exec` and `kubectl exec`, with metrics exported to Prometheus and Grafana
- AWS VPC and EC2 host via Terraform (validation rejects `0.0.0.0/0` SSH) and CI for lint, unit tests and `terraform validate`
`Python · bpftrace · Docker · Kubernetes · Terraform · Falco · Grafana`

### ✅ [Runtime Detection Validator](https://github.com/TanayThakare-sov/Runtime-Detection-Validator)
An automated test framework that attacks a Docker container (shell spawn, `/etc/shadow` read, outbound connection) and verifies an eBPF sensor detected each one, with clear pass/fail results.
- Log-position marker, unique tokens per test and in-kernel filtering of `openat` to sensitive paths to avoid false passes
- Safe TEST-NET address (`203.0.113.10`) for connection tests
- Unit tests that run anywhere (including CI) separated from root-only integration tests using pytest markers
`Python · pytest · bpftrace · Docker · GitHub Actions`

## 🛠 Tech stack
**Security & kernel:** eBPF (bpftrace), MITRE ATT&CK, runtime detection, Falco, syscalls
**Cloud & IaC:** AWS (EC2, VPC, Security Groups, IMDSv2), Azure (VM, NSG), Terraform
**Containers & CI/CD:** Docker, Kubernetes (DaemonSet, probes, kind), GitHub Actions
**Monitoring:** Prometheus, Grafana
**Languages:** Python, Bash, SQL, C, C++, JavaScript
**AI/ML:** PyTorch, scikit-learn, XGBoost, LangGraph, RAG, LoRA/PEFT

## 🤖 Other projects
- [FlightMail-SLM](link): LoRA fine-tuned Qwen2.5-0.5B for extracting booking details from airline emails (45.5% vs 31.5% regex baseline)
- [Ask-My-Business](link): text-to-SQL analyst agent with a safety guard and self-repair
- [Annual Report Red-Flag Detector](link): RAG agent with page-cited findings

## 📫 Connect
[LinkedIn](your-link) · tanaythakare2209@gmail.com
