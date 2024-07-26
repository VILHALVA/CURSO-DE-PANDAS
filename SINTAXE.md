# SINTAXE
## ESTRUTURAS DE DADOS PRINCIPAIS:
1. **Series**:
   - Uma Series é uma estrutura de dados unidimensional que pode conter qualquer tipo de dados, como inteiros, floats, strings, etc.
   - É semelhante a uma coluna em uma tabela ou a um array unidimensional.
   - Cada elemento em uma Series tem um rótulo, chamado de índice.

   ```python
   import pandas as pd
   s = pd.Series([1, 3, 5, 7, 9])
   print(s)
   ```

2. **DataFrame**:
   - Um DataFrame é uma estrutura de dados bidimensional, semelhante a uma tabela em uma base de dados, com linhas e colunas.
   - Cada coluna em um DataFrame é uma Series.
   - Pode ser criada a partir de listas, dicionários, arrays, etc.

   ```python
   data = {
       'Nome': ['Ana', 'Bruno', 'Carlos', 'Diana'],
       'Idade': [23, 35, 45, 29],
       'Cidade': ['São Paulo', 'Rio de Janeiro', 'Curitiba', 'Belo Horizonte']
   }
   df = pd.DataFrame(data)
   print(df)
   ```

## OPERAÇÕES BÁSICAS:
1. **Leitura de Dados**:
   - Pandas pode ler dados de vários formatos, como CSV, Excel, SQL, JSON, etc.

   ```python
   df = pd.read_csv('dados.csv')
   ```

2. **Visualização de Dados**:
   - Visualize as primeiras e últimas linhas do DataFrame.

   ```python
   print(df.head())  # primeiras 5 linhas
   print(df.tail())  # últimas 5 linhas
   ```

3. **Indexação e Seleção de Dados**:
   - Selecionar uma coluna: `df['Nome']`
   - Selecionar múltiplas colunas: `df[['Nome', 'Idade']]`
   - Selecionar uma linha por índice: `df.loc[0]`
   - Selecionar uma célula específica: `df.at[0, 'Nome']`

4. **Filtragem de Dados**:
   - Filtrar linhas com base em uma condição.

   ```python
   df_maiores_30 = df[df['Idade'] > 30]
   ```

5. **Operações em Colunas**:
   - Adicionar uma nova coluna.

   ```python
   df['NovaColuna'] = df['Idade'] * 2
   ```

6. **Agrupamento e Agregação**:
   - Agrupar dados por uma coluna e calcular estatísticas agregadas.

   ```python
   df_grouped = df.groupby('Cidade').mean()
   ```

## MANIPULAÇÃO AVANÇADA:
1. **Mesclagem e Junção de Dados**:
   - Combine dados de diferentes DataFrames.

   ```python
   df1 = pd.DataFrame({'A': ['A0', 'A1', 'A2'],
                       'B': ['B0', 'B1', 'B2']})
   df2 = pd.DataFrame({'A': ['A1', 'A2', 'A3'],
                       'C': ['C1', 'C2', 'C3']})
   df_merged = pd.merge(df1, df2, on='A', how='inner')
   ```

2. **Lidar com Dados Faltantes**:
   - Verificar dados faltantes e preenchê-los ou removê-los.

   ```python
   df.dropna()  # remove linhas com dados faltantes
   df.fillna(0)  # preenche dados faltantes com zero
   ```

3. **Pivot Tables**:
   - Criar tabelas dinâmicas para resumir dados.

   ```python
   pivot_table = df.pivot_table(values='Idade', index='Cidade', columns='Nome', aggfunc='mean')
   ```

