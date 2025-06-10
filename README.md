# 📘 Documentação do Projeto **MicroMES**

**MicroMES** é um sistema simplificado de execução de produção (MES) baseado em microsserviços, com coleta de dados de máquinas, registro de ordens de produção e consulta de status em tempo real.

---

## 🚀 Tecnologias e Arquitetura

### 🧱 Arquitetura

| Camada                                 | Descrição                                                                    |
| -------------------------------------- | ---------------------------------------------------------------------------- |
| **API Gateway**                        | Porta de entrada única. Faz roteamento para os serviços, validação de token. |
| **Microsserviço 1**: `auth-service`    | Cadastro e autenticação de usuários via JWT.                                 |
| **Microsserviço 2**: `order-service`   | Criação e consulta de ordens de produção.                                    |
| **Microsserviço 3**: `machine-service` | Simulação/recebimento de dados de máquina (via Kafka).                       |
| **Microsserviço 4**: `monitor-service` | Consome dados do Kafka e exibe métricas/processa status.                     |

### 🧰 Tecnologias

| Componente          | Stack                            |
| ------------------- | -------------------------------- |
| Linguagem backend   | NestJS (Typescript)              |
| Comunicação         | Apache Kafka                     |
| Proxy Reverso       | NGINX                            |
| Validações          | Zod                              |
| ORM                 | Prisma                           |
| Banco de dados      | PostgreSQL                       |
| Containerização     | Docker, Docker Compose           |
| Autenticação        | JWT                              |
| Testes automatizados| Jest                             |


---

## ✅ 1. Requisitos

### Funcionais

| ID   | Título                          | Descrição                                                                |
| ---- | ------------------------------- | ------------------------------------------------------------------------ |
| RF01 | Cadastrar usuário               | Um novo operador pode se registrar no sistema.                           |
| RF02 | Autenticar usuário              | Operador realiza login e recebe token de acesso.                         |
| RF03 | Criar ordem de produção         | Um operador autorizado cria uma nova ordem para uma máquina.             |
| RF04 | Enviar dados da máquina (Kafka) | O serviço da máquina envia eventos (temperatura, status etc.) via Kafka. |
| RF05 | Processar dados da produção     | Serviço de monitoramento consome eventos e atualiza status da ordem.     |

### Não Funcionais

| ID    | Título           | Descrição                                                           |
| ----- | ---------------- | ------------------------------------------------------------------- |
| RNF01 | Manutenabilidade | Uso de Clean Architecture nos microsserviços.                       |
| RNF02 | Usabilidade      | API RESTful clara, com documentação via Swagger.                    |
| RNF03 | Escalabilidade   | Microsserviços separados, escaláveis horizontalmente.               |