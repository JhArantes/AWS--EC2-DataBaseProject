
# 🚀 Configurando uma Máquina Virtual (EC2) na AWS

Este guia rápido explica como criar, configurar e proteger uma instância **EC2** na **Amazon Web Services** (AWS). Ideal para quem está começando e deseja documentar o processo em um repositório GitHub.

---

## 📋 Pré-requisitos

| Item | Descrição |
|------|-----------|
| Conta AWS | É necessário possuir uma conta ativa (será pedido um cartão de crédito para verificação). |
| Acesso ao Console | Faça login em <https://aws.amazon.com>. |
| Chave SSH | Será gerada durante a criação da instância (baixe e guarde com segurança). |

---

## 🗺️ Visão Geral do Processo

1. **Criar Instância EC2**  
2. **Escolher Sistema Operacional & AMI**  
3. **Selecionar Tipo de Instância**  
4. **Configurar Par de Chaves (Key Pair)**  
5. **Definir Rede & Segurança (Security Group)**  
6. **Ajustar Armazenamento (EBS)**  
7. **Adicionar Tags**  
8. **Revisar e Lançar**  

---

## 1. Criando a Instância EC2

1. Acesse **Services › EC2** → *Launch Instance*.  
2. Dê um **nome significativo** (ex. `alura-care-db-prod`) e adicione **tags** (`Name`, `Owner`, `Environment`).

---

## 2. Escolha do Sistema Operacional

| Passo | Detalhe |
|-------|---------|
| **AMI (Amazon Machine Image)** | Selecione *Ubuntu Server 22.04 LTS* (64-bit, x86). |
| **Arquitetura** | 64-bit (x86) ou ARM, conforme compatibilidade da aplicação. |

> 💡 *Dica:* Ubuntu possui comunidade extensa e muitos tutoriais.

---

## 3. Tipo de Instância

| Exemplo | vCPUs | Memória (GiB) | Free Tier? |
|---------|-------|---------------|------------|
| `t2.micro` | 1 | 1 | ✅ |

Escolha tamanho segundo a carga esperada. Para testes, `t2.micro` atende e é elegível ao **Free Tier**.

---

## 4. Par de Chaves (Key Pair)

1. Clique em **Create new key pair**.  
2. Selecione formato **PEM** (Linux/macOS) ou **PPK** (PuTTY/Windows).  
3. **Baixe** o arquivo e guarde em local seguro (necessário para SSH).

---

## 5. Configurações de Rede

| Regra | Porta | Origem (IP) | Uso |
|-------|-------|-------------|-----|
| SSH | **22** | `My IP` (ex. `203.0.113.7/32`) | Acesso administrativo |
| HTTPS | **443** | `0.0.0.0/0` | Servir sites/aplicações |
| Extra | **Custom** | Blocos específicos (ex. `10.0.0.0/24`) | Acesso interno |

> ⚠️ **Boa prática:** limitar SSH ao seu endereço IP; evitar `0.0.0.0/0` em produção.

---

## 6. Firewall (Security Group)

Crie (ou reutilize) um **Security Group**:

```text
Name: alura-care-sg
Description: Acesso SSH e HTTPS controlado
VPC: default (ou especificar)
Inbound:
  - SSH   | TCP 22  | My IP
  - HTTPS | TCP 443 | 0.0.0.0/0
Outbound:
  - All traffic | 0.0.0.0/0
```

---

## 7. Configurando Armazenamento

- Volume **EBS** primário: comece com 8 GiB (pague somente pelo uso).  
- Marque a opção **Delete on termination** se não precisar do volume após destruir a instância.  
- Você pode **aumentar** o disco depois via console, sem downtime.

---

## 8. Tags (Boas Práticas)

| Chave | Valor Exemplo | Motivo |
|-------|---------------|--------|
| `Name` | `alura-care-db-prod` | Identificação clara |
| `Owner` | `joao.arantes` | Responsável |
| `Environment` | `dev`, `staging`, `prod` | Filtro por ambiente |
| `SO` | `Ubuntu` | Sistema operacional |

---

## 9. Revisar e Lançar

1. Clique em **Review and Launch**.  
2. Verifique AMI, tipo, firewall, armazenamento e tags.  
3. Pressione **Launch**.  
4. Aguarde o estado **running**.

---

## 🔐 Acessando via SSH

```bash
chmod 400 alura-care-key.pem
ssh -i "alura-care-key.pem" ubuntu@<Public-IP>
```

Substitua `<Public-IP>` pelo endereço público exibido no console.

---

## 💸 Otimizando Custos

- **Pare** ou **terminate** instâncias quando não estiver usando (`Instance State › Stop`).  
- Use **Auto Scaling** e **Elastic Load Balancing** em produção para escalabilidade automática.  

---

## 🛡️ Segurança Extra

- **Ative MFA** na conta AWS.  
- Use **IAM Roles** para aplicações (evite chaves hard-coded).  
- Mantenha o sistema operacional **atualizado** (`sudo apt update && sudo apt upgrade`).

---

## 📚 Referências

- [AWS EC2 – Getting Started](https://docs.aws.amazon.com/ec2/)
- [Best Practices for Security Groups](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_SecurityGroups.html)
- [EBS Volume Types](https://docs.aws.amazon.com/ebs/)

---

> **Autor:** João Henrique Arantes  
> **Última atualização:** 26 Jun 2025
