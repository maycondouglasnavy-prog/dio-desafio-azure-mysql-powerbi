# Desafio de Projeto: Processando e Transformando Dados com Power BI

Projeto prático desenvolvido para a formação de Power BI Analyst da DIO, focado na construção de um pipeline de dados ponta a ponta: desde a hospedagem de um banco relacional na nuvem até a modelagem dimensional e visualização analítica.

## 🛠️ Tecnologias Utilizadas
* **Azure Database for MySQL**: Armazenamento e gerenciamento do banco de dados na nuvem.
* **MySQL Workbench / Terminal**: Execução de scripts DDL e DML.
* **Power BI Desktop & Power Query**: Coleta, tratamento, transformação e modelagem dimensional (*Star Schema*).
* **Git & GitHub**: Controle de versão e documentação do projeto.

## ⚙️ Etapas Executadas
1. **Setup na Nuvem**: Criação da instância MySQL na Azure e execução dos scripts para criação das tabelas (`employee`, `departament`, `dept_locations`, `project`, `works_on`, `dependent`) e inserção das cargas de dados.
2. **Integração**: Conexão do Power BI Desktop com o banco Azure MySQL via modo *Import*.
3. **Transformações (Power Query)**:
   - Ajustes de tipos de dados (conversão de salários para *double* preciso).
   - Tratamento de valores nulos (validação de gerentes e diretores sem `Super_ssn`).
   - Mesclagem das colunas de Nome e Sobrenome dos colaboradores.
   - Cruzamento de dados entre departamentos e funcionários.
   - Criação da coluna unificada de Departamento e Localização.
   - Agrupamento de colaboradores por gerente.

## 💡 Nota Técnica: Por que utilizamos Mesclagem (*Merge*) e não Atribuição (*Append*)?
Para unificar os nomes dos departamentos e suas respectivas localizações (`dept_locations`), utilizamos exclusivamente a operação de **Mesclagem (*Merge*)**. 
* **Justificativa**: O *Merge* atua de forma relacional (equivalente a um `JOIN` do SQL), cruzando tabelas distintas através de uma chave em comum (`Dnumber`) para agregar colunas descritivas lado a lado. A **Atribuição (*Append*)**, por sua vez, realiza o empilhamento vertical de linhas (equivalente a um `UNION`), o que exigiria que ambas as tabelas possuíssem exatamente a mesma estrutura de colunas, gerando erros lógicos e duplicidade indesejada neste cenário de enriquecimento dimensional.

## 📂 Estrutura do Repositório
* `sql/`: Contém os scripts SQL originais do banco de dados.
* `powerbi/`: Contém o arquivo `.pbix` com o relatório estruturado.
* `prints/`: Evidências visuais da modelagem e do dashboard.