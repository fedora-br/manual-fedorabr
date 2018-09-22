# Network Manager na CLI

O daemon do NetworkManager tenta tornar a configuração e a operação da rede tão indolor e automático quanto possível, gerenciando a conexão de rede primária e outras interfaces de rede, como dispositivos Ethernet, WiFi e dispositivos de banda larga móvel. O NetworkManager conectará qualquer dispositivo de rede quando uma conexão para esse dispositivo ficar disponível, a menos que esse comportamento esteja desativado.

Mostrar status dos dispositivos:
```
$ nmcli device status
```

Detalhes das conexões:
```
$ nmcli connection show
$ nmcli connection show Conexão\ Fedora
```

Ativar e desativar uma conexão:
```
$ nmcli connection up Conexão\ Fedora
$ nmcli connection down Conexão\ Fedora

```

## Adicionar e remover conexões
Adicionar uma conexão com endereço automático:
```
$ nmcli connection add  \
ifname eth0 \
type ethernet \
con-name 'Conexão Fedora'
```

Adicionar uma conexão com endereço manual:
```
$ nmcli connection add \
ipv4.method manual \
ifname eth0 \
type ethernet \
con-name 'Conexão Fedora' \
ip4 192.168.1.16/24 \
gw4 192.168.1.1 \
ipv4.dns 192.168.1.1,192.168.1.100
```

Remover uma conexão:
```
nmcli connection delete Conexão\ Fedora
```

## Modificar conexões
Desativar conexão automática:
```
$ nmcli con modify Conexão\ Fedora autoconnect off
```

Modificando para endereço manual:
```
$ nmcli com modify Conexão\ Fedora \
ipv4.method manual \
ip4 192.168.1.20/24 \
gw4 192.168.1.1 \
ipv4.dns 192.168.1.200
```

Adicionar e remover um servidor DNS:
```
$ nmcli con modify Conexão\ Fedora +ipv4.dns 1.1.1.1
$ nmcli con modify Conexão\ Fedora -ipv4.dns 8.8.8.8

```

## Conexões Wi-Fi
Ligar e desligar rádio da placa rede Wi-Fi via software:
```
$ nmcli radio wifi on
$ nmcli radio wifi off
```

Listar e adicionar uma rede Wi-Fi:
```
$ nmcli device wifi list
$ nmcli device wifi \
connect SSID \
password '123456' \
name Conexão\ Wi-Fi
```

Listar e adicionar uma rede Wi-Fi “oculta”:
```
$ nmcli device wifi list
$ nmcli device wifi \
connect SSID \
password '123456' \
name 'Conexão Wi-Fi' \
hidden yes
```

Ativar uma conexão Wi-Fi:
```
$ nmcli -p connection up Conexão\ Wi-Fi
```

## VPN

Adicionar conexão PPTP:
```
$ sudo dnf install NetworkManager-pptp
$ nmcli connection add \
connection.type vpn \
connection.id nome_da_conexão \
connection.permissions usuário_fedora \
vpn.service-type pptp \
vpn.data \
gateway=1.2.3.4 \
vpn.user-name usuário_vpn \
vpn.secrets password='123456' \
ifname all
```
Adicionar conexão OpenVPN:
```
$ sudo dnf install NetworkManager-openvpn
$ nmcli connction import \
type openvpn \
con-name nome_da_conexão \
file /caminho/para/arquivo.ovpn
```

## VLAN
Adicionar VLAN:
```
nmcli connection add \
ifname VLAN10 \
type vlan \
con-name 'Conexão VLAN10'
dev eth0 \
id 10 \
ip4 192.168.1.16/24 \
gw4 192.168.1.1 \
ipv4.dns 192.168.1.1,192.168.1.100
```
