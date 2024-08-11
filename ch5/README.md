## 서비스

- yarn 실행
  kubectl create -f {yaml file}

- 서비스 조회
  kubectl get svc

- 컨테이너에 원격명령으로 서비스 테스트
  kubectl exec {pod name} -- curl -s {cluster ip}

- 환경변수 조회

  - KUBERNETES_SERVICE_HOST, KUBIA_SERVICE_PORT
    kubectl exec {pod name} env

- endpoint 조회
  kubectl get endpoints {service name}

# 외부에서 접근

## Node 정보

kubectl get nodes -o wide

## LB

- LB 정보

kubectl get svc {service name}

Test
curl http://{external ip}

## Ingress

- 조회
  kubectl get ingress

## ReadinessProbe

- 확인
  kubectl get pod {pod name}

## Headless

- service와 pod 확인
  kubectl get svc {service name}
  kubectl get pods -l {label key=value}

- Docker로 확인
  kubectl run -i --tty --rm dnsutils --image=tutum/dnsutils --restart=Never -- nslookup kubia-headless

## Commands

- Yarn file 내부 object 삭제
  kubectl delete -f {yaml file name}
