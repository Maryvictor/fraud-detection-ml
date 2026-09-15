# 🔍 Detecção de Fraude com Machine Learning

Projeto desenvolvido durante o curso **"Modelos Preditivos em Dados: Detecção de Fraude"** da Alura.

> ✅ **Curso concluído** — este README foi atualizado para refletir a reta final: árvore de decisão, random forest, comparação de modelos e ajuste de hiperparâmetros.

---

## 📌 Sobre o projeto

O objetivo é construir um modelo de machine learning capaz de identificar transações financeiras fraudulentas. Os dados utilizados são gerados pelo **PaySim**, um simulador de transações via mobile money que replica padrões de fraude reais sem expor dados sensíveis de clientes.

O dataset contém **101.613 transações**, sendo apenas **116 fraudes** — um cenário extremamente desbalanceado que é o maior desafio do projeto.

---

## 🗂️ Estrutura do projeto

```
fraud-detection-ml/
│
├── fraud_detection_paysim.ipynb   # Notebook principal com todo o pipeline
├── fraud_dataset_example.csv      # Dataset utilizado (PaySim)
└── README.md
```

---

## 🔬 Etapas desenvolvidas

- [x] Análise exploratória com Pandas (`describe`, `groupby`, `isnull`)
- [x] Visualização com Pandas Profiling
- [x] Encoding de variáveis categóricas (One-Hot Encoding)
- [x] Limpeza de colunas desnecessárias
- [x] Treinamento com Regressão Logística
- [x] Avaliação de métricas (Acurácia, Recall, Precisão, F1 Score)
- [x] Matriz de Confusão
- [x] Curva ROC e AUC
- [x] Técnicas de balanceamento de classes (undersampling, oversampling, SMOTE)
- [x] Árvore de Decisão (`DecisionTreeClassifier`)
- [x] Random Forest (`RandomForestClassifier`)
- [x] Comparação entre Regressão Logística, Árvore de Decisão e Random Forest
- [x] Ajuste de hiperparâmetros com `RandomizedSearchCV`

---

## 📊 Resultados — Regressão Logística (linha de base)

| Métrica | Valor |
|---|---|
| Acurácia | 99,9% |
| Recall | 4,3% |
| Precisão | 20% |
| F1 Score | 7,1% |
| AUC | 95,8% |

A acurácia de 99,9% parece incrível, mas o F1 Score de 7,1% conta a verdade: o modelo detectou apenas **1 fraude de 23** no conjunto de teste. O problema é o desbalanceamento extremo das classes — o modelo aprendeu que dizer "não é fraude" para tudo funciona quase sempre.

A AUC de 95,8% mostra que o modelo **tem potencial** para separar as classes, mas não tem confiança suficiente para cruzar o limiar de decisão. As próximas etapas (balanceamento + outros modelos) foram desenhadas exatamente pra resolver isso.

## 🧠 O que cada etapa nova acrescentou

- **Balanceamento de classes** (undersampling, oversampling, SMOTE): sem isso, o modelo aprende que dizer "não é fraude" pra tudo já dá quase 100% de acerto — e fica cego pras poucas fraudes reais. Balancear obriga o modelo a prestar atenção nelas.
- **Árvore de Decisão:** separa as transações fazendo perguntas sucessivas (ex.: valor acima de tal limite? conta ficou zerada?). Fácil de interpretar, mas sozinha tende a decorar demais o conjunto de treino.
- **Random Forest:** treina várias árvores em amostras diferentes dos dados e decide por **votação da maioria**, não pela "melhor árvore". Isso costuma deixar o resultado mais equilibrado entre recall e precisão do que uma árvore sozinha.
- **RandomizedSearchCV:** em vez de escolher os parâmetros do Random Forest no chute, testa várias combinações sorteadas com validação cruzada, otimizando especificamente para **recall** — a métrica mais importante quando o custo de deixar uma fraude passar é maior que o de investigar um caso legítimo à toa.

---

## 🛠️ Tecnologias utilizadas

- Python 3
- Pandas
- Scikit-learn
- imbalanced-learn (SMOTE)
- Matplotlib
- ydata-profiling

---

## 📚 Referências

- [Curso Alura — Modelos Preditivos em Dados: Detecção de Fraude](https://www.alura.com.br)
- [PaySim: A financial mobile money simulator](https://www.kaggle.com/datasets/ealaxi/paysim1)

