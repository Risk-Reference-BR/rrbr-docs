# NTN-B — Nota do Tesouro Nacional série B

## Definição

A **NTN-B** (Nota do Tesouro Nacional série B), também chamada de **Tesouro IPCA+** no Tesouro Direto, é um título público federal **indexado ao IPCA** com pagamento de **cupom semestral** de 6% a.a. sobre o Valor Nominal Atualizado (VNA). É o principal instrumento de renda fixa de longo prazo do mercado brasileiro e referência para o mercado de juros reais.

> **Referência normativa:** Secretaria do Tesouro Nacional — Decreto 3.859/2001. ANBIMA — Manual de Marcação a Mercado, Seção 3.3.

## Características

| Atributo | Valor |
|----------|-------|
| Emissor | Tesouro Nacional |
| Moeda | BRL |
| Valor nominal de emissão | R$ 1.000,00 |
| Indexador | IPCA (IBGE) |
| Cupom | 6% a.a. sobre o VNA, pago semestralmente |
| Convenção de juros | bus/252 |
| Liquidação | D+1 (SELIC) |
| Registro | SELIC (BCB) |
| Vencimentos disponíveis | 2026, 2029, 2032, 2035, 2040, 2045, 2050, 2055 |

## Valor Nominal Atualizado (VNA)

O VNA é o valor de face corrigido pelo IPCA acumulado desde a data-base do índice:

```
VNA(t) = VNA_base × [IPCA_acumulado(data_base → t)]
```

- **Data-base:** 15/07/2000
- **VNA_base:** R$ 1.000,00
- O IPCA acumulado é calculado com base no número índice do IPCA divulgado mensalmente pelo IBGE

> **Atenção:** entre o dia 1º e o dia 15 de cada mês, o IPCA do mês corrente ainda não foi divulgado. Nesses casos, usa-se a projeção de IPCA pro-rata (ANBIMA ou mercado) para calcular o VNA do dia corrente.

## Datas de Cupom

Os cupons são pagos nos dias **15 de maio** e **15 de novembro** de cada ano (ou no próximo dia útil, se feriado).

Taxa de cupom semestral:
```
taxa_cupom_semestral = (1 + 0,06) ^ (1/2) - 1 = 2,9563% a.s.
```

Cada cupom pago:
```
cupom = VNA(data_pagamento) × 2,9563%
```

## Fórmula de Pricing

O PU da NTN-B é o valor presente dos fluxos futuros (cupons + principal), descontados pela taxa de juro real negociada:

```
PU = Σ [C_i / (1 + taxa_real) ^ (n_i / 252)]  +  VNA(vencimento) / (1 + taxa_real) ^ (n_N / 252)
```

Onde:
- `C_i = VNA(data_cupom_i) × 2,9563%` — valor do i-ésimo cupom
- `n_i` — dias úteis entre liquidação e data do i-ésimo cupom
- `taxa_real` — taxa de juro real negociada (ex: 0,0650 para 6,50% a.a.)
- `n_N` — dias úteis entre liquidação e vencimento

O **preço cotado** pela ANBIMA é o PU dividido pelo VNA da data de liquidação:

```
Preço_percentual = (PU / VNA) × 100
```

## Métricas de Risco

### DV01 Real
Variação no PU para variação de 1bp na taxa real:
```
DV01_real = PU(taxa_real + 0,0001) - PU(taxa_real)
```

### Duration Modificada Real
Sensibilidade percentual a variações na taxa real.

### Breakeven Inflation (BEI)
Diferença entre taxa nominal implícita (curva DI) e taxa real (NTN-B) para o mesmo prazo:
```
BEI = (1 + taxa_nominal) / (1 + taxa_real) - 1
```

O BEI representa a inflação implícita que o mercado espera para o período.

### Sensibilidade ao IPCA
Exposição à variação do índice IPCA (impacta o VNA e todos os fluxos futuros).

## Complexidade e Pontos de Atenção

1. **IPCA pro-rata:** entre os dias 1 e 14 de cada mês, o VNA requer projeção do IPCA corrente. A ANBIMA divulga a projeção oficial usada pelo mercado.

2. **Interpolação de IPCA:** o IPCA é divulgado mensalmente, mas o VNA precisa ser calculado para qualquer dia útil. Usa-se interpolação linear diária entre os dois últimos índices divulgados.

3. **Convexidade elevada:** NTN-Bs longas (2045, 2055) têm convexidade muito alta. Para grandes movimentos de taxa, a aproximação de primeira ordem (DV01) é insuficiente.

4. **Estrutura a termo de taxas reais:** a curva de juros reais é obtida pelo bootstrap das NTN-Bs e usada para precificação de todos os instrumentos indexados ao IPCA.

## FRTB-SA — Sensibilidade

- **Risk class:** Interest Rate (IR) — perna de juro real
- **Risk class adicional:** Inflation (subclasse de IR no FRTB) — perna IPCA
- Os dois fatores de risco são tratados separadamente no FRTB-SA

> **Referência normativa FRTB:** BCB Resolução 4.958/2021, Anexo I, Art. 7º (IR), Art. 8º (Inflation). ISDA FRTB-SA Technical Standards, §3.8.

## Benchmark de Validação

Preços indicativos publicados diariamente pela ANBIMA:
https://www.anbima.com.br/pt_br/informar/precos-e-indices/precos/tesouro-nacional.htm
