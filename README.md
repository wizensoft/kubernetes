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
kubectl apply -f samples/bookinfo/networking/bookinfo-gateway.yaml
kubectl apply -f samples/bookinfo/platform/kube/bookinfo.yaml
```

- 부하 발생
watch curl -s -o /dev/null 192.168.137.240/productpage

#### Kiali traffic management

- Weighted Routing
: Reviews > Create Weighted : Update Weighted Routing

- Matching Routing
```yaml
samples/bookinfo/networking/virtual-service-reviews-test-v2.yaml
```
: haders > end-user > exact > annguk

#### Horizontal Pod Autoscaler management

- Metrics Service 
``` yaml 
 kubectl -n kube-system top pods
 kubectl top pods
 kubectl top nodes 
 ```

