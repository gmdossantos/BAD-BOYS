# 🔨 Ansible – Instalação e Playbook Exemplo

## Instalação
```bash
sudo apt update
sudo apt install ansible -y
```

## Playbook Básico
```yaml
- name: Instalar Apache
  hosts: web
  become: yes
  tasks:
    - name: Instalar apache2
      apt:
        name: apache2
        state: present
```
