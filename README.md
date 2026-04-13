# Interpretabilidade de Modelos XGBoost via Agrupamento de Explicações SHAP (NMASHAP) e Indução de Árvores Substitutas Rasas

## Resumo Executivo

Este projeto implementa o pipeline **XCCSHAP (Explainable Cluster-Centric SHAP)**, uma metodologia robusta para a decomposição e auditoria de modelos de aprendizado de máquina do tipo "caixa-preta". O foco principal é a transição de previsões complexas de conjuntos (Ensembles) para regras de decisão discretas e interpretáveis, preservando a fidelidade local através de modelagem substituta.

---

## Arquitetura da Metodologia

O fluxo de processamento está estruturado em cinco etapas fundamentais de engenharia de dados e modelagem estatística:

### 1. Ingestão de Dados e Modelagem Base
Fase de provisionamento de dependências e indução do classificador primário utilizando o algoritmo **XGBoost**. O modelo é otimizado para performance preditiva antes da extração de explicabilidade.

### 2. Decomposição de Atributos via SHAP
Cálculo das contribuições marginais (Shapley Values) para cada instância do dataset. Esta etapa mapeia a importância de cada atributo no espaço de predição do modelo.

### 3. Transformação NMASHAP e Espaço Latente
Aplicação da técnica **NMASHAP (Normalized Magnitude SHAP)** para normalização das explicabilidades por magnitude local. Esta transformação é crítica para mitigar vieses de escala e preparar os dados para o particionamento não supervisionado.

### 4. Agrupamento Local (K-Means)
Utilização de **K-Means Clustering** sobre os vetores NMASHAP para identificar perfis de decisão latentes. O objetivo é segmentar a superfície de resposta do modelo em clusters com comportamentos de explicabilidade homogêneos.

### 5. Indução de Modelos Substitutos (Surrogate Models)
Indução de **Árvores de Decisão de Baixa Profundidade** (Shallow Trees) para cada cluster identificado. Esta etapa converte a lógica interna do XGBoost em regras de negócio em formato textual e visual, facilitando a auditoria e conformidade.

---

## Entregas Técnicas e Visualizações

O pipeline gera artefatos visuais de alta densidade informativa para suporte à decisão:
- **Análise de Variância de Atributos:** Matrizes de importância média por cluster.
- **Topologia de Grupos:** Projeções via PCA para validação da separação dos perfis de decisão.
- **Renderização de Fluxogramas:** Diagramas topológicos das árvores substitutas rasas.

---

## Stack Tecnológica

- **Core:** Python 3.x
- **Modelagem Base:** XGBoost
- **Explicabilidade:** SHAP
- **Manuseio de Dados:** Pandas, Numpy
- **Aprendizado Estatístico:** Scikit-learn (K-Means / Decision Trees)
- **Visualização:** Matplotlib, Seaborn

---

## Configuração do Ambiente

Para replicar o ambiente de desenvolvimento e as análises, instale as dependências via:

```bash
pip install -r requirements.txt
```

O pipeline completo pode ser executado através do notebook: `xccshap_surrogate_trees.ipynb`.
