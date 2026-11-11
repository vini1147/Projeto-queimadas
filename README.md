# Projeto-queimadas
## 📌 Visão geral

- **Objetivo:** Consolidar arquivos anuais de queimadas para análises no Power BI
- **Fonte dos dados:** https://dataserver-coids.inpe.br/queimadas/queimadas/focos/csv/anual/Brasil_sat_ref/
- **Destino:** tabelas Delta consumidas pelo Power BI
- **Frequência de atualização:** Diáriamente pelos workflows do Databricks


### Planejamento/Estruturação do projeto
URL Excalidraw - https://dbc-dd14da65-ca37.cloud.databricks.com/editor/files/2559291390849084?o=7474658522813524$0

## 🏗️ Arquitetura

```
Arquivos brutos (pasta no Databricks)
        │
        ▼
   [Bronze]  → ingestão fiel dos arquivos, sem alterações
        │
        ▼
   [Silver]  → limpeza, padronização de tipos, deduplicação
        │
        ▼
   [Gold]    → tabelas agregadas e modeladas para análise
        │
        ▼
    Power BI
```

## 📂 Estrutura do projeto

```
Projeto-queimadas/
├── documentos/
│   ├── Excalidraw - Arquitetura projeto queimadas.excalidraw   # arquivo editável do diagrama
│   └── Excalidraw - Arquitetura projeto queimadas.png          # imagem da arquitetura
├── notebooks/
│   ├── 01 - nb_bronze/
│   │   └── nb_raw_data_to_bronze      # ingestão dos dados brutos (Bronze)
│   ├── 02 - nb_silver/
│   │   └── nb_bronze_to_silver        # limpeza e padronização (Silver)
│   └── 03 - nb_gold/
│       └── <nb_silver_to_gold>        # agregações para o Power BI (Gold)
└── README.md
```