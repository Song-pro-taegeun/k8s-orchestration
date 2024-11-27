# kubernetes로 배포 실습

1. 클러스터 생성

   - $ kubectl apply -f wordpress-k8s.yml

   # 생성 클러스터 및 컴포넌트 리스트 확인

   - $ kubectl get all
   - $ kubectl get services
   - 위 명령어 입력 시 External-Ip 가 Pending 또는 none으로 보일 것이다.
   - 이 경우 외부로 서비스 IP를 노출시켜줘야한다.

2. 대시보드 접속

   - $ minikube dashboard

3. 외부로 서비스 IP 노출

   - $ minikube tunnel
   - $ kubectl get services
     ![alt text](pj-minikube/image/work1_runnig_service.png)

4. 해당 IP와 포트로 운영중인 서비스 접근

   - ex: 127.0.0.1:9001

5. 본인은 현재 nginx의 한개의 서비스에서 2개의 pod를 2개 구동하고 있다.

   - 왜 두개의 파드를 구축했는가?
     - 한 서비스에서 트래픽에 따른 로드밸런싱을 테스트 해보기 위함으로 두개의 파드를 구축해보았다.
       - 정상적인 로드밸런싱 처리가 가능한가?
     - 비정상적인 종료 테스팅을 위해 두개의 파드를 구축해보았다(이중화).
       - 비정상적인 종료 시 별도의 에러 없이 다른 파드로 로드밸런싱 처리가 되는가?

6. pod별 log 확인

   - $ kubectl get pod로 확인된 파드 Name으로 로그를 확인하자.
     - ![alt text](pj-minikube/image/work1_running_pod_list.png)
     - kubectl logs -f <파드명> 으로 nginx 두 개의 파드의 로그를 실시간으로 확인한다.
     - 127.0.0.1:9001 로 접속 시 트래픽 및 상황에 따라 두개의 파드로 적절히 배분되는게 확인된다.

7. 미니큐브 종료

   - $ minikube stop

8. wordpress-k8s.yml 리소스 제거

   - $ kubectl delete -f wordpress-k8s.yml

###

wordpress 파일을 매니패스트 파일이라고 한다.
매니패스트 파일이란
Deployment / Service / pod 등을 관리해주는 파일이고
해당 파일에선 nginx pod 2개 / apache 1개 / tomcat 1개 구성했다.

nginx 파드는 둘 다 같은 서버 포트이다.
즉 서버는 동일한데, 파드가 다르다
이중화 가능하며 트래픽에 따라 적절히 로드밸런싱 처리를 해준다.
kubectl logs -f <파드명> 으로 확인 가능

###
