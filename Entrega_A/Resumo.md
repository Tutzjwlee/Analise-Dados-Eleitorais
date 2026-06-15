#  Resumo da Entrega_A

## Visão Geral

Esta pasta contém a **Parte A** de um trabalho exploratório sobre comportamento eleitoral e atitudes políticas, baseado em uma pesquisa de opinião do **Cesop (Centro de Estudos de Opinião Pública)**. O objetivo é investigar a relação entre **desengajamento eleitoral** (não lembrar em quem votou e falta de vontade de participar da política) e outras dimensões políticas:

- Prioridades de governo.
- Percepção sobre combate a *fake news* (regulação vs. punição).
- Representatividade da amostra frente a dados oficiais de abstenção do TSE.

### Pesquisa principal
- **Instituição:** Ipec (acervo Cesop)
- **Tamanho da amostra:** 2.000 respondentes
- **Abrangência:** nacional
- **Variáveis principais:**
  - `P1A, P1B, P1C` – memória de voto (deputado estadual, federal, senador)
  - `P2_1, P2_2, P2_3` – prioridades políticas (três escolhas)
  - `P3_1` a `P3_6` – medidas de combate a *fake news*
  - `P4` – vontade de participar da política
  - `REGIAO` – região geográfica

### Base externa (validação)
- **Fonte:** TSE – abstenção oficial no 2º turno das eleições de 2022, por UF.
- **Agregação:** média simples por região (Norte, Nordeste, Sudeste, Sul, Centro-Oeste).

## Pré-processamento e Variáveis Derivadas

As seguintes variáveis foram criadas para facilitar as análises:

| Variável | Descrição | Construção |
|----------|-----------|-------------|
| `perfil_fn` | Postura sobre fake news | Contagem de respostas que indicam **regulação** (`P3_1,P3_3,P3_5`) vs **punição** (`P3_2,P3_4,P3_6`). Predominância define o perfil: “Mais regulação”, “Mais punição”, “Equilibrado”. |
| `lembra_algum` | Lembra de pelo menos um voto | `(P1A==1) or (P1B==1) or (P1C==1)` |
| `nlembra_nenhum` | Não lembra de nenhum voto | `(P1A==2) and (P1B==2) and (P1C==2)` |
| `n_respostas_p3` | Intensidade de opinião sobre fake news | Número de medidas válidas (diferentes de 99/NaN) escolhidas em `P3_1..P3_6` |

## Métodos Analíticos

- **Análise univariada:** distribuições de `P4` e `P1` (tabelas de frequência).
- **Análise bivariada:**
  - Cruzamento `P4 × P1`: % que lembra do voto por nível de vontade política.
  - Cruzamento `P1 × P2`: prioridades agregadas (P2_1+P2_2+P2_3) comparando quem lembra vs não lembra.
  - Cruzamento `P1 × P3`: intensidade de resposta e perfil de postura.
  - Cruzamento `P4 × P3`: perfil de postura por nível de engajamento.
- **Comparação com base externa:** correlação de Pearson entre `% que declarou não ter votado` (pesquisa) e `% abstenção oficial do TSE` por região.
- **Visualizações:** gráficos de barras, histogramas sobrepostos, gráficos de dispersão com linha de tendência.

## Principais Resultados

### 1. Perfil geral da amostra
- **Desinteresse político elevado:** 78% dos respondentes declararam “nenhuma vontade” de participar da política.
- **Baixa memória eleitoral:** apenas ~30% lembram em quem votaram para cada cargo; ~64% não lembram.

### 2. Memória eleitoral × vontade de participar
- Quem tem **muita/alguma vontade** lembra do voto **cerca de duas vezes mais** (≈58%) do que quem não tem nenhuma vontade (≈32%).
- Conclusão: memória e engajamento caminham juntos.

### 3. Prioridades políticas
- Ambos os grupos priorizam **temas materiais**: saúde, educação, empregos, redução da violência.
- Divergências aparecem em pautas **identitárias/abstratas**: engajados valorizam mais participação política e meio ambiente.

### 4. Postura sobre fake news
- **Majoritariamente punitivista:** 55,9% preferem punir (empresas, usuários, políticos), 18,8% regulamentar, 15,4% equilibrado.
- A intensidade de opinião (número de medidas citadas) é **semelhante** entre quem lembra e quem não lembra do voto.
- A preferência por punição é estável independentemente do nível de engajamento político.

### 5. Comparação com dados oficiais do TSE
- A pesquisa **subestima fortemente a abstenção** (2–9% declarados vs 18–24% oficiais).
- Correlação por região: **negativa (r ≈ –0,8)** – onde a abstenção real é maior (Norte), menos pessoas declaram não ter votado.
- Indica **viés de desejabilidade social** e **sub-representação de abstencionistas** nas regiões de maior abstenção.

## Limitações

- **Auto-relato:** memória de voto e vontade de participar podem sofrer viés de desejabilidade social.
- **Granularidade regional:** a base externa foi agregada em apenas 5 regiões, baixo poder estatístico.
- **Natureza descritiva:** as análises são exploratórias, sem inferência causal.
- **Representatividade:** a amostra tende a alcançar eleitores mais engajados, especialmente nas regiões Norte e Nordeste.

## Conclusões Gerais

1. O desengajamento eleitoral é muito elevado e está associado a menor memória do voto.
2. A agenda de políticas prioritária é material e consensual; divergências são secundárias.
3. A opinião sobre *fake news* é ampla, intensa e predominantemente punitivista, independentemente do engajamento.
4. A pesquisa apresenta viés de sub-relato de abstenção quando confrontada com dados oficiais do TSE – um alerta importante para qualquer inferência populacional.

## Gráficos Gerados

Os seguintes gráficos foram salvos durante a análise:

- `A_base_externa_TSE.png` – Comparação entre abstenção auto-declarada e oficial por região, com gráfico de barras e scatter plot com correlação.
- `P1xP2_prioridades.png` – Prioridades políticas comparando quem lembra vs não lembra dos votos.
- `P1xP3_intensidade.png` – Intensidade de opinião sobre fake news (histogramas e médias).
- `P4_distribuicao.png` – Distribuição da vontade de participar na política.
- `P4xP1_memoria.png` – Percentual que lembra do voto por nível de vontade política.
- `P4xP3_fakenews.png` – Medidas contra fake news por nível de vontade de participar.
- `S4_central_memoria_x_fakenews.png` – Perfil de postura sobre fake news (regulação vs punição) por grupo de memória eleitoral.
- `S4_perfil_geral.png` – Perfil geral de postura sobre fake news na amostra.

## Como Reproduzir

1. Execute o notebook `Eleitoral_final.ipynb` em ambiente Jupyter (ou Google Colab).
2. O notebook fará o download automático do arquivo `.sav` da pesquisa.
3. As análises serão executadas e os gráficos salvos no diretório de trabalho.
4. As bibliotecas necessárias estão listadas no notebook (`pyreadstat`, `gdown`, `pandas`, `matplotlib`, `seaborn`, `scipy`).