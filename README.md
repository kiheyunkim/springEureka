# springEureka
spring eureka with replication


#replication 설정 방법

host 파일에 다음과 같이 구성한다.
```
#/etc/hosts
{other instance ip} {other instance eureka.instance.hostname}

#ex)
127.0.0.1 eureka-cluster-8761
127.0.0.1 eureka-cluster-8762
```

eureka.client.service-url.defaultZone에 replication을 구성할 peer들의 주소를 등록해준다
```yaml
eureka:
  client:
    service-url:
      defaultZone: http://eureka-cluter-${peer.port}/eureka

#ex) eureka-cluster-8761 기준
eureka:
  client:
    service-url:
      defaultZone: http://eureka-cluter-8762/eureka
```