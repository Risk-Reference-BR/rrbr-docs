# Fator DI — Compounding Diário do CDI

## Definição

O **Fator DI** é o mecanismo de acumulação diária da taxa CDI (Certificado de Depósito Interbancário). É a base de praticamente todos os instrumentos pós-fixados do mercado brasileiro.

> **Referência normativa:** BCB — Circular 3.748/2015 (metodologia do CDI). ANBIMA — Manual de Marcação a Mercado.

## Taxa CDI

O CDI é divulgado pela B3 diariamente após o fechamento do mercado, expresso como taxa **anual** com base **bus/252**. Exemplo: CDI = 10,65% a.a.

## Fator Diário

```
fator_diario = (1 + CDI_anual / 100) ^ (1 / 252)
```

## Fator Acumulado entre duas datas

```
fator_acumulado = ∏ (1 + CDI_i / 100) ^ (1 / 252)
```

Onde o produtório é sobre todos os **dias úteis** do período `[data_inicial, data_final)`.

> **Importante:** feriados e fins de semana não entram no produtório. O fator acumulado em um dia não útil é igual ao do dia útil anterior.

## Aplicação em instrumentos DI%

Para um CDB com remuneração de **110% do CDI**:

```
fator_remuneracao_diario = (1 + CDI_i / 100) ^ (percentual_cdi / 100 / 252)
```

```
fator_acumulado = ∏ fator_remuneracao_diario  (sobre dias úteis)
```

> **Atenção:** o percentual do CDI **não** multiplica a taxa anual diretamente — ele é aplicado no expoente, não como múltiplo do fator.

## Aplicação em instrumentos CDI+spread (DI+)

Para um instrumento CDI + 2,5% a.a.:

```
fator_diario = (1 + CDI_i / 100) ^ (1/252)  ×  (1 + spread / 100) ^ (1/252)
```

As duas pernas (DI e spread) acumulam separadamente com base bus/252.

## IDI — Índice de Depósito Interbancário

O IDI é a série histórica do fator DI acumulado desde uma data-base. Publicado pela B3.

```
IDI(t) = IDI(t-1) × (1 + CDI(t-1) / 100) ^ (1/252)
```

Usado como base para opções sobre CDI (contratos IDI na B3).

## Diferença entre CDI e SELIC

| | CDI | SELIC |
|-|-----|-------|
| Definição | Média das operações de depósito interbancário | Média das operações compromissadas com títulos federais |
| Divulgação | B3 | BCB |
| Diferença típica | CDI ≈ SELIC − 0,10% a.a. | — |
| Uso principal | Benchmark de instrumentos privados | Meta de política monetária, LFT |

Na prática, CDI e SELIC diferem em apenas 0,10% a.a. (um ponto-base diário), mas são **produtos diferentes** com cotações distintas.
