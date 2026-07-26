# ETL — Extração e Transformação

## Fonte

| Item | Valor |
|---|---|
| Tipo de fonte | Excel |
| Arquivo | `Base de Dados Aula 01.xlsx` |
| Planilha | `Movimentação` |
| Modo de carga | Import |

## Etapas do Power Query (M)

| # | Etapa | O que faz |
|---|---|---|
| 1 | `Fonte` | Abre o arquivo Excel e lê o workbook |
| 2 | `Movimentação_Sheet` | Seleciona a planilha `Movimentação` |
| 3 | `Cabeçalhos Promovidos` | Promove a primeira linha a cabeçalho de coluna |
| 4 | `Tipo Alterado` | Define o tipo de dado de cada coluna (texto, número, data, inteiro) |
| 5 | `Valor Substituído` | Na coluna `Classificação`, substitui o texto `"Receita"` por `"-"` |

## Código M completo

```powerquery-m
let
    Fonte = Excel.Workbook(File.Contents("C:\Imersao\Aula 01\Base de Dados\Base de Dados Aula 01.xlsx"), null, true),
    Movimentação_Sheet = Fonte{[Item="Movimentação",Kind="Sheet"]}[Data],
    #"Cabeçalhos Promovidos" = Table.PromoteHeaders(Movimentação_Sheet, [PromoteAllScalars=true]),
    #"Tipo Alterado" = Table.TransformColumnTypes(#"Cabeçalhos Promovidos",{
        {"Cliente", type text},
        {"Estado do Cliente", type text},
        {"Valor", type number},
        {"Data da Movimentação", type date},
        {"Conta Contábil", Int64.Type},
        {"Tipo", type text},
        {"Natureza da Conta", type text},
        {"Categoria", type text},
        {"Classificação", type text}
    }),
    #"Valor Substituído" = Table.ReplaceValue(#"Tipo Alterado","Receita","-",Replacer.ReplaceText,{"Classificação"})
in
    #"Valor Substituído"
```

## Colunas resultantes

| Coluna | Tipo |
|---|---|
| Cliente | Texto |
| Estado do Cliente | Texto |
| Valor | Número |
| Data da Movimentação | Data |
| Conta Contábil | Inteiro |
| Tipo | Texto |
| Natureza da Conta | Texto |
| Categoria | Texto |
| Classificação | Texto |

> **Nota:** o passo `Valor Substituído` sugere que a coluna `Classificação` carregava algum prefixo/rótulo `"Receita"` que foi normalizado. Vale documentar a regra de negócio exata junto à fonte original, caso ela não seja óbvia só pelo dado.
