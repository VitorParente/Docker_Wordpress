# Configuração do Ambiente WordPress com Docker Compose

Este projeto configura um ambiente web utilizando Docker Compose, integrando WordPress, Redis e Prometheus para monitoramento.

## Pré-requisitos

- Docker instalado e configurado no seu sistema.
- Docker Compose instalado.

## Instruções de Instalação

### Clone o Repositório

```bash
git clone https://github.com/VitorParente/Docker_Wordpress.git
```
##Configure o Docker Daemon
Edite o arquivo daemon.json para incluir as seguintes configurações:
```json
{
  "builder": {
    "gc": {
      "defaultKeepStorage": "20GB",
      "enabled": true
    }
  },
  "metrics-addr": "0.0.0.0:9323",
  "experimental": true
}
```
- Localize o arquivo em /etc/docker/daemon.json ou no diretório .docker do seu usuário.
- Reinicie o serviço Docker para aplicar as novas configurações:
```bash
sudo systemctl restart docker
```
## Inicialize os Containers
```bash
docker-compose up -d
```
Este comando inicia os serviços definidos no Docker Compose em segundo plano (-d)

# USO
## Acessando o WordPress
1. Abra o navegador e vá para http://localhost:8080.
2. Siga as instruções para configurar o WordPress inicialmente.

## Instalando/Ativando Plugins no WordPress
1. Faça login no painel de administração do WordPress com as credenciais configuradas durante a instalação.
2. No menu lateral, vá para Plugins > Adicionar Novo.
3. Pesquise por "Redis Object Cache".
4. Clique em Instalar Agora e depois em Ativar.

## Monitorando com Prometheus
1. Abra o navegador e vá para http://localhost:9090.
2. Utilize o Prometheus para monitorar e analisar métricas do ambiente.

## Agora o Ambiente esta pronto!

