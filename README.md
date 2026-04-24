# Golang Node Notification Worker

## Objetivo
Processar notificações de forma assíncrona e desacoplada, evitando que a API bloqueie enquanto envia e-mails, push ou webhooks. A API recebe o evento, publica na fila e responde imediatamente; o worker consome a fila em segundo plano, aplicando retry em falhas transitórias.

## Stack
- Backend: Node.js (API produtora de eventos) e Go (worker consumidor)
- Frontend: não se aplica (projeto backend/mensageria)
- Banco: não se aplica (estado vive na fila; pode ser estendido para PostgreSQL/Redis)
- Cloud: Docker Compose (portável para AWS ECS, GCP Cloud Run ou Kubernetes)
- Testes: Jest (Node), testing nativo do Go

## Arquitetura
- Event-driven Architecture
- Producer/Consumer com RabbitMQ
- SOLID
- Clean Architecture (separação entre domínio, aplicação e infraestrutura)

## Funcionalidades
- Recebimento de eventos de notificação via API Node
- Publicação de mensagens em fila RabbitMQ
- Consumo assíncrono pelo worker em Go
- Retry simples em falhas de processamento
- Logs estruturados em produtor e consumidor
- Orquestração completa via Docker Compose

## Como executar
```
docker-compose up -d
```

## Prints
Adicionar imagens do painel do RabbitMQ e dos logs do worker processando mensagens.

## Aprendizados demonstrados
O projeto prova, tecnicamente, competência em arquitetura orientada a eventos e integração entre serviços escritos em linguagens diferentes. Mostra domínio de mensageria com RabbitMQ, construção de worker resiliente em Go, API produtora em Node.js, padrão producer/consumer com retry, logs estruturados para observabilidade e empacotamento com Docker Compose — fundamentos aplicáveis a cenários reais de alta carga e baixo acoplamento.
