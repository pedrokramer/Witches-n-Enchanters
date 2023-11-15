# Análise de propriedades de aço
## Status:
em desenvolvimento

#### Este é o trabalho final da disciplina de Aprendizado de Máquina da equipe "Witches-n-Enchanters" que analisa modelos no dataset Steel Strength [1] [2].

## Descrição
Neste trabalho, o dataset utilizado contém a quantidade de elementos em ligas metálicas de aço e algumas propriedades mecânicas (yield strength,	tensile strength,	elongation). O objetivo do projeto é fazer uma análise exploratória de dados para encontrar modelos preditivos de como cada elemento químico da liga influencia essas propriedades metálicas.

## Atributos
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

W = Tungstênio

Al = Alumínio

Ti = Titânio

Tensile strength = Resistência à tração 

## Etapas do trabalho
- Introdução
- Tratamento dos dados
- Imports
- Dataset (modificações)
- Matriz de correlação
- Modelos (k-nn, árvore, floresta aleatória, shap)
- Conclusão
- Referências

## Orientando-se no código
- Inicialmente, importamos o dataset que está em um arquivo (.csv) utilizando a biblioteca pandas. Armazenamos esse dataset em uma variável (steel_df)
- Feito isso, removemos a coluna que continha as fórmulas químicas no dataset, uma vez que esse atributo, por mais que contenha informações relevantes sobre o material, não influencia na análise dos dados. Fazemos essa remoção  utilizando o comando ".drop" do pandas responsável por remover linhas ou colunas de datasets. Se o objetivo do trabalho envolvesse um estudo a fundo de ligas metálicas, ferro e aço, seria interessante manter, mas nosso objetivo é outro.
- Perfeito! Observamos que agora nosso dataset está conciso. Temos apenas dados numéricos referentes aos atributos comentados. Contamos a quantidade de cada atributo para verificar qual a ocorrência de cada um, para isso usamos um for dentro de outro for. Verificamos que o atributo W (Tungstênio) apareceu apenas 16 vezes no dataset. Decidimos remover esse atributo porque em comparação com os demais, ele se apresenta com uma pequena frequência.
- Ótimo, podemos partir para o cálculo da porcentagem de ferro de cada aço presente no dataset. Para isso, subtraimos a soma dos percentuais dos elementos na lista "elementos" de 100% presumindo que a soma de todos esses elementos deve ser igual a 100% na composição do aço, e o restante seria considerado como ferro. Atribuimos o resultado a uma variável 'fe'. Adicionamos essa nova coluna responsável por calcular a porcentagem de ferro ao dataset.
- Podemos iniciar a tentativa de encontrar uma correlação entre os materiais e a resistência a tração máxima. Para isso, traçamos uma matriz de correlação usando a função '.corr' do pandas. Observe que quando os valores dão próximos de 1 significa que há uma grande correlação, enquanto para valores próximos ou abaixo de 0 há uma correlação fraca/negativa.
- Temos o necessário para começar o treino e avaliação do melhor modelo.
- Vamos começar com o K-NN. O k-nn é um regressor 

## Referências:
[1] https://figshare.com/articles/dataset/Steel_Strength_Data/7250453 (dataset)

[2] https://citrination.com/datasets/153092/show_files/ (informações do dataset)
