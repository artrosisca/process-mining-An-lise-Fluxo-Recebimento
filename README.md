# Mineração de Processos: Análise de Fluxo de Recebimento

> Projeto de análise de dados aplicado a fluxos financeiros (Accounts Payable) utilizando Python e PM4PY.

![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![PM4PY](https://img.shields.io/badge/Lib-PM4PY-orange)
![Status](https://img.shields.io/badge/Status-Concluído-success)

## 📝 Sobre o Projeto

Este projeto foi desenvolvido como parte da disciplina de **Mineração de Processos** no curso de Ciência da Computação. O objetivo foi aplicar técnicas de *Process Mining* para auditar, descobrir e otimizar o fluxo de **Confirmação de Recebimento** (*Receipt Phase*) de uma organização financeira.

Diferente de uma análise de dados tradicional (BI), este projeto foca na **perspectiva do processo**: como as atividades fluem, onde estão os gargalos temporais e se a execução real segue as regras de negócio.

## Dataset Utilizado

Utilizamos o dataset oficial **`receipt.xes`**, disponibilizado pelo repositório da *IEEE Task Force on Process Mining*.

* **Domínio:** Gestão Administrativa e Financeira.
* **Volume:** ~1.434 casos (processos únicos) e ~8.577 eventos.
* **Natureza:** Log de eventos contendo *Timestamps*, *Atividades* (Confirmation, Payment, Rejection) e *IDs de Caso*.

## Tecnologias e Ferramentas

* **Linguagem:** Python 3
* **Bibliotecas Principais:**
    * `pm4py`: Para algoritmos de descoberta, conformidade e visualização.
    * `pandas`: Para engenharia de dados, manipulação de dataframes e ETL.
    * `jupyterlab`: Ambiente de desenvolvimento interativo.

## Metodologia (Os 3 Pilares)

O projeto abordou os três pilares fundamentais da Mineração de Processos:

1.  **Descoberta (Discovery):**
    * Utilização do algoritmo **Inductive Miner** para gerar automaticamente o modelo de processo (Rede de Petri/BPMN) a partir dos dados brutos.
    * Estratégia *Data-Driven*: Filtragem das variantes mais frequentes ("Happy Path") para definir o modelo normativo.

2.  **Conformidade (Conformance Checking):**
    * Aplicação de **Token-based Replay** para verificar a aderência dos casos reais ao modelo ideal.
    * Identificação de desvios e cálculo de *Fitness*.

3.  **Melhoria (Enhancement/Performance):**
    * Projeção de dados temporais sobre o modelo gráfico.
    * Identificação visual de gargalos (*Bottlenecks*) através de mapas de calor e frequência.

## Principais Resultados e Insights

A análise dos dados revelou gargalos operacionais críticos que não seriam visíveis em relatórios convencionais:

* **Conformidade Alta:** O processo apresentou um *Fitness* de **93.07%**, indicando que o fluxo operacional é bem padronizado e os funcionários seguem as regras.
* **Gargalo de Performance:** Apesar da alta conformidade, a eficiência é o problema.
    * **Duração Média:** ~129.8 horas (aprox. 5 dias).
    * **Outliers Extremos:** O caso mais lento levou **6.621 horas** (aprox. 9 meses), indicando falhas graves de gestão em casos específicos.
    * **Variabilidade:** Alta discrepância entre casos instantâneos (automação) e casos manuais esquecidos.
