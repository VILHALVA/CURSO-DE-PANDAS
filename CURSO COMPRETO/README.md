# INSTRUÇÕES (GENERICAS -> USANDO O PYTHON)
## 01) CONCEITOS BÁSICOS
### INTRODUÇÃO
Pandas é uma biblioteca poderosa e versátil para análise de dados em Python. Ela fornece estruturas de dados de alto desempenho e ferramentas de análise de dados que facilitam a manipulação de grandes conjuntos de dados. Aqui estão os conceitos básicos que você precisa conhecer para começar a usar Pandas.

### ESTRUTURAS DE DADOS PRINCIPAIS
1. **SERIES**:
   - Uma Series é uma estrutura de dados unidimensional que pode conter qualquer tipo de dados, como inteiros, floats, strings, etc.
   - É semelhante a uma coluna em uma tabela ou a um array unidimensional.
   - Cada elemento em uma Series tem um rótulo, chamado de índice.

   ```python
   import pandas as pd
   s = pd.Series([1, 3, 5, 7, 9])
   print(s)
   ```

2. **DATAFRAME**:
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

### OPERAÇÕES BÁSICAS
1. **LEITURA DE DADOS**:
   - Pandas pode ler dados de vários formatos, como CSV, Excel, SQL, JSON, etc.

   ```python
   df = pd.read_csv('dados.csv')
   ```

2. **VISUALIZAÇÃO DE DADOS**:
   - Visualize as primeiras e últimas linhas do DataFrame.

   ```python
   print(df.head())  # Primeiras 5 linhas
   print(df.tail())  # Últimas 5 linhas
   ```

3. **INDEXAÇÃO E SELEÇÃO DE DADOS**:
   - Selecionar uma coluna: `df['Nome']`
   - Selecionar múltiplas colunas: `df[['Nome', 'Idade']]`
   - Selecionar uma linha por índice: `df.loc[0]`
   - Selecionar uma célula específica: `df.at[0, 'Nome']`

   ```python
   print(df['Nome'])  # Selecionar coluna 'Nome'
   print(df[['Nome', 'Idade']])  # Selecionar múltiplas colunas
   print(df.loc[0])  # Selecionar linha por índice
   print(df.at[0, 'Nome'])  # Selecionar célula específica
   ```

4. **FILTRAGEM DE DADOS**:
   - Filtrar linhas com base em uma condição.

   ```python
   df_maiores_30 = df[df['Idade'] > 30]
   print(df_maiores_30)
   ```

5. **OPERAÇÕES EM COLUNAS**:
   - Adicionar uma nova coluna.

   ```python
   df['NovaColuna'] = df['Idade'] * 2
   print(df)
   ```

6. **AGRUPAMENTO E AGREGAÇÃO**:
   - Agrupar dados por uma coluna e calcular estatísticas agregadas.

   ```python
   df_grouped = df.groupby('Cidade').mean()
   print(df_grouped)
   ```

### MANIPULAÇÃO AVANÇADA
1. **MESCLAGEM E JUNÇÃO DE DADOS**:
   - Combine dados de diferentes DataFrames.

   ```python
   df1 = pd.DataFrame({'A': ['A0', 'A1', 'A2'],
                       'B': ['B0', 'B1', 'B2']})
   df2 = pd.DataFrame({'A': ['A1', 'A2', 'A3'],
                       'C': ['C1', 'C2', 'C3']})
   df_merged = pd.merge(df1, df2, on='A', how='inner')
   print(df_merged)
   ```

2. **LIDAR COM DADOS FALTANTES**:
   - Verificar dados faltantes e preenchê-los ou removê-los.

   ```python
   df.dropna()  # Remove linhas com dados faltantes
   df.fillna(0)  # Preenche dados faltantes com zero
   ```

3. **PIVOT TABLES**:
   - Criar tabelas dinâmicas para resumir dados.

   ```python
   pivot_table = df.pivot_table(values='Idade', index='Cidade', columns='Nome', aggfunc='mean')
   print(pivot_table)
   ```

### CONCLUSÃO
Os conceitos básicos de Pandas incluem a compreensão de suas principais estruturas de dados (Series e DataFrame) e a execução de operações comuns, como leitura, visualização, seleção, filtragem e manipulação de dados. Pandas oferece uma ampla gama de funcionalidades que permitem uma análise de dados poderosa e eficiente. 

## 02) TIPOS DE VARIÁVEIS
No Pandas, você encontrará diferentes tipos de variáveis (ou tipos de dados) que são importantes para entender como os dados são armazenados e manipulados. Aqui estão os principais tipos de variáveis que você pode encontrar em Pandas:

### TIPOS DE DADOS NA SERIES
1. **INT (Inteiro)**
   - Armazena valores inteiros.
   - Exemplo: `int8`, `int16`, `int32`, `int64`.

   ```python
   s_int = pd.Series([1, 2, 3, 4, 5], dtype='int64')
   ```

2. **FLOAT (Ponto Flutuante)**
   - Armazena valores numéricos com ponto decimal.
   - Exemplo: `float32`, `float64`.

   ```python
   s_float = pd.Series([1.1, 2.2, 3.3, 4.4, 5.5], dtype='float64')
   ```

3. **OBJECT (Objeto)**
   - Usado para armazenar strings ou dados de tipos mistos.
   - Pode conter qualquer tipo de dados Python, mas geralmente é usado para strings.

   ```python
   s_obj = pd.Series(['apple', 'banana', 'cherry'], dtype='object')
   ```

4. **CATEGORY (Categoria)**
   - Usado para armazenar dados categóricos, que podem ser de um número finito de categorias.
   - É eficiente para dados com um número limitado de categorias.

   ```python
   s_cat = pd.Series(['a', 'b', 'a', 'c'], dtype='category')
   ```

5. **BOOLEAN (Booleano)**
   - Armazena valores `True` ou `False`.

   ```python
   s_bool = pd.Series([True, False, True])
   ```

6. **DATETIME (Data e Hora)**
   - Armazena informações de data e hora.
   - Usa `datetime64` e pode ser manipulado com funcionalidades específicas de data e hora.

   ```python
   s_datetime = pd.Series(pd.to_datetime(['2024-01-01', '2024-01-02']))
   ```

7. **TIMESTAMP (Carimbo de Data e Hora)**
   - Similar ao `DATETIME`, mas geralmente usado para pontos específicos no tempo.

   ```python
   ts = pd.Timestamp('2024-07-26')
   ```

### TIPOS DE DADOS NO DATAFRAME
Os DataFrames no Pandas podem conter diferentes tipos de dados em suas colunas, e cada coluna pode ter um tipo de dado diferente. Aqui estão algumas operações comuns relacionadas aos tipos de dados em um DataFrame:

1. **VERIFICAR TIPOS DE DADOS DAS COLUNAS**

   ```python
   df = pd.DataFrame({
       'A': [1, 2, 3],
       'B': [1.1, 2.2, 3.3],
       'C': ['apple', 'banana', 'cherry'],
       'D': pd.to_datetime(['2024-01-01', '2024-01-02', '2024-01-03'])
   })
   print(df.dtypes)
   ```

2. **ALTERAR TIPOS DE DADOS**

   - **Converter para Inteiro**:

     ```python
     df['A'] = df['A'].astype('int32')
     ```

   - **Converter para Float**:

     ```python
     df['B'] = df['B'].astype('float32')
     ```

   - **Converter para Categoria**:

     ```python
     df['C'] = df['C'].astype('category')
     ```

   - **Converter para Data e Hora**:

     ```python
     df['D'] = pd.to_datetime(df['D'])
     ```

### CONCLUSÃO
Entender os tipos de variáveis e como manipulá-los é essencial para trabalhar de forma eficaz com dados no Pandas. Os diferentes tipos de dados permitem armazenar e processar informações de forma adequada, e a escolha do tipo correto pode impactar tanto a eficiência quanto a precisão da sua análise de dados. 

## 03) IMPORTANDO UM DATASET
Importar dados é uma das primeiras etapas em qualquer análise de dados. Pandas oferece várias maneiras de carregar dados de diferentes formatos para um DataFrame. Abaixo estão os métodos mais comuns para importar datasets.

### IMPORTANDO DADOS DE UM ARQUIVO CSV
O formato CSV (Comma-Separated Values) é um dos formatos mais comuns para armazenar dados tabulares. Para importar um arquivo CSV, use o método `pd.read_csv()`.

```python
import pandas as pd

# Substitua 'caminho/para/seu/arquivo.csv' pelo caminho para o seu arquivo CSV
df_csv = pd.read_csv('caminho/para/seu/arquivo.csv')

# Exibir as primeiras linhas do DataFrame
print(df_csv.head())
```

### IMPORTANDO DADOS DE UM ARQUIVO EXCEL
Para importar dados de um arquivo Excel (.xls ou .xlsx), use o método `pd.read_excel()`. Você pode especificar a planilha se o arquivo tiver múltiplas planilhas.

```python
import pandas as pd

# Substitua 'caminho/para/seu/arquivo.xlsx' pelo caminho para o seu arquivo Excel
# Use o argumento 'sheet_name' para especificar a planilha se necessário
df_excel = pd.read_excel('caminho/para/seu/arquivo.xlsx', sheet_name='Planilha1')

# Exibir as primeiras linhas do DataFrame
print(df_excel.head())
```

### IMPORTANDO DADOS DE UM ARQUIVO JSON
Para arquivos no formato JSON, use o método `pd.read_json()`. JSON é um formato de dados hierárquico e pode ser usado para representar dados mais complexos.

```python
import pandas as pd

# Substitua 'caminho/para/seu/arquivo.json' pelo caminho para o seu arquivo JSON
df_json = pd.read_json('caminho/para/seu/arquivo.json')

# Exibir as primeiras linhas do DataFrame
print(df_json.head())
```

### IMPORTANDO DADOS DE UM ARQUIVO SQL
Para importar dados de um banco de dados SQL, use o método `pd.read_sql()`. Você precisará de uma conexão com o banco de dados.

```python
import pandas as pd
import sqlite3

# Conectar ao banco de dados SQLite (ou outro tipo de banco de dados)
conn = sqlite3.connect('caminho/para/seu/banco_de_dados.db')

# Executar uma consulta SQL e carregar os dados em um DataFrame
df_sql = pd.read_sql('SELECT * FROM sua_tabela', conn)

# Fechar a conexão
conn.close()

# Exibir as primeiras linhas do DataFrame
print(df_sql.head())
```

### IMPORTANDO DADOS DE UM ARQUIVO PARQUET
O Parquet é um formato de arquivo colunar eficiente para análise de dados. Para importar dados de um arquivo Parquet, use o método `pd.read_parquet()`.

```python
import pandas as pd

# Substitua 'caminho/para/seu/arquivo.parquet' pelo caminho para o seu arquivo Parquet
df_parquet = pd.read_parquet('caminho/para/seu/arquivo.parquet')

# Exibir as primeiras linhas do DataFrame
print(df_parquet.head())
```

### IMPORTANDO DADOS DE UM ARQUIVO HDF5
HDF5 é um formato de arquivo para armazenar grandes volumes de dados. Use o método `pd.read_hdf()` para importar dados de arquivos HDF5.

```python
import pandas as pd

# Substitua 'caminho/para/seu/arquivo.h5' pelo caminho para o seu arquivo HDF5
df_hdf = pd.read_hdf('caminho/para/seu/arquivo.h5', 'sua_chave')

# Exibir as primeiras linhas do DataFrame
print(df_hdf.head())
```

