Com certeza. Com base no seu notebook, preparei um `README.md` completo que explica o objetivo do projeto, as transformações realizadas e como executá-lo.

---

# Projeto de Limpeza de Dados de Marketing Bancário

## 📝 Visão Geral do Projeto

Este projeto tem como objetivo limpar e preparar os dados de uma campanha de marketing de um banco, que visava incentivar clientes a contratarem empréstimos pessoais. O objetivo final é estruturar os dados para que possam ser facilmente importados e armazenados em um banco de dados PostgreSQL, servindo como base para análises futuras e importação de dados de novas campanhas.

O script processa o arquivo `bank_marketing.csv` e o divide em três arquivos CSV limpos e formatados, conforme as especificações do cliente.

## 🚀 Etapas e Transformações Realizadas

O arquivo de entrada `bank_marketing.csv` foi dividido em três DataFrames lógicos (`client`, `campaign`, e `economics`), e as seguintes operações de limpeza e formatação foram aplicadas:

### 1. Tabela `client.csv`

Este arquivo contém os dados demográficos e de perfil dos clientes.

-   **Formatação de Strings:** Nas colunas `job` e `education`, os caracteres `.` foram substituídos por `_` para padronização.
-   **Tratamento de Dados Ausentes:** Na coluna `education`, os valores `"unknown"` foram convertidos para `NaN` (nulos).
-   **Conversão para Booleanos:**
    -   A coluna `credit_default` foi transformada para o tipo booleano, onde `"yes"` se torna `True` e outros valores (`"no"`, `"unknown"`) se tornam `False`.
    -   A coluna `mortgage` foi transformada para o tipo booleano, onde `"yes"` se torna `True` e os demais valores se tornam `False`.

### 2. Tabela `campaign.csv`

Este arquivo contém informações relacionadas à campanha de marketing atual e anterior.

-   **Conversão para Booleanos:**
    -   A coluna `previous_outcome` foi convertida para o tipo booleano, onde `"success"` se torna `True` e os demais valores (`"failure"`, `"nonexistent"`) se tornam `False`.
    -   A coluna `campaign_outcome` foi convertida para o tipo booleano, onde `"yes"` se torna `True` e `"no"` se torna `False`.
-   **Criação de Coluna de Data:**
    -   Uma nova coluna `last_contact_date` foi criada no formato `YYYY-MM-DD`.
    -   Para isso, foi adicionada uma coluna `year` com o valor fixo de `2022`, que foi então combinada com as colunas `month` e `day` do dataset original.

### 3. Tabela `economics.csv`

Este arquivo contém os indicadores econômicos associados a cada cliente no momento do contato.

-   Nenhuma transformação foi necessária além da extração das colunas `client_id`, `cons_price_idx` e `euribor_three_months`.

## ട്ടു Saída Final

O processo gera três arquivos CSV prontos para uso:

1.  `client.csv`
2.  `campaign.csv`
3.  `economics.csv`

## 💻 Tecnologias Utilizadas

-   **Linguagem:** Python
-   **Bibliotecas:** Pandas, NumPy

## ▶️ Como Executar

1.  Certifique-se de que o arquivo `bank_marketing.csv` esteja no mesmo diretório do script/notebook.
2.  Execute o notebook `notebook.ipynb` em um ambiente com Python e as bibliotecas necessárias instaladas.
3.  Os três arquivos de saída (`client.csv`, `campaign.csv`, `economics.csv`) serão gerados no mesmo diretório.
