# RRBR — Catálogo de Produtos Financeiros Brasileiros

Este catálogo documenta todos os produtos financeiros do mercado brasileiro que o RRBR tem como objetivo catalogar, implementar e validar. Cada produto possui documentação própria com definição, convenções de mercado, modelo de pricing, métricas de risco e referências normativas.

## Status de Implementação

| Status | Significado |
|--------|-------------|
| `documentado` | Definição e convenções documentadas, sem implementação Rust ainda |
| `em desenvolvimento` | Implementação Rust em andamento |
| `implementado` | Implementação Rust completa com testes |
| `validado` | Benchmark contra dados reais (ANBIMA, B3, BCB) aprovado |

---

## 1. Renda Fixa Soberana

Títulos emitidos pelo Tesouro Nacional, registrados no sistema SELIC do BCB.

| Produto | Arquivo | Status |
|---------|---------|--------|
| LTN — Letra do Tesouro Nacional | [sovereign/ltn.md](products/sovereign/ltn.md) | `documentado` |
| NTN-F — Nota do Tesouro Nacional série F | [sovereign/ntn-f.md](products/sovereign/ntn-f.md) | `documentado` |
| NTN-B — Nota do Tesouro Nacional série B | [sovereign/ntn-b.md](products/sovereign/ntn-b.md) | `documentado` |
| NTN-B Principal — Tesouro IPCA sem juros | [sovereign/ntn-b-principal.md](products/sovereign/ntn-b-principal.md) | `documentado` |
| LFT — Letra Financeira do Tesouro | [sovereign/lft.md](products/sovereign/lft.md) | `documentado` |
| NTN-C — Nota do Tesouro Nacional série C | [sovereign/ntn-c.md](products/sovereign/ntn-c.md) | `documentado` |

---

## 2. Renda Fixa Privada — Bancária

Títulos emitidos por instituições financeiras, registrados na B3 (CETIP).

| Produto | Arquivo | Status |
|---------|---------|--------|
| CDB — Certificado de Depósito Bancário | [fixed-income-private/cdb.md](products/fixed-income-private/cdb.md) | `documentado` |
| LCI — Letra de Crédito Imobiliário | [fixed-income-private/lci.md](products/fixed-income-private/lci.md) | `documentado` |
| LCA — Letra de Crédito do Agronegócio | [fixed-income-private/lca.md](products/fixed-income-private/lca.md) | `documentado` |
| LIG — Letra Imobiliária Garantida | [fixed-income-private/lig.md](products/fixed-income-private/lig.md) | `documentado` |
| LF — Letra Financeira | [fixed-income-private/lf.md](products/fixed-income-private/lf.md) | `documentado` |
| LC — Letra de Câmbio | [fixed-income-private/lc.md](products/fixed-income-private/lc.md) | `documentado` |
| RDB — Recibo de Depósito Bancário | [fixed-income-private/rdb.md](products/fixed-income-private/rdb.md) | `documentado` |
| DPGE — Depósito a Prazo com Garantia Especial | [fixed-income-private/dpge.md](products/fixed-income-private/dpge.md) | `documentado` |

---

## 3. Renda Fixa Privada — Mercado de Capitais

Títulos emitidos por empresas não-financeiras, registrados na B3.

