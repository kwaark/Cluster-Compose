# DevOps Challenge

Este repositório contém os componentes necessários para construir e executar uma aplicação que consiste em uma API REST e um Worker Assíncrono, ideal para simular um ambiente de produção com várias dependências.

## Descrição

Breve descrição do que cada componente faz:

- **API REST**: Descreva o propósito da sua API, os endpoints disponíveis e exemplos de como usá-la.
- **Worker Assíncrono**: Descreva como o Worker funciona, o que ele processa e como ele interage com a API REST.

## Pré-Requisitos

Antes de começar, certifique-se de ter instalado:

- Docker: [Instruções de instalação](https://docs.docker.com/get-docker/)
- Docker Compose: [Instruções de instalação](https://docs.docker.com/compose/install/)

## Configuração e Instalação

Para configurar e instalar a aplicação, siga estes passos:

1. Clone o repositório para a sua máquina local.
2. Navegue até o diretório que contém o arquivo `docker-compose.yml`.
3. Execute o comando abaixo para iniciar todos os serviços em modo detached e construir as imagens se necessário:
4. A flag `--build` é importante porque ela força o Docker a construir as imagens novamente, considerando as mudanças que você fez no código dos serviços.

```bash
sudo docker-compose up -d --build
```

## Uso

Após a instalação, os serviços estarão disponíveis nos seguintes endereços:

- **API REST**: `http://localhost:8000`
- **Kafka**: Internamente acessível pelos serviços no `kafka-network`

## Comandos Úteis

- Iniciar serviços: `sudo docker-compose up -d`
- Parar serviços: `sudo docker-compose stop`
- Ver logs de serviços: `sudo docker-compose logs -f [service_name]`

## Manutenção

Para parar e remover todos os containers, bem como redes e volumes não nomeados associados, use o comando:

```bash
sudo docker-compose down
```

## Monitoramento e Logs

Para monitorar os serviços e ver os logs em tempo real, utilize:

```bash
sudo docker-compose logs -f
```

Adicione o nome do serviço no final para logs específicos de um serviço.

## Troubleshooting

- **Erro com Kafka**: Se você encontrar erros relacionados ao Kafka, como `CoordinatorNotAvailableError`, geralmente isso significa que o Kafka ainda não está totalmente inicializado quando o Worker tenta se conectar. Isso pode ser resolvido assegurando que o Kafka esteja saudável antes de iniciar o Worker, ou implementando um mecanismo de retentativa na conexão do Worker.

## Contribuições

Contribuições são bem-vindas! Para contribuir, por favor, faça um fork do repositório, crie uma branch para suas mudanças e submeta um Pull Request.
