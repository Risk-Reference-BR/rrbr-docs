# FRTB-SA — Abordagem Padronizada para Risco de Mercado

## Definição

O **FRTB-SA** (Fundamental Review of the Trading Book — Standardised Approach) é o framework regulatório para cálculo de capital mínimo para risco de mercado em bancos. No Brasil, é implementado pela **Resolução BCB 4.958/2021**, que transpõe os padrões do Comitê de Basileia (BCBS) para o sistema financeiro nacional.

> **Referência normativa principal:**
> - BCB — Resolução 4.958/2021 (Requisitos de capital para risco de mercado — SA)
> - BCB — Resolução 4.557/2017 (Estrutura de gerenciamento de riscos)
> - BCBS — Minimum capital requirements for market risk (Jan 2019, rev. 2024)
> - ISDA — FRTB Standardised Approach Technical Standards

## Estrutura do FRTB-SA

O capital total FRTB-SA é a soma de três componentes:

```
Capital_total = SBM + DRC + RRAO
```

### 1. SBM — Sensitivities-Based Method

O SBM é o componente principal. Calcula capital com base nas **sensibilidades** (gregas) dos instrumentos a fatores de risco. Três cargas:

```
SBM = Delta + Vega + Curvature
```

**Classes de risco (Risk Classes):**
| Classe | Fatores de risco |
|--------|-----------------|
| IR (Interest Rate) | Taxas de juro por moeda e tenor |
| FX (Foreign Exchange) | Taxas de câmbio |
| EQ (Equity) | Preços de ações e índices |
| CMDTY (Commodity) | Preços de commodities |
| CSR Non-Sec | Spreads de crédito (non-securitisation) |
| CSR Sec CTP | Spreads de crédito (securitisation — CTP) |
| CSR Sec Non-CTP | Spreads de crédito (securitisation — non-CTP) |

### 2. DRC — Default Risk Charge

Capital para risco de salto-para-default (jump-to-default) em posições com exposição a risco de crédito de emissores específicos.

```
DRC = max(DRC_long_net, 0)
```

Aplicável a: ações, bonds, CDS, derivativos de crédito.

### 3. RRAO — Residual Risk Add-On

Capital adicional para instrumentos com riscos residuais não capturados pelo SBM e DRC:

| Tipo | Add-On |
|------|--------|
| Exotic underlyings | 1,0% × nocional bruto |
| Gap risk, correlation risk | 0,1% × nocional bruto |

### NMRF — Non-Modellable Risk Factors

Fatores de risco com dados de mercado insuficientes para modelagem são tratados como **não-modeláveis** e recebem um stress scenario charge:

```
NMRF_charge = max(stress_scenario, floor_regulatório)
```

## Metodologia SBM — Delta IR (Exemplo para Brasil)

Para posições em BRL com sensibilidade a taxa de juro:

**Tenores:** ON, 1M, 3M, 6M, 1Y, 2Y, 3Y, 5Y, 10Y, 15Y, 20Y, 30Y

**Risk weights (pesos de risco) por tenor — BCB 4.958, Tabela 1:**
| Tenor | Risk Weight |
|-------|------------|
| 0,25Y (ON) | 1,7% |
| 0,5Y | 1,6% |
| 1Y | 1,6% |
| 2Y | 1,3% |
| 3Y | 1,2% |
| 5Y | 1,1% |
| 10Y | 1,1% |
| 15Y | 1,1% |
| 20Y | 1,1% |
| 30Y | 1,1% |

> **Atenção:** estes são os parâmetros ISDA/BCBS. A BCB pode aplicar parâmetros ajustados para o mercado brasileiro. Consultar sempre a versão vigente da Resolução 4.958 e seus anexos.

**Cálculo Delta IR:**
```
WS_k = RW_k × s_k          // weighted sensitivity por tenor k
KB = sqrt(Σ WS_k² + Σ_{k≠l} ρ_{kl} × WS_k × WS_l)   // bucket capital
```

As correlações ρ_{kl} entre tenores são definidas pelo BCBS (fórmula de decaimento exponencial).

## Agregação entre Buckets e Risk Classes

```
Capital_SBM_delta = sqrt(Σ_b KB_b² + Σ_{b≠c} γ_{bc} × S_b × S_c)
```

Onde γ_{bc} são as correlações entre buckets, definidas no BCBS/BCB.

## SA-CVA — Risco de CVA

O **SA-CVA** (Standardised Approach for Credit Valuation Adjustment) calcula capital para o risco de variação do CVA das contrapartes em derivativos OTC.

> **Referência normativa:** BCB Resolução 4.958/2021, Capítulo IV. BCBS — Minimum capital requirements for CVA risk (Jul 2020).

## Contexto Brasileiro

A BCB implementou o FRTB-SA com as seguintes particularidades para o mercado brasileiro:
- **Curva BRL IR:** tratada com a moeda local como "specified currency" (menor risk weight)
- **BRL FX:** o par USD/BRL tem tratamento específico nas correlações FX
- **Títulos soberanos brasileiros:** tratamento regulatório específico no DRC

Todo parâmetro numérico (risk weights, correlações, líquidity horizons) deve ser citado com o artigo exato da Resolução 4.958/2021 e/ou do documento BCBS correspondente.
