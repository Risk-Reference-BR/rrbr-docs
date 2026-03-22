# RRBR — rrbr-docs

> **Documentation**: Technical architecture, regulatory references, and product catalog for the RRBR system.

[![License](https://img.shields.io/badge/license-Apache%202.0-blue.svg)](LICENSE)

## Overview

Central documentation for the Risk Reference BR project — architecture decisions, regulatory mappings, product catalog, and API references.

## Structure

```
docs/
├── architecture/       # System architecture and ADRs (Architecture Decision Records)
├── products/           # Product catalog: one page per financial product
│   ├── sovereign/      # LTN, NTN-F, NTN-B, LFT, NTN-C
│   ├── derivatives/    # DI1, DOL, Swaptions, FX Options
│   ├── credit/         # CDB, CRI, CRA, Debentures, FIDC
│   ├── equity/         # B3 equities, options, ETF
│   └── structured/     # FII, FIP, COE, FIAGRO
├── regulatory/         # BCB resolutions, ANBIMA manuals, ISDA references
│   ├── frtb-sa/        # FRTB-SA parameter tables and BCB mapping
│   └── conventions/    # bus/252, B3 calendar, settlement conventions
└── api/                # Protobuf and REST API references
```

## Regulatory Sources

| Institution | Documents |
|-------------|-----------|
| BCB | Resoluções 4.557, 4.958, Circular 3.748 |
| ANBIMA | Código de Melhores Práticas, Manuais de Marcação |
| B3 | Especificações de contratos, Calendário de feriados |
| ISDA | FRTB-SA Technical Standards |

## License

Apache 2.0
