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
- Análise Exploratória dos dados
- 
-

## Orientando-se no código
- Inicialmente, importamos o dataset que está em um arquivo (.csv) utilizando a biblioteca pandas. Armazenamos esse dataset em uma variável (steel_df)
- Feito isso, removemos a coluna que continha as fórmulas químicas no dataset, uma vez que esse atributo, por mais que contenha informações relevantes sobre o material, não influencia na análise dos dados. Fazemos essa remoção  utilizando o comando ".drop" do pandas responsável por remover linhas ou colunas de datasets. Se o objetivo do trabalho envolvesse um estudo a fundo de ligas metálicas, ferro e aço, seria interessante manter, mas nosso objetivo é outro.
- Perfeito! Observamos que agora nosso dataset está conciso. Temos apenas dados numéricos referentes aos atributos comentados 

## Referências:
[1] https://figshare.com/articles/dataset/Steel_Strength_Data/7250453 (dataset)

[2] https://citrination.com/datasets/153092/show_files/ (informações do dataset)