### CONCLUSÃO
Pandas suporta a leitura de dados de uma ampla variedade de formatos de arquivo, tornando-o uma ferramenta flexível para análise de dados. Dependendo do formato dos seus dados e da fonte, você pode escolher o método mais apropriado para importar seus datasets para um DataFrame do Pandas. 

## 04)INFORMAÇÕES DO DATASET 
Após importar um dataset para um DataFrame em Pandas, é crucial entender a estrutura e o conteúdo dos dados. Pandas oferece várias funções para obter informações sobre o DataFrame e explorar seus dados. Aqui estão algumas das funções e métodos mais úteis para obter informações sobre o seu dataset:

### VISUALIZANDO AS PRIMEIRAS E ÚLTIMAS LINHAS
1. **`head()`**:
   - Exibe as primeiras linhas do DataFrame. Por padrão, mostra as primeiras 5 linhas.

   ```python
   print(df.head())
   ```

2. **`tail()`**:
   - Exibe as últimas linhas do DataFrame. Por padrão, mostra as últimas 5 linhas.

   ```python
   print(df.tail())
   ```

### EXIBINDO ESTATÍSTICAS DESCRITIVAS
3. **`describe()`**:
   - Fornece estatísticas descritivas para colunas numéricas, como média, desvio padrão, valor mínimo e máximo.

   ```python
   print(df.describe())
   ```

4. **`describe(include='all')`**:
   - Fornece estatísticas descritivas para todas as colunas, incluindo não numéricas.

   ```python
   print(df.describe(include='all'))
   ```

### VISUALIZANDO INFORMAÇÕES GERAIS
5. **`info()`**:
   - Exibe um resumo do DataFrame, incluindo o número de entradas, o tipo de dados de cada coluna e o número de valores não nulos.

   ```python
   print(df.info())
   ```

### VERIFICANDO TIPOS DE DADOS
6. **`dtypes`**:
   - Exibe os tipos de dados de cada coluna.

   ```python
   print(df.dtypes)
   ```

### VERIFICANDO VALORES FALTANTES
7. **`isnull()`**:
   - Cria um DataFrame booleano que indica onde há valores faltantes.

   ```python
   print(df.isnull())
   ```

8. **`sum()`**:
   - Somar os valores booleanos do DataFrame gerado por `isnull()` para contar valores faltantes por coluna.

   ```python
   print(df.isnull().sum())
   ```

### VERIFICANDO DADOS ÚNICOS
9. **`unique()`**:
   - Exibe os valores únicos de uma coluna.

   ```python
   print(df['coluna'].unique())
   ```

10. **`value_counts()`**:
    - Conta a frequência de valores únicos em uma coluna.

    ```python
    print(df['coluna'].value_counts())
    ```

### CONTANDO O NÚMERO DE LINHAS E COLUNAS
11. **`shape`**:
    - Exibe o número de linhas e colunas do DataFrame.

    ```python
    print(df.shape)
    ```

### CHECANDO O ÍNDICE
12. **`index`**:
    - Exibe o índice do DataFrame.

    ```python
    print(df.index)
    ```

### CHECANDO COLUNAS
13. **`columns`**:
    - Exibe os nomes das colunas do DataFrame.

    ```python
    print(df.columns)
    ```

### VERIFICANDO VALORES NULOS
14. **`dropna()`**:
    - Remove linhas ou colunas com valores nulos.

    ```python
    df_cleaned = df.dropna()
    ```

15. **`fillna()`**:
    - Preenche valores nulos com um valor especificado.

    ```python
    df_filled = df.fillna(0)
    ```

### CONCLUSÃO
Essas funções e métodos fornecem uma visão abrangente do seu dataset e ajudam a identificar problemas como valores faltantes e tipos de dados incorretos. Ter uma compreensão clara das características do seu DataFrame é fundamental para realizar uma análise de dados eficaz e preparar os dados para operações mais complexas. 

## 05) DATAFRAME
O `DataFrame` é a estrutura de dados fundamental do Pandas para armazenar e manipular dados tabulares. Ele é semelhante a uma tabela em um banco de dados ou a uma planilha em uma ferramenta de planilha, com linhas e colunas que podem conter diferentes tipos de dados.

### CRIAÇÃO DE UM DATAFRAME
Você pode criar um DataFrame de várias maneiras. Aqui estão alguns exemplos comuns:

1. **Criar um DataFrame a partir de um Dicionário**

   ```python
   import pandas as pd

   data = {
       'Nome': ['Ana', 'Bruno', 'Carlos', 'Diana'],
       'Idade': [23, 35, 45, 29],
       'Cidade': ['São Paulo', 'Rio de Janeiro', 'Curitiba', 'Belo Horizonte']
   }

   df = pd.DataFrame(data)
   print(df)
   ```

2. **Criar um DataFrame a partir de uma Lista de Listas**

   ```python
   import pandas as pd

   data = [
       ['Ana', 23, 'São Paulo'],
       ['Bruno', 35, 'Rio de Janeiro'],
       ['Carlos', 45, 'Curitiba'],
       ['Diana', 29, 'Belo Horizonte']
   ]

   columns = ['Nome', 'Idade', 'Cidade']

   df = pd.DataFrame(data, columns=columns)
   print(df)
   ```

3. **Criar um DataFrame a partir de um Arquivo CSV**

   ```python
   import pandas as pd

   df = pd.read_csv('caminho/para/seu/arquivo.csv')
   print(df)
   ```

### ESTRUTURA DE UM DATAFRAME
Um DataFrame é composto por:

- **Índice**: Identifica cada linha de forma única. Pode ser numérico, de datas, ou de qualquer outro tipo.
- **Colunas**: Identificam os dados em cada coluna. Cada coluna pode ter um nome e um tipo de dado.
- **Valores**: Os dados armazenados em cada célula do DataFrame.

### OPERAÇÕES COM DATAFRAMES
1. **Visualizar as Primeiras e Últimas Linhas**

   ```python
   print(df.head())  # Primeiras 5 linhas
   print(df.tail())  # Últimas 5 linhas
   ```

2. **Selecionar Colunas**

   ```python
   print(df['Nome'])           # Selecionar a coluna 'Nome'
   print(df[['Nome', 'Idade']])  # Selecionar múltiplas colunas
   ```

3. **Selecionar Linhas**

   ```python
   print(df.loc[0])          # Selecionar a linha com índice 0
   print(df.iloc[0])         # Selecionar a primeira linha usando a posição
   ```

4. **Filtrar Dados**

   ```python
   df_filtrado = df[df['Idade'] > 30]
   print(df_filtrado)
   ```

5. **Adicionar e Modificar Colunas**

   ```python
   df['NovaColuna'] = df['Idade'] * 2  # Adicionar uma nova coluna
   df['Idade'] = df['Idade'] + 1       # Modificar uma coluna existente
   print(df)
   ```

6. **Agrupar e Agregar Dados**

   ```python
   df_grouped = df.groupby('Cidade').mean()
   print(df_grouped)
   ```

7. **Ordenar Dados**

   ```python
   df_sorted = df.sort_values(by='Idade', ascending=False)  # Ordenar por idade de forma decrescente
   print(df_sorted)
   ```

8. **Lidar com Dados Faltantes**

   - **Remover Dados Faltantes**:

     ```python
     df_cleaned = df.dropna()
     ```

   - **Preencher Dados Faltantes**:

     ```python
     df_filled = df.fillna(0)
     ```

### FUNÇÕES ÚTEIS
1. **`info()`**:
   - Exibe um resumo do DataFrame, incluindo o número de entradas, tipos de dados e valores não nulos.

   ```python
   print(df.info())
   ```

2. **`describe()`**:
   - Fornece estatísticas descritivas das colunas numéricas.

   ```python
   print(df.describe())
   ```

3. **`shape`**:
   - Exibe o número de linhas e colunas.

   ```python
   print(df.shape)
   ```

4. **`columns`**:
   - Exibe os nomes das colunas.

   ```python
   print(df.columns)
   ```

5. **`index`**:
   - Exibe o índice do DataFrame.

   ```python
   print(df.index)
   ```

### CONCLUSÃO
O DataFrame é uma estrutura fundamental no Pandas para análise de dados, permitindo uma variedade de operações para manipular e explorar dados tabulares. Compreender como criar, modificar e analisar DataFrames é essencial para qualquer trabalho com dados em Python. 

## 06) SERIES
A `Series` é uma das estruturas de dados fundamentais do Pandas, representando uma coluna unidimensional de dados. Pode ser pensada como uma coluna em uma tabela ou um array unidimensional. Cada `Series` possui um índice que rotula seus valores, permitindo o acesso e manipulação de dados de maneira eficiente.

### CRIAÇÃO DE UMA SERIES
Você pode criar uma `Series` a partir de uma variedade de fontes de dados, como listas, arrays, dicionários e até mesmo séries de tempo.

1. **Criar uma Series a partir de uma Lista**

   ```python
   import pandas as pd

   s = pd.Series([1, 3, 5, 7, 9])
   print(s)
   ```

2. **Criar uma Series a partir de um Dicionário**

   ```python
   data = {'a': 10, 'b': 20, 'c': 30}
   s = pd.Series(data)
   print(s)
   ```

3. **Criar uma Series com um Índice Personalizado**

   ```python
   data = [100, 200, 300]
   index = ['A', 'B', 'C']
   s = pd.Series(data, index=index)
   print(s)
   ```

4. **Criar uma Series a partir de um Array Numpy**

   ```python
   import numpy as np
   data = np.array([1.5, 2.5, 3.5])
   s = pd.Series(data)
   print(s)
   ```

### ACESSO E SELEÇÃO DE DADOS
1. **Acessar um Valor pelo Índice**

   ```python
   print(s['A'])  # Acessa o valor associado ao índice 'A'
   ```

2. **Acessar um Valor pelo Posição**

   ```python
   print(s[0])  # Acessa o primeiro valor
   ```

3. **Selecionar um Subconjunto de Dados**

   ```python
   print(s[['A', 'B']])  # Seleciona os valores para os índices 'A' e 'B'
   ```

4. **Usar Condições para Filtrar Dados**

   ```python
   print(s[s > 15])  # Seleciona os valores maiores que 15
   ```

### OPERANDO COM SERIES
1. **Realizar Operações Matemáticas**

   ```python
   s = pd.Series([1, 2, 3])
   s2 = pd.Series([4, 5, 6])
   print(s + s2)  # Soma os valores das duas séries
   ```

2. **Aplicar Funções**

   ```python
   print(s.apply(lambda x: x ** 2))  # Eleva cada valor ao quadrado
   ```

3. **Calcular Estatísticas**

   ```python
   print(s.mean())   # Média dos valores
   print(s.sum())    # Soma dos valores
   ```

### MANIPULAÇÃO DE SERIES
1. **Renomear o Índice**

   ```python
   s.index = ['X', 'Y', 'Z']
   print(s)
   ```

2. **Alterar o Tipo de Dados**

   ```python
   s = pd.Series([1.1, 2.2, 3.3])
   s = s.astype('int')
   print(s)
   ```

3. **Verificar Valores Nulos**

   ```python
   print(s.isnull())  # Verifica se há valores nulos
   ```

