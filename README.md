# Projeto de Dashboard de Vendas com Python

Este projeto é uma análise de vendas de um supermercado utilizando **Python** e as bibliotecas **Pandas**, **Plotly Express** e **Streamlit**. O objetivo do projeto é criar um dashboard interativo que permita visualizar os principais indicadores de desempenho das vendas ao longo do tempo.

## 🚀 Tecnologias Utilizadas

- **Python**: Linguagem de programação principal do projeto.
- **Pandas**: Para manipulação e análise dos dados.
- **Plotly Express**: Para criação de gráficos interativos.
- **Streamlit**: Para criação do dashboard web interativo.

---

## 📊 Descrição do Projeto

O projeto realiza a leitura de um arquivo CSV contendo dados de vendas de um supermercado e exibe visualizações interativas através de um dashboard. O dashboard permite filtrar os dados por mês e apresenta diferentes gráficos que analisam o faturamento por dia, tipo de produto, cidade, forma de pagamento e avaliações das filiais.

### 📂 Estrutura do Código

O arquivo principal do projeto é o `dashboards.py`, que contém o seguinte fluxo:

1. **Importação de bibliotecas**:

   ```python
   import streamlit as st
   import pandas as pd
   import plotly.express as px
   ```

2. **Configuração da página do Streamlit**:

   ```python
   st.set_page_config(layout="wide")
   ```

3. **Leitura e manipulação dos dados**:

   - Leitura do arquivo CSV.
   - Conversão da coluna de datas para o tipo datetime.
   - Criação de uma nova coluna com o mês de cada venda.

   ```python
   df = pd.read_csv("supermarket_sales.csv", sep=";", decimal=",")
   df["Date"] = pd.to_datetime(df["Date"])
   df = df.sort_values("Date")
   df["Month"] = df["Date"].apply(lambda x: str(x.year) + "-" + str(x.month))
   ```

4. **Filtro por mês**:

   ```python
   month = st.sidebar.selectbox("Mês", df["Month"].unique())
   df_filtered = df[df["Month"] == month]
   ```

5. **Criação dos gráficos**:

   - Gráfico de faturamento por dia.
   - Gráfico de faturamento por tipo de produto.
   - Gráfico de faturamento por filial.
   - Gráfico de faturamento por tipo de pagamento.
   - Gráfico de avaliação das filiais.

   Exemplo de criação de um gráfico:

   ```python
   fig_date = px.bar(df_filtered, x="Date", y="Total", color="City", title="Faturamento por dia")
   col1.plotly_chart(fig_date, use_container_width=True)
   ```

---

## 📈 Gráficos Gerados no Dashboard

1. **Faturamento por Dia**: Mostra o faturamento total por dia, categorizado por cidade.
2. **Faturamento por Tipo de Produto**: Mostra o faturamento por linha de produto.
3. **Faturamento por Filial**: Mostra o total de vendas por cidade.
4. **Faturamento por Tipo de Pagamento**: Exibe um gráfico de pizza mostrando a contribuição de cada tipo de pagamento.
5. **Avaliação das Filiais**: Mostra a média das avaliações dos clientes por cidade.

---

## 💻 Como Rodar o Projeto

1. **Instale as bibliotecas necessárias**:

   ```bash
   pip install streamlit pandas plotly
   ```

2. **Execute o script no terminal**:

   ```bash
   streamlit run dashboards.py
   ```

3. **Acesse o dashboard no navegador**: O Streamlit abrirá uma aba no navegador com o dashboard interativo.

---

## 📂 Estrutura do Arquivo CSV

O arquivo `supermarket_sales.csv` contém as seguintes colunas:

| Coluna        | Descrição            |
| ------------- | -------------------- |
| Invoice ID    | ID da Nota Fiscal    |
| Branch        | Filial               |
| City          | Cidade               |
| Customer Type | Tipo de Cliente      |
| Gender        | Gênero do Cliente    |
| Product Line  | Linha de Produto     |
| Unit Price    | Preço Unitário       |
| Quantity      | Quantidade Vendida   |
| Tax 5%        | Imposto de 5%        |
| Total         | Total da Venda       |
| Date          | Data da Venda        |
| Payment       | Método de Pagamento  |
| Rating        | Avaliação do Cliente |

---

## 🔥 Funcionalidades do Dashboard

- Filtro por mês para visualizar os dados de vendas de um período específico.
- Gráficos interativos que permitem uma melhor visualização dos dados.
- Análises de faturamento por dia, tipo de produto, cidade, forma de pagamento e avaliação das filiais.

---


## 📚 Referências

- [Documentação do Pandas](https://pandas.pydata.org/)
- [Documentação do Plotly Express](https://plotly.com/python/plotly-express/)
- [Documentação do Streamlit](https://docs.streamlit.io/)