| Produto | Arquivo | Status |
|---------|---------|--------|
| Debênture simples | [fixed-income-private/debenture-simples.md](products/fixed-income-private/debenture-simples.md) | `documentado` |
| Debênture incentivada (Lei 12.431) | [fixed-income-private/debenture-incentivada.md](products/fixed-income-private/debenture-incentivada.md) | `documentado` |
| Debênture conversível | [fixed-income-private/debenture-conversivel.md](products/fixed-income-private/debenture-conversivel.md) | `documentado` |
| Debênture permutável | [fixed-income-private/debenture-permutavel.md](products/fixed-income-private/debenture-permutavel.md) | `documentado` |
| CRI — Certificado de Recebíveis Imobiliários | [fixed-income-private/cri.md](products/fixed-income-private/cri.md) | `documentado` |
| CRA — Certificado de Recebíveis do Agronegócio | [fixed-income-private/cra.md](products/fixed-income-private/cra.md) | `documentado` |
| CCB — Cédula de Crédito Bancário | [fixed-income-private/ccb.md](products/fixed-income-private/ccb.md) | `documentado` |
| CDCA — Certificado de Direitos Creditórios do Agronegócio | [fixed-income-private/cdca.md](products/fixed-income-private/cdca.md) | `documentado` |
| CPR — Cédula de Produto Rural | [fixed-income-private/cpr.md](products/fixed-income-private/cpr.md) | `documentado` |
| CCI — Cédula de Crédito Imobiliário | [fixed-income-private/cci.md](products/fixed-income-private/cci.md) | `documentado` |

---

## 4. Estruturados e Certificados

| Produto | Arquivo | Status |
|---------|---------|--------|
| COE — Certificado de Operações Estruturadas | [funds-structured/coe.md](products/funds-structured/coe.md) | `documentado` |
| CDB Estruturado | [funds-structured/cdb-estruturado.md](products/funds-structured/cdb-estruturado.md) | `documentado` |

---

## 5. Fundos de Investimento

| Produto | Arquivo | Status |
|---------|---------|--------|
| FII — Fundo de Investimento Imobiliário | [funds-structured/fii.md](products/funds-structured/fii.md) | `documentado` |
| FIAGRO | [funds-structured/fiagro.md](products/funds-structured/fiagro.md) | `documentado` |
| FIINFRA | [funds-structured/fiinfra.md](products/funds-structured/fiinfra.md) | `documentado` |
| FIP — Fundo de Investimento em Participações | [funds-structured/fip.md](products/funds-structured/fip.md) | `documentado` |
| FIDC — Fundo de Investimento em Direitos Creditórios | [funds-structured/fidc.md](products/funds-structured/fidc.md) | `documentado` |
| ETF | [funds-structured/etf.md](products/funds-structured/etf.md) | `documentado` |

---

## 6. Derivativos de Juros (B3 e Balcão)

| Produto | Arquivo | Status |
|---------|---------|--------|
| Futuro DI (DI1) | [derivatives-rates/di1.md](products/derivatives-rates/di1.md) | `documentado` |
| Futuro DI Longo (DA) | [derivatives-rates/da.md](products/derivatives-rates/da.md) | `documentado` |
| Futuro IPCA (DAP) | [derivatives-rates/dap.md](products/derivatives-rates/dap.md) | `documentado` |
| IDI — Índice de Depósito Interbancário | [derivatives-rates/idi.md](products/derivatives-rates/idi.md) | `documentado` |
| Opção sobre DI1 | [derivatives-rates/opcao-di1.md](products/derivatives-rates/opcao-di1.md) | `documentado` |
| FRA de DI | [derivatives-rates/fra-di.md](products/derivatives-rates/fra-di.md) | `documentado` |
| Swap pré × DI | [derivatives-rates/swap-pre-di.md](products/derivatives-rates/swap-pre-di.md) | `documentado` |
| Swap IPCA × DI | [derivatives-rates/swap-ipca-di.md](products/derivatives-rates/swap-ipca-di.md) | `documentado` |
| Swap IPCA × Pré | [derivatives-rates/swap-ipca-pre.md](products/derivatives-rates/swap-ipca-pre.md) | `documentado` |
| Swap IGP-M × DI | [derivatives-rates/swap-igpm-di.md](products/derivatives-rates/swap-igpm-di.md) | `documentado` |
| Swap DI × USD (Cupom Cambial) | [derivatives-rates/swap-di-usd.md](products/derivatives-rates/swap-di-usd.md) | `documentado` |
| Swaption | [derivatives-rates/swaption.md](products/derivatives-rates/swaption.md) | `documentado` |

---

## 7. Câmbio e Derivativos Cambiais (B3 e Balcão)