4. **Preencher Valores Nulos**

   ```python
   s = pd.Series([1, np.nan, 3])
   s = s.fillna(0)  # Preenche valores nulos com 0
   print(s)
   ```

### FUNCIONALIDADES ADICIONAIS
1. **`value_counts()`**

   - Conta a frequência de valores únicos na Series.

   ```python
   s = pd.Series(['a', 'b', 'a', 'b', 'a'])
   print(s.value_counts())
   ```

2. **`unique()`**

   - Retorna um array com os valores únicos da Series.

   ```python
   print(s.unique())
   ```

3. **`index` e `values`**

   - **`index`**: Retorna o índice da Series.
   - **`values`**: Retorna os valores da Series como um array.

   ```python
   print(s.index)
   print(s.values)
   ```

### CONCLUSÃO
A `Series` é uma estrutura de dados muito útil em Pandas para armazenar e manipular dados unidimensionais. Com seu índice associado, ela oferece uma maneira flexível e poderosa de acessar e operar sobre dados.

## 07) ATRIBUINDO VALORES A UM DATAFRAME
Uma das tarefas comuns ao trabalhar com DataFrames no Pandas é atribuir valores a novas colunas ou modificar colunas existentes. Aqui estão diferentes formas de atribuição e atualização de valores em um DataFrame:

### 1. ADICIONAR UMA NOVA COLUNA
Você pode adicionar uma nova coluna a um DataFrame simplesmente atribuindo uma lista, uma `Series` ou outro tipo de dados a um novo nome de coluna.

```python
import pandas as pd

# Criar um DataFrame exemplo
df = pd.DataFrame({
    'Nome': ['Ana', 'Bruno', 'Carlos'],
    'Idade': [23, 35, 45]
})

# Adicionar uma nova coluna
df['Cidade'] = ['São Paulo', 'Rio de Janeiro', 'Curitiba']

print(df)
```

### 2. MODIFICAR UMA COLUNA EXISTENTE
Para modificar uma coluna existente, você pode atribuir novos valores à coluna usando o nome da coluna.

```python
import pandas as pd

# Criar um DataFrame exemplo
df = pd.DataFrame({
    'Nome': ['Ana', 'Bruno', 'Carlos'],
    'Idade': [23, 35, 45]
})

# Modificar os valores da coluna 'Idade'
df['Idade'] = [24, 36, 46]

print(df)
```

### 3. ATRIBUIR VALORES BASEADOS EM CONDIÇÕES
Você pode usar condições para atribuir valores a uma coluna baseada em valores de outras colunas.

```python
import pandas as pd

# Criar um DataFrame exemplo
df = pd.DataFrame({
    'Nome': ['Ana', 'Bruno', 'Carlos'],
    'Idade': [23, 35, 45]
})

# Adicionar uma coluna 'Categoria' baseada na coluna 'Idade'
df['Categoria'] = df['Idade'].apply(lambda x: 'Jovem' if x < 30 else 'Adulto')

print(df)
```

### 4. ATRIBUIR VALORES USANDO `loc` E `iloc`
Para atualizar valores em linhas e colunas específicas, use `loc` e `iloc`.

- **Usando `loc`** (baseado em rótulo de índice e coluna):

  ```python
  import pandas as pd

  # Criar um DataFrame exemplo
  df = pd.DataFrame({
      'Nome': ['Ana', 'Bruno', 'Carlos'],
      'Idade': [23, 35, 45]
  })

  # Atualizar um valor específico
  df.loc[1, 'Idade'] = 36

  print(df)
  ```

- **Usando `iloc`** (baseado em posição de índice e coluna):

  ```python
  import pandas as pd

  # Criar um DataFrame exemplo
  df = pd.DataFrame({
      'Nome': ['Ana', 'Bruno', 'Carlos'],
      'Idade': [23, 35, 45]
  })

  # Atualizar um valor específico
  df.iloc[2, 1] = 46

  print(df)
  ```

### 5. ATRIBUIR VALORES USANDO `apply()`
Você pode usar o método `apply()` para aplicar uma função a uma coluna ou linha do DataFrame.

```python
import pandas as pd

# Criar um DataFrame exemplo
df = pd.DataFrame({
    'Nome': ['Ana', 'Bruno', 'Carlos'],
    'Idade': [23, 35, 45]
})

# Adicionar uma coluna 'Idade em Meses'
df['Idade em Meses'] = df['Idade'].apply(lambda x: x * 12)

print(df)
```

### 6. ATRIBUIR VALORES A PARTIR DE OUTRAS COLUNAS
Você pode criar uma nova coluna com base na operação de outras colunas.

```python
import pandas as pd

# Criar um DataFrame exemplo
df = pd.DataFrame({
    'Salário Base': [3000, 3500, 4000],
    'Bonificação': [200, 300, 250]
})

# Adicionar uma coluna 'Salário Total'
df['Salário Total'] = df['Salário Base'] + df['Bonificação']

print(df)
```

### 7. ADICIONAR VALORES EM UMA LINHA NOVA
Para adicionar uma nova linha ao DataFrame, você pode usar o método `append()`.

```python
import pandas as pd

# Criar um DataFrame exemplo
df = pd.DataFrame({
    'Nome': ['Ana', 'Bruno', 'Carlos'],
    'Idade': [23, 35, 45]
})

# Adicionar uma nova linha
nova_linha = pd.DataFrame({'Nome': ['Diana'], 'Idade': [30]})
df = df.append(nova_linha, ignore_index=True)

print(df)
```

### CONCLUSÃO
Atribuir e atualizar valores em um DataFrame é uma parte essencial da manipulação de dados no Pandas. Com as funções e métodos acima, você pode adicionar novas colunas, modificar colunas existentes, atribuir valores com base em condições e muito mais. 

## 08) CRIANDO COLUNAS/ATRIBUTOS
Adicionar novas colunas a um DataFrame no Pandas é uma operação comum que pode ser realizada de várias maneiras. Essas novas colunas podem ser preenchidas com valores constantes, calculados com base em outras colunas, ou mesmo importados de fontes externas.

Aqui estão as formas mais comuns de criar novas colunas em um DataFrame:

### 1. CRIAR UMA NOVA COLUNA COM VALORES CONSTANTES
Você pode adicionar uma nova coluna e preenchê-la com um valor constante.

```python
import pandas as pd

# Criar um DataFrame exemplo
df = pd.DataFrame({
    'Nome': ['Ana', 'Bruno', 'Carlos'],
    'Idade': [23, 35, 45]
})

# Adicionar uma nova coluna com um valor constante
df['Cidade'] = 'São Paulo'

print(df)
```

### 2. CRIAR UMA NOVA COLUNA COM VALORES BASEADOS EM OUTRAS COLUNAS
Você pode criar uma nova coluna com base em cálculos realizados com outras colunas.

```python
import pandas as pd

# Criar um DataFrame exemplo
df = pd.DataFrame({
    'Salário Base': [3000, 3500, 4000],
    'Bonificação': [200, 300, 250]
})

# Adicionar uma nova coluna 'Salário Total'
df['Salário Total'] = df['Salário Base'] + df['Bonificação']

print(df)
```

### 3. USAR A FUNÇÃO `apply()` PARA CRIAR NOVAS COLUNAS
A função `apply()` permite aplicar uma função a cada elemento de uma coluna, e você pode usar isso para criar novas colunas.

```python
import pandas as pd

# Criar um DataFrame exemplo
df = pd.DataFrame({
    'Nome': ['Ana', 'Bruno', 'Carlos'],
    'Idade': [23, 35, 45]
})

# Adicionar uma nova coluna 'Categoria' baseada na idade
df['Categoria'] = df['Idade'].apply(lambda x: 'Jovem' if x < 30 else 'Adulto')

print(df)
```

### 4. CRIAR UMA NOVA COLUNA COM BASE EM CONDIÇÕES
Você pode usar o método `numpy.where()` para criar novas colunas baseadas em condições lógicas.

```python
import pandas as pd
import numpy as np

# Criar um DataFrame exemplo
df = pd.DataFrame({
    'Nome': ['Ana', 'Bruno', 'Carlos'],
    'Idade': [23, 35, 45]
})

# Adicionar uma nova coluna 'Idade em Categorias'
df['Faixa Etária'] = np.where(df['Idade'] < 30, 'Jovem', 'Adulto')

print(df)
```

### 5. CRIAR UMA NOVA COLUNA COM VALORES ALEATÓRIOS
Você pode usar bibliotecas como `numpy` para gerar valores aleatórios e adicionar esses valores a uma nova coluna.

```python
import pandas as pd
import numpy as np

# Criar um DataFrame exemplo
df = pd.DataFrame({
    'Nome': ['Ana', 'Bruno', 'Carlos'],
    'Idade': [23, 35, 45]
})

# Adicionar uma nova coluna com valores aleatórios
df['Valor Aleatório'] = np.random.rand(len(df))

print(df)
```

### 6. CRIAR UMA NOVA COLUNA COM VALORES A PARTIR DE UMA LISTA
Você pode criar uma nova coluna a partir de uma lista de valores, garantindo que o tamanho da lista seja igual ao número de linhas no DataFrame.

```python
import pandas as pd

# Criar um DataFrame exemplo
df = pd.DataFrame({
    'Nome': ['Ana', 'Bruno', 'Carlos'],
    'Idade': [23, 35, 45]
})

# Adicionar uma nova coluna a partir de uma lista
nova_coluna = [100, 200, 300]
df['Novo Atributo'] = nova_coluna

print(df)
```

### 7. CRIAR UMA NOVA COLUNA COM VALORES DE UMA FUNÇÃO EXTERNA
Você pode definir uma função externa e aplicá-la para criar uma nova coluna.

```python
import pandas as pd

# Criar um DataFrame exemplo
df = pd.DataFrame({
    'Nome': ['Ana', 'Bruno', 'Carlos'],
    'Idade': [23, 35, 45]
})

# Definir uma função externa
def categorizar_idade(idade):
    if idade < 30:
        return 'Jovem'
    elif idade < 60:
        return 'Adulto'
    else:
        return 'Idoso'

# Adicionar uma nova coluna usando a função externa
df['Categoria'] = df['Idade'].apply(categorizar_idade)

print(df)
```

### CONCLUSÃO
Adicionar e criar novas colunas em um DataFrame no Pandas é uma operação flexível e poderosa que permite personalizar e enriquecer seus dados conforme necessário. Usando essas técnicas, você pode facilmente adicionar novos atributos e realizar cálculos complexos para análise de dados. 

## 09) ÍNDICES
No Pandas, o índice é uma parte crucial da estrutura de dados de um DataFrame, funcionando como rótulos para as linhas. Ele ajuda a acessar e organizar dados de maneira eficiente. Os índices podem ser personalizados e manipulados de várias maneiras para atender às necessidades específicas da análise de dados.

### TIPOS DE ÍNDICES
1. **Índice Padrão (Numérico)**

   Por padrão, o Pandas usa um índice numérico baseado em zero.

   ```python
   import pandas as pd

   df = pd.DataFrame({
       'Nome': ['Ana', 'Bruno', 'Carlos'],
       'Idade': [23, 35, 45]
   })

   print(df)
   ```

   Saída:
   ```
      Nome  Idade
   0   Ana     23
   1  Bruno     35
   2 Carlos     45
   ```

