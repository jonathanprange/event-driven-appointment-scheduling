# event-driven-appointment-scheduling
Event driven appointment scheduling is a sample project using FastAPI, MongoDB, AWS SNS/SQS, and Mandrill to create an asynchronous scheduling system. It uses clean code architecture and email notifications to ensure reliability and availability

```mermaid
sequenceDiagram
participant Client
participant API
participant Controller
participant Service
participant Event Mediator
participant SNS
participant SQS
participant Email Service
participant MongoDB

Client->>+API: Faz requisições HTTP
API->>+Controller: Encaminha requisições
Controller->>+Service: Aciona casos de uso
Service->>+MongoDB: Executa operações no banco
Service->>Event Mediator: Publica eventos
Event Mediator->>SNS: Publica eventos
SNS->>+SQS: Encaminha eventos
SQS->>-Email Service: Consome eventos
Email Service->>+Email Gateway: Dispara e-mails
Email Gateway-->>-Email Service: Confirma o envio
```