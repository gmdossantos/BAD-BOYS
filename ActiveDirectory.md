🔧 Pré-requisitos
Active Directory - Guia Passo a Passo
Guia detalhado para instalação e configuração do Active Directory Domain Services no Windows Server.
📋 Pré-requisitos
✅ Verificar Hardware

 Processador 1,4 GHz 64 bits ou superior
 RAM mínima 2 GB (recomendado 4 GB)
 40 GB de espaço livre em disco
 Adaptador de rede funcionando

✅ Verificar Software

 Windows Server 2019/2022 instalado
 Conta com privilégios administrativos
 Sistema atualizado

🌐 ETAPA 1: Configurar Rede
Passo 1.1: Configurar IP Estático

Abrir Painel de Controle → Centro de Rede e Compartilhamento
Clicar em Alterar configurações do adaptador
Clicar com botão direito no adaptador de rede → Propriedades
Selecionar Protocolo TCP/IPv4 → Propriedades
Marcar Usar o seguinte endereço IP:
Endereço IP: 192.168.1.10
Máscara de sub-rede: 255.255.255.0
Gateway padrão: 192.168.1.1

Em Servidor DNS preferencial: deixar em branco por enquanto
Clicar OK → OK

Passo 1.2: Testar Conectividade
cmdping 192.168.1.1
ping google.com
📦 ETAPA 2: Instalar Active Directory Domain Services
Passo 2.1: Abrir Server Manager

Clicar no ícone Server Manager na barra de tarefas
Aguardar carregamento completo da interface

Passo 2.2: Adicionar Função AD DS

No Server Manager, clicar Gerenciar → Adicionar funções e recursos
Tela de boas-vindas → Avançar
Selecionar Instalação baseada em função ou recurso → Avançar
Certificar que o servidor local está selecionado → Avançar

Passo 2.3: Selecionar Active Directory

Na lista Funções de Servidor, marcar ☑️ Active Directory Domain Services
Janela pop-up aparece → Adicionar Recursos
Avançar → Avançar (manter características padrão)

Passo 2.4: Confirmar Instalação

Revisar opções na tela de confirmação
Marcar ☑️ Reinicie o servidor de destino automaticamente se necessário
Instalar
Aguardar conclusão (pode demorar alguns minutos)

🏰 ETAPA 3: Promover a Domain Controller
Passo 3.1: Iniciar Promoção

Após instalação, clicar no ícone de notificação (⚠️) no Server Manager
Clicar Promover este servidor para controlador de domínio

Passo 3.2: Configurar Nova Floresta

Selecionar Adicionar uma nova floresta
Nome de domínio raiz: empresa.local
Avançar

Passo 3.3: Configurar Opções do DC

Nível funcional da floresta: Windows Server 2016 (ou superior)
Nível funcional do domínio: Windows Server 2016 (ou superior)
Marcar:

☑️ Servidor de Sistema de Nomes de Domínio (DNS)
☑️ Catálogo Global (GC)


Senha DSRM: Criar uma senha forte (anotar em local seguro)
Avançar

Passo 3.4: Configurar DNS

Se aparecer aviso sobre delegação DNS → ignorar
Avançar

Passo 3.5: Nome NetBIOS

Nome será preenchido automaticamente: EMPRESA
Avançar

Passo 3.6: Definir Caminhos

Manter caminhos padrão:
Database: C:\Windows\NTDS
Log files: C:\Windows\NTDS  
SYSVOL: C:\Windows\SYSVOL

Avançar

Passo 3.7: Finalizar Instalação

Revisar todas as configurações
Instalar
Servidor reiniciará automaticamente

🔧 ETAPA 4: Configurar DNS
Passo 4.1: Atualizar Configuração de Rede

Após reinicialização, voltar às Propriedades do adaptador de rede
Protocolo TCP/IPv4 → Propriedades
Servidor DNS preferencial: 127.0.0.1
OK → OK

Passo 4.2: Verificar DNS

Server Manager → Ferramentas → DNS
Verificar se existem:

Zonas de pesquisa direta: empresa.local
Zonas de pesquisa inversa: correspondente ao IP



