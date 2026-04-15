# XCCSHAP Interpretability

Implementacao de interpretabilidade para modelos XGBoost baseada em SHAP values, co-clustering PB-tauCC e arvores substitutas rasas.

## Referencia

Pensa, R. G., Crombach, A., Peignier, S., & Rigotti, C. (2025).
Explaining Random Forest and XGBoost with Shallow Decision Trees by Co-clustering Feature Importance.
Machine Learning, 114(12).
https://doi.org/10.1007/s10994-025-06932-9

## Objetivo

Fornecer um pipeline reprodutivel para:

1. Treinar um modelo opaco (XGBoost).
2. Explicar o modelo com SHAP.
3. Agrupar instancias e atributos no espaco NMASHAP.
4. Induzir arvores substitutas por cluster.
5. Avaliar fidelidade e compreensibilidade.
6. Gerar visualizacoes tecnicas para analise global e local.

## Estrutura do Projeto

```text
.
|-- notebooks/
|   `-- xccshap_v5_final.ipynb
|-- xccshap_surrogate_trees.ipynb
|-- requirements.txt
`-- README.md
```

## Dataset

O pipeline utiliza o arquivo `uci_dataset_222.pkl` (Bank Marketing, UCI), disponibilizado no repositorio oficial do XCCSHAP:

https://github.com/rupensa/xccshap/tree/main/uci_dataset

O notebook assume que o dataset ja esta previamente curado no formato esperado pela implementacao base.

## Pipeline (Notebook v5)

1. Configuracao e ingestao.
2. Treinamento e avaliacao do XGBoost.
3. XCCSHAP core: SHAP, MASHAP, NMASHAP e co-clustering PB-tauCC.
4. Validacao do co-clustering (Silhouette, Davies-Bouldin, tau).
5. Inducao do modelo substituto por cluster.
6. Avaliacao global (fidelidade e compreensibilidade).
7. Explicacoes locais de predicoes individuais.
8. Visualizacoes (heatmaps, arvore fundida e projecoes).

## Ambiente

Recomendado:

- Python 3.10+
- Pip atualizado

Instalacao:

```bash
pip install -r requirements.txt
```

## Execucao

1. Abra o notebook principal `notebooks/xccshap_v5_final.ipynb`.
2. Execute as celulas em ordem.
3. Revise os artefatos gerados (figuras, metricas e relatorios no output das celulas).

## Observacoes

- A implementacao inclui ajuste de compatibilidade para ambiente Python moderno na biblioteca base do XCCSHAP.
- As metricas de fidelidade sao calculadas contra as predicoes do modelo opaco, conforme a abordagem surrogate.
