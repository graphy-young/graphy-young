> Container Orchestration Platform, 컨테이너화된 애플리케이션을 자동으로 배포, 확장, 관리하기 위한 오픈소스 플랫폼

## Architecture
```
Control Plane
+----------------+      +----------------+       +----------------+
|   API Server   |<---->|    etcd        |<----->|   Scheduler    |
+----------------+      +----------------+       +----------------+
                                   ^
                                   |
                                   v
                              +----------------+
                              | Controller     |
                              | Manager        |
                              +----------------+
                                   ^
                                   |
                                   v
                         +------------------------+
                         |      Worker Nodes      |
+----------------+      +----------------+       +----------------+
|     Kubelet    |<---->|  Container     |<----->|   Kube-Proxy   |
|                |      |  Runtime       |       |                |
+----------------+      +----------------+       +----------------+
```
### Control Plane (Master Node)
- **API 서버**: 관리 작업을 위한 모든 REST 명령어의 엔트리 포인트
- **etcd**: 구성 데이터를 위한 키-값 저장소
- **스케줄러**: 리소스 가용성을 기반으로 컨테이너를 배치
- **컨트롤러 매니저**: 노드 컨트롤러, 복제 컨트롤러 등 다양한 컨트롤러를 관리
### Worker Node
- **Kubelet**: 각 노드에서 실행되는 에이전트로 마스터 노드와 통신
- **컨테이너 런타임**: 컨테이너를 실행하는 소프트웨어, 예를 들면, Docker, containerd
- **Kube-Proxy**: 네트워크 트래픽을 관리
- 주요 원리
    - **선언적 구성**: Kubernetes는 사용자가 애플리케이션의 상태를 "선언"하고, 시스템이 그 상태를 유지하도록 함
    - **자동화된 스케줄링**: 노드(서버)에 컨테이너를 효율적으로 배포
    - **자동 스케일링**: 리소스 사용률에 따라 애플리케이션의 인스턴스 수를 자동으로 조정
    - **자동 복구**: 실패한 컨테이너를 자동으로 다시 시작하거나, 예상치 못한 오류를 자동으로 복구
### Raft Algorithm for High availability
- [Kubernetes 운영을 위한 etcd 기본 동작 원리의 이해 (Kakao)](https://tech.kakao.com/2021/12/20/kubernetes-etcd/)
- [Simple Leader Election with Kubernetes and Docker (GitHub)](https://github.com/kubernetes-retired/contrib/tree/master/election)