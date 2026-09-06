# Desafio de Projeto: Processando e Transformando Dados com Power BI

Projeto prático desenvolvido para a formação de Power BI Analyst da DIO, focado na construção de um pipeline de dados ponta a ponta: desde a hospedagem de um banco relacional na nuvem até a modelagem dimensional e visualização analítica[cite: 1, 2].

## 🛠️ Tecnologias Utilizadas
* **Azure Database for MySQL**: Armazenamento e gerenciamento do banco de dados na nuvem[cite: 1, 2].
* **MySQL Workbench / Terminal**: Execução de scripts DDL e DML[cite: 1, 2].
* **Power BI Desktop & Power Query**: Coleta, tratamento, transformação e modelagem dimensional (*Star Schema*)[cite: 1, 2].
* **Git & GitHub**: Controle de versão e documentação do projeto[cite: 1, 2].

## ⚙️ Etapas Executadas
1. **Setup na Nuvem**: Criação da instância MySQL na Azure e execução dos scripts para criação das tabelas (`employee`, `departament`, `dept_locations`, `project`, `works_on`, `dependent`) e inserção das cargas de dados[cite: 1, 2].
2. **Integração**: Conexão do Power BI Desktop com o banco Azure MySQL via modo *Import*[cite: 1, 2].
3. **Transformações (Power Query)**:
   - Ajustes de tipos de dados (conversão de salários para *double* preciso)[cite: 1, 2].
   - Tratamento de valores nulos (validação de gerentes e diretores sem `Super_ssn`)[cite: 1, 2].
   - Mesclagem das colunas de Nome e Sobrenome dos colaboradores[cite: 1, 2].
   - Cruzamento de dados entre departamentos e funcionários[cite: 1, 2].
   - Criação da coluna unificada de Departamento e Localização[cite: 1, 2].
   - Agrupamento de colaboradores por gerente[cite: 1, 2].

## 💡 Nota Técnica: Por que utilizamos Mesclagem (*Merge*) e não Atribuição (*Append*)?
Para unificar os nomes dos departamentos e suas respectivas localizações (`dept_locations`), utilizamos exclusivamente a operação de **Mesclagem (*Merge*)**. 
* **Justificativa**: O *Merge* atua de forma relacional (equivalente a um `JOIN` do SQL), cruzando tabelas distintas através de uma chave em comum (`Dnumber`) para agregar colunas descritivas lado a lado. A **Atribuição (*Append*)**, por sua vez, realiza o empilhamento vertical de linhas (equivalente a um `UNION`), o que exigiria que ambas as tabelas possuíssem exatamente a mesma estrutura de colunas, gerando erros lógicos e duplicidade indesejada neste cenário de enriquecimento dimensional.

## 📂 Estrutura do Repositório
* `sql/`: Contém os scripts SQL originais do banco de dados[cite: 1, 2].
* `powerbi/`: Contém o arquivo `.pbix` com o relatório estruturado[cite: 1, 2].
* `prints/`: Evidências visuais da modelagem e do dashboard[cite: 1, 2].