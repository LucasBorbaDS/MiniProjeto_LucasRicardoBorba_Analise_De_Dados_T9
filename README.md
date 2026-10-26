# 🛒 Mini-Projeto Avaliativo - Módulo 1 (Semana 07)
## Análise Exploratória de Dados (AED) - Base Varejo

- **Disciplina:** Análise de Dados com Python
- **Turma:** `Analise_de_Dados_T9`
- **Aluno:** Lucas Ricardo Borba
- **Dataset:** `Base Varejo.csv` (830.000 registros originais)
- **Notebook Principal:** [`miniprojeto_analise.ipynb`](miniprojeto_analise.ipynb)

---

## 📋 Sumário
1. [Visão Geral e Objetivos](#-visão-geral-e-objetivos)
2. [Instruções de Execução](#-instruções-de-execução)
3. [Estrutura do Projeto e Sprints](#-estrutura-do-projeto-e-sprints)
4. [Reflexão Teórica: ETL e Qualidade de Dados (Critério 1)](#-reflexão-teórica-etl-e-qualidade-de-dados-critério-avaliativo-1)
5. [Respostas às Perguntas de Negócio (Perguntas Operacionais)](#-respostas-às-perguntas-de-negócio-perguntas-operacionais)
6. [Principais Insights e Conclusões da Análise (Critério 2)](#-principais-insights-e-conclusões-critério-avaliativo-2)
7. [Resultados e Resumo dos Contadores](#-painel-final-de-contadores-do-pipeline)

---

## 🎯 Visão Geral e Objetivos

Este projeto implementa um pipeline completo, estruturado e reproduzível de **Extração, Transformação e Carga (ETL)** e **Análise Exploratória de Dados (AED)** aplicada ao setor varejista. O objetivo é transformar um conjunto bruto de dados transacionais com inconsistências em uma base higienizada de alta fidelidade analítica, apta a alimentar relatórios executivos e dashboards de BI.

---

## 🚀 Instruções de Execução

O projeto foi configurado com Python 3.14 utilizando o gerenciador de pacotes **`uv`**.

### Opção 1: Executando localmente no VS Code
1. Clone o repositório:
   ```bash
   git clone https://github.com/LucasBorbaDS/MiniProjeto_LucasRicardoBorba_Analise_De_Dados_T9.git
   cd MiniProjeto_LucasRicardoBorba_Analise_De_Dados_T9
   ```
2. Crie e sincronize o ambiente virtual:
   ```bash
   uv sync
   ```
3. Abra o arquivo [`miniprojeto_analise.ipynb`](miniprojeto_analise.ipynb) no VS Code.
4. Selecione o kernel do Python localizado em `.venv\Scripts\python.exe`.
5. Clique em **"Run All" (Executar Todas as Células)**.


### Opção 2: Instalando dependências via pip
1. Clone o repositório:
   ```bash
   git clone https://github.com/LucasBorbaDS/MiniProjeto_LucasRicardoBorba_Analise_De_Dados_T9.git
   cd MiniProjeto_LucasRicardoBorba_Analise_De_Dados_T9
   ```
2. Crie e ative um ambiente virtual:
   ```bash
   python -m venv .venv
   source .venv/bin/activate
   ```
   > No Windows, use: `.venv\Scripts\activate`
3. Instale os requisitos do projeto:
   ```bash
   pip install -r requirements.txt
   ```
4. Abra o arquivo [`miniprojeto_analise.ipynb`](miniprojeto_analise.ipynb) no VS Code.
5. Selecione o kernel do Python do ambiente virtual criado.
6. Clique em **"Run All" (Executar Todas as Células)**.


### Opção 3: Executando via Google Colab
1. Faça o upload do notebook [`miniprojeto_analise.ipynb`](miniprojeto_analise.ipynb) e do arquivo [`Base Varejo.csv`](Base%20Varejo.csv) na raiz do Colab.
2. No menu superior, clique em **Ambiente de Execução > Executar Tudo**.

---

## 🏗️ Estrutura do Projeto e Sprints

O notebook está estruturado rigorosamente conforme os 6 sprints avaliativos:

- **Sprint 1 (Importação e Diagnóstico):**
  - Extração nativa e estruturada em fluxo de dicionários com `csv.DictReader`.
  - Carga otimizada em DataFrame via `pandas.read_csv`.
  - Diagnóstico inicial de dimensões (830.000 linhas × 14 colunas) e tipagem primitiva.
- **Sprint 2 (Transformação e Regras de Negócio):**
  - Funções de sanitização textual usando Expressões Regulares (`re`).
  - Validação estrita da regra de negócio do identificador de compras (`CO_ID`): confirmação de que cada carrinho pertence exclusivamente a 1 cliente e 1 data.
  - Conversão da coluna `DATA` de string para `datetime` com tratamento de possíveis inconformidades cronológicas.
- **Sprint 3 (Limpeza de Nulos e Duplicatas):**
  - Mapeamento e quantificação de valores nulos.
  - Eliminação justificada das 4 colunas excedentes (`Unnamed: 10` a `13`), decorrentes de delimitadores residuais no arquivo CSV.
  - Tratamento condicional com `if/else` da coluna de categoria (`PR_CAT`), convertendo valores ausentes e `#N/D` para `"Sem Categoria"`.
  - Expurgo criterioso de **96.553 linhas duplicadas**, garantindo a integridade dos volumes.
- **Sprint 4 (Estatística Descritiva da Coluna de Filhos `CL_FHL`):**
  - Cálculo de todas as métricas: Média, Mediana, Moda, Desvio Padrão, Mínimo, Máximo, Contagem, Quartis (Q1 25%, Q2 50%, Q3 75%) e Intervalo Interquartil (IQR).
  - Análise em dois níveis: nível transacional e nível demográfico de clientes únicos (`CL_ID`).
  - Visualização com Histograma percentual e Boxplot detalhado.
- **Sprint 5 (Agrupamentos, Relatório e Conclusões):**
  - Agrupamentos analíticos usando `groupby()` e `pivot_table()`:
    1. Comportamento e volume por Gênero (`CL_GENERO`);
    2. Vendas e participação percentual por Categoria (`PR_CAT`);
    3. Cruzamento multidimensional de Segmento de Cliente (`CL_SEG`) vs. Estado Civil (`CL_EC`), com aplicação do mapeamento semântico padronizado (`1: Solteiro`, `2: Casado`, `3: Divorciado`, `4: Viúvo`, `5: Outro`) derivado das convenções demográficas e cadastrais brasileiras (como IBGE e formulários de ERP/CRM) para assegurar interpretabilidade analítica na nova coluna `CL_EC_DESC`;
    4. Tendência temporal e histórico de compras anual.
  - Visualizações analíticas com paletas modernas (Matplotlib / Seaborn).
  - Painel consolidado de contadores exibido em formato de relatório de terminal.
  - 5 conclusões e insights estratégicos do negócio.
- **Sprint 6 (Versionamento e Exportação):**
  - Geração do arquivo processado final [`df_varejo_limpo.csv`](df_varejo_limpo.csv) pronto para consumo.

---

## 🧠 Reflexão Teórica: ETL e Qualidade de Dados

O processo de **ETL (Extract, Transform, Load)** constitui o pilar fundamental de qualquer iniciativa de Ciência de Dados, Engenharia de Dados e Business Intelligence. Na prática do mercado, dados transacionais dificilmente chegam prontos para consumo; frequentemente apresentam ruídos decorrentes de divergências de sistemas legados, falhas em formulários de cadastro e exportações incorretas.

### Dimensões Críticas de Qualidade de Dados Aplicadas no Projeto:
1. **Completude (Completeness):** A base original continha 4 colunas com 100% de dados ausentes (`Unnamed: 10` a `13`) e 3.650 registros com categorias inexistentes (`#N/D`). A identificação e imputação padronizada (`"Sem Categoria"`) asseguram que nenhuma transação seja perdida nos agrupamentos analíticos.
2. **Consistência e Unicidade (Uniqueness):** A detecção de 96.553 duplicatas estritas evidenciou redundância no processo de extração da fonte. A manutenção desses registros inflaria artificialmente a contagem de itens vendidos em mais de 11,6%, distorcendo a curva de demanda real.
3. **Conformidade de Tipos (Conformity):** A conversão de datas armazenadas em texto (`string`) para o formato temporal nativo (`datetime`) é requisito indispensável para permitir ordenação cronológica precisa, agrupamentos sazonais (ano/mês) e filtros de intervalo temporal.
4. **Validade e Integridade Referencial (Integrity):** A validação do grão da compra (`CO_ID`) garantiu a consistência relacional do negócio, comprovando que cada cesta de compras representa uma única transação de um cliente específico em uma determinada data.
5. **Interpretabilidade e Semântica Categórica (Interpretability):** A coluna `CL_EC` continha originalmente códigos numéricos brutos (`1` a `5`). Para viabilizar a tomada de decisão executiva na matriz analítica multidimensional, adotou-se a convenção clássica de cadastros demográficos e socioeconômicos brasileiros (IBGE / ERPs varejistas), mapeando `1: Solteiro`, `2: Casado`, `3: Divorciado`, `4: Viúvo` e `5: Outro` na coluna derivada `CL_EC_DESC`.

*Conclusão teórica:* Investir na camada de preparação e governança da qualidade dos dados assegura que as decisões tomadas pela gestão estejam ancoradas em fatos consistentes, evitando o clássico axioma *"Garbage In, Garbage Out"* (GIGO).

---

## 💼 Respostas às Perguntas de Negócio (Perguntas Operacionais)

### 1️⃣ Pergunta 1: Quem compra mais?
* **Distribuição por Gênero (`CL_GENERO`):**
  - **Liderança Feminina:** As clientes do gênero feminino lideram o consumo, respondendo por **52,14%** de todo o volume de produtos comercializados (**382.438 itens**) e **51,70%** das compras realizadas (**9.549 transações** em 517 clientes cadastradas).
  - **Público Masculino:** É responsável por **47,86%** do volume (**351.009 itens** em **8.922 transações** de 483 clientes cadastrados).
  - **Cesta Média:** A média de itens por transação é rigorosamente idêntica entre os gêneros (**39,6 itens/compra no masculino** vs. **40,0 itens/compra no feminino**). Isso comprova que a maior participação feminina decorre de uma **maior frequência e taxa de visitação** à loja.
* **Distribuição por Segmento de Clientes (`CL_SEG`):**
  - **Segmento B:** Concentra **63,88%** do volume total transacionado (**468.552 itens**).
  - **Segmento C:** Representa a segunda maior fatia comercial, com **27,90%** (**204.604 itens**).
  - **Segmento A (Premium):** Responde por apenas **8,22%** (**60.291 itens**).
  - *Conclusão:* Mais de **91,7%** da demanda é impulsionada pelos clientes dos segmentos médios e populares (B e C).
* **Perfil Familiar e Demográfico:**
  - Clientes **sem filhos** constituem a expressiva maioria dos compradores (**52,5% da base de clientes**, com mediana = 0).
  - Na análise bivariada de Segmento vs. Estado Civil (`CL_SEG` x `CL_EC_DESC`), **clientes casados e solteiros dos segmentos B e C** são os principais geradores de receita e volume na rede.

---

### 2️⃣ Pergunta 2: Quais categorias vendem mais?
* **Ranking Geral de Volume e Participação por Categoria (`PR_CAT`):**

| Posição | Categoria | Quantidade de Itens | Participação no Mix (%) | Compras Distintas (`CO_ID`) |
| :---: | :--- | :---: | :---: | :--- |
| 🥇 1º | **ALIMENTOS** | 386.816 | **52,74%** | 18.411 |
| 🥈 2º | **HIGIENE** | 137.822 | **18,79%** | 16.518 |
| 🥉 3º | **LIMPEZA** | 129.317 | **17,63%** | 16.208 |
| 4º | **PET** | 39.141 | **5,34%** | 10.707 |
| 5º | **ACESSÓRIOS / OUTROS** | 37.116 | **5,06%** | 10.427 |
| - | **Sem Categoria (Imputados no ETL)** | 3.235 | **0,44%** | 2.502 |
| **TOTAL** | - | **733.447** | **100,00%** | **18.471** |

* **Diagnóstico Estratégico de Sortimento:**
  - O negócio é marcadamente centrado em bens de primeira necessidade: as categorias **Alimentos, Higiene e Limpeza somam 89,16%** de todas as saídas de estoque.
  - As categorias **Pet** (5,34%) e **Acessórios** (5,06%) possuem potencial estratégico para campanhas de venda casada (*cross-selling*) em pontos quentes do supermercado (gôndolas de checkout).

---

### 3️⃣ Pergunta 3: Como variam as vendas ao longo do tempo?
* **Histórico Temporal do Volume Anual de Vendas:**

| Ano | Volume Total de Itens | Compras Únicas Realizadas | Média de Itens por Compra | Diagnóstico Operacional |
| :---: | :---: | :---: | :---: | :--- |
| **2019** | 190.435 | 4.787 | 39,78 | Operação plena e estável |
| **2020** | 192.176 | 4.821 | 39,86 | Leve crescimento (+0,91%), forte resiliência na demanda de itens básicos |
| **2021** | 191.092 | 4.819 | 39,65 | Manutenção do padrão histórico médio |
| **2022** | 159.744 | 4.044 | 39,50 | Período parcial: dados finalizados em **08/12/2022** |

* **Diagnóstico da Tendência Cronológica:**
  - O volume de vendas nos três anos com histórico completo (2019, 2020 e 2021) manteve-se excepcionalmente regular (~191.000 itens e ~4.800 transações anuais).
  - A variação observada em 2022 é pontual e artificial, decorrendo exclusivamente do encerramento da coleta de dados em **08 de dezembro de 2022**. Projetando os dias remanescentes do mês com as compras de fim de ano, 2022 acompanha o mesmo patamar histórico anual.

---

## 💡 Principais Insights e Conclusões

A partir da exploração dos dados limpos, foram identificados os seguintes direcionamentos estratégicos para a operação de varejo:

1. **Liderança Feminina no Volume de Compras e Frequência:** O público feminino responde por **52,1% do volume total de itens comprados** e transações, mantendo média de itens por cesta similar à masculina. Campanhas promocionais e programas de fidelidade com apelo direcionado ao perfil feminino apresentam maior potencial de tração e retorno financeiro.
2. **Alimentos como Core Business de Alta Recorrência:** A categoria `ALIMENTOS` concentra **52,7% de todas as vendas**, seguida por `HIGIENE` (18,8%) e `LIMPEZA` (17,6%). Juntas, essas 3 categorias perfazem quase 90% do movimento da rede, caracterizando o negócio como varejo alimentar de reposição básica. As categorias `PET` e `ACESSÓRIOS` apresentam oportunidades claras de *cross-selling* (venda cruzada no caixa).
3. **Predominância dos Segmentos B e C:** Mais de **91% das vendas** concentram-se nos segmentos de clientes `B` (63,9%) e `C` (27,9%), com o segmento `A` respondendo por apenas 8,2%. As estratégias de precificação, comunicação visual e promoções de encarte devem priorizar a percepção de custo-benefício e marcas de combate.
4. **Perfil Familiar Predominante sem Filhos:** A análise estatística da coluna `CL_FHL` revelou que **52,5% dos clientes não possuem filhos** (mediana e moda = 0), com uma média global de apenas 1,14 filhos por cliente. O sortimento de produtos deve balancear tamanhos familiares com porções individuais e embalagens fracionadas para casais ou solteiros, reduzindo atrito de compra.
5. **Diagnóstico da Base e Oportunidades Futuras de Melhoria:** 
   - *Sucessos:* A higienização removeu com segurança o ruído estrutural de 96.553 duplicatas e 4 colunas nulas, restabelecendo a confiança analítica.
   - *Limitação Remanescente:* O dataset atual não possui colunas explícitas de valores monetários (preço unitário, receita ou desconto). Recomenda-se no próximo ciclo de engenharia a junção (*merge*) com a tabela dimensão de preços para permitir o cálculo de faturamento bruto, margem e ticket médio em reais.

---

## 📊 Painel Final de Contadores do Pipeline

```text
=================================================================
           RELATÓRIO CONSOLIDADO DE QUALIDADE E NEGÓCIO         
=================================================================
 Total de Registros Brutos Processados:    830,000
 Duplicatas Eliminadas:                     96,553
 Total de Registros Limpos e Válidos:       733,447
 Clientes Únicos na Base:                   1,000
 Transações Únicas de Compra (CO_ID):       18,471
 Média de Itens por Cesta de Compra:        39.71 itens
 Categoria Líder em Volume:                ALIMENTOS (52.74%)
 Produtos sem Categoria Imputados:          3,235
 Período Histórico Coberto:                 04/01/2019 a 08/12/2022
=================================================================
 Status: Pipeline de ETL e Análise Exploratória concluído com 100% de sucesso!
```
