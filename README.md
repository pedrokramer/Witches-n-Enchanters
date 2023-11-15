# Análise de propriedades de aço
## Status:
em desenvolvimento

#### Este é o trabalho final da disciplina de Aprendizado de Máquina da equipe "Witches-n-Enchanters" que analisa modelos no dataset Steel Strength [1] [2].

## Descrição
Neste trabalho, o dataset utilizado contém a quantidade de elementos em ligas metálicas de aço e algumas propriedades mecânicas (yield strength,	tensile strength,	elongation). O objetivo do projeto é fazer uma análise exploratória de dados para encontrar modelos preditivos de como cada elemento químico da liga influencia essas propriedades metálicas.

## Atributos utilizados no modelo
C = Carbono

Mn = Manganês

Si = Silício

Cr = Cromo

Ni = Níquel

Mo = Molibdênio

V = Vanádio

N = Nitrogênio

Nb = Nióbio

Co = Cobalto

Al = Alumínio

Ti = Titânio

Fe = Ferro

## Target

Tensile strength = Resistência Máxima à tração 

## Etapas do trabalho
- Introdução
- Tratamento dos dados
- Imports
- Dataset (modificações)
- Matriz de correlação
- Modelos (k-nn, árvore, floresta aleatória)
- SHAP
- Conclusão
- Referências

## Orientando-se no código
- Inicialmente, importamos o dataset que está em um arquivo (.csv) utilizando a biblioteca pandas. Armazenamos esse dataset em uma variável (steel_df)
- Feito isso, removemos a coluna que continha as fórmulas químicas no dataset, uma vez que esse atributo, por mais que contenha informações relevantes sobre o material, não influencia na análise dos dados. Fazemos essa remoção  utilizando o comando ".drop" do pandas responsável por remover linhas ou colunas de datasets. Se o objetivo do trabalho envolvesse um estudo a fundo de ligas metálicas, ferro e aço, seria interessante manter, mas nosso objetivo é outro.
- Perfeito! Observamos que agora nosso dataset está conciso. Temos apenas dados numéricos referentes aos atributos comentados. Contamos a quantidade de cada atributo para verificar qual a ocorrência de cada um, para isso usamos um 'for' dentro de outro 'for'. Verificamos que o atributo W (Tungstênio) apareceu apenas 16 vezes no dataset. Decidimos remover esse atributo porque em comparação com os demais, ele se apresenta com uma pequena frequência.
- Ótimo, podemos partir para o cálculo da porcentagem de ferro de cada aço presente no dataset. Para isso, subtraimos a soma dos percentuais dos elementos na lista "elementos" de 100% presumindo que a soma de todos esses elementos deve ser igual a 100% na composição do aço, e o restante seria considerado como ferro. Atribuimos o resultado a uma variável 'fe'. Adicionamos essa nova coluna responsável por calcular a porcentagem de ferro ao dataset.
- Podemos iniciar a tentativa de encontrar uma correlação entre os materiais e a resistência a tração máxima. Para isso, traçamos uma matriz de correlação usando a função '.corr' do pandas. Observe que quando os valores dão próximos de 1 significa que há uma grande correlação, enquanto para valores próximos ou abaixo de 0 há uma correlação fraca/negativa.
- Temos o necessário para começar o treino e avaliação do melhor modelo. Para isso usaremos alguns dos modelos que aprendemos ao longo da disciplina e otimizadores para conseguir encontrar o melhor modelo.

