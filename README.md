# 🧠 Motor Preditivo Hiper Inteligente para UANs Universitárias

> **Dissertação de Mestrado** — Indústria 5.0 na Gestão Pública: Redução do Desperdício Alimentar em Unidades de Alimentação e Nutrição através de Stacking Ensemble e BERT.

[![Python](https://img.shields.io/badge/Python-3.10+-blue?logo=python)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebooks-orange?logo=jupyter)](https://jupyter.org/)
[![XGBoost](https://img.shields.io/badge/XGBoost-LightGBM-green)](https://xgboost.readthedocs.io/)
[![BERT](https://img.shields.io/badge/NLP-BERT-yellow)](https://huggingface.co/)
[![License](https://img.shields.io/badge/Licença-Acadêmica-lightgrey)](LICENSE)

---

## 📋 Resumo

Este repositório contém os notebooks de pesquisa para o desenvolvimento e validação de um **"Motor Preditivo Hiper Inteligente"** voltado à otimização da demanda por refeições em Unidades de Alimentação e Nutrição (UANs) públicas.

Fundamentada no paradigma da **Design Science Research (DSR)**, a pesquisa propõe um artefato tecnológico que integra variáveis multimodais — previsões meteorológicas, calendários acadêmicos e semântica dos cardápios — para prever com precisão a demanda diária de refeições.

### 🏆 Resultados Principais

| Métrica | Resultado |
|---|---|
| MAPE (Erro Percentual Médio) | **6,4%** |
| Economia Potencial Anual | **R$ 172.500,00** |
| Redução de Desperdício | ~30% das refeições preparadas |
| Algoritmo Base | Stacking Ensemble (XGBoost + LightGBM + CatBoost) |

---

## 🎯 Problema de Pesquisa

UANs universitárias enfrentam um "ponto de decisão cego": a necessidade de empenhar insumos perecíveis com grande antecedência, baseando-se em reservas que frequentemente não se concretizam. Os dois fenômenos centrais do problema são:

-   **No-show**: Reserva feita, mas não consumida (motivos climáticos ou de rotina).
-   **Walk-in**: Consumo sem reserva, gerando pressão não planejada.

A pergunta norteadora da pesquisa é: *Como um Modelo Sistêmico Híbrido, fundamentado em Comitês Preditivos e BERT, pode mitigar o desperdício alimentar e otimizar a gestão financeira em uma UAN pública brasileira?*

---

## 🏗️ Arquitetura da Solução

```
┌──────────────────────────────────────────────────────────┐
│                    FONTES DE DADOS                       │
│  Reservas · Consumo · Cardápio · Calendário · Clima      │
└────────────────────────┬─────────────────────────────────┘
                         │
┌────────────────────────▼─────────────────────────────────┐
│              ENGENHARIA DE FEATURES (243 preditores)      │
│  Lags Temporais · Embeddings BERT · Encoding Calendário   │
└────────────────────────┬─────────────────────────────────┘
                         │
┌────────────────────────▼─────────────────────────────────┐
│              STACKING ENSEMBLE (Meta-Modelo)              │
│     XGBoost  ·  LightGBM  ·  CatBoost  →  Regressão     │
│           (Otimizado via Optuna — Bayes Search)           │
└────────────────────────┬─────────────────────────────────┘
                         │
┌────────────────────────▼─────────────────────────────────┐
│         SIMULAÇÃO DE RISCO (Monte Carlo — 10.000 iter.)   │
│     Margem de Segurança Inteligente · Análise de Risco    │
└──────────────────────────────────────────────────────────┘
```

---

## 📁 Estrutura dos Notebooks

### 📥 Fase 1 — Ingestão de Dados
| Notebook | Descrição |
|---|---|
| `01a_ingestao_reservas.ipynb` | Ingestão e anonimização das reservas de refeições |
| `01b_ingestao_consumo.ipynb` | Ingestão e anonimização dos dados de consumo real |
| `01c_ingestao_cardapio.ipynb` | Extração e tratamento dos cardápios diários |
| `01d_ingestao_calendario.ipynb` | Integração do calendário acadêmico (feriados, provas, etc.) |
| `01e_ingestao_clima.ipynb` | Coleta de dados climáticos via API |

### 🧹 Fase 2 — Preparação
| Notebook | Descrição |
|---|---|
| `02_consolidacao_limpeza.ipynb` | Consolidação e limpeza da base mestra |
| `03_analise_exploratoria.ipynb` | Análise exploratória completa (EDA) |

### ⚙️ Fase 3 — Engenharia de Features
| Notebook | Descrição |
|---|---|
| `04_engenharia_features_lags.ipynb` | Criação de variáveis defasadas (lags) e janelas de tempo |
| `05_engenharia_features_bert.ipynb` | Embeddings semânticos do cardápio com BERT |
| `06_selecao_features_avancada.ipynb` | Seleção de features via SHAP, importância e correlação |

### 🤖 Fase 4 — Modelagem de Candidatos
| Notebook | Descrição |
|---|---|
| `07a_modelagem_linear.ipynb` | Regressão Linear e Ridge |
| `07b_modelagem_knn.ipynb` | K-Nearest Neighbors |
| `07c_modelagem_svr.ipynb` | Support Vector Regression |
| `07d_modelagem_arvores.ipynb` | Árvores de Decisão e Random Forest |
| `07e_modelagem_boosting.ipynb` | XGBoost, LightGBM e CatBoost |
| `07f_modelagem_ann.ipynb` | Redes Neurais Artificiais (MLP) |
| `07g_modelagem_arima.ipynb` | ARIMA |
| `07h_modelagem_sarimax.ipynb` | SARIMAX |
| `07i_modelagem_prophet.ipynb` | Facebook Prophet |

### 🏆 Fase 5 — Modelo Final e Validação
| Notebook | Descrição |
|---|---|
| `08_modelagem_machine_learning.ipynb` | Comparativo consolidado de todos os modelos |
| `09_modelagem_ensemble_hibrido.ipynb` | Stacking Ensemble híbrido (modelo principal) |
| `10_simulacao_risco_monte_carlo.ipynb` | Simulação de Monte Carlo para análise de risco |
| `11_dashboard_resultados_final.ipynb` | Dashboard interativo com todos os resultados |
| `16_modelagem_hiper_inteligente.ipynb` | Motor Preditivo Hiper Inteligente (versão final) |
| `17_validacao_cruzada_modelo_final.ipynb` | Validação cruzada rigorosa do modelo final |

### 🚀 Fase 6 — Operacionalização
| Notebook | Descrição |
|---|---|
| `12_preparacao_entrada_operacional.ipynb` | Preparação dos dados de entrada para uso operacional |
| `13_predicao_operacional.ipynb` | Predição para a semana operacional |
| `14_predicao_dinamica_diaria.ipynb` | Predição dinâmica diária com atualização em tempo real |
| `15_motor_hiper_inteligente.ipynb` | Interface de uso do motor preditivo |

---

## 🛠️ Tecnologias Utilizadas

| Categoria | Ferramentas |
|---|---|
| **Linguagem** | Python 3.10+ |
| **Notebooks** | Jupyter Lab |
| **ML/DL** | Scikit-learn, XGBoost, LightGBM, CatBoost |
| **NLP** | HuggingFace Transformers, BERT (BERTimbau) |
| **Séries Temporais** | Statsmodels (ARIMA/SARIMAX), Prophet |
| **Otimização** | Optuna (Bayes Search) |
| **Visualização** | Matplotlib, Seaborn, Plotly |
| **Explicabilidade** | SHAP (XAI) |
| **Simulação** | NumPy (Monte Carlo) |

---

## 🚀 Como Executar

### Pré-requisitos
```bash
# Clone o repositório
git clone https://github.com/micheldigui/mestrado.git
cd mestrado

# Crie e ative o ambiente virtual
python -m venv .venv
.venv\Scripts\activate   # Windows

# Instale as dependências
pip install -r requirements.txt
```

### Executando os Notebooks
```bash
jupyter lab
```
> **Recomendação:** Execute os notebooks em ordem numérica (01a → 17) para garantir que as dependências de dados sejam respeitadas.

---

## 📚 Referencial Teórico

-   **Indústria 5.0** — European Commission (2021): foco em resiliência e humanocentrismo.
-   **Design Science Research (DSR)** — Hevner et al. (2004): metodologia para desenvolvimento de artefatos científicos.
-   **BERT** — Devlin et al. (2018): modelo de linguagem bidirecional para extração semântica.
-   **Stacking Ensemble** — Wolpert (1992): comitê de modelos com meta-aprendizado.
-   **Monte Carlo** — simulação probabilística para gestão de risco operacional.

---

## 👤 Autor

**Michel Diguim Guimarães**
Programa de Pós-Graduação em Computação Aplicada — Mestrado
Orientador: Prof. Dr. [Nome do Orientador]

---

## 📄 Citação

Se este trabalho for útil para sua pesquisa, cite:

```bibtex
@mastersthesis{guimaraes2025,
  title  = {Indústria 5.0 na Gestão Pública: Redução do Desperdício Alimentar em UANs através de Stacking Ensemble e BERT},
  author = {Guimarães, Michel Diguim},
  year   = {2025},
  school = {Programa de Pós-Graduação em Computação Aplicada}
}
```
