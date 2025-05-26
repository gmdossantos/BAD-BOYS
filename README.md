# BAD-BOYS
Projeto de Infraestrutura de Servidores e Redes 📋 Descrição do Projeto Este repositório documenta detalhadamente o processo de instalação e configuração de diversos sistemas operacionais e serviços em um ambiente de rede. O projeto abrange desde sistemas básicos até implementações avançadas de segurança e automação. 🎯 Objetivos

Documentar instalação e configuração de sistemas operacionais servidor Implementar serviços essenciais de rede (DNS, DHCP, Active Directory) Configurar sistemas de monitoramento e segurança Automatizar processos através de scripts Ansible Criar ambiente completo de laboratório para testes de segurança

🛠️ Tecnologias Utilizadas Sistemas Operacionais

Windows Server - Servidor corporativo Microsoft Debian Linux - Distribuição estável para servidores Kali Linux - Distribuição focada em segurança e testes de penetração pfSense - Firewall e roteador baseado em FreeBSD

Serviços e Ferramentas

DNS - Sistema de nomes de domínio DHCP - Protocolo de configuração dinâmica de host Active Directory - Serviço de diretório Microsoft Wazuh - Plataforma de monitoramento de segurança Ansible - Ferramenta de automação e orquestração

📋 Pré-requisitos Hardware Mínimo

RAM : 16 GB (recomendado 32 GB para várias VMs) Armazenamento : 500GB de espaço livre Processador : Suporte à virtualização (Intel VT-x ou AMD-V)

Software Necessário

VirtualBox ou VMware Git instalado Acesso à internet para downloads Editor de texto (VS Code recomendado)

📁 Estrutura do Repositório / ├── README.md # Este arquivo ├── windows-server/ # Documentação Windows Server │ ├── instalacao.md # Instalação do sistema │ ├── dns/ # Configuração DNS │ ├── dhcp/ # Configuração DHCP │ └── active-directory/ # Configuração AD ├── debian/ # Documentação Debian │ ├── instalacao.md # Instalação do sistema │ ├── dns/ # Configuração DNS │ └── dhcp/ # Configuração DHCP ├── wazuh/ # Sistema de monitoramento │ └── instalacao.md # Instalação e configuração ├── kali/ # Ambiente de testes │ └── instalacao.md # Instalação e ferramentas ├── pfsense/ # Firewall e roteador │ └── instalacao.md # Configuração de rede ├── ansible/ # Automação │ ├── README.md # Documentação dos scripts │ ├── playbooks/ # Playbooks de automação │ └── inventario/ # Arquivos de inventário └── docs/ # Documentação adicional ├── topologia-rede.md # Diagrama da rede └── troubleshooting.md # Resolução de problemas 🚀 Como Navegar no Projeto

Instalação dos Sistemas Base Comece pela instalação dos sistemas operacionais:
Servidor Windows Debian Linux Kali Linux pfSense

Configuração de Serviços Configure os serviços essenciais:
DNS : Windows | Debian DHCP : Windows | Debian Active Directory : Configuração

Implementação de Segurança
Wazuh - Monitoramento Kali Linux - Testes

Automação
Scripts Ansible

🤖 Uso de IA no Projeto Este projeto utilizou ferramentas de Inteligência Artificial para:

Geração de scripts Ansible : Criação automatizada de playbooks Documentação : Estruturação e formatação de manuais Solução de problemas : Identificação de soluções para problemas comuns

Ferramentas Utilizadas

ChatGPT para geração de scripts Claude para revisão da documentação GitHub Copilot para automação de código

📊 Topologia da Rede Internet | [pfSense] - 192.168.1.1 | Switch Virtual | ├── Windows Server - 192.168.1.10 (DNS, DHCP, AD) ├── Debian Server - 192.168.1.20 (DNS, DHCP) ├── Wazuh Server - 192.168.1.30 └── Kali Linux - 192.168.1.100 🔧 Solução de problemas Comum Problemas de Conectividade

Verifique as configurações de rede das VMs Confirme se o DHCP está funcionando Testar resolução DNS

Problemas com Ansible

Verificar conectividade SSH Confirmar permissões de usuário Validar sintaxe dos playbooks

👥 Equipe

Guilherme Edimar - Pedro Morais - Hugo dos Anjos

📚 Referências e Recursos Documentação Oficial

Documentação do Windows Server Manual do Administrador Debian Documentação Ansible Documentação Wazuh

Guias e Tutoriais

Documentação oficial do pfSense Documentação do Kali Linux Manual do Usuário do VirtualBox
