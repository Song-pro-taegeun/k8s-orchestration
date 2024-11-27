# k8s-orchestration

# minikube란?

- Minikube는 단일 노드 Kubernetes 클러스터를 로컬 컴퓨터에 생성하여 빠르게 테스트할 수 있도록 도와주는 도구
- Minikube는 Kubernetes의 핵심 기능(서비스, 포드, 디플로이먼트 등)을 완전히 지원하며, Ingress, LoadBalancer, Persistent Volume과 같은 추가 기능도 사용할 수 있다.

# kubectl란?

- Kubernetes를 관리하기 위한 CLI 도구

# k8s 셋팅 가이드(mac)

1. minikube 설치

   - $ brew install minikube
   - $ minikube version

2. minikube 실행(컨테이너 생성)

   - $ minikube start --driver=docker

3. kubectl 설치

   - $ brew install kubectl

4. docker-compose.yml / wordpress-k8s.yml 셋팅

   - 본 프로젝트의 셋팅 파일을 참조한다. 본 프로젝트는 minikube를 통한 워드프레스 테스트이므로 도커 컴포즈는 참조만 한다.

# 참고 사이트

[공식 사이트] https://subicura.com/k8s/
[집중 블로그] https://velog.io/@pinion7/macOs-m1-%ED%99%98%EA%B2%BD%EC%97%90%EC%84%9C-kubernetes-%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0

- minikube 설치(window)
- https://kk-7790.tistory.com/130
- kubectl 설치(window)
- https://kubernetes.io/ko/docs/tasks/tools/install-kubectl-windows/

# minikube 명령어

1. 대시보드

- $ minikube dashboard

2. minikube 상태확인

- $ minikube status

3. minikube 실행

- $ minikube start

4. 특정 k8s 버전 실행

- $ minikube start --kubernetes-version=v1.23.1

5. 특정 driver 실행

- $ minikube start --driver=virtualbox --kubernetes-version=v1.23.1

6. minikube ip 확인 (접속테스트시 필요)

- $ minikube ip

7. minikube 종료

- $ minikube stop

8. minikube 제거

- $ minikube delete
