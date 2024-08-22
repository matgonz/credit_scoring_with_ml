### Credit Card Approval Solution Using Machine Learning

Credit scoring models evaluate an individual profile by analyzing factors like their payment history, number of accounts, credit types, and other financial information, along with demographic information to create a credit score. This credit score is then used by lending firms to determine if it's safe to lend money to an application.






Análise Exploratória
- Verificar o número de linhas e colunas
- Verificar o tipo dos dados
- Verificar se existem valores nulos
    . Qual estratégia de preenchimento de nulos?
- Análise descritiva das variáveis
    - Entendendo a distribuição das variáveis
    - Frequência das classes
- Análise de outliers
    - Identificação de outliers utilizando z-score
    . Qual estratégia utilizaria para tratar ou remover outliers?
- Análise da vaiável alvo
    . A variável é balanceada?
    . Caso não, quais estratégias utilizaria de balanceamento?

Pré-processamento dos Dados
- LabelEncoder = OneHotEncoder das variáveis categóricas
- Separação das bases entre treino/validação/teste

Experimentos:
- Algoritmos de classificação: Regressão Logistica, Decision Tree, Random Forest, XGBoost, GradientBoosting, NeuralNet
- GridSearchCV para otimização dos hiperparâmetros
- Avaliação do modelo
    - Métricas apropriadas para o modelo
    - Cross-Validation para evitar overfiting



```
MLE Programming Case - Objetivo da entrevista:

- Nesta entrevista compartilhamos um contexto relacionado à Machine Learning com uma base de código de trabalho e discutiremos qual é o objetivo do contexto e como ele funciona.
- Durante o case, serão criadas problematizações sobre o contexto inical apresentado que exigirão não só alterações no código, mas também discussões sobre conceitos técnicos de negócio para a definição da melhor abordagem a ser tomada.


O que avaliamos:
- Compreensão e resolução de problemas
- Expressar e defender um ponto de vista
- Capacidade analítica em processos de decisão
- Arquitetura de software
- Estrutura de código e qualidade dos testes
- Intuição de negócio

Dicas:
- Discuta suas ideias com a pessoa entrevistadora antes de implementar e testar a solução
- Tente explorar como a solução interage com o contexto de negócio

Nossas expectativas:
- Familiaridade com Python
- Conhecimento básico do uso da biblioteca pytest
```