## importtent port number
```
DNS - 53
Tomocat -8080
jennkins - 8080
mysql -3306
postGreSQL -5432    
ssh -22
Rdp - 3389
ladap -389
prometheus -9090
grafana - 3000
sonarqube -9000
kubeapi server -6443
etcd -2379
kubelet -10250
Nodeportrange -30000 to 32767
kibana -5601
Elastic Search -9200
Redis -3679
```
## importent error codes
## 200 – Success
   - bakeend return valid respose 

## 401 – Unauthorized 
   - missing authentication token
   - expired JWT token
## 403 – Forbidden
  - No permission
  - iam role missing

404 – Not Found
## 500 – Internal Server Error
   - apps crashed
   - database connection failure
   - unhandled exceptions

## 502 – Bad Gateway
   - load balancer/proxy received invalid response from backend
   - pod crashed or pod restarting
   
## 503 – Service Unavailable
   - No healthy backend
   - application overload
   - Rediness probe failing
## 504 – Gateway Timeout
   - Database too slow
   - database query slow
   - network latery

## 429 – Too Many Requests
   - Rate limit exceeded
   - user sending two many request