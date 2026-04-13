# Interpretabilidade de Modelos XGBoost via Agrupamento de Explicações SHAP (NMASHAP) e Indução de Árvores Substitutas Rasas

Este projeto apresenta uma metodologia para a extração de regras legíveis por humanos a partir de modelos complexos "caixa-preta" (XGBoost) utilizando o pipeline **XCCSHAP**.

## 🚀 Visão Geral

O projeto utiliza o dataset da UCI e aplica as seguintes etapas:
1. **Treinamento do Modelo Base:** Utilização do algoritmo XGBoost para alta performance preditiva.
2. **Explicabilidade SHAP:** Cálculo das contribuições marginais de cada atributo para as predições.
3. **Transformação NMASHAP:** Normalização por magnitude local das explicações SHAP.
4. **Agrupamento Latente (K-Means):** Identificação de perfis de decisão similares no espaço de explicabilidade.
5. **Modelos Substitutos (Surrogate Trees):** Indução de Árvores de Decisão rasas para cada cluster, permitindo a extração de regras de negócio em texto.

## 📊 Visualizações

O pipeline gera diversas visualizações para auditoria:
- Matriz de Importância de Atributos por Cluster.
- Projeção PCA de Componentes de Explicabilidade.
- Árvores de Decisão Renderizadas.

## 🛠️ Tecnologias

- Python 3.x
- XGBoost
- SHAP
- Scikit-learn
- Matplotlib / Seaborn

## 📂 Estrutura do Repositório

- `xccshap_surrogate_trees.ipynb`: Notebook principal com todo o pipeline.
- `xccshap/`: Pasta contendo os datasets utilizados.
- `*.png`: Gráficos e visualizações geradas durante a execução.
