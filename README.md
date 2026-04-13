# Interpretabilidade de Modelos XGBoost: Agrupamento de Explicações via NMASHAP e Árvores Substitutas

## Resumo
Este repositório apresenta a implementação do método XCCSHAP (Explainable Cluster-Centric SHAP). A metodologia consiste na decomposição de modelos de aprendizado de máquina baseados em árvores em regras de decisão legíveis, utilizando agrupamento local e modelos substitutos para a representação das predições.

## Metodologia

O processo de análise é dividido em cinco etapas:

### 1. Modelo Base
Treinamento e ajuste do classificador XGBoost. O modelo é processado para atingir a convergência preditiva antes da análise de explicabilidade.

### 2. Vetores de Atribuição (SHAP)
Cálculo dos valores de Shapley para quantificar a contribuição individual de cada variável nas saídas do modelo.

### 3. Normalização NMASHAP
Aplicação da transformação de magnitude local (NMASHAP). Esta etapa padroniza os vetores de importância, preparando os dados para o processo de segmentação.

### 4. Agrupamento (K-Means)
Particionamento dos dados em clusters baseados nos perfis de explicabilidade NMASHAP. O objetivo é identificar padrões de decisão no espaço de atributos.

### 5. Árvores Substitutas
Treinamento de árvores de decisão de profundidade limitada para cada cluster identificado. O resultado é a extração de regras lógicas que descrevem o modelo original em subconjuntos específicos dos dados.

## Artefatos Gerados
- Estatísticas de importância de atributos por cluster.
- Análise de componentes principais (PCA) dos vetores de explicabilidade.
- Diagramas das árvores substitutas geradas.

## Tecnologias e Requisitos
- Python 3.x
- Bibliotecas: XGBoost, SHAP, Scikit-learn, Pandas, Numpy, Matplotlib, Seaborn.

## Utilização
Instalação das dependências:
```bash
pip install -r requirements.txt
```
Execução do pipeline: `xccshap_surrogate_trees.ipynb`.
