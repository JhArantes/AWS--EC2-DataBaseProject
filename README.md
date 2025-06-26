# 🌩️ Projeto de Modernização de Infraestrutura de Dados com AWS

Este repositório contém os materiais, scripts e configurações utilizados no curso de **Introdução à Engenharia de Dados** da Alura, focado na migração de dados locais para a nuvem utilizando **AWS (Amazon Web Services)**.

---

## 💼 Contexto

A **Alura Care** é uma startup na área da saúde em pleno crescimento. Inicialmente, utilizava uma estrutura simples para armazenar dados: pequenos bancos locais e arquivos CSV dispersos. Porém, com o aumento da base de clientes e da equipe, surgiu um grande desafio:

> **Como escalar a infraestrutura de dados de forma segura, organizada e eficiente?**

---

## 🎯 Objetivo do Projeto

Modernizar a arquitetura de dados da startup, garantindo:

- 🔄 Elasticidade: capacidade de crescer conforme a demanda;
- 🚀 Escalabilidade: estrutura preparada para o crescimento contínuo;
- 💾 Centralização: unificação de dados dispersos (CSV, bancos) na nuvem;
- 🔐 Segurança: configuração correta de acessos e instâncias.

---

## 🧰 Tecnologias Utilizadas

- **AWS EC2 (Elastic Compute Cloud)**: Criação de instância Linux (Ubuntu) para instalação do banco de dados.
- **AWS Free Tier**: Uso consciente de recursos para evitar cobranças desnecessárias.
- **Python**: Scripts de migração de dados locais (CSV) para o banco na nuvem.
- **Chave SSH**: Acesso seguro à instância EC2.
- **Firewall (Security Groups)**: Controle de acesso baseado em IP e portas.

---

## 🧱 Etapas da Solução

### 1. Escolha pela Nuvem

A equipe descartou a expansão de servidores locais por custos elevados e complexidade de previsões de uso. A AWS foi escolhida por:

- Modelo **pay-as-you-go** (pague pelo que usar);
- Facilidade de escalonamento;
- Infraestrutura confiável e amplamente documentada.

### 2. Criação da Instância EC2

- Seleção do sistema operacional **Ubuntu**, por ser leve, estável e bem suportado.
- Escolha da instância **t2.micro** (grátis pelo Free Tier).
- Configuração de disco com **uso inteligente de armazenamento** (começando com 8 GB e escalando sob demanda).
- Aplicação de **tags de identificação** (nome, dono, sistema operacional).
- Definição de **Security Group (firewall)** com liberação da porta SSH (22) e controle de IPs.

### 3. Segurança

- Geração de **par de chaves** (pública e privada) para acesso via terminal.
- Recomendação de salvar a chave `.pem` em local seguro (é a identidade da sua máquina na nuvem).
- Boas práticas para desligamento da instância após o uso, evitando cobranças desnecessárias.

---

## 🔁 Próximos Passos (Previstos)

- Configuração do banco de dados (MySQL/PostgreSQL) na instância EC2.
- Criação de scripts Python para ingestão e transformação dos arquivos CSV.
- Monitoramento de recursos da instância e automação de escalonamento.

---

## 🤝 Público-Alvo

Este projeto é ideal para:

- Estudantes de Ciência de Dados e Engenharia de Dados;
- Desenvolvedores interessados em infraestrutura e cloud computing;
- Equipes de startups que desejam migrar de dados locais para a nuvem com baixo custo inicial.

---

## 💡 Aprendizados-Chave

- Nuvem não é apenas "um lugar para guardar coisas", é uma **estratégia de negócio**.
- Mesmo em um ambiente educacional, é essencial aplicar boas práticas de segurança e organização.
- O uso eficiente de recursos na nuvem pode gerar grande **economia financeira** e **flexibilidade operacional**.

---

## 📚 Recursos Extras

- [Documentação oficial da AWS EC2](https://docs.aws.amazon.com/ec2/)
- [Conceitos de Elasticidade e Escalabilidade](https://aws.amazon.com/pt/autoscaling/)
- [Artigo: Como acessar instâncias EC2 com SSH](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AccessingInstancesLinux.html)

---

## 🧠 Contribuições

Contribuições são bem-vindas! Se você quiser sugerir melhorias, exemplos ou automações para este projeto, fique à vontade para abrir uma issue ou pull request.

---

## 🛡️ Aviso

> Este projeto foi desenvolvido em ambiente educacional. Para uso em produção, recomenda-se seguir políticas avançadas de segurança, backups e monitoramento.

---

Gravado e produzido por [Alura Cursos](https://www.alura.com.br/).

---

