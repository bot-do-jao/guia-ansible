
# Guia de Configuração de Servidor SSH com Docker para Ansible

Este documento ensina como configurar e utilizar servidores SSH em containers Docker, que serão usados como "VMs" para testes com Ansible. Aqui, configuramos dois servidores SSH simulando VMs que podem ser gerenciadas via Ansible.

---

## Configurando os Servidores SSH com Docker


## Passos para Subir o Ambiente

1. **Abra o terminal** e navegue até o diretório onde estão os arquivos `Dockerfile` e `docker-compose.yml`.

2. **Suba os containers com o Docker Compose:**
   ```bash
   docker-compose up -d
   ```
   O comando acima cria e executa os containers em segundo plano (modo "detached").

3. **Verifique se os containers estão rodando:**
   ```bash
   docker ps
   ```
   Você deve ver os containers `insecure_ssh_server00` e `insecure_ssh_server01` listados como em execução.

---

## Obtendo o IP dos Servidores SSH

Para que o Ansible possa se conectar às "VMs" (containers), você precisará do IP de cada container.

### Obtendo o IP de um Container

Use o seguinte comando para obter o IP de cada container:

```bash
docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' nome_do_container
```

- **Para o container `ssh00`:**
  ```bash
  docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' insecure_ssh_server00
  ```

- **Para o container `ssh01`:**
  ```bash
  docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' insecure_ssh_server01
  ```

Esses comandos irão retornar o IP interno de cada container na rede Docker.

---

## Conectando-se aos Servidores SSH

### Opção 1: Conectando Usando o IP do Container

Após obter o IP do container, você pode se conectar via SSH usando:

```bash
ssh root@<IP_do_container>
```

- **Usuário:** `root`
- **Senha:** `senha`



---

## Usando os Servidores SSH com Ansible

Agora que os servidores SSH estão configurados, você pode usá-los como hosts gerenciados em seu inventário Ansible. Adicione os IPs ou portas em seu arquivo de inventário e configure seus playbooks conforme necessário.

---

Pronto! Com isso, você tem um ambiente configurado para testar playbooks do Ansible com servidores SSH em containers Docker.
