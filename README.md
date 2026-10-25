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
4. [Reflexão Teórica: ETL e Qualidade de Dados](#-reflexão-teórica-etl-e-qualidade-de-dados-critério-avaliativo-1)
5. [Principais Insights e Conclusões da Análise](#-principais-insights-e-conclusões-critério-avaliativo-2)
6. [Resultados e Resumo dos Contadores](#-painel-final-de-contadores-do-pipeline)

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

## 🧠 Reflexão Teórica: ETL e Qualidade de Dados (Critério Avaliativo 1)

O processo de **ETL (Extract, Transform, Load)** constitui o pilar fundamental de qualquer iniciativa de Ciência de Dados, Engenharia de Dados e Business Intelligence. Na prática do mercado, dados transacionais dificilmente chegam prontos para consumo; frequentemente apresentam ruídos decorrentes de divergências de sistemas legados, falhas em formulários de cadastro e exportações incorretas.

### Dimensões Críticas de Qualidade de Dados Aplicadas no Projeto:
1. **Completude (Completeness):** A base original continha 4 colunas com 100% de dados ausentes (`Unnamed: 10` a `13`) e 3.650 registros com categorias inexistentes (`#N/D`). A identificação e imputação padronizada (`"Sem Categoria"`) asseguram que nenhuma transação seja perdida nos agrupamentos analíticos.
2. **Consistência e Unicidade (Uniqueness):** A detecção de 96.553 duplicatas estritas evidenciou redundância no processo de extração da fonte. A manutenção desses registros inflaria artificialmente a contagem de itens vendidos em mais de 11,6%, distorcendo a curva de demanda real.
3. **Conformidade de Tipos (Conformity):** A conversão de datas armazenadas em texto (`string`) para o formato temporal nativo (`datetime`) é requisito indispensável para permitir ordenação cronológica precisa, agrupamentos sazonais (ano/mês) e filtros de intervalo temporal.
4. **Validade e Integridade Referencial (Integrity):** A validação do grão da compra (`CO_ID`) garantiu a consistência relacional do negócio, comprovando que cada cesta de compras representa uma única transação de um cliente específico em uma determinada data.
5. **Interpretabilidade e Semântica Categórica (Interpretability):** A coluna `CL_EC` continha originalmente códigos numéricos brutos (`1` a `5`). Para viabilizar a tomada de decisão executiva na matriz analítica multidimensional, adotou-se a convenção clássica de cadastros demográficos e socioeconômicos brasileiros (IBGE / ERPs varejistas), mapeando `1: Solteiro`, `2: Casado`, `3: Divorciado`, `4: Viúvo` e `5: Outro` na coluna derivada `CL_EC_DESC`.

*Conclusão teórica:* Investir na camada de preparação e governança da qualidade dos dados assegura que as decisões tomadas pela gestão estejam ancoradas em fatos consistentes, evitando o clássico axioma *"Garbage In, Garbage Out"* (GIGO).

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
