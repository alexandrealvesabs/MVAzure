# MVAzure
💻 Instalação e Configuração de Máquina Virtual (VM) no Microsoft Azure
Este guia documenta de forma completa e detalhada como criar, configurar e acessar uma Máquina Virtual (VM) no Microsoft Azure usando o portal gráfico. O objetivo é oferecer uma base sólida para quem está começando com computação em nuvem na plataforma Azure.

🧾 Sumário
Pré-requisitos

Objetivo

Passo a Passo

1. Acesso ao Portal Azure

2. Criação de Grupo de Recursos

3. Criação da Máquina Virtual

4. Configurações Detalhadas

5. Validação e Criação

6. Acesso à Máquina Virtual

Gerenciamento e Boas Práticas

Encerramento e Limpeza

Recursos Oficiais

✅ Pré-requisitos
Conta ativa no Azure Portal

Navegador de internet (Chrome, Edge, Firefox)

Se for a primeira vez, uma conta gratuita pode ser criada em azure.microsoft.com/free

Conhecimentos básicos sobre SSH ou RDP (para acessar a VM)

🎯 Objetivo
Criar uma máquina virtual hospedada no Azure, com as seguintes características:

Sistema Operacional: Ubuntu Server 20.04 LTS ou Windows Server 2019

Tamanho: B1s (baixo custo para testes)

Acesso: SSH (Linux) ou RDP (Windows)

Rede: pública com IP dinâmico

Uso: fins educacionais e laboratoriais

🛠️ Passo a Passo
1. Acesso ao Portal Azure
Acesse: https://portal.azure.com

Faça login com sua conta Microsoft

2. Criação de Grupo de Recursos
Um grupo de recursos organiza todos os componentes relacionados.

No menu esquerdo, clique em "Grupos de recursos"

Clique em "Criar"

Informe:

Nome: lab-rg-vm

Região: Brazil South (ou a mais próxima)

Clique em “Revisar + criar”, depois “Criar”

3. Criação da Máquina Virtual
No portal, clique em "Criar um recurso"

Selecione "Máquina virtual"

Clique em "Criar"

4. Configurações Detalhadas
Aba: Básico
Assinatura: mantenha padrão

Grupo de Recursos: selecione lab-rg-vm

Nome da VM: vm-teste-linux ou vm-teste-windows

Região: Brazil South

Disponibilidade: Sem redundância (para testes)

Imagem: Ubuntu Server 20.04 LTS ou Windows Server 2019 Datacenter

Tamanho: B1s (pode ser alterado conforme necessidade)

Aba: Autenticação
Linux:

Tipo: Senha ou Chave pública SSH

Usuário: azureuser

Senha: SenhaForte123!

Windows:

Nome de usuário: adminazure

Senha: SenhaForte123!

Aba: Portas de Entrada
Linux: Marcar porta 22 (SSH)

Windows: Marcar porta 3389 (RDP)

Aba: Discos
Tipo de disco: SSD padrão

Criptografia padrão do Azure

Aba: Rede
Rede virtual: será criada automaticamente

IP Público: Dinâmico (aceitável para testes)

Grupo de segurança de rede (NSG): permitir acesso por porta escolhida (22 ou 3389)

5. Validação e Criação
Clique em "Revisar + criar"

Verifique todas as configurações

Clique em "Criar"

Aguarde a implantação (leva cerca de 2–3 minutos)

6. Acesso à Máquina Virtual
Linux (SSH)
bash
Copiar
Editar
ssh azureuser@IP_PUBLICO
Windows (RDP)
Abra o app "Conexão de Área de Trabalho Remota"

Digite o IP público

Faça login com o usuário/senha definidos

⚙️ Gerenciamento e Boas Práticas
Monitoramento: Acompanhe uso de CPU, rede e disco no painel da VM

Backups: Configure backup automático se for produção

Segurança:

Use senhas fortes ou chave SSH

Restrinja IPs no NSG (grupo de segurança de rede)

Custos: Verifique o custo por hora na calculadora do Azure

🧹 Encerramento e Limpeza
Para evitar cobranças desnecessárias:

Pare a VM quando não estiver usando

Delete a VM e o grupo de recursos após terminar os testes:

bash
Copiar
Editar
az group delete --name lab-rg-vm --yes
📚 Recursos Oficiais
Criar uma VM no Azure (Linux)

Criar uma VM no Azure (Windows)

Treinamento Gratuito Microsoft Learn

📂 Estrutura sugerida do repositório
bash
Copiar
Editar
.
├── README.md
├── /images
│   ├── tela-criacao-vm.png
│   ├── vm-pronta.png
│   └── acesso-ssh-ou-rdp.png
