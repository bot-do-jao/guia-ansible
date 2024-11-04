
# Introdução ao Ansible

## O que é Ansible?

O Ansible é uma ferramenta open-source de automação de TI que permite a automação de provisionamento, gerenciamento de configurações, implantação de aplicativos e muitas outras tarefas. Ele usa uma linguagem de configuração simples e baseada em YAML chamada Playbook, que descreve a automação de forma clara e compreensível.

### Características Principais:

O Ansible é agentless, ou seja, não requer a instalação de agentes nas máquinas gerenciadas, pois a comunicação é realizada via SSH. Ele também garante que as operações sejam executadas apenas quando necessário, evitando mudanças desnecessárias no sistema. Além disso, o Ansible se destaca pela sua simplicidade, sendo fácil de aprender e usar, com uma sintaxe baseada em YAML que é intuitiva e legível.

Para mais detalhes, você pode consultar a [documentação oficial](https://docs.ansible.com/ansible/latest/getting_started/index.html).

## Configuração Inicial

Antes de começar a utilizar o Ansible, é necessário criar um arquivo de inventário que liste os hosts (máquinas) que serão gerenciados. Vamos configurar um arquivo de inventário básico com três máquinas virtuais. Esse arquivo está disponivel na pasta inventario, e foi feito em formato yaml mas existem outros padrões de formato.

No caso, estamos usando um servidor ssh presente na pasta ../VMs para realizar a conexão com as máquinas virtuais.

Com isso, siga para essa pasta e execute o tutorial.

Após ele, com os IPs anotados, atualizemos o arquivo de inventário.



## Comandos Básicos do Ansible

Vamos explorar alguns comandos básicos para verificar a conectividade e gerenciar as máquinas do inventário.

### 1. Testando a Conectividade com `ping`

```bash
ansible lappis -i inventario/inventory.yaml -m ping --ask-pass
```

- Este comando utiliza o módulo `ping` do Ansible para verificar se todas as máquinas no grupo `lappis` estão acessíveis.

### 2. Instalando e Ativando o Nginx

```bash
ansible lappis -i inventario/inventory.yaml -m apt -a "name=nginx state=present" --ask-pass --ask-become-pass --become --become-method=su
```

- O módulo `apt` é usado para instalar o pacote `nginx` em todas as máquinas.
- A opção `state=present` garante que o pacote esteja instalado.
- O `--become` permite que o comando seja executado com privilégios elevados (similar ao `sudo`).

### 3. Copiando um Arquivo HTML para uma Máquina Específica

```bash
ansible vm1 -i inventario/inventory.yaml -m copy -a "src=html/hello.html dest=/var/www/html/index.html" --ask-pass --ask-become-pass --become --become-method=su
```

- Este comando usa o módulo `copy` para transferir o arquivo `hello.html` para o diretório web de uma única máquina (`vm1`).


## Explorando Módulos do Ansible

O Ansible possui uma grande variedade de módulos que permitem realizar diversas tarefas. Os módulos estão organizados em coleções e podem ser encontrados na [documentação oficial de módulos do Ansible](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/index.html#plugins-in-ansible-builtin).

Aqui estão alguns módulos úteis:

- **ping**: Verifica a conectividade.
- **apt**: Gerencia pacotes em sistemas baseados em Debian.
- **yum**: Gerencia pacotes em sistemas baseados em RedHat.
- **copy**: Copia arquivos para hosts gerenciados.
- **file**: Gerencia propriedades de arquivos e diretórios.
- **service**: Gerencia serviços no sistema operacional.

