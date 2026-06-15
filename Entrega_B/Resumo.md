#  Resumo da Entrega_B

## Visão Geral

Este notebook realiza uma Análise Exploratória de Dados (EDA) completa sobre a inadimplência no Brasil, utilizando dados públicos do **Banco Central do Brasil (BCB/SGS)** via API REST.

### Séries analisadas
| Série | Código SGS | Fonte |
|-------|------------|-------|
| Inadimplência total | 21082 | BCB/Depec |
| Inadimplência — Pessoas Físicas | 21112 | BCB/Depec |
| Inadimplência — Pessoas Jurídicas | 21086 | BCB/Depec |
| Taxa Selic (% a.a.) | 4189 | BCB/Copom |
| Câmbio BRL/USD | 1 | BCB |
| Taxa de Desemprego (PNAD) | 24369 | IBGE/BCB |

---

## 1. Coleta e preparação dos dados

Os dados foram coletados via API do BCB e consolidados em um único DataFrame com frequência mensal, de **março/2012 a abril/2026** (170 observações).

✅ Nenhum valor ausente – série completa.

---

## 2. Estatísticas descritivas

| Indicador | Média | Desvio | Mín | Q1 | Mediana | Q3 | Máx |
|-----------|-------|--------|-----|----|---------|----|-----|
| Inadimplência Total (%) | 3.19 | 0.48 | 2.11 | 2.92 | 3.18 | 3.54 | 4.44 |
| Inadimplência PF (%) | 5.62 | 0.79 | 4.01 | 5.06 | 5.61 | 6.15 | 7.20 |
| Inadimplência PJ (%) | 3.27 | 1.10 | 1.45 | 2.52 | 3.28 | 3.76 | 5.94 |
| Selic (% a.a.) | 9.79 | 3.82 | 1.90 | 6.44 | 10.50 | 13.58 | 14.90 |
| Câmbio (R$/USD) | 4.04 | 1.26 | 1.80 | 3.14 | 3.95 | 5.24 | 6.10 |
| Desemprego (%) | 9.64 | 2.82 | 5.10 | 7.12 | 8.80 | 12.10 | 14.90 |

> **Interpretação**: A inadimplência de PF é sistematicamente maior que a de PJ, com maior variabilidade no segmento PJ. A Selic e o desemprego apresentam alta dispersão, refletindo ciclos econômicos.

---

## 3. Teste de normalidade (Shapiro-Wilk)

| Série | Estatística | p-valor | Normal? |
|-------|-------------|---------|---------|
| Inadimplência Total | 0.9832 | 0.0383 | **Não** |
| Inadimplência PF | 0.9814 | 0.0224 | **Não** |
| Inadimplência PJ | 0.9560 | 0.0000 | **Não** |
| Selic | 0.9296 | 0.0000 | **Não** |
| Câmbio | 0.9151 | 0.0000 | **Não** |
| Desemprego | 0.9189 | 0.0000 | **Não** |

> **Conclusão**: Nenhuma das séries segue distribuição normal. Isso justifica o uso de transformações (diferenças, médias móveis) e abordagens não paramétricas para correlação.

---

## 4. Evolução histórica da inadimplência

![02_serie_historica](02_serie_historica.png)

- **Pico recente em 2026**: 4,44% (total) – maior patamar da série.
- **Vale histórico em 2020**: queda acentuada durante a pandemia, possivelmente devido a auxílios emergenciais e programas de renegociação.
- **Ciclo de alta em 2015/16**: associado à recessão econômica.
- **PF sempre acima de PJ**, com distância crescente nos períodos de crise.

---

## 5. Variação mensal e anual

![03_variacoes](03_variacoes.png)

- **Variação mensal**: picos positivos ocorrem em momentos de estresse econômico (ex.: 2015, 2021).  
- **Variação anual (diff 12)**: mostra mudanças estruturais mais suaves, com aceleração significativa a partir de 2022.

---

## 6. Decomposição da série temporal (inadimplência total)

![decomposicao](decomposicao.png)

- **Tendência**: ascendente de longo prazo, com inflexão a partir de 2022.
- **Sazonalidade**: padrão anual bem definido – picos geralmente no início do ano (efeito de “virada de ano” e inadimplência no comércio).
- **Resíduo**: ruído aleatório, com maior variabilidade após 2020.

---

## 7. Autocorrelação (ACF) e autocorrelação parcial (PACF)

- **ACF**: decaimento lento, típico de série não estacionária com forte memória.  
- **PACF**: corte abrupto após o primeiro lag – indicativo de que um modelo **AR(1)** ou **ARIMA** pode ser adequado.

---

## 8. Relação com variáveis macroeconômicas

### Correlação de Pearson (sem defasagem)

|                | Inad Total | Selic | Câmbio | Desemprego |
|----------------|------------|-------|--------|-------------|
| Inad Total     | 1.00       | 0.61  | 0.58   | 0.77        |
| Selic          | 0.61       | 1.00  | 0.63   | 0.52        |
| Câmbio         | 0.58       | 0.63  | 1.00   | 0.55        |
| Desemprego     | 0.77       | 0.52  | 0.55   | 1.00        |

> **Destaque**: Desemprego é a variável mais correlacionada com a inadimplência (0.77).

### Correlação cruzada com defasagens (lag)

- **Selic → Inad**: correlação máxima ocorre com **lag de 6 a 9 meses** (impacto da política monetária sobre a inadimplência).
- **Desemprego → Inad**: correlação praticamente instantânea (lag 0) e se mantém alta por vários meses.
- **Câmbio → Inad**: correlação mais fraca, com pico em lag 2.

---

## 9. Impacto de eventos específicos

- **Recessão 2015/16**: elevação da inadimplência PF e PJ, acompanhada de alta do desemprego.
- **Pandemia (2020)**: queda atípica da inadimplência – contraintuitiva, explicada por auxílio emergencial e suspensão de dívidas.
- **Alta da Selic (2022–2023)**: aumento da inadimplência com defasagem de cerca de 6 meses.

---

## 10. Conclusões e recomendações

1. A inadimplência é **não estacionária**, com forte componente de tendência e sazonalidade.
2. O **desemprego** é o macroindicador mais relevante para explicar a inadimplência, tanto contemporânea quanto defasada.
3. A **Selic** influencia a inadimplência com **lag de 6 a 9 meses** – útil para modelos de previsão.
4. Sazonalidade anual sugere que ações de prevenção à inadimplência devem ser intensificadas no **final do ano**.
5. Para modelagem preditiva, recomenda-se:
   - Modelos ARIMAX com variáveis exógenas (desemprego, Selic defasada)
   - Ou modelos de machine learning com janelas temporais (XGBoost, LSTM)