## K-NN
- O algoritmo K-Nearest Neighbour (KNN) é uma técnica popular de aprendizado de máquina usada para tarefas de classificação e regressão. Baseia-se na ideia de que pontos de dados semelhantes tendem a ter rótulos ou valores semelhantes, ou seja, é uma maneira de chegar num valor do target para o input do usuário ao ver os targets dos vizinhos mais próximos. É necessário separar os atributos e target do dataset, assim como separar em dados de treino e teste fazendo um split dos dados. Podemos usar a função 'train_test_split' do sckit-learn. Para testar o modelo utilizamos um hiperparâmetro fixo. Para isso, usamos uma 'Pipeline' também do scikit-learn, cujo objetivo é montar várias etapas que podem ser validadas de forma cruzada enquanto se definem parâmetros diferentes. É um tipo de preparação dos dados em etapas, resumindo. Inicialmente definimos uma normalização padrão dos dados utilizando o 'StandardScaler' que faz a normalização subtraindo a média e dividindo pelo desvio padrão. Feito isso, o código parte para o modelo k-nn. Usamos a métrica 'nan_euclidean' para lidar com os dados NaN na hora de calcular a distância euclidiana. Realizamos o 'fit' e o modelo é treinado, por fim calculamos o RMSE. Para otimizar o modelo, podemos usar o optuna, que será descrito melhor abaixo. Para isso, criamos uma instância para o modelo usando o 'trial' do Optuna, definimos os hiperparâmetros a serem otimizados e depois definimos outra instância do modelo com os hiperparâmetros já definidos. Realizamos a validação cruzada e calculamos a métrica RMSE. Esse valor retorna negativo.

## Optuna 
- Esse otimizador de hiperparâmetros será bastante utilizado nesse notebook, portanto é importante saber do que se trata. No modelo do K-nn mencionado acima utilizamos ele inclusive. Optuna é uma estrutura de software de otimização automática de hiperparâmetros, especialmente projetada para aprendizado de máquina.

## Árvore de decisão
- É um modelo muito importante em machine learning e funciona de forma semelhante a um fluxograma. Uma árvore de decisão é um algoritmo de aprendizado de máquina supervisionado que é utilizado para classificação e para regressão. Isto é, pode ser usado para prever categorias discretas (sim ou não, por exemplo) e para prever valores numéricos. Todas as etapas da árvore estão bem explicadas no notebook, por isso recomendamos que se oriente pelas etapas descritas lá!

## Floresta Aleatória
- A floresta aleatória é uma abordagem que utiliza várias árvores de decisão para melhorar a precisão e a generalização do modelo. Ela funciona como um comitê (*ensemble*) contendo diversas árvores de decisão onde cada uma realiza sua previsão individual.
- Este modelo introduz aleatoriedade no processo de treinamento, como a seleção aleatória de subamostras do conjunto de dados e de características para dividir em cada nó da árvore. Isso ajuda a reduzir o sobreajuste e aumentar a generalização do modelo, criando modelos mais robustos e menos suscetíveis ao *overfitting*.
- Assim como na árvore de decisão, podemos nos orientar pelo notebook para entender todas as etapas que estão bem explicadas, inclusive a otimização dos hiperparâmetros.

## SHAP
- O SHAP é um cálculo de importância de cada atributo de um modelo para o target previsto. É calculado através da permutação de valores dos atributos do modelo e assim armazenando o quanto tal alteração muda no valor do target.
- O objetivo do uso do SHAP para o projeto então foi de entender como o modelo da floresta aleatória compreende a importância de cada elemento na liga.

## Referências:
[1] https://figshare.com/articles/dataset/Steel_Strength_Data/7250453 (dataset)

[2] https://citrination.com/datasets/153092/show_files/ (informações do dataset)

[3] https://www.analyticsvidhya.com/blog/2018/03/introduction-k-neighbours-algorithm-clustering/#h-what-is-knn-k-nearest-neighbor-algorithm (K-nn)

[4] https://scikit-learn.org/stable/modules/generated/sklearn.pipeline.Pipeline.html (Pipeline)

[5] https://optuna.readthedocs.io/en/stable/ (Optuna)

[6] https://blog.somostera.com/data-science/arvores-de-decisao (Árvore)

[7] https://medium.com/big-data-blog/shap-o-que-%C3%A9-e-por-que-usar-6b01d37ae592 (SHAP)
