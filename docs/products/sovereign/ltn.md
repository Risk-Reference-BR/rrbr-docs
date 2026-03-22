# LTN — Letra do Tesouro Nacional

## Definição

A **LTN** (Letra do Tesouro Nacional), também chamada de **Tesouro Prefixado** no Tesouro Direto, é um título público federal de renda fixa com taxa de juro **pré-fixada** e **sem pagamento de cupom** (zero coupon). O investidor compra com desconto e resgata o valor de face na data de vencimento.

> **Referência normativa:** Secretaria do Tesouro Nacional — Decreto 3.859/2001. ANBIMA — Manual de Marcação a Mercado, Seção 3.1.

## Características

| Atributo | Valor |
|----------|-------|
| Emissor | Tesouro Nacional (República Federativa do Brasil) |
| Moeda | BRL |
| Valor de face (no vencimento) | R$ 1.000,00 |
| Cupom | Nenhum (zero coupon) |
| Indexador | Pré-fixado |
| Convenção de juros | bus/252 |
| Liquidação | D+1 (SELIC) |
| Registro | SELIC (BCB) |
| Vencimentos típicos | Jan e Jul de cada ano (prazos de 3 meses a 4 anos) |

## Fórmula de Pricing

```
PU = 1.000 / (1 + taxa_anual) ^ (dias_uteis / 252)
```

Onde:
- `taxa_anual`: taxa de juro pré-fixada, em decimal (ex: 0,1265 para 12,65% a.a.)
- `dias_uteis`: número de dias úteis entre a data de liquidação (inclusive) e a data de vencimento (exclusive), pelo calendário ANBIMA
- `PU`: preço unitário, em reais (cotação convencional por 1.000 de face)

## Exemplo

LTN com vencimento em 01/07/2026, negociada em 20/03/2026 (liquidação D+1 = 23/03/2026):
- Suponha 70 dias úteis entre 23/03/2026 e 01/07/2026
- Taxa negociada: 14,50% a.a.

```
PU = 1.000 / (1,145) ^ (70/252) = 1.000 / 1,03812 = R$ 963,28
```

## Métricas de Risco

### DV01 (Dollar Value of 1 Basis Point)
Variação no PU para uma variação de 1 ponto-base (0,01%) na taxa:

```
DV01 = PU(taxa + 0,0001) - PU(taxa)
```

Para uma LTN com prazo de 1 ano a 14,50% a.a.:
```
DV01 ≈ -PU × (dias_uteis/252) / (1 + taxa) × 0,0001
```

### Duration Modificada
```
DM = (dias_uteis / 252) / (1 + taxa)
```

Para uma LTN, a duration modificada é simplesmente o prazo em anos ajustado pelo fator (1+taxa), pois não há cupons.

### Convexidade
```
Convexidade = (dias_uteis/252) × (dias_uteis/252 + 1) / (1 + taxa)^2
```

### Carry
Taxa de retorno diária da posição (assumindo curva constante):
```
Carry_diario = PU × [(1 + taxa)^(1/252) - 1]
```

## FRTB-SA — Sensibilidade

Para fins de FRTB-SA, a LTN gera sensibilidade no **bucket IR Brasil**:
- **Risk class**: Interest Rate (IR)
- **Tenor bucket**: conforme prazo (ON, 1M, 3M, 6M, 1Y, 2Y, 3Y, 5Y, 10Y, 15Y, 20Y, 30Y)
- **Sensibilidade Delta IR**: `s_k = -DV01 × 10.000` (por ponto-base × 10.000 = por 1% de taxa)

> **Referência normativa FRTB:** BCB Resolução 4.958/2021, Anexo I, Art. 5º. ISDA FRTB-SA Technical Standards, Tabela 2.

## Benchmark de Validação

Os preços indicativos de LTN são publicados diariamente pela **ANBIMA** (boletim de marcação a mercado). Toda implementação deve ser validada contra esses preços.

Fonte: https://www.anbima.com.br/pt_br/informar/precos-e-indices/precos/tesouro-nacional.htm
