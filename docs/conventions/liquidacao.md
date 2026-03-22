# Convenções de Liquidação — D+0, D+1, D+2

## Definição

**Liquidação** é a transferência efetiva de ativos e recursos financeiros entre as partes de uma operação. No mercado brasileiro, a liquidação ocorre em **D+n**, onde **D** é a data de negociação e **n** é o número de **dias úteis** (calendário ANBIMA) até a liquidação.

> **Referência normativa:** B3 — Regulamento de Operações. BCB — Circular 3.507/2010. CVM — Instrução 461/2007.

## Tabela de Convenções por Instrumento

| Instrumento | Liquidação | Observação |
|-------------|-----------|------------|
| Ações B3 (à vista) | **D+2** | Padrão atual desde 2019 |
| ETF de ações | **D+2** | Igual à ação subjacente |
| Opções sobre ações (exercício) | **D+2** | |
| Futuro DI (DI1) — ajuste diário | **D+1** | Ajuste via câmara B3 |
| Futuro USD/BRL (DOL) — vencimento | **D+1** | Liquidação financeira |
| Títulos públicos (SELIC) | **D+1** | Operações no SELIC |
| Compromissadas (operações abertas) | **D+0** | Liquidação no mesmo dia |
| CDB, LCI, LCA (emissão primária) | **D+0** ou **D+1** | Depende do emissor |
| Debêntures (mercado secundário) | **D+2** ou **D+3** | Depende da operação |
| FX spot (USD/BRL interbancário) | **D+2** | Padrão internacional |
| NDF (vencimento) | **D+2** | Liquidação financeira |
| Swap (vencimento) | **D+1** | Liquidação financeira |
| FII (cotas em bolsa) | **D+2** | Igual à ação |

## Impacto no Pricing

A data de liquidação é o ponto de partida para o cálculo de dias úteis em todos os instrumentos. Em uma LTN negociada em D para liquidação em D+1:

```
dias_uteis = bus_days(D+1, vencimento)   // não a partir de D
PU = 1000 / (1 + taxa) ^ (dias_uteis / 252)
```

**Erro comum:** calcular dias úteis a partir da data de negociação (D) em vez da data de liquidação (D+1 ou D+2).

## Liquidação Antecipada

Alguns instrumentos permitem negociação com liquidação **antecipada** (D+0 para um instrumento normalmente D+2). Isso é chamado de **operação de liquidação antecipada** e implica ajuste de taxa (custo de carregamento até D+2).

## Horário de Corte

Para efeito de liquidação D+0, existe um **horário de corte** no STR (Sistema de Transferência de Reservas) do BCB — tipicamente às **18h00** para TED e às **17h00** para DOC. Operações após o corte liquidam no próximo dia útil.
