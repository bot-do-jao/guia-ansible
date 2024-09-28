# como instalar o ansible


## instalação

Para instalar o ansible, você pode seguir o [guia oficial](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html) ou seguir algum dos comandos abaixo:

## via pipx

```bash
pipx install --include-deps ansible
```

## via apt

```bash
sudo apt update
sudo apt install software-properties-common
sudo add-apt-repository --yes --update ppa:ansible/ansible
sudo apt install ansible
```

## via pacman

```bash
sudo pacman -S ansible
```

## via dnf

```bash
sudo dnf install ansible
```