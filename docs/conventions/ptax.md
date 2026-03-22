# PTAX — Taxa de Câmbio Oficial do BCB

## Definição

A **PTAX** é a taxa de câmbio USD/BRL oficial divulgada pelo Banco Central do Brasil (BCB). É o fixing de referência para liquidação de contratos de câmbio e derivativos no mercado brasileiro.

> **Referência normativa:** BCB — Resolução 3.568/2008. BCB — Circular 3.506/2010. Metodologia publicada em: https://www.bcb.gov.br/estabilidadefinanceira/txcambio

## Metodologia de Cálculo

O BCB realiza **quatro consultas** ao mercado ao longo do dia para calcular a PTAX:

| Boletim | Horário de consulta |
|---------|-------------------|
| Boletim de Abertura | 10h00–10h10 |
| Boletim Intermediário 1 | 11h00–11h10 |
| Boletim Intermediário 2 | 12h00–12h10 |
| Boletim de Fechamento | 12h30–13h00 |

A PTAX de **fechamento** (publicada por volta das 13h15) é calculada como a **média das taxas de compra e venda** do boletim de fechamento, após exclusão de cotações extremas (trimmed mean).

## Dois tipos de PTAX

| Tipo | Descrição | Uso |
|------|-----------|-----|
| **PTAX Compra** | Taxa que o BCB compraria USD | Referência para exportadores |
| **PTAX Venda** | Taxa que o BCB venderia USD | Referência para importadores |

A **PTAX de fechamento (venda)** é o fixing padrão usado em contratos de derivativos (NDF, DOL, swaps cambiais).

## Uso em Derivativos

### Futuro USD/BRL (DOL)

A liquidação financeira do contrato DOL na B3 usa a **PTAX de fechamento do dia anterior ao vencimento**:

```
PU_liquidação = 50.000 × PTAX_venda(D-1_vencimento)
```

### NDF (Non-Deliverable Forward)

A liquidação usa a PTAX de fechamento na data de fixing acordada no contrato:

```
resultado = nocional_USD × (PTAX_fixing − taxa_NDF_contratada)
```

### Swap Cambial

Perna USD: acumulação pelo cupom cambial contratado, com variação cambial medida pela PTAX.

## Dias sem PTAX

A PTAX **não é divulgada** em:
- Feriados nacionais brasileiros (calendário ANBIMA)
- Finais de semana

Contratos que vencem em dias sem PTAX geralmente usam a PTAX do **último dia útil anterior**.

## PTAX vs Taxa Spot de Mercado

A PTAX é uma referência, não necessariamente a taxa negociada. A taxa spot interbancária (negociada entre bancos) pode diferir da PTAX intraday. A diferença entre PTAX e spot é chamada de **basis PTAX**.
