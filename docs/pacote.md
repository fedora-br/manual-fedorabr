# Gerenciamento de Pacotes
## Procurar por pacotes que contenham um arquivo específico

### Através do dnf provides
```
$ dnf provides /usr/bin/play
```
ou
```
$ dnf provides *play
```

Com o provides é retornado o nome do repositório, o resumo da descrição do pacote e se ele está instalado no sistema "@system".

### Através do repoquery

#### Listar os arquivos contidos em um pacote:
Sintaxe: $ dnf repoquery -l nome-do-pacote

Exemplo:
```
$ dnf repoquery -l python3-pycparser
```

#### Listar o pacote que é dono do arquivo
Sintaxe: dnf repoquery -f caminho-absoluto-do-arquivo/arquivo

Exemplo:
```
dnf repoquery -f /usr/bin/bash
```

## Listar os arquivos intalados por um rpm:
```
rpm -ql hda-bb-0.1-1.noarch
```

## Listar todos os pacotes de um repositório específico:
Sintaxe: $ sudo dnf repo-pkgs nome-do-repositório list available

```
sudo dnf repo-pkgs folkswithhats list available
```

available para disponíveis ou installed para instalados

## Listar os pacotes instalados de um repositório:
Sintaxe: $ sudo dnf repo-pkgs nome-do-repo list installed

### Baixar um pacote sem instalá-lo:
Sintaxe: $ dnf download pacote

## Extrair o conteúdo de um arquivo rpm
Sintaxe: $ rpm2cpio pacote.rpm | cpio -idmv

## Listar as dependências de um pacote:

### Através do dnf repoquery
Sintaxe: $ dnf repoquery --requires nome-do-pacote

```
dnf repoquery --requires openssh-askpass
```

### Através do rpm
Sintaxe: rpm -qpR pacote.rpm

```
rpm -qpR google-chrome-stable-69.0.3497.81-1.x86_64.rpm
```

# Trabalhando com o copr

Copr (Cool Other Package Repo) é um projeto do Fedora para ajudar a construir e gerenciar repositórios de pacotes de terceiros de forma fácil.

Os repositórios no copr são criados por usuários e/ou contribuidores do Projeto Fedora,
os repositórios no copr são nomeados pelo nome-do-usuário/nome-do-repositório.

Um usuário pode ter vários repositórios.


## Pesquisar repositórios por uma palavra-chave
Exemplo:
```
$ dnf copr search retro
```

## Pesquisar repositórios de um usuário
Sintaxe: $ dnf copr list --available-by-user=nome-do-usuário

```
$ dnf copr list --available-by-user=fredlima
```
## Habilitar repositório copr
Sintaxe: # dnf copr enable nome/repositório

```
# dnf copr enable nome/projeto
```
## Desabilitar repositório copr
Sintaxe: # dnf copr disable nome/repositório
```
# dnf copr disable hernanarce/Retroarch-1.2.2
```
## Instalar pacote copr
Sintaxe: # dnf install pacote

Exemplo:
```
# dnf install bash
```

## Listar pacotes de um repositório copr
Sintaxe: $ dnf copr list nome/repositório
```
$ dnf copr list hernanarce/Retroarch-1.2.2
```