| Produto | Arquivo | Status |
|---------|---------|--------|
| Futuro USD/BRL (DOL) | [derivatives-fx/dol.md](products/derivatives-fx/dol.md) | `documentado` |
| Mini Futuro USD/BRL (WDO) | [derivatives-fx/wdo.md](products/derivatives-fx/wdo.md) | `documentado` |
| Futuro EUR/BRL (EBR) | [derivatives-fx/ebr.md](products/derivatives-fx/ebr.md) | `documentado` |
| NDF USD/BRL | [derivatives-fx/ndf.md](products/derivatives-fx/ndf.md) | `documentado` |
| DDI — Cupom Cambial | [derivatives-fx/ddi.md](products/derivatives-fx/ddi.md) | `documentado` |
| DCO — Cupom de Onshore | [derivatives-fx/dco.md](products/derivatives-fx/dco.md) | `documentado` |
| FX Swap | [derivatives-fx/fx-swap.md](products/derivatives-fx/fx-swap.md) | `documentado` |
| Opção de câmbio vanilla | [derivatives-fx/opcao-fx-vanilla.md](products/derivatives-fx/opcao-fx-vanilla.md) | `documentado` |
| Opção de câmbio exótica | [derivatives-fx/opcao-fx-exotica.md](products/derivatives-fx/opcao-fx-exotica.md) | `documentado` |
| Opção sobre DOL | [derivatives-fx/opcao-dol.md](products/derivatives-fx/opcao-dol.md) | `documentado` |

---

## 8. Ações e Derivativos de Ações (B3)

| Produto | Arquivo | Status |
|---------|---------|--------|
| Ação ON / PN | [equity/acoes.md](products/equity/acoes.md) | `documentado` |
| BDR (nível I, II, III) | [equity/bdr.md](products/equity/bdr.md) | `documentado` |
| ETF de ações | [equity/etf-acoes.md](products/equity/etf-acoes.md) | `documentado` |
| Futuro mini IBOV (WIN) | [equity/win.md](products/equity/win.md) | `documentado` |
| Futuro IBOV (IND) | [equity/ind.md](products/equity/ind.md) | `documentado` |
| Opção vanilla sobre ação | [equity/opcao-acao-vanilla.md](products/equity/opcao-acao-vanilla.md) | `documentado` |
| Opção sobre IBOV | [equity/opcao-ibov.md](products/equity/opcao-ibov.md) | `documentado` |
| Termo de ações | [equity/termo.md](products/equity/termo.md) | `documentado` |
| Aluguel de ações (BTB) | [equity/btb.md](products/equity/btb.md) | `documentado` |

---

## 9. Commodities (B3)

| Produto | Arquivo | Status |
|---------|---------|--------|
| Futuro de boi gordo (BGI) | [commodities/bgi.md](products/commodities/bgi.md) | `documentado` |
| Futuro de café arábica (ICF) | [commodities/icf.md](products/commodities/icf.md) | `documentado` |
| Futuro de milho (CCM) | [commodities/ccm.md](products/commodities/ccm.md) | `documentado` |
| Futuro de soja (SFI) | [commodities/sfi.md](products/commodities/sfi.md) | `documentado` |
| Futuro de açúcar (ISU) | [commodities/isu.md](products/commodities/isu.md) | `documentado` |
| Futuro de etanol (ETH) | [commodities/eth.md](products/commodities/eth.md) | `documentado` |
| Futuro de ouro (OZ1) | [commodities/oz1.md](products/commodities/oz1.md) | `documentado` |
| Opções sobre commodities | [commodities/opcoes-commodities.md](products/commodities/opcoes-commodities.md) | `documentado` |

---

## 10. Operações Compromissadas (Repo)

| Produto | Arquivo | Status |
|---------|---------|--------|
| Compromissada overnight (LFT) | [repo/compromissada-lft.md](products/repo/compromissada-lft.md) | `documentado` |
| Compromissada com LTN/NTN | [repo/compromissada-ltn-ntn.md](products/repo/compromissada-ltn-ntn.md) | `documentado` |
| Repo no SELIC | [repo/repo-selic.md](products/repo/repo-selic.md) | `documentado` |
| Repo no B3 | [repo/repo-b3.md](products/repo/repo-b3.md) | `documentado` |

