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
│   ├── 03-visualizacao.md   # Dashboard e mapeamento de campos
│   └── 04-insights-e-recomendacoes.md  # Leitura de negócio, KPIs e recomendações
└── assets/
    └── dashboard-financeiro.png
```

## Resumo do pipeline

1. **Extração**: leitura da planilha `Movimentação` de um arquivo Excel local.
2. **Transformação**: promoção de cabeçalhos, tipagem de colunas e limpeza da coluna `Classificação`.
3. **Modelagem**: tabela fato `Movimentação` + tabela calendário automática do Power BI, relacionada por `Data da Movimentação`. Duas colunas calculadas (`Valor com Sinal`, `Mês Abrev`) dão suporte às visualizações.
4. **Visualização**: dashboard único com KPIs (Receita, Custo, Despesa, Lucro), evolução mensal da receita, receita por categoria, custos/despesas por mês e top 5 clientes.

Detalhes de cada etapa nos documentos da pasta [`docs/`](./docs).

## Principais insights

- Custo + Despesa consomem 88,8% da receita, resultando em margem líquida de **11,2%**.
- Os 5 maiores clientes concentram **34,4%** da receita total do ano.
- 74,2% da estrutura de custos é variável, o que amplifica o efeito da sazonalidade na margem.
- Receita e custos têm o mesmo padrão sazonal (pico em jun/jul, queda no 2º semestre), o que sugere causa comum.

Leitura completa, com números por indicador e recomendações de negócio, em [`04-insights-e-recomendacoes.md`](./docs/04-insights-e-recomendacoes.md).

## Observação

Este documento descreve a camada de dados (ETL + modelo) extraída diretamente do arquivo `.pbix` via conexão ao modelo semântico. A camada de relatório (posição exata dos visuais, formatação) foi documentada a partir de inspeção visual do dashboard, não da definição técnica do relatório.
