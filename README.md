# 📊 Projeto de Ciência de Dados: Opinião Pública e Séries Temporais

Este repositório contém a entrega final do projeto de Ciência de Dados, dividido em duas frentes principais de estudo: **Pesquisas de Opinião** (com foco em memória eleitoral e engajamento) e **Séries Temporais**.

![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![Google Colab](https://img.shields.io/badge/Colab-F9AB00?style=for-the-badge&logo=googlecolab&color=525252)

---

## 📑 Sumário
1. [Visão Geral dos Sub-projetos](#-visão-geral-dos-sub-projetos)
2. [Entregáveis e Links Rápidos](#-entregáveis-e-links-rápidos)
3. [Como Executar](#-como-executar)
4. [Integrantes do Grupo](#-integrantes-do-grupo)
5. [Referências e Declaração de Uso de IA](#-referências-e-declaração-de-uso-de-ia)

---

## 🔍 Visão Geral dos Subprojetos

### ✅ Parte A – Pesquisas de Opinião (`Entrega_A`)
Análise Exploratória de Dados (EDA) baseada em uma pesquisa de opinião nacional do **Ipec (acervo Cesop)**. O recorte temático investiga a relação entre o **engajamento e memória eleitoral** (eleições de 2022) e atitudes políticas cotidianas, como prioridades de governo e posicionamento sobre o combate às *fake news*.

### ✅ Parte B – Séries Temporais (`Entrega_B`)
Análise completa da evolução da **inadimplência no Brasil** utilizando dados públicos do **Banco Central do Brasil (BCB/SGS)**. Foram analisadas as séries de inadimplência total, pessoas físicas e jurídicas, correlacionadas com **Taxa Selic, câmbio e desemprego**. O estudo abrange o período de março/2012 a abril/2026 e inclui decomposição sazonal, autocorrelação e análise de defasagem (*cross‑correlation*).

---

## 📦 Entregáveis e Links Rápidos

### 📁 Entrega A
- **Notebook (Colab):** [Abrir notebook](https://colab.research.google.com/drive/1a9Mhg2Ohan4gK5E8hybe-TwZwiKQ3kk3?usp=sharing)
- **Texto Resumo:** [Visualizar MD](https://github.com/Tutzjwlee/Analise-Dados-Eleitorais/blob/main/Entrega_A/Resumo.md)

### 📁 Entrega B
- **Notebook (Colab):** [Abrir notebook](https://colab.research.google.com/drive/11xduGKlTtZYul0bL0esx_W8LKARXatXo?usp=sharing)
- **Texto Resumo:** [Visualizar MD](https://github.com/Tutzjwlee/Analise-Dados-Eleitorais/blob/main/Entrega_B/Resumo.md)

**Slides da Apresentação:** [Baixar slides](link-para-os-slides-B.pdf)
**Vídeo (YouTube):** [Assistir à apresentação](link-do-video-B)

---

## 🚀 Como Executar

Os notebooks são **100% executáveis no Google Colab** e não exigem configuração manual de ambiente. Basta seguir os passos:

1. Acesse os links dos notebooks fornecidos acima (eles abrirão diretamente no Colab).
2. No menu do Colab, clique em `Ambiente de execução` → `Executar tudo` (ou pressione `Ctrl+F9`).
3. Os dados serão carregados automaticamente via APIs ou URLs públicas durante a execução.

> Caso prefira executar localmente, certifique-se de ter as bibliotecas listadas na primeira célula de cada notebook.
> Os arquivos estão presentes nas pastas Entrega_A e Entrega_B com um resumo do que foi feito.

---

## 👥 Integrantes do Grupo

- **Arthur Jin Woo Lee** - *22.01519-0*
- **André Renato Almeida Abreu** - *22.01255-9*
- **Fernando Minharro Alves Gimenez** - *22.00833-0*
- **Leonardo Henrique Dias Moura** - *21.01837-5*
- **Leonardo Tagliati da Silva** - *22.00170-0*

---

## 📚 Referências e Declaração de Uso de IA

### Referências Principais
- **BCB – Banco Central do Brasil**. *Sistema Gerenciador de Séries Temporais (SGS)*. Dados de inadimplência, Selic, câmbio e desemprego. Acesso via API REST.
- **CESOP – Centro de Estudos de Opinião Pública**. *Pesquisa de Opinião Nacional – Ipec* (acervo utilizado para a Parte A).
- *Outras referências específicas estão citadas nos próprios notebooks.*

### Declaração de Uso de Inteligência Artificial
Em conformidade com as diretrizes do projeto, declaramos o uso de ferramentas de IA Generativa (ex: ChatGPT, Gemini, Claude) **exclusivamente como assistentes de codificação e produtividade**. Os usos incluíram:
- Geração de *snippets* para aprimoramento estético de gráficos (Matplotlib/Seaborn).
- Auxílio na refatoração e otimização de funções Python.
- Revisão gramatical de partes do texto final.
- Ajuda na criação dos slides e do roteiro do video (Uso estético, gramatical e organizacional da estrutura dos slide e roteiro do vídeo)
- Auxílio na organização e criação desse arquivo md

Nenhuma etapa de validação cruzada, interpretação dos fenômenos políticos/econômicos ou tomada de decisão metodológica sobre os modelos foi delegada de forma autônoma às ferramentas de IA. A autoria analítica pertence integralmente ao grupo.
