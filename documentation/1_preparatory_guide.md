### 1. Como você abordaria a implementação de um modelo de machine learning para determinar a elegibilidade de crédito inicial e ajuste de limite?

***Exercício: Escreva um esboço de como estruturaria o pipeline de dados para esse modelo, desde a coleta de dados até a implementação do modelo em produção.***

Bom, eu executaria algumas etapas como entendimento do negócio, coleta de dados, análise exploratória, preparação e modelagem de dados, experimentos, deploy e monitoramento do modelo em produção.

- Em entendimento do negócio eu buscaria entender as regras de negócio e as métricas mais importantes da área de crédito. Isso me ajudaria a compreender o cenário atual de crédito da empresa, o objetivo de negócio e as métricas mais importantes.

- Em coleta de dados, após o levantamento de requisitos realizado com a àrea de negócios, eu buscaria por dados relacionados ao aplicante/cliente como exemplo: Idade, Estado Civil, Escolaridade, Possui Casa Própria, Possui Carro Próprio, Número de Filhos, Score do Serasa, Número de dias/meses inadimplente, Dados de transações bancárias (i/o). Então eu buscaria por informações como essas dentro da companhia e verificaria a disponibilidade e qualidade dos dados. Caso exista alguma questão de acesso aos dados ou qualidade, a ideia seria trabalhar em pair com um Analytics Engineer do time para trabalhar na coleta e disponibilidade dos dados em paralelo aos experimentos do modelo.

- Em análise exploratória eu buscaria analisar alguns pontos como: Tipo dos dados, Nulos, Outliers, Classes/Categorias com pouca amostragem, Escala, Colinearidade, Correlação com o target.
```
    . Em tipos dos dados eu checaria se os dados estão com seus tipos corretos
    
    . Em nulos eu analisaria o número de observações nulas e também a distribuição da variável, com isso eu analisária as melhores abordagens para os experimentos utilizando a média, mediana, moda ou preenchimento com zero. Aqui eu testaria as 4 abordagens e avaliaria o modelo.

    . Em outliers eu utilizaria o cálculo do z-score, onde pra cada observação é calculado um score indicando quantos desvios acima ou abaixo a observação está em relação a média. Com isso eu poderia criar uma flag por observação marcando como outlier sim/não caso o score seja menor que -3 ou maior que 3.

    . Em classes com pouca amostragem, exemplo escolaridade igual a pós doutorado, eu pensaria em aplicar feature engineering pra criar novas classes e agrupar categorias com pouca amostragem na etapa de preparação e modelagem dos dados.

    . Em escala de dados, eu analisaria quais variáveis precisam se reescalonadas de maneira a não atrapalhar o fit do modelo.
    
    . Em colinearidade, eu analisaria se as variáveis são realmente independentes e caso exista uma correlação forte entre algumas variáveis eu pensaria em algumas estratégias de feature engineering de maneira a combinar essas variáveis ou até mesmo em aplicar uma análise componentes principais (PCA) e criar novas features através desse processo.

    . E por último eu analisaria a distribuição da variável dias/meses inadimplentes e identificaria qual a melhor forma de criar o target de acordo com as informações levantadas com a área de negócios. Por exemplo, definir como True (aprovado) observações com até 60 dias como inadimplente e False (negado) acima de 60 dias.
```

- Em preparação e modelagem dos dados eu aplicaria basicamente as tratativas levantadas na análise exploratória e também a transformação de variáveis categóricas utilizando OneHotEncoding, por exemplo.

- Após a preparação dos dados eu trabalharia no design dos experimentos
```
    . 
```


- Após analisar os dados, já seria possível definir quais estratégias de modelagem e feature engineering são importantes e começaria a desenhar os primeiros experimentos. Para isso eu separaria a base em treino e teste 90/10 e utilizaria cross validation baseado em acurácia balanceada.

- Outra abordagem que utilizaria em dados desbalanceados seria o balanceamento através de pesos das classes informados via parâmetro para o modelo. Para os pesos podemos utilizar a proporção inversa das classes, exemplo, classe 1 possui 70% das observações, classe 0 possui 30%, então os pesos ficariam class_weight = {1: 0.3, 0: 0.7}

- Como baseline usaria uma Regressão Logistica sem ajuste de hiperparâmetros, e depois compararia o baseline com outros modelos como Decision Tree, Random Forest e XGBoost.

- Para cada experimento eu faria otimização de hiperparâmetros avaliando o trade-off entre viés e variância.
```
    . Overfitting = Ajuste excessivo
    . Underfitting = Ajuste insuficiente

    O objetivo dos modelos de ML é estimar a função que melhor ajusta aos dados de entrada para obter previsões corretas de forma generalizada. A melhor maneira de medir e otimizar o desempenho do modelo é levar em consideração o viés e a variação resultante.

    Bias (viés) = Erro devido à diferença entre as previsões médias e os valores corretos que estamos tentando prever.

    Variância = Erro devido à variabilidade de uma previsão do modelo para um determinado ponto de dados.
```




----

2. Quais são as principais métricas de performance que você consideraria ao avaliar a eficácia de um modelo de underwriting de crédito?

Exercício: Implementar uma função em Python para calcular e comparar diferentes métricas, como AUC-ROC, precisão, recall, e F1-score, aplicadas a um dataset de classificação binária.

3. Como você garantiria que o modelo de crédito é justo e não discrimina com base em atributos sensíveis como idade ou gênero?

Exercício: Simule um cenário onde você tem que identificar possíveis vieses no modelo de crédito e escreva um código para medir e mitigar esses vieses.

4. Se um modelo de crédito precisa ser ajustado para um novo mercado, como você abordaria a customização desse modelo sem perder a generalização?

Exercício: Desenhe um experimento A/B em Python que testaria o modelo em diferentes subsets de dados (e.g., diferentes regiões geográficas) e analise os resultados.

5. Qual seria a sua abordagem para lidar com dados desbalanceados no contexto de underwriting de crédito?

Exercício: Implementar técnicas de balanceamento de dados, como oversampling, undersampling, ou SMOTE, e discutir os impactos na performance do modelo.

6. Como você lidaria com a necessidade de explicabilidade do modelo em um ambiente regulado como o de crédito?

Exercício: Explore a utilização de bibliotecas como LIME ou SHAP para explicar as previsões de um modelo de machine learning, garantindo que as explicações sejam claras e acionáveis.

7. Como garantir que o código do modelo esteja bem estruturado e fácil de manter à medida que a solução evolui?

Exercício: Refatorar um código existente de machine learning, melhorando a modularidade e a legibilidade, e escreva testes utilizando pytest para garantir a qualidade do código.

8. Como você implementaria um sistema de monitoramento para garantir que o modelo de crédito continue a performar bem em produção?

Exercício: Desenvolver um script em Python que monitore a drift de dados e a performance do modelo ao longo do tempo, enviando alertas quando forem detectadas anomalias.

9. Como você abordaria a necessidade de reavaliar a elegibilidade de crédito dos aplicantes periodicamente?

Exercício: Escreva um cron job em Python que reavalie periodicamente os scores de crédito dos aplicantes utilizando um modelo previamente treinado.

10. Quais desafios você antecipa ao integrar soluções de machine learning com sistemas legados em um banco, e como você os abordaria?

Exercício: Planeje uma estratégia de integração para um modelo de machine learning com um sistema legado, incluindo uma abordagem de versionamento e rollback para modelos em produção.