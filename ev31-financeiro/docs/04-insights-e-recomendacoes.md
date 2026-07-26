# Insights e Recomendações de Negócio

## Contexto

A LogiCore (Soluções Integradas) precisava consolidar sua movimentação financeira de 2018 — hoje dispersa em planilhas — em um painel único que permitisse à diretoria acompanhar receita, custo, despesa e lucro sem depender de exportações manuais mensais.

## Objetivo do projeto

Construir um dashboard executivo que respondesse, a qualquer momento e com poucos cliques, três perguntas de negócio:

1. Qual é a saúde financeira da empresa (receita, custo, despesa e lucro) em um determinado ano?
2. Onde a receita e o custo estão concentrados (categoria, natureza da conta, cliente)?
3. Como a receita e os custos evoluem ao longo dos meses — existe sazonalidade?

## KPIs — Ano de 2018

| Indicador | Valor | Leitura |
|---|---|---|
| Receita | R$ 27,02 Mi | Faturamento bruto do período |
| Custo | R$ 19,19 Mi | 71,0% da receita |
| Despesa | R$ 4,79 Mi | 17,7% da receita |
| Lucro | R$ 3,03 Mi | Margem líquida de **11,2%** |

> Custo + Despesa consomem **88,8%** da receita, deixando uma margem líquida de pouco mais de um décimo do faturamento — um indicador que, isoladamente, já justifica investigar a composição dos custos (próxima seção).

## Principais Insights

### 1. A receita depende de poucos clientes (risco de concentração)
Os 5 maiores clientes somam **R$ 9,3 Mi**, ou seja, **34,4% de toda a receita do ano** vem de apenas 5 contas:

| Cliente | Receita | % da receita total |
|---|---|---|
| Cliente 26 | R$ 3,8 Mi | 14,1% |
| Cliente 9 | R$ 2,6 Mi | 9,6% |
| Cliente 1586 | R$ 1,3 Mi | 4,8% |
| Cliente 202 | R$ 0,9 Mi | 3,3% |
| Cliente 941 | R$ 0,7 Mi | 2,6% |

O Cliente 26 sozinho responde por mais receita do que os clientes 202 e 941 somados com folga — a perda desse único cliente teria um impacto direto e imediato na receita anual.

### 2. A receita operacional domina, mas a fonte não operacional é residual
92,4% da receita (≈ R$ 24,97 Mi) vem da operação principal (`Classificação = Operacional`), contra apenas 7,6% (≈ R$ 2,04 Mi) de receita não operacional. Isso indica um modelo de negócio pouco diversificado fora do core — o que é saudável do ponto de vista de foco, mas arriscado se a operação principal sofrer algum choque (perda de contrato, sazonalidade, concorrência).

### 3. O custo variável domina a estrutura de custos — e amplifica o risco de volume
Do total de Custo + Despesa (R$ 23,98 Mi), **74,2% é variável** (≈ R$ 17,78 Mi) contra **25,8% fixo** (≈ R$ 6,20 Mi). Uma estrutura majoritariamente variável é positiva para flexibilidade em meses fracos, mas também significa que qualquer aumento de volume/receita vem acompanhado de um aumento quase proporcional de custo — o que ajuda a explicar por que a margem líquida (11,2%) fica relativamente comprimida mesmo em um ano de receita alta.

### 4. Sazonalidade clara com pico em junho e vale em maio
A evolução mensal da receita mostra um padrão de "U invertido": queda entre janeiro e maio (mínimo em maio, ~R$ 1,7 Mi), forte recuperação até um pico em junho/julho (~R$ 3,8 Mi) e retração gradual até dezembro, estabilizando por volta de R$ 2 Mi no último trimestre. O gráfico de custos e despesas por mês acompanha esse mesmo padrão, com picos em abril, junho e agosto — ou seja, os meses de maior receita também concentram os maiores desembolsos, reforçando o ponto 3 (estrutura de custo majoritariamente variável).

### 5. O segundo semestre fecha mais fraco que o primeiro
Apesar do pico em junho/julho, receita e custo desaceleram de forma consistente de agosto em diante, terminando o ano em um patamar mensal próximo ao do início — um sinal de que o crescimento de meio de ano não se sustentou e vale investigar a causa (perda de contratos pontuais? sazonalidade do setor logístico? concorrência?).

## Recomendações de negócio

1. **Reduzir a dependência dos top 5 clientes** — criar metas comerciais para diversificar a carteira, com atenção especial ao Cliente 26 (14% da receita total isoladamente).
2. **Revisar a composição variável dos custos** — mapear quais componentes variáveis (frete, combustível, mão de obra terceirizada, etc.) mais crescem junto com a receita, buscando ganhos de escala que hoje não aparecem na margem.
3. **Investigar a queda de receita/custo no segundo semestre** — cruzar o mês de virada (agosto) com eventos de negócio (perda de contrato, sazonalidade do setor, ação da concorrência) para confirmar a causa raiz.
4. **Formalizar KPIs como medidas DAX explícitas** (ver [`02-modelo-dados.md`](./02-modelo-dados.md)) — hoje os totais dependem de agregação implícita, o que dificulta reutilizar as mesmas regras de negócio em outros relatórios.

## Limitações da análise

- Os valores por categoria/cliente acima foram calculados combinando os cartões de KPI com os percentuais exibidos nos gráficos de rosca do próprio dashboard — não a partir de uma nova consulta à base bruta.
- O painel cobre apenas o ano de 2018; não há comparação ano a ano (YoY) porque a base de dados de origem não trouxe outros anos.
- A causa da sazonalidade (ponto 4 e 5) é uma hipótese de análise, não uma conclusão validada com a área de negócio.

## Habilidades demonstradas neste projeto

`ETL com Power Query (M)` · `Modelagem de dados tabular` · `DAX` · `Storytelling com dados` · `Leitura de KPIs financeiros` · `Priorização de recomendações de negócio`
