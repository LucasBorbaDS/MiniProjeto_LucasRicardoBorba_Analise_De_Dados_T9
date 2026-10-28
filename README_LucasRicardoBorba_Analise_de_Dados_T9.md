# 🛒 Mini-Projeto Avaliativo - Módulo 1 (Semana 07)
## Instruções Rápidas de Execução e Entrega

- **Aluno:** Lucas Ricardo Borba
- **Turma:** `Analise_de_Dados_T9`
- **Repositório:** `Miniprojeto_LucasBorba_Analise_de_Dados_T9`
- **Arquivo Principal:** [`Notebook/miniprojeto_analise.ipynb`](Notebook/miniprojeto_analise.ipynb)

---

### 🚀 Como Executar o Projeto

#### No VS Code:
1. Abra a pasta do projeto no VS Code.
2. Certifique-se de que o ambiente virtual está ativo (`.venv`).
3. Abra o notebook [`Notebook/miniprojeto_analise.ipynb`](Notebook/miniprojeto_analise.ipynb).
4. No canto superior direito, selecione o kernel **Python (.venv)**.
5. Clique no botão **"Run All" (Executar Todas)** para rodar todas as células do pipeline sequencialmente.

#### No Google Colab:
1. Acesse [Google Colab](https://colab.research.google.com).
2. Faça o upload do notebook [`Notebook/miniprojeto_analise.ipynb`](Notebook/miniprojeto_analise.ipynb) e do arquivo [`Data/Base_Varejo.csv`](Data/Base_Varejo.csv).
3. No menu superior, vá em **Ambiente de execução > Executar tudo**.

---

### 📦 Estrutura e Versionamento de Arquivos na Entrega

```text
MiniProjeto_LucasRicardoBorba_Analise_De_Dados_T9/
├── Data/
│   ├── Base_Varejo.csv               # Dataset bruto transacional original (830.000 linhas)
│   └── df_varejo_limpo.csv           # Dataset higienizado e deduplicado final (733.447 linhas)
├── Notebook/
│   └── miniprojeto_analise.ipynb     # Pipeline analítico completo (Sprints 1 a 6)
├── .gitignore                        # Políticas de exclusão do Git (.venv, __pycache__, uv.lock)
├── .python-version                   # Fixação da versão do Python (3.14)
├── pyproject.toml                    # Configurações do projeto e dependências (uv)
├── requirements.txt                  # Dependências para instalação via pip
├── README.md                         # Relatório técnico completo de ETL e respostas de negócio
└── README_LucasRicardoBorba_Analise_de_Dados_T9.md # Guia rápido executivo de entrega
```

#### 🏷️ Detalhamento dos Componentes Entregues:
- [`Notebook/miniprojeto_analise.ipynb`](Notebook/miniprojeto_analise.ipynb): Notebook Jupyter completo com código documentado, testes de hipóteses, tabelas dinâmicas e gráficos executados.
- [`Data/Base_Varejo.csv`](Data/Base_Varejo.csv): Dataset bruto transacional preservado para reproduzibilidade.
- [`Data/df_varejo_limpo.csv`](Data/df_varejo_limpo.csv): Dataset final tratado, deduplicado e pronto para consumo analítico / BI.
- [`README.md`](README.md): Documentação completa contendo a reflexão teórica de ETL e Qualidade de Dados (Critério 1), respostas quantificadas às perguntas de negócio e conclusões estratégicas (Critério 2).