2. **Índice Personalizado**

   Você pode definir um índice personalizado ao criar o DataFrame ou alterar o índice existente.

   ```python
   import pandas as pd

   df = pd.DataFrame({
       'Nome': ['Ana', 'Bruno', 'Carlos'],
       'Idade': [23, 35, 45]
   }, index=['a', 'b', 'c'])

   print(df)
   ```

   Saída:
   ```
         Nome  Idade
   a      Ana     23
   b     Bruno     35
   c   Carlos     45
   ```

### MANIPULANDO ÍNDICES
1. **Acessar um Valor Usando o Índice**

   Use o método `loc` para acessar linhas baseadas em índices personalizados.

   ```python
   print(df.loc['b'])  # Acessa a linha com índice 'b'
   ```

2. **Selecionar um Subconjunto de Dados**

   Você pode selecionar linhas baseadas em índices usando `loc`.

   ```python
   print(df.loc[['a', 'c']])  # Seleciona as linhas com índices 'a' e 'c'
   ```

3. **Modificar o Índice**

   Você pode alterar o índice de um DataFrame usando o atributo `index`.

   ```python
   df.index = ['x', 'y', 'z']
   print(df)
   ```

   Saída:
   ```
         Nome  Idade
   x      Ana     23
   y     Bruno     35
   z   Carlos     45
   ```

4. **Resetar o Índice**

   Para redefinir o índice para o padrão numérico e adicionar o índice antigo como uma coluna, use `reset_index()`.

   ```python
   df_reset = df.reset_index()
   print(df_reset)
   ```

   Saída:
   ```
     index     Nome  Idade
   0     x      Ana     23
   1     y     Bruno     35
   2     z   Carlos     45
   ```

   Se você não quiser manter a coluna do índice antigo, use `drop=True`.

   ```python
   df_reset = df.reset_index(drop=True)
   print(df_reset)
   ```

5. **Definir um Índice Baseado em Colunas**

   Você pode definir uma coluna existente como o índice usando `set_index()`.

   ```python
   df = pd.DataFrame({
       'Nome': ['Ana', 'Bruno', 'Carlos'],
       'Idade': [23, 35, 45]
   })

   df = df.set_index('Nome')
   print(df)
   ```

   Saída:
   ```
          Idade
   Nome        
   Ana       23
   Bruno     35
   Carlos    45
   ```

6. **Alterar o Nome do Índice**

   Você pode nomear o índice do DataFrame usando o atributo `name`.

   ```python
   df.index.name = 'Identificador'
   print(df)
   ```

   Saída:
   ```
                  Idade
   Identificador       
   Ana                23
   Bruno              35
   Carlos             45
   ```

### OPERANDO COM ÍNDICES
1. **Verificar o Índice**

   Use o atributo `index` para verificar os índices atuais.

   ```python
   print(df.index)
   ```

2. **Verificar se um Índice Existe**

   Use o operador `in` para verificar se um índice específico existe no DataFrame.

   ```python
   print('Ana' in df.index)  # Verifica se 'Ana' está no índice
   ```

3. **Reindexar um DataFrame**

   Você pode reindexar um DataFrame para adicionar ou remover índices usando `reindex()`.

   ```python
   new_index = ['Ana', 'Carlos', 'Diana']
   df_reindexed = df.reindex(new_index)
   print(df_reindexed)
   ```

   Saída:
   ```
          Idade
   Ana       23
   Carlos    45
   Diana     NaN
   ```

### CONCLUSÃO
O índice em um DataFrame do Pandas desempenha um papel vital na organização e acesso dos dados. A capacidade de personalizar, modificar e manipular índices oferece flexibilidade na análise e apresentação de dados. 

## 10) SELEÇÃO POR ÍNDICES
Selecionar dados com base em índices é uma parte fundamental do trabalho com DataFrames no Pandas. Isso permite que você acesse, modifique e analise linhas e colunas de maneira eficiente. O Pandas oferece várias maneiras de realizar essa seleção, dependendo se você está lidando com índices baseados em rótulos ou posições.

### SELEÇÃO DE LINHAS POR ÍNDICE
1. **Selecionar Linha por Índice com `loc`**

   Use o método `loc` para acessar uma linha específica com base no índice rótulo.

   ```python
   import pandas as pd

   df = pd.DataFrame({
       'Nome': ['Ana', 'Bruno', 'Carlos'],
       'Idade': [23, 35, 45]
   }, index=['a', 'b', 'c'])

   # Selecionar linha com índice 'b'
   linha = df.loc['b']
   print(linha)
   ```

   Saída:
   ```
   Nome    Bruno
   Idade      35
   Name: b, dtype: object
   ```

2. **Selecionar Múltiplas Linhas por Índice com `loc`**

   Você pode selecionar múltiplas linhas fornecendo uma lista de índices.

   ```python
   linhas = df.loc[['a', 'c']]
   print(linhas)
   ```

   Saída:
   ```
         Nome  Idade
   a      Ana     23
   c   Carlos     45
   ```

3. **Selecionar Linha por Posição com `iloc`**

   Use o método `iloc` para selecionar linhas com base na posição inteira.

   ```python
   linha = df.iloc[1]  # Seleciona a segunda linha (posição 1)
   print(linha)
   ```

   Saída:
   ```
   Nome    Bruno
   Idade      35
   Name: b, dtype: object
   ```

4. **Selecionar Múltiplas Linhas por Posição com `iloc`**

   Forneça uma lista de posições para selecionar múltiplas linhas.

   ```python
   linhas = df.iloc[[0, 2]]  # Seleciona as linhas nas posições 0 e 2
   print(linhas)
   ```

   Saída:
   ```
         Nome  Idade
   a      Ana     23
   c   Carlos     45
   ```

### SELEÇÃO DE COLUNAS
1. **Selecionar Coluna por Nome**

   Você pode acessar uma coluna usando o nome da coluna.

   ```python
   coluna = df['Nome']
   print(coluna)
   ```

   Saída:
   ```
   a       Ana
   b     Bruno
   c   Carlos
   Name: Nome, dtype: object
   ```

2. **Selecionar Múltiplas Colunas**

   Use uma lista de nomes de colunas para selecionar várias colunas.

   ```python
   colunas = df[['Nome', 'Idade']]
   print(colunas)
   ```

   Saída:
   ```
         Nome  Idade
   a      Ana     23
   b    Bruno     35
   c   Carlos     45
   ```

### SELEÇÃO DE LINHAS E COLUNAS COMBINADAS
1. **Selecionar um Valor Específico com `loc`**

   Para acessar um valor específico usando `loc`, forneça o índice da linha e o nome da coluna.

   ```python
   valor = df.loc['b', 'Nome']
   print(valor)
   ```

   Saída:
   ```
   Bruno
   ```

2. **Selecionar um Valor Específico com `iloc`**

   Para acessar um valor específico usando `iloc`, forneça a posição da linha e a posição da coluna.

   ```python
   valor = df.iloc[1, 0]  # Linha 1, Coluna 0
   print(valor)
   ```

   Saída:
   ```
   Bruno
   ```

3. **Selecionar Um Subconjunto de Dados**

   Você pode combinar `loc` e `iloc` para selecionar um subconjunto de dados.

   ```python
   subset = df.loc[['a', 'b'], ['Nome']]
   print(subset)
   ```

   Saída:
   ```
         Nome
   a      Ana
   b    Bruno
   ```

   ```python
   subset = df.iloc[0:2, 1]  # Linhas 0 a 1, Coluna 1
   print(subset)
   ```

   Saída:
   ```
   a    23
   b    35
   Name: Idade, dtype: int64
   ```

### SELEÇÃO COM CONDIÇÕES
1. **Selecionar Linhas com Condições**

   Você pode usar condições para filtrar linhas.

   ```python
   filtrado = df[df['Idade'] > 30]
   print(filtrado)
   ```

   Saída:
   ```
         Nome  Idade
   b    Bruno     35
   c   Carlos     45
   ```

2. **Selecionar Linhas e Colunas com Condições**

   Para aplicar condições e selecionar colunas específicas, combine filtragem e seleção de colunas.

   ```python
   filtrado = df[df['Idade'] > 30][['Nome']]
   print(filtrado)
   ```

   Saída:
   ```
         Nome
   b    Bruno
   c   Carlos
   ```

### CONCLUSÃO
Selecionar dados por índices é uma habilidade essencial ao trabalhar com DataFrames no Pandas. Com métodos como `loc` e `iloc`, você pode acessar, filtrar e manipular dados de maneira eficiente. 

## 11) SELEÇÃO POR LABELS
No Pandas, a seleção por labels é feita principalmente com o método `loc`, que permite acessar dados usando rótulos de índices e colunas. Essa abordagem é útil quando você deseja acessar ou filtrar dados com base em nomes e rótulos específicos em vez de posições inteiras.

### SELEÇÃO DE LINHAS POR LABEL
1. **Selecionar uma Linha Única pelo Label**

   Use o método `loc` para acessar uma linha específica baseada no rótulo do índice.

   ```python
   import pandas as pd

   df = pd.DataFrame({
       'Nome': ['Ana', 'Bruno', 'Carlos'],
       'Idade': [23, 35, 45]
   }, index=['a', 'b', 'c'])

   linha = df.loc['b']
   print(linha)
   ```

   Saída:
   ```
   Nome    Bruno
   Idade      35
   Name: b, dtype: object
   ```

2. **Selecionar Múltiplas Linhas por Labels**

   Você pode selecionar várias linhas fornecendo uma lista de rótulos.

   ```python
   linhas = df.loc[['a', 'c']]
   print(linhas)
   ```

   Saída:
   ```
         Nome  Idade
   a      Ana     23
   c   Carlos     45
   ```

3. **Selecionar Intervalos de Linhas por Labels**

   Use a notação de fatias para selecionar um intervalo de linhas por rótulo.

   ```python
   intervalo = df.loc['a':'b']
   print(intervalo)
   ```

   Saída:
   ```
         Nome  Idade
   a      Ana     23
   b    Bruno     35
   ```

### SELEÇÃO DE COLUNAS POR LABEL
1. **Selecionar Uma Coluna por Label**

   Para acessar uma coluna específica, use o nome da coluna.

   ```python
   coluna = df.loc[:, 'Nome']
   print(coluna)
   ```

   Saída:
   ```
   a       Ana
   b     Bruno
   c   Carlos
   Name: Nome, dtype: object
   ```

2. **Selecionar Múltiplas Colunas por Labels**

   Forneça uma lista de rótulos de colunas para selecionar várias colunas.

   ```python
   colunas = df.loc[:, ['Nome', 'Idade']]
   print(colunas)
   ```

   Saída:
   ```
         Nome  Idade
   a      Ana     23
   b    Bruno     35
   c   Carlos     45
   ```

### SELEÇÃO COMBINADA DE LINHAS E COLUNAS POR LABEL
1. **Selecionar Valores Específicos**

   Para acessar um valor específico, forneça o rótulo da linha e da coluna.

   ```python
   valor = df.loc['b', 'Nome']
   print(valor)
   ```

   Saída:
   ```
   Bruno
   ```

2. **Selecionar Subconjunto de Dados**

   Combine linhas e colunas para selecionar um subconjunto de dados.

   ```python
   subset = df.loc[['a', 'c'], ['Nome']]
   print(subset)
   ```

   Saída:
   ```
         Nome
   a      Ana
   c   Carlos
   ```

