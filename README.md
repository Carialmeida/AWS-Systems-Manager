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

