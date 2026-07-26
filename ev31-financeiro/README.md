# Dashboard Financeiro — LogiCore

Análise financeira em Power BI com ETL em Power Query, modelagem tabular e dashboard executivo (Receita, Custo, Despesa e Lucro).

![Dashboard Financeiro](assets/dashboard-financeiro.png)

## Stack

| Camada | Ferramenta |
|---|---|
| Fonte de dados | Excel (`Base de Dados Aula 01.xlsx`) |
| ETL | Power Query (M) |
| Modelagem | Power BI Desktop (modelo tabular) |
| Visualização | Power BI Desktop |

## Estrutura do repositório

```
ev31-financeiro/
├── README.md
├── docs/
│   ├── 01-etl.md            # Extração e transformação (Power Query)
│   ├── 02-modelo-dados.md   # Tabelas, colunas, relacionamentos
│   └── 03-visualizacao.md   # Dashboard e mapeamento de campos
└── assets/
    └── dashboard-financeiro.png
```

## Resumo do pipeline

1. **Extração**: leitura da planilha `Movimentação` de um arquivo Excel local.
2. **Transformação**: promoção de cabeçalhos, tipagem de colunas e limpeza da coluna `Classificação`.
3. **Modelagem**: tabela fato `Movimentação` + tabela calendário automática do Power BI, relacionada por `Data da Movimentação`. Duas colunas calculadas (`Valor com Sinal`, `Mês Abrev`) dão suporte às visualizações.
4. **Visualização**: dashboard único com KPIs (Receita, Custo, Despesa, Lucro), evolução mensal da receita, receita por categoria, custos/despesas por mês e top 5 clientes.

Detalhes de cada etapa nos documentos da pasta [`docs/`](./docs).

## Observação

Este documento descreve a camada de dados (ETL + modelo) extraída diretamente do arquivo `.pbix` via conexão ao modelo semântico. A camada de relatório (posição exata dos visuais, formatação) foi documentada a partir de inspeção visual do dashboard, não da definição técnica do relatório.
