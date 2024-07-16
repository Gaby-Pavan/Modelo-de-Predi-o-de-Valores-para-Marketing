# Modelo-de-Predicao-de-Valores-para-Marketing
Construção de um modelo de regressão 

CONTEXTO DO PROJETO:
A empresa está investindo mensalmente em plataformas de publicidade online, como Youtube, Facebook e newspaper, para a prospecção de leads 
(pessoas interessadas em seus produtos). A fim de acompanhar o desempenho desses investimentos, a empresa registra todos os gastos com 
publicidade e todos os retornos de vendas gerados a partir desses investimentos em uma tabela de excel.
Para entender melhor a relação entre as variáveis presentes nesses registros e identificar os fatores que mais impactam na geração de leads,
a empresa solicitou a análise de um especialista em dados par criar um modelo de predição de valores para estimar o retorno de vendas que 
pode ser gerado a partir de um determinado investimento em publicidade.

Para entregar esse projeto, fiz uma analise descritiva dos dados para compreender melhor as variáveis e identificar possíveis problemas com 
os dados. Posteriormente foi feita uma análise exploratória para identificar as relações entre as variáveis e descobrir padrões relevantes.
Tudo foi realizado em Python utilizando o Collab.

Parplot para indentificar a relação dos investimentos com o retorno em vendas:

![parplot](https://github.com/user-attachments/assets/03005efa-baf5-42bd-a70e-3edf93fb433d)

Heatmap para avaliar a correlação entre as variáveis:

![heatmap](https://github.com/user-attachments/assets/28fa7ef7-3445-429f-a279-2ee00947f117)


Feita essas análises estatísticas iniciei a etapa de modelagem, onde foi escolhido o modelo de Regressão Linear para construir a previsão 
solicitada pela empresa. 

```
#definindo as variáveis para o modelo de regressão
x = base_mkt[['youtube','facebook','newspaper']]
y = base_mkt[['sales']]

from sklearn.model_selection import train_test_split
x_train, x_test, y_train, y_test = train_test_split(x, y, train_size = 0.7, test_size = 0.3, random_state = 4)

reg_linear = LinearRegression()

reg_linear.fit(x_train, y_train)

y_pred = reg_linear.predict(x_test) #treinando o modelo

#calculando o coeficiente de determinação
from sklearn.metrics import r2_score
r = r2_score(y_test, y_pred)

print('r_quadrado: ', r) #o resultado mostra uma alta linearidade entre as variáveis, 90%

# exemplo de aplicação do modelo, prevendo as vendas com base nos investimentos

inv_facebook = 50
inv_youtube = 300
inv_newspaper = 15
entrada = [[inv_facebook, inv_youtube, inv_newspaper]]
reg_linear.predict(entrada)[0]

```

Acesse o arquivo ipynb para ver o código completo


