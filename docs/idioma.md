# Personalização do Idioma
Existe um comando do systemd que facilita tudo na hora de definir o locale do sistema, ele é o localectl.

### Exibir o locale e leiaute de teclado atual
```
$ localectl status
```

### Exibir os locales disponiveis instalados no sistema
```
$ localectl list-locales
```

### Instalando o pacote do Português do Brasil
```
# dnf install langpacks-pt_BR
```

### Definir o locale para pt_BR

```
# localectl set-locale LANG=pt_BR.utf8
```

### Exibir os leiautes de teclado disponíveis
```
$ localectl list-keymaps
```

### Definir o teclado para o padrão brasileiro no console e no Wayland e Xorg

```
# localectl set-keymap br
```