📁 ETAPA 5: Criar Estrutura Organizacional
Passo 5.1: Abrir AD Users and Computers

Server Manager → Ferramentas → Usuários e Computadores do Active Directory

Passo 5.2: Criar OUs Principais

Clicar com botão direito em empresa.local
Novo → Unidade Organizacional
Nome: Departamentos → OK

Passo 5.3: Criar Sub-OUs
Repetir processo para criar dentro de "Departamentos":

 TI
 RH
 Financeiro
 Vendas

Criar também na raiz:

 Servidores
 Estações de trabalho
 Contas de serviço

👥 ETAPA 6: Criar Usuários e Grupos
Passo 6.1: Criar Primeiro Usuário

Navegar até Departamentos → TI
Botão direito → Novo → Usuário
Preencher:
Nome: João
Sobrenome: Silva
Nome de usuário: joao.silva

Avançar
Definir senha inicial
Configurar opções:

☑️ O usuário deve alterar a senha no próximo login
☐ O usuário não pode alterar a senha
☐ A senha nunca expira
☐ A conta está desativada


Avançar → Concluir

Passo 6.2: Criar Grupo

Botão direito na OU TI → Novo → Grupo
Nome do grupo: TI-Administradores
Escopo do grupo: Global
Tipo de grupo: Segurança
OK

Passo 6.3: Adicionar Usuário ao Grupo

Duplo clique no grupo TI-Administradores
Aba Membros → Adicionar
Digitar: joao.silva
Verificar Nomes → OK → OK

🔐 ETAPA 7: Configurar Políticas de Grupo
Passo 7.1: Abrir Group Policy Management

Server Manager → Ferramentas → Gerenciamento de Política de Grupo

Passo 7.2: Criar Nova GPO

Expandir Floresta → Domínios → empresa.local
Botão direito em Group Policy Objects → Novo
Nome: Política de Segurança TI
OK

Passo 7.3: Configurar Política de Senha

Botão direito na GPO criada → Editar
Navegar até:
Configuração do Computador → Políticas → Configurações do Windows 
→ Configurações de Segurança → Políticas de Conta → Política de Senha

Configurar:

Comprimento mínimo da senha: 8 caracteres
A senha deve atender aos requisitos de complexidade: Habilitado
Idade máxima da senha: 90 dias
Idade mínima da senha: 1 dia



Passo 7.4: Vincular GPO

Botão direito na OU TI → Vincular um GPO existente
Selecionar Política de Segurança TI
OK

✅ ETAPA 8: Verificação Final
Passo 8.1: Testar Login de Domínio

Em uma estação de trabalho, fazer logoff
Tentar login com: empresa\joao.silva

Passo 8.2: Verificar Serviços

Services.msc → verificar se estão rodando:

Active Directory Domain Services
DNS Server
Kerberos Key Distribution Center



Passo 8.3: Comandos de Verificação
cmd# Verificar domínio
echo %USERDOMAIN%

# Testar replicação
repadmin /replsum

# Verificar DNS
nslookup empresa.local

# Status do DC
dcdiag
💾 ETAPA 9: Configurar Backup
Passo 9.1: Instalar Windows Server Backup

Server Manager → Gerenciar → Adicionar funções e recursos
Recursos → Ferramentas de Administração de Servidor Remoto → Ferramentas de Administração de Funções → Ferramentas do AD DS

Passo 9.2: Criar Backup Manual
powershell# Abrir PowerShell como Administrador
wbadmin start systemstatebackup -backuptarget:E: -quiet
🎉 Parabéns!
Seu Active Directory está configurado e funcionando. Próximos passos recomendados:

 Adicionar mais usuários e grupos
 Configurar políticas de grupo adicionais
 Integrar estações de trabalho ao domínio
 Configurar backup automático
 Documentar senhas e configurações

🆘 Solução de Problemas
DNS não resolve
cmdipconfig /flushdns
ipconfig /registerdns
Erro de replicação
cmdrepadmin /syncall
GPO não aplica
cmdgpupdate /force