3. **Selecionar Com Condições**

   Filtre linhas com base em condições e selecione colunas específicas.

   ```python
   filtrado = df.loc[df['Idade'] > 30, ['Nome']]
   print(filtrado)
   ```

   Saída:
   ```
         Nome
   b    Bruno
   c   Carlos
   ```

### SELEÇÃO DE LINHAS E COLUNAS COM LABELS MULTIPLOS
1. **Selecionar Várias Linhas e Várias Colunas**

   Utilize listas para selecionar múltiplas linhas e colunas.

   ```python
   subset = df.loc[['a', 'b'], ['Nome', 'Idade']]
   print(subset)
   ```

   Saída:
   ```
         Nome  Idade
   a      Ana     23
   b    Bruno     35
   ```

2. **Selecionar Intervalos de Linhas e Colunas**

   Use intervalos para selecionar múltiplas linhas e colunas.

   ```python
   subset = df.loc['a':'b', 'Nome']
   print(subset)
   ```

   Saída:
   ```
   a      Ana
   b    Bruno
   Name: Nome, dtype: object
   ```

### SELEÇÃO COM `query()`
1. **Filtrar Dados Usando `query()`**

   O método `query()` permite usar expressões para filtrar dados com base em condições.

   ```python
   filtrado = df.query('Idade > 30')
   print(filtrado)
   ```

   Saída:
   ```
         Nome  Idade
   b    Bruno     35
   c   Carlos     45
   ```

### CONCLUSÃO
Selecionar dados por labels no Pandas oferece uma maneira flexível e intuitiva de acessar e manipular dados. Usar `loc` para selecionar linhas e colunas por rótulos é uma prática comum e poderosa para análise de dados.

## 12) SELEÇÃO DE COLUNAS/ATRIBUTOS
A seleção de colunas em um DataFrame do Pandas é uma operação fundamental e pode ser feita de várias maneiras, dependendo das necessidades da sua análise. Aqui estão as formas mais comuns de selecionar colunas em um DataFrame.

### SELEÇÃO DE UMA ÚNICA COLUNA
1. **Selecionar uma Coluna Usando o Nome**

   Você pode acessar uma única coluna usando o nome da coluna como uma chave.

   ```python
   import pandas as pd

   df = pd.DataFrame({
       'Nome': ['Ana', 'Bruno', 'Carlos'],
       'Idade': [23, 35, 45],
       'Cidade': ['São Paulo', 'Rio de Janeiro', 'Belo Horizonte']
   })

   coluna_nome = df['Nome']
   print(coluna_nome)
   ```

   Saída:
   ```
   0      Ana
   1    Bruno
   2  Carlos
   Name: Nome, dtype: object
   ```

2. **Selecionar uma Coluna Usando o Acesso com `dot`**

   Quando o nome da coluna é um identificador válido, você pode usar a notação de ponto (`.`) para acessá-la.

   ```python
   coluna_idade = df.Idade
   print(coluna_idade)
   ```

   Saída:
   ```
   0    23
   1    35
   2    45
   Name: Idade, dtype: int64
   ```

### SELEÇÃO DE MÚLTIPLAS COLUNAS
1. **Selecionar Múltiplas Colunas Usando uma Lista de Nomes**

   Forneça uma lista de nomes de colunas para selecionar várias colunas.

   ```python
   colunas_nome_idade = df[['Nome', 'Idade']]
   print(colunas_nome_idade)
   ```

   Saída:
   ```
      Nome  Idade
   0    Ana     23
   1  Bruno     35
   2 Carlos     45
   ```

2. **Selecionar Múltiplas Colunas Usando `filter()`**

   O método `filter()` pode ser usado para selecionar colunas com base em critérios.

   ```python
   colunas = df.filter(items=['Nome', 'Cidade'])
   print(colunas)
   ```

   Saída:
   ```
      Nome        Cidade
   0    Ana    São Paulo
   1  Bruno  Rio de Janeiro
   2 Carlos  Belo Horizonte
   ```

### SELEÇÃO DE COLUNAS COM CONDIÇÕES
1. **Selecionar Colunas com Base em um Filtro Condicional**

   Use uma condição para filtrar linhas e, em seguida, selecione colunas específicas.

   ```python
   filtrado = df[df['Idade'] > 30][['Nome', 'Cidade']]
   print(filtrado)
   ```

   Saída:
   ```
      Nome           Cidade
   1  Bruno  Rio de Janeiro
   2 Carlos  Belo Horizonte
   ```

### SELEÇÃO DE COLUNAS POR INTERVALOS
1. **Selecionar Colunas por Intervalo de Índices**

   Utilize o método `iloc` para selecionar um intervalo de colunas por índice.

   ```python
   colunas_intervalo = df.iloc[:, 0:2]  # Seleciona as duas primeiras colunas
   print(colunas_intervalo)
   ```

   Saída:
   ```
      Nome  Idade
   0    Ana     23
   1  Bruno     35
   2 Carlos     45
   ```

### ALTERANDO O NOME DAS COLUNAS
1. **Renomear Colunas Usando `rename()`**

   Você pode renomear colunas usando o método `rename()`.

   ```python
   df_renomeado = df.rename(columns={'Nome': 'Nome Completo', 'Idade': 'Idade Anos'})
   print(df_renomeado)
   ```

   Saída:
   ```
     Nome Completo  Idade Anos           Cidade
   0           Ana           23        São Paulo
   1         Bruno           35    Rio de Janeiro
   2       Carlos           45  Belo Horizonte
   ```

2. **Renomear Colunas Diretamente**

   Alterar diretamente os nomes das colunas.

   ```python
   df.columns = ['Nome Completo', 'Idade Anos', 'Cidade']
   print(df)
   ```

   Saída:
   ```
     Nome Completo  Idade Anos           Cidade
   0           Ana           23        São Paulo
   1         Bruno           35    Rio de Janeiro
   2       Carlos           45  Belo Horizonte
   ```

### SELEÇÃO DE COLUNAS BASEADA EM FUNÇÕES
1. **Selecionar Colunas com Funções de Agregação**

   Use funções como `mean()`, `sum()`, etc., para selecionar colunas com base em cálculos.

   ```python
   soma_idade = df['Idade'].sum()
   print(soma_idade)
   ```

   Saída:
   ```
   103
   ```

2. **Selecionar Colunas Usando `apply()`**

   Use o método `apply()` para aplicar uma função a cada coluna.

   ```python
   df_nova_coluna = df.apply(lambda x: x + ' Extra', axis=1)
   print(df_nova_coluna)
   ```

   Saída:
   ```
     Nome Completo Extra  Idade Anos Extra          Cidade Extra
   0          Ana Extra              23 Extra       São Paulo Extra
   1        Bruno Extra             35 Extra   Rio de Janeiro Extra
   2      Carlos Extra             45 Extra Belo Horizonte Extra
   ```

### CONCLUSÃO
Selecionar e manipular colunas em um DataFrame é uma operação essencial ao trabalhar com dados no Pandas. Usar diferentes métodos e técnicas permite que você acesse, modifique e analise colunas de maneira eficiente.

## 13) SALVANDO UM DATASET NO PANDAS
Depois de manipular e analisar seus dados usando Pandas, você pode querer salvar o DataFrame em um formato de arquivo para uso futuro ou compartilhamento. O Pandas oferece suporte a vários formatos de arquivo para salvar DataFrames, como CSV, Excel, JSON, e HDF5.

### SALVANDO COMO CSV
1. **Salvar um DataFrame em um Arquivo CSV**

   O método `to_csv()` permite salvar um DataFrame em um arquivo CSV.

   ```python
   import pandas as pd

   # Criando um DataFrame de exemplo
   df = pd.DataFrame({
       'Nome': ['Ana', 'Bruno', 'Carlos'],
       'Idade': [23, 35, 45]
   })

   # Salvando o DataFrame em um arquivo CSV
   df.to_csv('dados.csv', index=False)
   ```

   - `index=False` é usado para não salvar o índice do DataFrame no arquivo CSV.

2. **Salvar CSV com Configurações Adicionais**

   Você pode ajustar várias configurações, como o delimitador ou a codificação.

   ```python
   df.to_csv('dados.csv', sep=';', encoding='utf-8', index=False)
   ```

   - `sep=';'` define o delimitador como ponto e vírgula.
   - `encoding='utf-8'` define a codificação do arquivo.

### SALVANDO COMO EXCEL
1. **Salvar um DataFrame em um Arquivo Excel**

   O método `to_excel()` permite salvar um DataFrame em um arquivo Excel.

   ```python
   df.to_excel('dados.xlsx', sheet_name='Sheet1', index=False)
   ```

   - `sheet_name='Sheet1'` define o nome da aba no arquivo Excel.
   - `index=False` é usado para não salvar o índice do DataFrame no arquivo Excel.

2. **Salvar Múltiplas Abas em um Arquivo Excel**

   Para salvar várias DataFrames em diferentes abas do mesmo arquivo Excel, use um objeto `ExcelWriter`.

   ```python
   with pd.ExcelWriter('dados_multiplas_abas.xlsx') as writer:
       df.to_excel(writer, sheet_name='Aba1', index=False)
       df.to_excel(writer, sheet_name='Aba2', index=False)
   ```

### SALVANDO COMO JSON
1. **Salvar um DataFrame em um Arquivo JSON**

   O método `to_json()` permite salvar um DataFrame em um arquivo JSON.

   ```python
   df.to_json('dados.json', orient='records', lines=True)
   ```

   - `orient='records'` define o formato JSON como uma lista de registros.
   - `lines=True` escreve o JSON em formato de linha por linha.

2. **Salvar JSON com Configurações Adicionais**

   Ajuste o formato e a codificação se necessário.

   ```python
   df.to_json('dados.json', orient='columns', encoding='utf-8')
   ```

   - `orient='columns'` salva os dados em formato de colunas.

### SALVANDO COMO HDF5
1. **Salvar um DataFrame em um Arquivo HDF5**

   O método `to_hdf()` permite salvar um DataFrame em um arquivo HDF5. Este formato é eficiente para armazenar grandes volumes de dados.

   ```python
   df.to_hdf('dados.h5', key='dados', mode='w')
   ```

   - `key='dados'` é a chave para acessar o DataFrame no arquivo HDF5.
   - `mode='w'` define o modo de abertura como escrita.

### SALVANDO COMO PARQUET
1. **Salvar um DataFrame em um Arquivo Parquet**

   O método `to_parquet()` permite salvar um DataFrame em um arquivo Parquet. Parquet é um formato de arquivo colunar eficiente para leitura e escrita de dados.

   ```python
   df.to_parquet('dados.parquet')
   ```

### CONCLUSÃO
Salvar seus dados em diferentes formatos de arquivo permite compartilhar e reutilizar os dados de maneira eficaz. Escolha o formato que melhor se adequa às suas necessidades e configurações. 

## 14-19) FILTRAGEM 
A filtragem de dados em um DataFrame do Pandas é uma técnica essencial para selecionar subconjuntos específicos de dados com base em condições. Você pode filtrar dados com base em valores, condições lógicas, e até mesmo utilizando funções de agregação. Abaixo estão os métodos e técnicas mais comuns para filtrar dados em um DataFrame.

