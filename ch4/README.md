## Liveness Probe

컨테이너가 살아 있는지 확인하고 실패하면 다시 시작

### 쿠버네티스에서 healthcheck

- 스타트업 프로브: 아래 두개 수행 전 사전 체크 -> 파드 재시작
- 라이브니스 프로브: 일시적 서비스 상태 체크 -> 서비스 Object 연결 대상 제외
- 레디니스 프로브: 지속적인 상태 체크 -> 파드 재시작하여 복구 시도

```bash
# 생성
kubectl create -f liveness-probe.yaml
# 조회
kubectl get pod {pod name}
# 삭제 사유
kubectl describe po {pod name}
```

## Replica Controller

리소스로서 파드가 항상 실행되도록 보장하여 교체 파드를 생성

### RC 3가지 요소

- spec.selector: RC 범위 파드 결정
- spec.replicas: 파드 수 결정
- spec.template: 새로운 파드 레플리카 정의 결정

```bash
# 생성
kubectl create -f rc.yaml
# 삭제
kubectl delete po {pod name}
# pods 조회
kubectl get pods
# rc 조회
kubectl get rc
# label 생성
kubectl label pod {pod name} {label key=value}
# label 속성 추가 (-o wide 자세한 정보)
kubectl get pods --show-labels
# label 속성 변경(-> 여기서는 app을 바꿔서 rc가 관리안하도록)
kubectl label pod {pod name} app={value} --overwrite
# pod tempalte 변경
kubectl edit rc {rc name}
# scale만 변경
kubectl scale rc {rc name} --replicas={갯수}
# 삭제(--cascade=false 옵션 주면 rc만 삭제)
kubectl delete rc {rc name} --cascade=false
```

## Replica Set

레플리케이션컨트롤러 + 파드 셀렉터(more expressions)

```bash
# 생성
kubectl create -f replicaset.yaml
# 조회
kubectl get rs
# 삭제
kubectl delete rs {rs name}
```

## Daemon Set

파드의 타깃 노드가 지정, 스케줄러 스킵

```bash
# 생성
kubectl create -f replicaset.yaml
# 조회
kubectl get rs
# 삭제
kubectl delete rs {rs name}
```

## Job

한번 실행되고 종료되는 태스크

```bash
# 생성
kubectl create -f job.yaml
# 조회
kubectl get jobs
```

## CronJob

반복실행

```bash
# 생성
kubectl create -f cronJob.yaml
# 조회
kubectl get jobs
```

## Commands

```bash
# 생성
kubectl create -f {yaml file}
# 삭제
kubectl delete -f {yaml file}
kubectl delete po -f {yaml file}
kubectl delete po {pod name}
kubectl delete pods -l {label key=value}
kubectl delete rc {rc name}
kubectl delete rs {rs name}
# 수정
kubectl apply -f {yaml file}
kubectl edit rc {rc name}
# 조회
kubectl get node
kubectl get pods
kubectl get rc
kubectl get rs
kubectl get ds
```
