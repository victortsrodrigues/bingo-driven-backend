# Bingo Driven - Backend

## Link deploy:
https://bingo-driven-backend-e27r.onrender.com

## Link repositório:
https://github.com/victortsrodrigues/bingo-driven-backend

## Execução com Docker:

### 1. Crie uma network:
Execute no terminal: docker network create NOMENETWORK

### 2. Crie um volume:
Execute no terminal: docker volume create NOMEVOLUME

### 3. Crie um container PostgreSQL:
Execute no terminal:
  docker run -d \ 
  --name NOMECONTAINERPOSTGRES \
  --network=NOMENETWORK \
  -e POSTGRES_PASSWORD=SUASENHAPOSTGRES \
  -p 5433:5432 \
  -v NOMEVOLUME:/var/lib/postgresql/data \
  postgres

### 4. Construa a imagem do container backend:
Execute no terminal: docker build -t mybackend .

### 5. Execute o container backend:
Execute no terminal:
  docker run -d \
  --name NOMECONTAINER \
  --network=NOMENETWORK \
  -e DATABASE_URL=postgressql://postgres:SUASENHAPOSTGRES@NOMECONTAINERPOSTGRES:5432/NOMEBANCODEDADOS?schema=public \
  -p 5000:5000 \
  mybackend

## Execução com Docker Compose:
### 1. Crie um arquivo .env com as variáveis de ambiente:
DATABASE_URL=
POSTGRES_PASSWORD=

### 2. Execute o comando docker-compose up -d para iniciar os containers:
Execute no terminal: docker compose up -d