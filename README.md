# banco-de-dados-Azure
Este repositório contém o resumo das lições aprendidas durante o desenvolvimento do lab na DIO, referentes aos conceitos dos tipos de computação em nuvem e a criação de banco de dados com Microsoft Azure.
# 🗄️ Desafio – Banco de Dados no Microsoft Azure  

---

## 🎯 Objetivo do Desafio  
Este laboratório tem como objetivo praticar a **configuração de uma instância de Banco de Dados no Azure**.  

O entregável consiste em um repositório contendo **resumos, anotações e dicas** sobre o uso da plataforma, servindo como material de apoio para estudos e futuras implementações.  

---

## ☁️ Introdução  
O **Microsoft Azure** oferece diferentes formas de provisionar e gerenciar bancos de dados em nuvem, permitindo flexibilidade, escalabilidade e segurança.  

Antes de explorar os serviços específicos, é essencial compreender os **modelos de computação em nuvem** e como se distribuem as **responsabilidades entre provedor e usuário**.  

---

## 🌐 Modelos de Serviço em Nuvem (IaaS, PaaS, SaaS)  

Antes de criar um banco de dados no Azure, é importante entender os **três modelos de computação em nuvem** e as responsabilidades de cada parte (usuário e provedor):  

### 🔹 IaaS (Infrastructure as a Service)  
- **Descrição**: o provedor entrega apenas a infraestrutura (rede, armazenamento, máquinas virtuais).  
- **Exemplo no Azure**: SQL Server instalado em uma VM.  
- **Responsabilidades**:  
  - **Provedor** → hardware, datacenter, virtualização e disponibilidade básica.  
  - **Usuário** → sistema operacional, instalação do SGBD, patching, backup, configuração e segurança.  

### 🔹 PaaS (Platform as a Service)  
- **Descrição**: o provedor oferece uma plataforma pronta, incluindo o motor de banco de dados.  
- **Exemplo no Azure**: Azure SQL Database, Azure Database for PostgreSQL/MySQL.  
- **Responsabilidades**:  
  - **Provedor** → atualizações do motor, backups automáticos, alta disponibilidade, escalabilidade.  
  - **Usuário** → modelagem de dados, consultas, índices, permissões e segurança lógica.  

### 🔹 SaaS (Software as a Service)  
- **Descrição**: software pronto para uso, sem que o usuário precise se preocupar com infraestrutura ou banco.  
- **Exemplo no Azure**: Power BI, Dynamics 365.  
- **Responsabilidades**:  
  - **Provedor** → gerencia toda a pilha (infra, plataforma e aplicação).  
  - **Usuário** → utiliza o serviço, insere e administra apenas os dados de negócio.  

---

## 🚀 Criando um Banco de Dados no Azure (Portal)  

### Passo a Passo  

1. Acesse o [Portal do Azure](https://portal.azure.com/) e pesquise por **Azure SQL**.  
2. Clique em **Criar** > **Banco de Dados SQL**.  
3. Configure:  
   - **Grupo de recursos** → crie ou selecione um existente.  
   - **Nome do banco** → `sqldb-lab`.  
   - **Servidor lógico** → crie um novo (nome único, região, usuário admin e senha forte).  
   - **Camada de compute** → escolha *Uso Geral* ou *Serverless*.  
   - **Rede** → habilite o acesso do seu IP atual (ou configure *Private Endpoint* em cenários corporativos).  
4. Clique em **Examinar + Criar** → depois em **Criar**.  
5. Aguarde a implantação e vá em **Ir para o recurso**.  
6. No painel do banco, acesse **Query Editor (Preview)**, conecte-se com suas credenciais e rode um teste simples.  

### Exemplo de script T-SQL no Query Editor:  
```sql
CREATE TABLE Produtos (
    Id INT IDENTITY PRIMARY KEY,
    Nome NVARCHAR(100),
    Preco DECIMAL(10,2)
);

INSERT INTO Produtos (Nome, Preco)
VALUES (N'Caneca Azul', 49.90), (N'Camiseta Dev', 79.90);

SELECT * FROM Produtos;


## 🚀 Conclusão  
Compreender os **modelos de nuvem e suas responsabilidades** é essencial para aproveitar ao máximo os serviços do Azure, seja configurando uma **instância de banco de dados**, escalando aplicações ou garantindo segurança e governança.  