### FILTRAGEM BÁSICA
1. **Filtrar Linhas com Base em uma Condição Simples**

   Para filtrar linhas com base em uma condição simples, você pode usar uma expressão booleana.

   ```python
   import pandas as pd

   # Criando um DataFrame de exemplo
   df = pd.DataFrame({
       'Nome': ['Ana', 'Bruno', 'Carlos', 'Diana'],
       'Idade': [23, 35, 45, 28]
   })

   # Filtrar linhas onde a idade é maior que 30
   filtrado = df[df['Idade'] > 30]
   print(filtrado)
   ```

   Saída:
   ```
      Nome  Idade
   1  Bruno     35
   2 Carlos     45
   ```

2. **Filtrar Linhas com Base em Múltiplas Condições**

   Combine várias condições usando operadores lógicos (`&` para `E`, `|` para `OU`).

   ```python
   # Filtrar linhas onde a idade é maior que 25 e menor que 40
   filtrado = df[(df['Idade'] > 25) & (df['Idade'] < 40)]
   print(filtrado)
   ```

   Saída:
   ```
      Nome  Idade
   0    Ana     23
   1  Bruno     35
   3  Diana     28
   ```

### FILTRAGEM COM CONDIÇÕES DE STRING
1. **Filtrar Linhas com Base em Condições de String**

   Para filtrar com base em condições de string, você pode usar métodos de string disponíveis no Pandas.

   ```python
   # Filtrar linhas onde o nome começa com 'A'
   filtrado = df[df['Nome'].str.startswith('A')]
   print(filtrado)
   ```

   Saída:
   ```
     Nome  Idade
   0   Ana     23
   ```

2. **Filtrar Linhas com Base em Correspondência de Expressões Regulares**

   Use o método `str.contains()` para correspondência parcial ou expressões regulares.

   ```python
   # Filtrar linhas onde o nome contém 'a'
   filtrado = df[df['Nome'].str.contains('a', case=False)]
   print(filtrado)
   ```

   Saída:
   ```
      Nome  Idade
   0    Ana     23
   2 Carlos     45
   3  Diana     28
   ```

### FILTRAGEM COM `query()`
1. **Filtrar Dados Usando `query()`**

   O método `query()` permite usar expressões para filtrar dados de forma mais legível.

   ```python
   # Filtrar linhas onde a idade é maior que 30 usando query
   filtrado = df.query('Idade > 30')
   print(filtrado)
   ```

   Saída:
   ```
      Nome  Idade
   1  Bruno     35
   2 Carlos     45
   ```

2. **Usar Variáveis com `query()`**

   Para usar variáveis em uma expressão `query()`, você deve usar o símbolo `@`.

   ```python
   idade_min = 30
   filtrado = df.query('Idade > @idade_min')
   print(filtrado)
   ```

   Saída:
   ```
      Nome  Idade
   1  Bruno     35
   2 Carlos     45
   ```

### FILTRAGEM COM `loc` E `iloc`
1. **Filtrar Linhas Usando `loc`**

   Você pode usar o método `loc` para selecionar linhas com base em uma condição.

   ```python
   # Filtrar linhas onde a idade é maior que 30 usando loc
   filtrado = df.loc[df['Idade'] > 30]
   print(filtrado)
   ```

   Saída:
   ```
      Nome  Idade
   1  Bruno     35
   2 Carlos     45
   ```

2. **Filtrar Linhas Usando `iloc`**

   `iloc` é mais para seleção por posição, mas pode ser usado em combinação com filtragem.

   ```python
   # Filtrar as 2 primeiras linhas
   filtrado = df.iloc[0:2]
   print(filtrado)
   ```

   Saída:
   ```
      Nome  Idade
   0    Ana     23
   1  Bruno     35
   ```

### FILTRAGEM COM `apply()`
1. **Filtrar Dados Usando `apply()`**

   O método `apply()` pode ser usado para aplicar uma função em cada linha ou coluna e filtrar com base no resultado.

   ```python
   # Função para verificar se a idade é maior que 30
   def idade_maior_que_30(row):
       return row['Idade'] > 30

   # Filtrar usando apply
   filtrado = df[df.apply(idade_maior_que_30, axis=1)]
   print(filtrado)
   ```

   Saída:
   ```
      Nome  Idade
   1  Bruno     35
   2 Carlos     45
   ```

### FILTRAGEM POR DUPLICATAS
1. **Remover Linhas Duplicadas**

   Use o método `drop_duplicates()` para remover linhas duplicadas.

   ```python
   df_duplicado = df.append(df)
   print(df_duplicado.drop_duplicates())
   ```

   Saída:
   ```
      Nome  Idade
   0    Ana     23
   1  Bruno     35
   2 Carlos     45
   ```

2. **Encontrar Linhas Duplicadas**

   Use o método `duplicated()` para encontrar linhas duplicadas.

   ```python
   duplicados = df_duplicado[df_duplicado.duplicated()]
   print(duplicados)
   ```

   Saída:
   ```
      Nome  Idade
   3  Bruno     35
   4 Carlos     45
   ```

### CONCLUSÃO
Filtrar dados em um DataFrame é uma habilidade essencial para análise e manipulação de dados. Usando condições simples, múltiplas condições, expressões regulares, e métodos especializados como `query()`, você pode extrair exatamente o subconjunto de dados que precisa.

## 20-21) LIMPEZA DE DADOS 
A limpeza de dados é uma etapa crucial no processo de análise de dados. Ela envolve a identificação e a correção de problemas nos dados para garantir que as análises subsequentes sejam precisas e confiáveis. O Pandas oferece diversas ferramentas e métodos para realizar a limpeza de dados de forma eficiente. Aqui estão algumas das operações mais comuns de limpeza de dados.

### 1. REMOVER DADOS FALTANTES
1. **Identificar Dados Faltantes**

   Use o método `isnull()` para identificar valores ausentes em um DataFrame.

   ```python
   import pandas as pd

   df = pd.DataFrame({
       'Nome': ['Ana', 'Bruno', None],
       'Idade': [23, None, 45],
       'Cidade': ['São Paulo', 'Rio de Janeiro', 'Belo Horizonte']
   })

   print(df.isnull())
   ```

   Saída:
   ```
      Nome  Idade  Cidade
   0  False  False   False
   1  False   True   False
   2   True  False   False
   ```

2. **Remover Linhas com Dados Faltantes**

   Use `dropna()` para remover linhas com dados faltantes.

   ```python
   df_sem_nulos = df.dropna()
   print(df_sem_nulos)
   ```

   Saída:
   ```
      Nome  Idade           Cidade
   0    Ana   23.0        São Paulo
   2  Carlos   45.0  Belo Horizonte
   ```

3. **Remover Colunas com Dados Faltantes**

   Para remover colunas com dados faltantes, use o parâmetro `axis=1`.

   ```python
   df_sem_colunas_nulas = df.dropna(axis=1)
   print(df_sem_colunas_nulas)
   ```

   Saída:
   ```
         Cidade
   0   São Paulo
   1  Rio de Janeiro
   2  Belo Horizonte
   ```

4. **Preencher Dados Faltantes**

   Use o método `fillna()` para preencher dados ausentes com um valor específico.

   ```python
   df_preenchido = df.fillna({'Nome': 'Desconhecido', 'Idade': df['Idade'].mean()})
   print(df_preenchido)
   ```

   Saída:
   ```
         Nome  Idade           Cidade
   0      Ana   23.0        São Paulo
   1  Desconhecido   29.0  Rio de Janeiro
   2   Carlos   45.0  Belo Horizonte
   ```

5. **Interpolar Dados Faltantes**

   O método `interpolate()` pode ser usado para preencher valores ausentes com base em valores adjacentes.

   ```python
   df_interpolado = df.interpolate()
   print(df_interpolado)
   ```

   Saída:
   ```
      Nome  Idade           Cidade
   0    Ana   23.0        São Paulo
   1  Bruno   34.0  Rio de Janeiro
   2  Carlos   45.0  Belo Horizonte
   ```

### 2. REMOVER DUPLICATAS
1. **Identificar Duplicatas**

   Use o método `duplicated()` para encontrar linhas duplicadas.

   ```python
   duplicados = df[df.duplicated()]
   print(duplicados)
   ```

   Saída:
   ```
   Empty DataFrame
   Columns: [Nome, Idade, Cidade]
   Index: []
   ```

2. **Remover Linhas Duplicadas**

   Para remover linhas duplicadas, use o método `drop_duplicates()`.

   ```python
   df_unico = df.drop_duplicates()
   print(df_unico)
   ```

   Saída:
   ```
      Nome  Idade           Cidade
   0    Ana   23.0        São Paulo
   1  Bruno   35.0  Rio de Janeiro
   2  Carlos   45.0  Belo Horizonte
   ```

### 3. CORRIGIR TIPOS DE DADOS
1. **Converter Tipos de Dados**

   Use o método `astype()` para converter tipos de dados.

   ```python
   df['Idade'] = df['Idade'].astype(int)
   print(df.dtypes)
   ```

   Saída:
   ```
   Nome      object
   Idade      int64
   Cidade    object
   dtype: object
   ```

2. **Detectar Tipos de Dados Incorretos**

   Verifique se há tipos de dados inesperados usando `dtypes`.

   ```python
   print(df.dtypes)
   ```

### 4. NORMALIZAR E PADRONIZAR DADOS
1. **Normalizar Valores Numéricos**

   Normalização é o processo de ajustar os valores numéricos para uma faixa comum, como [0, 1].

   ```python
   df['Idade_Normalizada'] = (df['Idade'] - df['Idade'].min()) / (df['Idade'].max() - df['Idade'].min())
   print(df)
   ```

   Saída:
   ```
      Nome  Idade           Cidade  Idade_Normalizada
   0    Ana     23        São Paulo                 0.0
   1  Bruno     35  Rio de Janeiro                 0.6
   2  Carlos     45  Belo Horizonte                 1.0
   ```

2. **Padronizar Valores Numéricos**

   Padronização ajusta os valores para ter uma média de 0 e um desvio padrão de 1.

   ```python
   from sklearn.preprocessing import StandardScaler

   scaler = StandardScaler()
   df['Idade_Padronizada'] = scaler.fit_transform(df[['Idade']])
   print(df)
   ```

   Saída:
   ```
      Nome  Idade           Cidade  Idade_Padronizada
   0    Ana     23        São Paulo           -1.224745
   1  Bruno     35  Rio de Janeiro            0.000000
   2  Carlos     45  Belo Horizonte            1.224745
   ```

### 5. TRATAR VALORES INCORRETOS
1. **Substituir Valores Específicos**

   Use o método `replace()` para substituir valores específicos.

   ```python
   df['Cidade'] = df['Cidade'].replace('Rio de Janeiro', 'RJ')
   print(df)
   ```

   Saída:
   ```
      Nome  Idade           Cidade
   0    Ana     23        São Paulo
   1  Bruno     35                RJ
   2  Carlos     45  Belo Horizonte
   ```

2. **Aplicar Funções de Limpeza**

   Use o método `apply()` para aplicar funções personalizadas de limpeza.

   ```python
   def limpar_nome(nome):
       if nome is None:
           return 'Desconhecido'
       return nome.strip().title()

   df['Nome'] = df['Nome'].apply(limpar_nome)
   print(df)
   ```

   Saída:
   ```
      Nome  Idade           Cidade
   0    Ana     23        São Paulo
   1  Bruno     35                RJ
   2  Carlos     45  Belo Horizonte
   ```