---

## 11. Capital Regulatório BCB (FRTB-SA)

| Componente | Arquivo | Status |
|------------|---------|--------|
| Visão geral FRTB-SA | [regulatory/frtb-sa/overview.md](regulatory/frtb-sa/overview.md) | `documentado` |
| SBM Delta — IR | [regulatory/frtb-sa/sbm-delta-ir.md](regulatory/frtb-sa/sbm-delta-ir.md) | `documentado` |
| SBM Delta — FX | [regulatory/frtb-sa/sbm-delta-fx.md](regulatory/frtb-sa/sbm-delta-fx.md) | `documentado` |
| SBM Delta — Equity | [regulatory/frtb-sa/sbm-delta-equity.md](regulatory/frtb-sa/sbm-delta-equity.md) | `documentado` |
| SBM Delta — Commodity | [regulatory/frtb-sa/sbm-delta-commodity.md](regulatory/frtb-sa/sbm-delta-commodity.md) | `documentado` |
| SBM Delta — CSR | [regulatory/frtb-sa/sbm-delta-csr.md](regulatory/frtb-sa/sbm-delta-csr.md) | `documentado` |
| SBM Vega | [regulatory/frtb-sa/sbm-vega.md](regulatory/frtb-sa/sbm-vega.md) | `documentado` |
| SBM Curvature | [regulatory/frtb-sa/sbm-curvature.md](regulatory/frtb-sa/sbm-curvature.md) | `documentado` |
| DRC — Default Risk Charge | [regulatory/frtb-sa/drc.md](regulatory/frtb-sa/drc.md) | `documentado` |
| RRAO — Residual Risk Add-On | [regulatory/frtb-sa/rrao.md](regulatory/frtb-sa/rrao.md) | `documentado` |
| NMRF — Non-Modellable Risk Factors | [regulatory/frtb-sa/nmrf.md](regulatory/frtb-sa/nmrf.md) | `documentado` |
| SA-CVA | [regulatory/frtb-sa/sa-cva.md](regulatory/frtb-sa/sa-cva.md) | `documentado` |

---

## 12. Curvas, Superfícies e Convenções Brasileiras

| Item | Arquivo | Status |
|------|---------|--------|
| Curva DI (pré nominal) | [curves/curva-di.md](curves/curva-di.md) | `documentado` |
| Curva real (IPCA implícita) | [curves/curva-real-ipca.md](curves/curva-real-ipca.md) | `documentado` |
| Curva IGP-M implícita | [curves/curva-igpm.md](curves/curva-igpm.md) | `documentado` |
| Cupom cambial (DDI) | [curves/cupom-cambial.md](curves/cupom-cambial.md) | `documentado` |
| Superfície de volatilidade USD/BRL | [curves/vol-surface-usd-brl.md](curves/vol-surface-usd-brl.md) | `documentado` |
| Superfície de volatilidade IBOV | [curves/vol-surface-ibov.md](curves/vol-surface-ibov.md) | `documentado` |
| Convenção bus/252 | [conventions/bus252.md](conventions/bus252.md) | `documentado` |
| Calendário ANBIMA | [conventions/calendario-anbima.md](conventions/calendario-anbima.md) | `documentado` |
| Fator DI — compounding diário | [conventions/fator-di.md](conventions/fator-di.md) | `documentado` |
| PTAX — taxa de câmbio BCB | [conventions/ptax.md](conventions/ptax.md) | `documentado` |
| Convenções de liquidação (D+0, D+1, D+2) | [conventions/liquidacao.md](conventions/liquidacao.md) | `documentado` |
| Contagem de dias (corridos vs úteis) | [conventions/contagem-dias.md](conventions/contagem-dias.md) | `documentado` |
