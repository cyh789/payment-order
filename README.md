[Client]
    |
[API Gateway / ALB]
    |
[Order Service] ---(Kafka)---> [Payment Service]
    |                               |
  (Redis) <---(Pub/Sub)--- [Notification Service]
    |
(PostgreSQL RDS)


- 모든 서비스는 Spring Boot + JPA 기반

- Kafka: 주문 이벤트 전송 (OrderPlaced → PaymentUpdated)

- Redis: 주문 상태 캐싱 및 실시간 알림

- AWS: EC2, RDS(Postgres), S3(주문 첨부파일), CloudWatch 로그
