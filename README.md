# 🧰 Usando o AWS Systems Manager

## 📘 Visão Geral do Laboratório
O **AWS Systems Manager** é um conjunto de recursos que permite **centralizar dados operacionais e automatizar tarefas** em recursos da AWS.  
Com ele, é possível configurar e gerenciar instâncias do **Amazon EC2**, servidores locais, máquinas virtuais e outros recursos em escala.

---

## 🎯 Objetivos
Após concluir este laboratório, você será capaz de:

✅ Verificar configurações e permissões  
✅ Executar tarefas em vários servidores simultaneamente  
✅ Atualizar configurações e definições de aplicativos  
✅ Acessar a linha de comando de uma instância EC2 via **Session Manager**

---

## ⚙️ Arquitetura do Laboratório

Abaixo está o fluxo básico do Systems Manager sendo usado para executar comandos em uma instância EC2:

![Arquitetura do Systems Manager](imagens/system.png)

---

## 🖥️ Etapas Realizadas

### 1️⃣ Verificação da Instância EC2
Executei o comando para listar as instâncias e confirmar o estado de execução:

```bash
aws ec2 describe-instances \
  --query "Reservations[*].Instances[*].{ID:InstanceId,IP:PublicIpAddress,Estado:State.Name}" \
  --output table

### 2️⃣ Confirmação de Tags e Stack do CloudFormation

A instância está sendo gerenciada pelo Systems Manager, conforme tags exibidas via CLI:

aws ec2 describe-tags \
  --filters "Name=resource-id,Values=i-0e12251ee83c4bcc0" \
  --output table

3️⃣ Acesso pelo Session Manager

O acesso foi feito diretamente pelo AWS Systems Manager > Session Manager:

A instância i-0e12251ee83c4bcc0 foi identificada como Managed Instance, com o agente 3.3.3050.0 ativo e status running na região us-west-2a.

4️⃣ Execução de Comandos via Run Command

Com o documento AWS-RunShellScript, foi possível executar scripts diretamente na instância, como instalação de pacotes, atualizações ou verificações de status.

5️⃣ Visualização do Inventário

O inventário de software coletado pelo Systems Manager mostra todas as aplicações e bibliotecas instaladas:

Exemplo de resultado exibido:

Name	Application Type	Version	Installed Time
jbigkit-libs	Development/Libraries	2.0	2025-10-08T07:27:03Z
libtasn1	System Environment/Libs	4.10	2025-10-08T07:27:04Z
🧩 Resultados Obtidos

✔️ Instância EC2 registrada e gerenciada com sucesso pelo Systems Manager
✔️ Acesso remoto via Session Manager (sem necessidade de SSH)
✔️ Execução de comandos via Run Command
✔️ Coleta de inventário completa e visualização detalhada de pacotes

🏁 Conclusão

O AWS Systems Manager facilita a administração de servidores em larga escala, proporcionando:

Segurança (sem abrir portas SSH)

Centralização de logs e comandos

Automação de tarefas repetitivas

Monitoramento e inventário de aplicações
