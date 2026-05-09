# Detecção de Anomalias em Transações em Python

Esse projeto foi desenvolvido como desafio final do bloco de análise de dados do bootcamp Afya Dados na DIO. O objetivo foi construir um sistema de detecção de fraudes bancárias usando machine learning em Python.

O maior desafio foi lidar com os dados desbalanceados — menos de 0,2% das transações são fraudes, o que faz qualquer modelo parecer bom só pela acurácia. Aprendi na prática que acurácia não serve pra esse tipo de problema e passei a usar ROC-AUC, Precision e Recall.

Testei diferentes abordagens: undersampling manual, SMOTE pra criar amostras sintéticas de fraude e o parâmetro `class_weight='balanced'` no Random Forest. Também usei RandomizedSearchCV pra encontrar os melhores hiperparâmetros e SHAP pra entender quais variáveis mais influenciaram as previsões.

No final, todos os modelos passaram de 0.96 de ROC-AUC, o que mostrou que a combinação de balanceamento com Random Forest funciona bem nesse tipo de dado.

---

## Objetivo

Construir um pipeline completo de detecção de fraudes partindo de dados brutos até a explicabilidade do modelo final, abordando o principal desafio prático: **classificação desbalanceada** (< 0.2% de fraudes no dataset).

---

## Dataset

**Credit Card Fraud Detection** — dataset público disponibilizado pelo TensorFlow/Google.  
- ~284.807 transações de cartão de crédito europeias
- 30 features: `V1`–`V28` (PCA anonimizado), `Amount`, `Time`
- `Class`: 0 = legítima, 1 = fraude (492 fraudes no total)

---

## Estrutura do Notebook

### Módulo 1 — Primeiros Passos
- Carregamento e exploração dos dados (EDA)
- Feature Engineering (`Amount_log`, escalonamento com `RobustScaler`)
- Divisão treino/teste estratificada
- Modelo baseline: Regressão Logística

### Módulo 2 — Avaliação e Técnicas de Balanceamento
- Métricas adequadas: Confusion Matrix, ROC-AUC, Precision-Recall
- Undersampling manual
- Oversampling com SMOTE
- Random Forest com `class_weight="balanced"`

### Módulo 3 — Modelos Avançados e Explicabilidade
- Importância das variáveis
- Ajuste de hiperparâmetros com `RandomizedSearchCV`
- Explicabilidade com SHAP (`TreeExplainer` + `summary_plot`)
- Avaliação final do melhor modelo

---

## Como Executar

1. Clone ou baixe o repositório
2. Instale as dependências:
```bash
pip install -r requirements.txt
```
3. Abra o notebook:
```bash
jupyter notebook deteccao_fraudes.ipynb
```
Ou abra diretamente no VS Code com a extensão **Jupyter**.

4. Execute todas as células em ordem: `Kernel → Restart & Run All`

---

## Resultados Esperados

| Métrica | Resultado |
|---|---|
| ROC-AUC | > 0.95 |
| Recall (fraude) | > 0.70 |
| Precision-Recall AUC | > 0.80 |

---

## Tecnologias Utilizadas

- Python 3.10+
- pandas, numpy
- scikit-learn
- imbalanced-learn (SMOTE)
- matplotlib, seaborn
- SHAP

---

## Boas Práticas Aplicadas

- Funções modulares com docstrings
- `random_state=42` para reprodutibilidade
- Constantes no topo do notebook
- Markdown estruturado separando cada seção
- Sem data leakage: escalonamento fit apenas no treino

---

## Autoria

Projeto desenvolvido como Desafio Final do bloco **Python Aplicado à Análise de Dados**  
Bootcamp Afya Dados — DIO — 2026
