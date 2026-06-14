# 🐳 Containers Load Balance — Ambiente de Testes

> ⚠️ **Este repositório é um ambiente de estudo/testes. Não utilize em produção.**

Orquestração de containers com **Docker Compose** simulando uma arquitetura web com balanceamento de carga.

## 🏗️ Arquitetura

| Container | Tecnologia     | Função                        |
|-----------|----------------|-------------------------------|
| `nginx`   | NGINX          | Load Balancer / Reverse Proxy |
| `web1`    | Apache2 + PHP  | Servidor de aplicação         |
| `web2`    | Apache2 + PHP  | Servidor de aplicação         |
| `web3`    | Apache2 + PHP  | Servidor de aplicação         |
| `db`      | MariaDB        | Banco de dados                |

O NGINX distribui as requisições entre os três servidores web utilizando o algoritmo **Least Connections**, garantindo que o servidor com menor carga receba as novas requisições. Todos os containers se comunicam em uma rede bridge isolada chamada `redelab`.

## 🚀 Como executar

Certifique-se de ter o **Docker** e o **Docker Compose** instalados.

```bash
docker compose up -d
```

Acesse a aplicação em: [http://localhost](http://localhost)

Para encerrar os containers:

```bash
docker compose down
```

## 📦 Imagens Docker Hub

As imagens utilizadas estão publicadas em:

- `b2rr0s/nginx:latest`
- `b2rr0s/web`
- `b2rr0s/db`

## 📌 Observações

- Ambiente criado para fins de aprendizado em DevOps
- Rede interna isolada: `redelab` (driver: bridge)
- O banco de dados é inicializado automaticamente com um dump SQL no startup
