# ☸️ K8S_LAB

Kubernetes 클러스터 구축, 컨테이너 런타임(CRI) 최적화, 네트워크(CNI) 및 패키지 매니저(Helm) 등 필수 컴포넌트 배포와 실무 운용을 체계적으로 다루는 실습형 저장소입니다.

---

## 📌 목표 및 목적 (Objectives)

- **클러스터 인프라 표준화**: `kubeadm`과 `containerd` 기반의 클러스터 초기화 및 Cgroup v2/SystemdCgroup 환경 표준 정립
- **네트워크 및 애드온 아키텍처 이해**: Calico CNI, MetalLB, Ingress Controller 등 클러스터 필수 컴포넌트의 연동 메커니즘 학습
- **애플리케이션 배포 및 패키징 자동화**: Helm Chart를 활용한 효율적인 인프라 패키지 관리 및 배포 실습
- **트러블슈팅 데이터베이스화**: CRI 소켓 연동, Master Taint 격리, HTTPS 인증서/보안 통신 이슈 등 실전 트러블슈팅 레퍼런스 축적

---

## 🖥️ 환경 정보 (Environment Specs)

| 구분 | 사양 / 버전 | 비고 |
| :--- | :--- | :--- |
| **OS** | Ubuntu 22.04 LTS (Linux) | 64-bit |
| **Kernel** | 5.15+ | Overlay & br_netfilter 모듈 로드 |
| **Orchestration** | Kubernetes `v1.32.x` | `kubeadm`, `kubelet`, `kubectl` |
| **Container Runtime (CRI)** | containerd `v1.7.x`+ | CRI v1, `SystemdCgroup = true` |
| **Pod Network (CNI)** | Project Calico `v3.28.x` | CIDR: `192.168.0.0/16` |
| **Package Manager** | Helm `v3.x` | 클러스터 애드온 및 앱 배포용 |
| **Management UI** | Kubernetes Dashboard `v2.6.x` | NodePort / HTTPS 통신 |

---

## 📂 프로젝트 구조 (Repository Structure)

각 디렉터리별 상세 가이드 및 매니페스트 파일은 해당 하위 폴더의 `README.md`를 참고합니다.

```text
K8S_LAB/
├── README.md                          # 전체 프로젝트 개요 및 환경 명세
├── 01_cluster_installation/           # 1. 클러스터 설치 및 초기 구성
│   ├── README.md                      # OS 사전작업, CRI(containerd) 설정, kubeadm init
│   └── scripts/                       # 초기화 및 커널 모듈 활성화 자동화 스크립트
├── 02_cni_networking/                 # 2. CNI 및 네트워크 구성
│   ├── README.md                      # Calico CNI 설치, CoreDNS 트러블슈팅, Pod CIDR 매핑
│   └── calico/                        # Calico 배포 YAML 파일
├── 03_addons_and_tools/               # 3. 필수 애드온 및 도구 설정
│   ├── 01_dashboard/                  # K8s Dashboard 설치, NodePort 노출, RBAC 토큰 발급
│   ├── 02_helm/                       # Helm v3 바이너리 설치 및 레포지토리 연동
│   └── 03_metrics_server/             # HPA 및 자원 모니터링용 Metrics Server 구성
├── 04_workloads_and_services/         # 4. 워크로드 및 서비스 배포 실습
│   ├── apps/                          # Nginx, StatefulSet, DB 실습 매니페스트
│   └── ingress/                       # Ingress Nginx / LoadBalancer 구성
└── 99_troubleshooting/               # 5. 이슈 해결 및 트러블슈팅 레퍼런스
    └── README.md                      # CRI rpc unimplemented, Taint, HTTPS 보안 경고 정리****
