# Detecção de Anomalias em Transações em Python

Projeto final do Bootcamp de Dados — DIO/Anhanguera.  
Detecção de fraudes bancárias em transações com cartão de crédito usando técnicas de Machine Learning supervisionado e não-supervisionado.

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
Bootcamp Afya Dados — DIO / Anhanguera — 2026
