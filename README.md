# kubernetes 

## 1. 소개

docker와 kubernetes의 기본 기능을 알아보자.

### 참고 자료

- [도커(Docker)란 무엇인가?](https://subicura.com/2017/01/19/docker-guide-for-beginners-1.html)
- [쿠버네티스(Kubernetes)란 무엇인가?](https://subicura.com/2019/05/19/kubernetes-basic-1.html)

## 2. Docker 기본

- Docker 실습
- Docker Compose 실습


## 3. Kube 기본

- 기본 실습

### 마이크로 서비스 트래픽

- istio - bookinfo
```yaml
kubectl apply -f bookinfo/bookinfo-gateway.yaml
kubectl apply -f bookinfo/bookinfo.yaml
```

- 부하 발생
````yaml
watch curl -s -o /dev/null 192.168.137.240/productpage
````

#### Kiali traffic management

- Weighted Routing
: Reviews > Create Weighted : Update Weighted Routing

- Matching Routing
```yaml
samples/bookinfo/networking/virtual-service-reviews-test-v2.yaml
```
: haders > end-user > exact > annguk

#### Grafana dashboard(Querying Metrics from Prometheu)

````yaml
kubectl -n istio-system port-forward $(kubectl -n istio-system get pod -l app=grafana -o jsonpath='{.items[0].metadata.name}') 3000:3000
````

#### Horizontal Pod Autoscaler management

- Metrics Service 
``` yaml 
 kubectl -n kube-system top pods
 kubectl top pods
 kubectl top nodes 
 ```
- Sample 10m
``` yaml
kubectl apply -f  1-nginx-deployment.yaml
kubectl expose -n wizen deploy nginx-deploy --port 80 --type NodePort 
kubectl -n wizen get all -o wide
http://kworker1:32416

# Replica, cpu 설정
kubectl autoscale -n wizen deploy nginx-deploy --min 1 --max 5 --cpu-percent 20

# 부하
siege –q –c 5 –t 2m http://kworker1:32416


```
