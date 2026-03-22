# Futuro DI (DI1) — Contrato Futuro de Taxa Média de Depósitos Interfinanceiros de Um Dia

## Definição

O **Futuro DI** (código B3: **DI1**) é o derivativo de taxa de juros mais líquido do Brasil e um dos mais líquidos do mundo em seu segmento. Permite a negociação da taxa de juro pré-fixada para um prazo futuro, usando como referência a taxa CDI acumulada até o vencimento do contrato.

> **Referência normativa:** B3 — Especificações do Contrato Futuro de Taxa Média de Depósitos Interfinanceiros de Um Dia (DI1). Disponível em: https://www.b3.com.br/pt_br/produtos-e-servicos/negociacao/renda-fixa/futuro-di.htm

## Características do Contrato

| Atributo | Valor |
|----------|-------|
| Código | DI1 |
| Ativo objeto | Taxa CDI acumulada no período |
| Tamanho do contrato | PU × R$ 1,00 (o PU é o "notional" em reais) |
| Valor de face | R$ 100.000,00 no vencimento |
| Cotação | Taxa de juro anual, base bus/252, em % a.a. |
| Vencimento | Primeiro dia útil de cada mês |
| Liquidação no vencimento | Financeira (D+1) |
| Ajuste diário | Sim — variação de PU ajustada diariamente |
| Garantia | Câmara B3 (novação) |

## Mecânica de Cotação — PU vs Taxa

O DI1 é cotado em **taxa** (ex: 14,50% a.a.), mas o valor financeiro é calculado em **PU (Preço Unitário)**:

```
PU = 100.000 / (1 + taxa/100) ^ (dias_uteis / 252)
```

Onde `dias_uteis` é o número de dias úteis entre D+1 (data de liquidação da operação, ou seja, o dia seguinte à negociação) e a data de vencimento do contrato.

> **Importante:** a cotação em taxa é invertida em relação ao PU. Quando a taxa sobe, o PU cai. Um comprador de DI1 ganha quando a taxa cai (PU sobe).

## Exemplo de Cálculo

Contrato DI1 com vencimento em 01/07/2026, negociado em 20/03/2026:
- Dias úteis entre 23/03/2026 (D+1) e 01/07/2026: 70 du
- Taxa negociada: 14,50% a.a.

```
PU = 100.000 / (1,145) ^ (70/252) = R$ 96.328,xx
```

## Ajuste Diário

O DI1 tem ajuste diário de posições. A variação de PU entre dois dias é liquidada financeiramente:

```
ajuste = (PU_hoje - PU_ontem) × quantidade_contratos
```

Esse ajuste diário gera um **convexity adjustment** que diferencia o pricing do futuro de um equivalente forward puro.

## Posições e Direção

| Posição | Expectativa | Ganha quando |
|---------|------------|--------------|
| **Comprado** em DI1 | Taxa vai cair | Taxas caem, PU sobe |
| **Vendido** em DI1 | Taxa vai subir | Taxas sobem, PU cai |

**Atenção:** a linguagem de mercado é às vezes invertida — "comprado em DI" pode significar comprado em taxa (vendido em PU). O Risk Reference BR adota a convenção B3: **posição comprada = comprada em PU = apostando em queda de taxa**.

## Curva de Juros a Partir do DI1

O conjunto de contratos DI1 com diferentes vencimentos forma a **curva de juros pré-fixada** brasileira. O bootstrap da curva DI é feito a partir dos preços dos futuros DI1.

A taxa forward entre dois vencimentos `t1` e `t2`:
```
(1 + taxa_forward) ^ ((du_t2 - du_t1)/252) = (1 + taxa_t2) ^ (du_t2/252) / (1 + taxa_t1) ^ (du_t1/252)
```

## Métricas de Risco

### DV01 do Futuro DI1

```
DV01 = -PU × (dias_uteis/252) / (1 + taxa) × 0,0001
```

Unidade: reais por contrato por ponto-base.

### Duration de um contrato DI1

Duration ≈ dias_uteis/252 (sem ajuste de convexidade para pequenos movimentos).

## Convexity Adjustment

Devido ao ajuste diário de margem (mark-to-market), o futuro DI1 não é idêntico a um forward de taxa de juro. A diferença é o **convexity adjustment**:

```
CA = - σ^2 × t × T / 2
```

Onde σ é a volatilidade da taxa, t é o prazo do futuro e T é o prazo total. Para futuros curtos (< 1 ano), o CA é pequeno. Para futuros longos (> 3 anos), deve ser aplicado.

## FRTB-SA — Sensibilidade

- **Risk class:** Interest Rate (IR)
- **Currency:** BRL
- **Tenor bucket:** conforme prazo do vencimento
- **Delta sensibilidade:** calculada como DV01 × 10.000

> **Referência normativa FRTB:** BCB Resolução 4.958/2021, Anexo I. ISDA FRTB-SA Technical Standards, Tabela 2 — IR risk weights.

## Benchmark de Validação

Taxas e volumes negociados disponíveis em tempo real na B3:
https://www.b3.com.br/pt_br/market-data-e-indices/servicos-de-dados/market-data/cotacoes/
