# MANUAL
## INSTALAÇÃO:
1. **INSTALAÇÃO VIA PIP**:
   - Abra o terminal (ou prompt de comando) e execute o seguinte comando:

   ```sh
   pip install pandas
   ```

2. **INSTALAÇÃO VIA CONDA (ANACONDA/DISTRIBUIÇÃO MINICONDA)**:
   - Se você estiver usando Anaconda ou Miniconda, pode instalar o Pandas com o seguinte comando:

   ```sh
   conda install pandas
   ```

3. **VERIFICAR A INSTALAÇÃO**:
   - Após a instalação, verifique se o Pandas foi instalado corretamente importando-o no Python:

   ```python
   import pandas as pd
   print(pd.__version__)
   ```

## CONFIGURAÇÃO DO AMBIENTE:
1. **INSTALAR UM AMBIENTE VIRTUAL** (OPCIONAL MAS RECOMENDADO):
   - Crie e ative um ambiente virtual para isolar suas dependências de projeto:

   ```sh
   python -m venv myenv
   source myenv/bin/activate  # Para Windows: myenv\Scripts\activate
   ```

2. **INSTALAR EDITOR DE CÓDIGO**:
   - Utilize um editor de código como Visual Studio Code, PyCharm ou Jupyter Notebook para escrever e executar seu código Python.

## PRIMEIRO PROJETO:
Vamos criar um pequeno projeto para demonstrar as funcionalidades básicas do Pandas.

1. **IMPORTAR O PANDAS**:
   - Em seu editor de código, crie um novo arquivo Python (ex: `primeiro_projeto.py`) e importe o Pandas:

   ```python
   import pandas as pd
   ```

2. **CRIAR UM DATAFRAME**:
   - Crie um DataFrame simples usando um dicionário de dados:

   ```python
   data = {
       'Nome': ['Ana', 'Bruno', 'Carlos', 'Diana'],
       'Idade': [23, 35, 45, 29],
       'Cidade': ['São Paulo', 'Rio de Janeiro', 'Curitiba', 'Belo Horizonte']
   }
   df = pd.DataFrame(data)
   print(df)
   ```

3. **LEITURA DE DADOS A PARTIR DE UM ARQUIVO CSV**:
   - Suponha que você tenha um arquivo CSV chamado `dados.csv`. Vamos ler este arquivo em um DataFrame:

   ```python
   df = pd.read_csv('dados.csv')
   print(df.head())
   ```

4. **VISUALIZAR DADOS**:
   - Visualize as primeiras e últimas linhas do DataFrame:

   ```python
   print(df.head())  # Primeiras 5 linhas
   print(df.tail())  # Últimas 5 linhas
   ```

5. **SELEÇÃO E FILTRAGEM DE DADOS**:
   - Selecionar uma coluna e filtrar dados com base em uma condição:

   ```python
   print(df['Nome'])  # Selecionar coluna 'Nome'
   df_filtrado = df[df['Idade'] > 30]  # Filtrar linhas onde a idade é maior que 30
   print(df_filtrado)
   ```

6. **ADICIONAR E MODIFICAR COLUNAS**:
   - Adicionar uma nova coluna e modificar uma existente:

   ```python
   df['NovaColuna'] = df['Idade'] * 2  # Adicionar nova coluna
   df['Idade'] = df['Idade'] + 1  # Modificar coluna existente
   print(df)
   ```

7. **AGRUPAMENTO E AGREGAÇÃO**:
   - Agrupar dados por uma coluna e calcular estatísticas agregadas:

   ```python
   df_grouped = df.groupby('Cidade').mean()
   print(df_grouped)
   ```

8. **SALVAR O DATAFRAME EM UM ARQUIVO CSV**:
   - Salvar o DataFrame modificado em um novo arquivo CSV:

   ```python
   df.to_csv('dados_modificados.csv', index=False)
   ```

## CONCLUSÃO:
Parabéns! Você instalou o Pandas, configurou seu ambiente de desenvolvimento e criou seu primeiro projeto com Pandas. Este é apenas o começo. Pandas oferece muitas outras funcionalidades avançadas para manipulação e análise de dados. Continue explorando a documentação e experimentando com seus próprios conjuntos de dados para se tornar proficiente no uso desta poderosa biblioteca. 