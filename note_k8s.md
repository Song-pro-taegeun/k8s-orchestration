# k8s 셋팅 가이드(mac)

1. minikube 설치
   - $ brew install minikube
   - $ minikube version
2. minikube 실행

   - $ minikube start --driver=docker

3. kubectl 설치

   - $ brew install kubectl

4. docker-compose.yml / wordpress-k8s.yml 셋팅

   - https://subicura.com/k8s/guide/#%E1%84%8B%E1%85%AF%E1%84%83%E1%85%B3%E1%84%91%E1%85%B3%E1%84%85%E1%85%A6%E1%84%89%E1%85%B3-%E1%84%87%E1%85%A2%E1%84%91%E1%85%A9

<!-- -->

# kubernetes로 배포 실습

1. 클러스터 생성

   - $ kubectl apply -f wordpress-k8s.yml

   # 생성 클러스터 및 컴포넌트 리스트 확인

   - $ kubectl get all
   - wordpress-5f59577d4d-8t2dg와 pod/wordpress-mysql-545d9c6dc-dwnjp의 상태Status가 Running인지 확인하고 service/wordpress의 포트가 몇번인지 확인

2. minikube 접속

   - $ minikube service wordpres 실행으로 접속 또는
   - $ minikube ip 명령어로 얻은 주소 및 포트(kubectl get all 에서 service/wordpress 포트)로 접속
     - mac의 경우 위 방법이 정상적으로 진행되지 않는 현상이 발생한다.
     - 포트 포워딩을 하거나, minikube NodePort로 접근 $ minikube service wordpress
     - 127.0.0.1:랜덤포트 로 지정되어 실행이된다.

3. wordpress-k8s.yml 리소스 제거
   - $ kubectl delete -f wordpress-k8s.yml

wordpress 파일을 매니패스트 파일이라고 한다.
매니패스트 파일이란
Deployment / Service / pod 등을 관리해주는 파일이고
해당 파일에선 nginx pod 2개 / apache 1개 / tomcat 1개 구성했다.

nginx 파드는 둘 다 같은 서버 포트이다.
즉 서버는 동일한데, 파드가 다르다
이중화 가능하며 트래픽에 따라 적절히 로드밸런싱 처리를 해준다.
kubectl logs -f <파드명> 으로 확인 가능

<!-- - $ minikube tunnel -->

<!--
   # 참고 사이트
   [공식 사이트] https://subicura.com/k8s/
   [집중 블로그] https://velog.io/@pinion7/macOs-m1-%ED%99%98%EA%B2%BD%EC%97%90%EC%84%9C-kubernetes-%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0
 -->

# 대시보드

minikube dashboard

# minikube 상태확인

minikube status

# minikube 실행

minikube start

# 특정 k8s 버전 실행

minikube start --kubernetes-version=v1.23.1

# 특정 driver 실행

minikube start --driver=virtualbox --kubernetes-version=v1.23.1

# minikube ip 확인 (접속테스트시 필요)

minikube ip

# minikube 종료

minikube stop

# minikube 제거

minikube delete -->
