# Projeto de Previsão de Nota IMDB

Este projeto tem como objetivo prever a nota de filmes no IMDB utilizando um modelo de Machine Learning treinado com dados históricos. O código foi desenvolvido em Python e utiliza bibliotecas como Pandas, Scikit-learn e Matplotlib para análise, processamento e modelagem de dados.

Requisitos
Para executar este projeto, você precisará ter os seguintes softwares e bibliotecas instalados:

Python 3.7+: Recomendamos o uso de uma versão recente do Python.

Pip: O gerenciador de pacotes do Python (geralmente vem com a instalação do Python).

As bibliotecas Python necessárias podem ser instaladas através do pip. Crie um ambiente virtual (recomendado) e execute o seguinte comando:

Bash

pip install pandas numpy scikit-learn matplotlib seaborn
Arquivos do Projeto
O repositório deve conter os seguintes arquivos:

imdb.csv: O arquivo contendo os dados brutos dos filmes.

IMDB_Top_1000.ipynb: O notebook Jupyter com todo o código de análise, pré-processamento, treinamento e previsão.

modelo_imdb_gb_pipeline.pkl: O modelo de Machine Learning treinado e serializado (será gerado após a execução do notebook).

README.md: Este arquivo, explicando como configurar e executar o projeto.

Como Instalar
Clone o repositório:

Bash

git clone https://github.com/RonaldoBispoLima/Top-1000-Movies-by-IMDB-Rating
cd Top-1000-Movies-by-IMDB-Rating

Crie e ative um ambiente virtual (recomendado):

Bash

python -m venv venv
### No Windows:
.\venv\Scripts\activate

### No macOS/Linux:
source venv/bin/activate
Instale as dependências:

Bash
pip install -r requirements.txt

Como Executar
Execute o Notebook Jupyter:
Para rodar a análise completa, treinar o modelo e realizar previsões, abra o notebook IMDB_Top_1000.ipynb em seu ambiente Jupyter (Notebook ou Lab).

Bash

jupyter notebook
#### Ou
jupyter lab
Navegue até o diretório do projeto, clique no arquivo IMDB_Top_1000.ipynb e execute todas as células sequencialmente.

O que acontece:

O notebook ira carregar o arquivo imdb.csv.

Realizar a limpeza e pré-processamento dos dados.

Trainar o modelo GradientBoostingRegressor.

Avalia o desempenho do modelo.

Salva o modelo treinado no arquivo modelo_imdb_gb_pipeline.pkl.

Realiza uma previsão de exemplo para o filme "The Shawshank Redemption".

Como Realizar Novas Previsões
Após executar o notebook pela primeira vez e ter o arquivo modelo_imdb_gb_pipeline.pkl gerado, você pode reutilizar o modelo para prever a nota de outros filmes.

Você pode adaptar a seção 5. Previsão da Nota do IMDB para um Novo Filme no notebook:

Carregue o modelo treinado:

Python

with open('modelo_imdb_gb_pipeline.pkl', 'rb') as file:
    loaded_model = pickle.load(file)
Crie um DataFrame com os dados do novo filme que você deseja prever. Certifique-se de que as colunas e seus formatos sejam consistentes com os dados originais (ex: Runtime como string "X min", Gross como string com vírgulas, Genre como string separada por vírgulas). O pipeline se encarregará do resto.

Python

new_movie_data = pd.DataFrame([{
    'Series_Title': 'Nome do Novo Filme',
    'Released_Year': 'Ano',
    'Certificate': 'Classificação',
    'Runtime': 'XX min',
    'Genre': 'Gênero1, Gênero2',
    'Overview': 'Descrição do filme...',
    'Meta_score': 75.0, # Valor numérico
    'Director': 'Nome do Diretor',
    'Star1': 'Nome do Ator Principal',
    # ... outras colunas relevantes se usadas no treinamento ...
    'No_of_Votes': 100000, # Valor numérico
    'Gross': '10,000,000' # String com vírgulas
}])
Faça a previsão:

Python

predicted_rating = loaded_model.predict(new_movie_data)
print(f"A nota prevista para o filme é: {predicted_rating[0]:.2f}")
Contribuições
Contribuições são bem-vindas! Sinta-se à vontade para abrir uma issue ou enviar um pull request com melhorias, correções de bugs ou novas funcionalidades.