### 6. TRATAR DADOS DESBALANÇADOS
1. **Reamostrar Dados**

   Use técnicas de sobremuestreo (oversampling) ou subamostragem (undersampling) para tratar dados desbalanceados.

   ```python
   from sklearn.utils import resample

   # Exemplo de sobremuestreo
   df_maj = df[df['Idade'] > 30]
   df_min = df[df['Idade'] <= 30]

   df_min_oversampled = resample(df_min,
                                 replace=True, # amostragem com reposição
                                 n_samples=len(df_maj), # igualar ao tamanho da classe majoritária
                                 random_state=123)

   df_balanced = pd.concat([df_maj, df_min_oversampled])
   print(df_balanced)
   ```

   Saída (ajustada conforme os dados):
   ```
      Nome  Idade           Cidade
   0    Ana     23        São Paulo
   1  Bruno     35                RJ
   2  Carlos     45  Belo Horizonte
   2  Ana     23        São Paulo
   ```

### CONCLUSÃO
A limpeza de dados é um passo crucial para garantir a integridade e a qualidade dos dados antes de realizar análises e modelagem. O Pandas fornece uma variedade de ferramentas e métodos para tratar dados faltantes, remover duplicatas, corrigir tipos de dados, normalizar e padronizar dados, e tratar valores incorretos.

## 22) ESTATÍSTICAS DESCRITIVAS 
Estatísticas descritivas são essenciais para compreender a distribuição, a tendência central e a dispersão dos dados. O Pandas oferece várias funções para calcular essas estatísticas de maneira eficiente. Abaixo estão as operações básicas e avançadas para obter estatísticas descritivas de um DataFrame.

### 1. ESTATÍSTICAS BÁSICAS
1. **Resumo Estatístico com `describe()`**

   O método `describe()` fornece um resumo estatístico básico para colunas numéricas de um DataFrame.

   ```python
   import pandas as pd

   df = pd.DataFrame({
       'Nome': ['Ana', 'Bruno', 'Carlos', 'Diana'],
       'Idade': [23, 35, 45, 28],
       'Salário': [3000, 5000, 7000, 6000]
   })

   resumo = df.describe()
   print(resumo)
   ```

   Saída:
   ```
             Idade      Salário
   count   4.000000     4.000000
   mean   32.750000  5250.000000
   std    8.970483  1600.000000
   min    23.000000  3000.000000
   25%    25.500000  3750.000000
   50%    28.000000  5500.000000
   75%    39.500000  6750.000000
   max    45.000000  7000.000000
   ```

2. **Contar Valores Únicos com `value_counts()`**

   O método `value_counts()` conta a frequência de valores únicos em uma coluna.

   ```python
   contagem_nomes = df['Nome'].value_counts()
   print(contagem_nomes)
   ```

   Saída:
   ```
   Ana      1
   Bruno    1
   Carlos   1
   Diana    1
   Name: Nome, dtype: int64
   ```

3. **Cálculo da Média, Mediana e Moda**

   - **Média** com `mean()`

     ```python
     media_idade = df['Idade'].mean()
     print(f'Média da Idade: {media_idade}')
     ```

     Saída:
     ```
     Média da Idade: 32.75
     ```

   - **Mediana** com `median()`

     ```python
     mediana_idade = df['Idade'].median()
     print(f'Mediana da Idade: {mediana_idade}')
     ```

     Saída:
     ```
     Mediana da Idade: 28.0
     ```

   - **Moda** com `mode()`

     ```python
     moda_idade = df['Idade'].mode()
     print(f'Moda da Idade: {moda_idade}')
     ```

     Saída:
     ```
     Moda da Idade: 0    23
     dtype: int64
     ```

### 2. ESTATÍSTICAS DE DISPERSÃO
1. **Desvio Padrão com `std()`**

   O método `std()` calcula o desvio padrão, que mede a dispersão dos dados.

   ```python
   desvio_padrao_salario = df['Salário'].std()
   print(f'Desvio Padrão do Salário: {desvio_padrao_salario}')
   ```

   Saída:
   ```
   Desvio Padrão do Salário: 1600.0
   ```

2. **Variância com `var()`**

   O método `var()` calcula a variância, que é o quadrado do desvio padrão.

   ```python
   variancia_salario = df['Salário'].var()
   print(f'Variância do Salário: {variancia_salario}')
   ```

   Saída:
   ```
   Variância do Salário: 2560000.0
   ```

3. **Intervalo com `max()` e `min()`**

   O intervalo é a diferença entre o valor máximo e mínimo.

   ```python
   intervalo_salario = df['Salário'].max() - df['Salário'].min()
   print(f'Intervalo do Salário: {intervalo_salario}')
   ```

   Saída:
   ```
   Intervalo do Salário: 4000
   ```

4. **Coeficiente de Variação**

   O coeficiente de variação é a razão entre o desvio padrão e a média, expressa como uma porcentagem.

   ```python
   coef_variacao = (df['Salário'].std() / df['Salário'].mean()) * 100
   print(f'Coeficiente de Variação do Salário: {coef_variacao:.2f}%')
   ```

   Saída:
   ```
   Coeficiente de Variação do Salário: 30.48%
   ```

### 3. ESTATÍSTICAS AVANÇADAS
1. **Quartis e Percentis com `quantile()`**

   Use `quantile()` para calcular quartis e percentis específicos.

   ```python
   quartis = df['Idade'].quantile([0.25, 0.5, 0.75])
   print(f'Quartis da Idade:\n{quartis}')
   ```

   Saída:
   ```
   Quartis da Idade:
   0.25    25.5
   0.50    28.0
   0.75    39.5
   Name: Idade, dtype: float64
   ```

2. **Correlação com `corr()`**

   O método `corr()` calcula a correlação entre colunas numéricas.

   ```python
   correlacao = df.corr()
   print(f'Correlação entre colunas:\n{correlacao}')
   ```

   Saída:
   ```
               Idade  Salário
   Idade       1.000000  0.825717
   Salário     0.825717  1.000000
   ```

3. **Covariância com `cov()`**

   O método `cov()` calcula a covariância entre colunas numéricas.

   ```python
   covariancia = df.cov()
   print(f'Covariância entre colunas:\n{covariancia}')
   ```

   Saída:
   ```
              Idade    Salário
   Idade    80.833333  8000000.0
   Salário  8000000.0  2560000000.0
   ```

### 4. ESTATÍSTICAS DESCRITIVAS PARA CATEGORIAS
1. **Contagem de Valores Únicos com `value_counts()`**

   O método `value_counts()` fornece a frequência de valores únicos em uma coluna categórica.

   ```python
   contagem_cidades = df['Cidade'].value_counts()
   print(f'Contagem de Cidades:\n{contagem_cidades}')
   ```

   Saída:
   ```
   Contagem de Cidades:
   São Paulo        1
   Rio de Janeiro   1
   Belo Horizonte   1
   Name: Cidade, dtype: int64
   ```

2. **Tabela de Contingência com `crosstab()`**

   O método `crosstab()` cria uma tabela de contingência entre duas colunas.

   ```python
   tabela_contingencia = pd.crosstab(df['Nome'], df['Cidade'])
   print(f'Tabela de Contingência:\n{tabela_contingencia}')
   ```

   Saída:
   ```
   Cidade  Belo Horizonte  Rio de Janeiro  São Paulo
   Nome                                           
   Ana                  0               0          1
   Bruno                0               1          0
   Carlos               1               0          0
   Diana                0               0          0
   ```

### CONCLUSÃO
As estatísticas descritivas fornecem uma visão geral importante sobre a natureza dos dados. Com o Pandas, você pode facilmente calcular medidas de tendência central, dispersão, e relacionamentos entre variáveis.

## 22) USANDO `apply()` E `map()`
Tanto `apply()` quanto `map()` são métodos poderosos no Pandas para aplicar funções a dados em DataFrames e Series. No entanto, eles são usados em contextos ligeiramente diferentes e possuem características distintas. Vamos explorar cada um deles.

### `apply()`
O método `apply()` é utilizado para aplicar uma função ao longo de um eixo de um DataFrame ou em uma Series. Ele pode ser usado para aplicar funções tanto em linhas quanto em colunas de um DataFrame.

#### 1. **Aplicar Funções em Series**
Você pode aplicar uma função a cada elemento de uma Series usando `apply()`.

```python
import pandas as pd

# Criando uma Series
s = pd.Series([1, 2, 3, 4, 5])

# Aplicando uma função para calcular o quadrado de cada valor
quadrado = s.apply(lambda x: x ** 2)
print(quadrado)
```

Saída:
```
0     1
1     4
2     9
3    16
4    25
dtype: int64
```

#### 2. **Aplicar Funções em DataFrames**
Para DataFrames, `apply()` pode ser usado para aplicar uma função em linhas ou colunas.

```python
# Criando um DataFrame
df = pd.DataFrame({
    'A': [1, 2, 3],
    'B': [4, 5, 6]
})

# Aplicando uma função em cada coluna
soma_colunas = df.apply(lambda x: x.sum())
print(soma_colunas)
```

Saída:
```
A     6
B    15
dtype: int64
```

#### 3. **Aplicar Funções em Linhas**
Use o parâmetro `axis` para especificar se a função deve ser aplicada em linhas (`axis=1`) ou colunas (`axis=0`).

```python
# Aplicando uma função em cada linha
soma_linhas = df.apply(lambda x: x.sum(), axis=1)
print(soma_linhas)
```

Saída:
```
0     5
1     7
2     9
dtype: int64
```

#### 4. **Aplicar Funções Complexas**
Você pode usar `apply()` para aplicar funções mais complexas, como funções que utilizam múltiplos argumentos ou funções definidas pelo usuário.

```python
# Função que calcula a média e o desvio padrão
def calc_estatisticas(x):
    return pd.Series([x.mean(), x.std()], index=['Média', 'Desvio Padrão'])

# Aplicando a função para cada coluna
estatisticas = df.apply(calc_estatisticas)
print(estatisticas)
```

Saída:
```
         A         B
Média  2.0  5.0
Desvio Padrão  1.0  1.0
```

---

### `map()`
O método `map()` é utilizado para aplicar uma função ou um mapeamento a cada elemento de uma Series. É geralmente usado para transformar dados ou fazer substituições.

#### 1. **Aplicar Funções em Series**
Você pode usar `map()` para aplicar uma função a cada valor em uma Series.

```python
# Criando uma Series
s = pd.Series(['a', 'b', 'c'])

# Mapeando cada valor para seu código ASCII
mapa = s.map(lambda x: ord(x))
print(mapa)
```

Saída:
```
0    97
1    98
2    99
dtype: int64
```

#### 2. **Substituição de Valores com `map()`**
`map()` é útil para substituir valores em uma Series usando um dicionário de mapeamento.

```python
# Criando uma Series
s = pd.Series(['maçã', 'banana', 'laranja'])

# Dicionário de substituição
substituicoes = {'maçã': 'apple', 'banana': 'banana', 'laranja': 'orange'}

# Aplicando a substituição
s_substituido = s.map(substituicoes)
print(s_substituido)
```

Saída:
```
0    apple
1    banana
2    orange
dtype: object
```

#### 3. **Mapeamento com Funções Pré-definidas**
Você pode usar `map()` para aplicar funções pré-definidas ou métodos incorporados.

```python
# Criando uma Series de números
s = pd.Series([1, 2, 3, 4])

# Mapeando para a representação em string
s_str = s.map(str)
print(s_str)
```

