# 🔍 Detecção de Fraude com Machine Learning

Projeto desenvolvido durante o curso **"Modelos Preditivos em Dados: Detecção de Fraude"** da Alura.

> 🚧 **Em andamento** — o repositório será atualizado conforme o curso avança.

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

## 🔬 Etapas desenvolvidas até agora

- [x] Análise exploratória com Pandas (`describe`, `groupby`, `isnull`)
- [x] Visualização com Pandas Profiling
- [x] Encoding de variáveis categóricas (One-Hot Encoding)
- [x] Limpeza de colunas desnecessárias
- [x] Treinamento com Regressão Logística
- [x] Avaliação de métricas (Acurácia, Recall, Precisão, F1 Score)
- [x] Matriz de Confusão
- [x] Curva ROC e AUC
- [ ] Técnicas de balanceamento de classes *(em breve)*
- [ ] Comparação com outros modelos *(em breve)*

---

## 📊 Resultados parciais — Regressão Logística

| Métrica | Valor |
|---|---|
| Acurácia | 99,9% |
| Recall | 4,3% |
| Precisão | 20% |
| F1 Score | 7,1% |
| AUC | 95,8% |

A acurácia de 99,9% parece incrível, mas o F1 Score de 7,1% conta a verdade: o modelo detectou apenas **1 fraude de 23** no conjunto de teste. O problema é o desbalanceamento extremo das classes — o modelo aprendeu que dizer "não é fraude" para tudo funciona quase sempre.

A AUC de 95,8% mostra que o modelo **tem potencial** para separar as classes, mas não tem confiança suficiente para cruzar o limiar de decisão. A solução vem nas próximas etapas do curso.

---

## 🛠️ Tecnologias utilizadas

- Python 3
- Pandas
- Scikit-learn
- Matplotlib
- ydata-profiling

---

## 📚 Referências

- [Curso Alura — Modelos Preditivos em Dados: Detecção de Fraude](https://www.alura.com.br)
- [PaySim: A financial mobile money simulator](https://www.kaggle.com/datasets/ealaxi/paysim1)
