# Projeto-queimadas
## 📌 Visão geral

- **Objetivo:** Consolidar arquivos anuais de queimadas para análises em ferramentas de BI's
- **Fonte dos dados:** https://dataserver-coids.inpe.br/queimadas/queimadas/focos/csv/anual/Brasil_sat_ref/
- **Destino:** tabelas Delta consumidas pelo Power BI
- **Frequência de atualização:** Diáriamente pelos workflows do Databricks

#### Planejamento/Estruturação do projeto
![Arquitetura do projeto](imagens/Excalidraw - Arquitetura projeto queimadas.png)

## 🧰 Tecnologias e ferramentas

#### Linguagens

![PySpark](https://img.shields.io/badge/PySpark-E25A1C?style=for-the-badge&logo=apachespark&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=postgresql&logoColor=white)

#### Plataforma e armazenamento

![Databricks](https://img.shields.io/badge/Databricks-FF3621?style=for-the-badge&logo=databricks&logoColor=white)
![Delta Lake](https://img.shields.io/badge/Delta%20Lake-00ADD8?style=for-the-badge&logo=delta&logoColor=white)
![Apache Spark](https://img.shields.io/badge/Apache%20Spark-E25A1C?style=for-the-badge&logo=apachespark&logoColor=white)

#### Visualização e BI

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![Databricks Dashboards](https://img.shields.io/badge/Databricks%20AI%2FBI%20Dashboard-FF3621?style=for-the-badge&logo=databricks&logoColor=white)
![Databricks Genie](https://img.shields.io/badge/Databricks%20Genie-FF3621?style=for-the-badge&logo=databricks&logoColor=white)

#### Versionamento e documentação

![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)
![Excalidraw](https://img.shields.io/badge/Excalidraw-6965DB?style=for-the-badge&logo=excalidraw&logoColor=white)


## 🏗️ Arquitetura

```
Arquivos brutos (pasta no Databricks - raw_data)
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
    Power BI | Dashboard (Databricks)
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