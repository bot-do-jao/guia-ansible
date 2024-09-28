
# Aula Avançada: Evoluindo para Playbooks

## O que é um Playbook?

No Ansible, um **Playbook** é um arquivo YAML que descreve um conjunto de tarefas de automação a serem executadas em hosts ou grupos de hosts específicos. Ele oferece uma maneira mais estruturada e repetível de definir operações complexas em comparação aos comandos ad-hoc, permitindo que você organize tarefas em sequências lógicas e controladas.

### Principais características de um Playbook:
- **Idempotência**: As tarefas são executadas apenas se necessário, evitando mudanças desnecessárias.
- **Modularidade**: Permite dividir configurações e procedimentos complexos em tarefas menores e reutilizáveis.
- **Legibilidade**: Utiliza a sintaxe YAML, que é fácil de ler e escrever.

Playbooks podem conter múltiplos "plays", onde cada "play" aplica tarefas a um grupo de hosts definido. Para saber mais sobre Playbooks, consulte a [documentação oficial](https://docs.ansible.com/ansible/latest/user_guide/playbooks.html).

## Convertendo Ações em um Playbook

Agora vamos transformar as ações executadas anteriormente (ping, instalação do Nginx e criação de arquivo HTML) em um único Playbook.

Para isso, visualize o arquivo `site.yaml` na pasta `playbook`


## Executando o Playbook

Para executar este playbook, basta utilizar o seguinte comando:

```bash
ansible-playbook -i ../parte1/inventario/hosts.yaml site.yaml
```

Isso aplicará todas as tarefas definidas no playbook às máquinas listadas no arquivo de inventário `hosts`.



Com isso, você aprendeu a transformar comandos ad-hoc em um playbook organizado e reutilizável! Se precisar de mais ajuda, consulte a documentação oficial ou pratique com diferentes módulos e configurações.

