# 🐧 Debian – Instalação e Configuração

## Instalação
1. Crie VM com ISO do Debian.
2. Instale com ambiente mínimo.
3. Crie usuário e senha.
4. Instale o GRUB e reinicie.

## Configuração
- IP fixo em `/etc/network/interfaces`
- Instalar serviços:
```bash
sudo apt update
sudo apt install bind9 isc-dhcp-server -y
```
