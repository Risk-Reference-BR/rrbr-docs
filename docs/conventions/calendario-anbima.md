# Calendário ANBIMA — Feriados do Mercado Financeiro Brasileiro

## Definição

O **calendário ANBIMA** é o padrão de feriados utilizado para cômputo de dias úteis em todos os instrumentos financeiros do mercado brasileiro. É publicado anualmente pela ANBIMA e inclui feriados nacionais e pontos facultativos bancários.

> **Referência normativa:** ANBIMA — Calendário de Feriados (publicado anualmente). Disponível em: https://www.anbima.com.br/pt_br/informar/calendarios/calendario-de-feriados.htm

## Composição do Calendário

O calendário ANBIMA inclui:

### Feriados Nacionais Fixos
| Data | Feriado |
|------|---------|
| 01/janeiro | Confraternização Universal (Ano Novo) |
| 21/abril | Tiradentes |
| 01/maio | Dia do Trabalho |
| 07/setembro | Independência do Brasil |
| 12/outubro | Nossa Senhora Aparecida |
| 02/novembro | Finados |
| 15/novembro | Proclamação da República |
| 25/dezembro | Natal |

### Feriados Móveis (variam por ano)
| Feriado | Regra |
|---------|-------|
| Carnaval (segunda) | 48 dias antes da Páscoa |
| Carnaval (terça) | 47 dias antes da Páscoa |
| Quarta-feira de Cinzas (meio dia) | 46 dias antes da Páscoa |
| Sexta-feira Santa | 2 dias antes da Páscoa |
| Páscoa | Algoritmo de Gauss |
| Corpus Christi | 60 dias após a Páscoa |

### Ponto Facultativo
- **20/novembro** — Dia da Consciência Negra (ponto facultativo bancário, tratado como feriado pelo mercado)
- **24/dezembro** (tarde) e **31/dezembro** (tarde) — meio expediente, não contam como dia útil completo em alguns contextos

## Importância para o Cálculo bus/252

A contagem correta de dias úteis **depende inteiramente** do calendário ANBIMA. Um erro no calendário implica erro em todos os cálculos de pricing.

Exemplo: entre 30/dezembro e 02/janeiro de um ano qualquer:
- Dias corridos: 3
- Dias úteis (calendário ANBIMA): **0** (31/dez, 01/jan são não-úteis)
- Impacto: fator DI não acumula nesse período

## Diferença entre Calendários

| Calendário | Feriados incluídos | Uso |
|------------|-------------------|-----|
| ANBIMA | Nacionais + pontos facultativos bancários | Padrão para todos os instrumentos BRL |
| B3 | Similar ao ANBIMA, com pequenas diferenças para pregão | Liquidação de operações em bolsa |
| Bacen | Para operações no SELIC/STR | Operações com títulos públicos |

Na prática, ANBIMA, B3 e BACEN têm calendários quase idênticos — as diferenças são raras e bem documentadas.

## Publicação Anual

O calendário é publicado pela ANBIMA antes do início de cada ano. O Risk Reference BR deve manter o calendário atualizado para todos os anos relevantes (histórico + projeção futura).
