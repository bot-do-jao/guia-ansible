
# Parte Prática do Povo

## Explicando a Atividade

Nesta atividade prática, vocês vão rodar um playbook do Ansible que fará duas coisas:

1. **Modificar um Arquivo Existente**: O playbook vai adicionar uma linha ao final de um arquivo já existente, contendo a mensagem personalizada: `"pessoa chegou até aqui"`, onde `pessoa` é uma variável que vocês devem passar como parâmetro ao rodar o playbook.
2. **Copiar o Arquivo**: Antes de modificar, o playbook vai copiar o arquivo original para um novo arquivo na mesma pasta. Isso garantirá que cada aluno tenha seu próprio arquivo modificado, evitando conflitos.

### O Desafio:

1. Escolha um nome ou apelido para a variável `pessoa` e também para o arquivo destino que será copiado.
2. Utilize o comando de ping para testar a conectividade com a máquina `vm1` (usada para esta prática).
3. Altere o nome do arquivo de destino dentro do playbook para o nome que você escolheu.
4. Execute o playbook fornecido passando a variável `pessoa`.



Vamos começar com um comando simples para que todos possam se habituar ao uso do Ansible e verificar a conectividade com a máquina.

### Comando de Ping

```bash
ansible vm1 -i ../parte1/inventario/inventory.yaml -m ping --ask-pass
```

- Certifique-se de que todos possam rodar esse comando com sucesso antes de continuar para o próximo passo. Se o comando retornar `pong`, a máquina está acessível e pronta para receber comandos do Ansible.

## Criando e Modificando Arquivo na Máquina

Agora vamos rodar o playbook que realiza as tarefas descritas acima.


Nele iremos explorar uma das formas de parametrizar um playbook, passando uma variável dentro do proprio playbook.


Disponivel dentro da pasta playbook, iremos trocar o nome do arquivo de destino e a mensagem que será adicionada ao arquivo.


### Executando o Playbook

Para rodar o playbook com o nome de sua escolha, utilize o seguinte comando:

```bash
ansible-playbook -i ../parte1/inventario/inventory.yaml  playbook/troca-arquivo.yaml -e "pessoa=SeuNome" --ask-pass --ask-become-pass
```

- Substitua `SeuNome` pela variável que você quer passar. Por exemplo, `ansible-playbook -i ../parte1/inventario/inventory.yaml  playbook/troca-arquivo.yaml -e "pessoa=Joao"`.

### Verificando o Resultado

Após executar o playbook, verifique o arquivo gerado na máquina `vm1` para garantir que a linha personalizada foi adicionada com sucesso.

```bash
ansible vm1 -i ../parte1/inventario/inventory.yaml  -m shell -a "cat ~/vcs.txt"
```

- O comando acima exibirá o conteúdo do arquivo `vcs.txt` na máquina `vm1`. Novamente, lembre de passar o nome que você nomeou o arquivo nesse comando.