Saída:
```
0    1
1    2
2    3
3    4
dtype: object
```

---

### COMPARAÇÃO ENTRE `apply()` E `map()`
- **`apply()`**: Mais versátil e pode ser usado em DataFrames e Series. Ideal para aplicar funções complexas ou funções que dependem de múltiplas colunas ou linhas.
- **`map()`**: Mais simples e específico para Series. Ideal para transformar ou substituir valores com base em um mapeamento ou função simples.

### CONCLUSÃO
Os métodos `apply()` e `map()` no Pandas são ferramentas poderosas para manipular e transformar dados. O `apply()` é útil para aplicar funções complexas em DataFrames e Series, enquanto o `map()` é excelente para transformar ou substituir valores em uma Series. Escolha o método que melhor se adapta às suas necessidades com base no contexto e na complexidade das operações desejadas. 

## 23-24) AGRUPAMENTO
O agrupamento de dados é uma técnica poderosa para agregar, sumarizar e analisar subconjuntos de dados. No Pandas, o método `groupby()` é utilizado para dividir um DataFrame em grupos com base nos valores de uma ou mais colunas e, em seguida, aplicar funções de agregação ou transformação a esses grupos.

Vamos explorar como usar `groupby()` e algumas operações relacionadas:

---

### 1. **USANDO `groupby()`**
O método `groupby()` permite dividir um DataFrame em grupos com base no valor das colunas e aplicar funções de agregação ou transformação a cada grupo.

#### **1.1 Agrupando por uma Coluna**
Suponha que você tenha um DataFrame com informações sobre vendas por região.

```python
import pandas as pd

# Criando um DataFrame
df = pd.DataFrame({
    'Região': ['Norte', 'Sul', 'Norte', 'Leste', 'Sul', 'Norte'],
    'Vendas': [200, 300, 250, 150, 350, 100]
})

# Agrupando por 'Região' e somando as vendas
grupo_regiao = df.groupby('Região')
soma_vendas = grupo_regiao['Vendas'].sum()
print(soma_vendas)
```

Saída:
```
Região
Leste    150
Norte    550
Sul      650
Name: Vendas, dtype: int64
```

#### **1.2 Agrupando por Múltiplas Colunas**
Você pode agrupar por várias colunas. Suponha que você tenha informações sobre vendas por região e por vendedor.

```python
# Criando um DataFrame
df = pd.DataFrame({
    'Região': ['Norte', 'Sul', 'Norte', 'Leste', 'Sul', 'Norte'],
    'Vendedor': ['A', 'B', 'A', 'C', 'B', 'C'],
    'Vendas': [200, 300, 250, 150, 350, 100]
})

# Agrupando por 'Região' e 'Vendedor' e somando as vendas
grupo_regiao_vendedor = df.groupby(['Região', 'Vendedor'])
soma_vendas = grupo_regiao_vendedor['Vendas'].sum()
print(soma_vendas)
```

Saída:
```
Região  Vendedor
Leste   C           150
Norte   A           450
        C           100
Sul     B           650
Name: Vendas, dtype: int64
```

---

### 2. **FUNÇÕES DE AGREGAÇÃO**
Após agrupar os dados, você pode usar funções de agregação para calcular estatísticas resumidas.

#### **2.1 Funções Básicas de Agregação**
- **`sum()`**: Soma dos valores em cada grupo.
- **`mean()`**: Média dos valores em cada grupo.
- **`min()`**: Valor mínimo em cada grupo.
- **`max()`**: Valor máximo em cada grupo.
- **`count()`**: Contagem de valores em cada grupo.

```python
# Usando funções de agregação
resumo = grupo_regiao['Vendas'].agg(['sum', 'mean', 'min', 'max', 'count'])
print(resumo)
```

Saída:
```
         sum  mean  min  max  count
Região                                
Leste    150  150.0  150  150      1
Norte    550  183.3  100  250      3
Sul      650  325.0  300  350      2
```

#### **2.2 Aplicando Funções Customizadas**
Você pode aplicar funções customizadas usando `agg()` ou `apply()`.

```python
# Função customizada
def range_vendas(vendas):
    return vendas.max() - vendas.min()

# Aplicando a função customizada
range_vendas_por_regiao = grupo_regiao['Vendas'].agg(range_vendas)
print(range_vendas_por_regiao)
```

Saída:
```
Região
Leste    0
Norte    150
Sul      50
Name: Vendas, dtype: int64
```

---

### 3. **TRANSFORMAÇÕES E FILTRAGENS**
Além de agregações, o método `groupby()` permite transformar e filtrar dados.

#### **3.1 Transformação com `transform()`**
O método `transform()` é usado para aplicar uma função a cada grupo e retornar um DataFrame ou Series com o mesmo índice do original.

```python
# Normalizando vendas por região
vendas_normalizadas = grupo_regiao['Vendas'].transform(lambda x: (x - x.mean()) / x.std())
print(vendas_normalizadas)
```

Saída:
```
0    0.000000
1    1.000000
2    0.000000
3    NaN
4    1.000000
5   -1.000000
Name: Vendas, dtype: float64
```

#### **3.2 Filtragem com `filter()`**
O método `filter()` é usado para filtrar grupos com base em uma condição.

```python
# Filtrando regiões com vendas totais acima de 500
regioes_filtradas = grupo_regiao.filter(lambda x: x['Vendas'].sum() > 500)
print(regioes_filtradas)
```

Saída:
```
  Região Vendedor  Vendas
1    Sul        B     300
4    Sul        B     350
0   Norte        A     200
2   Norte        A     250
5   Norte        C     100
```

---

### 4. **ORDENANDO GRUPOS**
Você pode ordenar os resultados agrupados usando `sort_values()` ou `sort_index()`.

```python
# Ordenar pela soma das vendas
ordenado_por_soma = grupo_regiao['Vendas'].sum().sort_values(ascending=False)
print(ordenado_por_soma)
```

Saída:
```
Região
Sul      650
Norte    550
Leste    150
Name: Vendas, dtype: int64
```

---

### CONCLUSÃO
O agrupamento no Pandas com `groupby()` é uma ferramenta poderosa para resumir, transformar e analisar dados. Usando `groupby()`, você pode agregar dados, aplicar funções customizadas, transformar valores e filtrar grupos com base em condições específicas. Essas operações são essenciais para a análise de dados e podem ajudar a obter insights valiosos a partir de grandes conjuntos de dados. 

## 25) ORDENANDO DADOS 
Ordenar dados é uma tarefa comum e essencial para análise de dados. O Pandas oferece várias maneiras de ordenar dados em DataFrames e Series. Vamos explorar os métodos principais para ordenar dados.

---

### 1. **ORDENANDO UMA SERIES**
Para ordenar uma Series, você pode usar o método `sort_values()`, que ordena os valores em ordem crescente por padrão.

#### **1.1 Ordenar em Ordem Crescente**
```python
import pandas as pd

# Criando uma Series
s = pd.Series([5, 3, 9, 1, 7])

# Ordenar em ordem crescente
s_ordenado = s.sort_values()
print(s_ordenado)
```

Saída:
```
3    1
1    3
4    7
0    5
2    9
dtype: int64
```

#### **1.2 Ordenar em Ordem Decrescente**
Para ordenar em ordem decrescente, use o parâmetro `ascending=False`.

```python
# Ordenar em ordem decrescente
s_ordenado_decrescente = s.sort_values(ascending=False)
print(s_ordenado_decrescente)
```

Saída:
```
2    9
4    7
0    5
1    3
3    1
dtype: int64
```

---

### 2. **ORDENANDO UM DATAFRAME**
Para DataFrames, você pode usar o método `sort_values()` para ordenar por uma ou mais colunas. O método `sort_index()` pode ser usado para ordenar por índice.

#### **2.1 Ordenar por uma Coluna**
```python
# Criando um DataFrame
df = pd.DataFrame({
    'Nome': ['Ana', 'Bruno', 'Carlos', 'Diana'],
    'Idade': [23, 35, 45, 28],
    'Salário': [3000, 5000, 7000, 6000]
})

# Ordenar por 'Idade'
df_ordenado_idade = df.sort_values(by='Idade')
print(df_ordenado_idade)
```

Saída:
```
    Nome  Idade  Salário
0    Ana     23     3000
3  Diana     28     6000
1  Bruno     35     5000
2 Carlos     45     7000
```

#### **2.2 Ordenar por Múltiplas Colunas**
Você pode ordenar por várias colunas especificando uma lista de colunas.

```python
# Ordenar por 'Região' e 'Salário'
df_ordenado_multicolunas = df.sort_values(by=['Idade', 'Salário'], ascending=[True, False])
print(df_ordenado_multicolunas)
```

Saída:
```
    Nome  Idade  Salário
0    Ana     23     3000
3  Diana     28     6000
1  Bruno     35     5000
2 Carlos     45     7000
```

#### **2.3 Ordenar por Índice**
Para ordenar por índice, use o método `sort_index()`.

```python
# Ordenar por índice
df_ordenado_indice = df.sort_index()
print(df_ordenado_indice)
```

Saída:
```
    Nome  Idade  Salário
0    Ana     23     3000
1  Bruno     35     5000
2 Carlos     45     7000
3  Diana     28     6000
```

---

### 3. **ORDENANDO POR VALORES EM ORDENS CUSTOMIZADAS**
Se você precisa ordenar por valores em uma ordem específica, pode usar a função `pd.Categorical()` para definir uma ordem personalizada.

```python
# Criando um DataFrame com uma coluna categórica
df = pd.DataFrame({
    'Categoria': ['B', 'C', 'A', 'C', 'B'],
    'Valores': [10, 20, 15, 25, 5]
})

# Definindo uma ordem personalizada para a coluna 'Categoria'
df['Categoria'] = pd.Categorical(df['Categoria'], categories=['A', 'B', 'C'], ordered=True)

# Ordenando por 'Categoria'
df_ordenado_categoria = df.sort_values(by='Categoria')
print(df_ordenado_categoria)
```

Saída:
```
  Categoria  Valores
2         A       15
4         B        5
0         B       10
1         C       20
3         C       25
```

---

### 4. **ORDENANDO COM FUNÇÕES CUSTOMIZADAS**
Você também pode usar funções customizadas para definir a ordem dos dados.

```python
# Criando um DataFrame
df = pd.DataFrame({
    'Nome': ['Ana', 'Bruno', 'Carlos', 'Diana'],
    'Idade': [23, 35, 45, 28]
})

# Função para definir a ordem personalizada
def ordem_customizada(nome):
    ordem = {'Carlos': 1, 'Ana': 2, 'Diana': 3, 'Bruno': 4}
    return ordem.get(nome, 0)

# Ordenar usando a função customizada
df_ordenado_customizado = df.sort_values(by='Nome', key=lambda x: x.map(ordem_customizada))
print(df_ordenado_customizado)
```

Saída:
```
    Nome  Idade
2 Carlos     45
0    Ana     23
3  Diana     28
1  Bruno     35
```

---

### CONCLUSÃO
Ordenar dados é uma operação fundamental para análise e visualização de dados. Com os métodos `sort_values()` e `sort_index()` do Pandas, você pode facilmente ordenar Series e DataFrames com base em uma ou mais colunas, por índice ou usando ordens customizadas. Esses métodos são altamente flexíveis e permitem personalizar a ordenação conforme suas necessidades específicas.

