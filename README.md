![SQL](https://img.shields.io/badge/Tool-SQL-3776AB)
![Power BI](https://img.shields.io/badge/Tool-Power%20BI-4A73A8)
![Python](https://img.shields.io/badge/Tool-Python-3776AB)

# Case – Análise de Chamados de Suporte Técnico

Este projeto consiste em um estudo de caso de análise de dados, desenvolvido para fins de portfólio, simulando um cenário real de uma operação de suporte técnico.

O objetivo é demonstrar minhas habilidades práticas em Power BI, SQL e Python, desde a organização dos dados até a geração de insights que auxiliam na tomada de decisão.

---

## Objetivo do Projeto

- Analisar o desempenho do atendimento de suporte técnico
- Identificar gargalos operacionais e pontos de melhoria
- Avaliar cumprimento de SLA
- Explorar métricas relevantes para gestão de suporte

---

## Perguntas de Negócio

- Qual é o tempo médio de resolução dos chamados?
- Quais categorias apresentam maior volume de chamados?
- Qual a porcentagem de chamados fora do tempo estimado pelo SLA?
- Existem categorias com maior tempo médio de atendimento?

---

## Planos de Ação 
Com base nas análises realizadas, foi identificado que 73,4% dos chamados estão fora do SLA de 4 horas, 
indicando problemas operacionais e oportunidades claras de melhoria nos processos de suporte.

A partir dos insights obtidos, foi desenvolvido os seguintes planos de ação:

1️⃣ Revisão da Priorização dos Chamados

Problema: Chamados com prioridade baixa e média impactam diretamente o cumprimento do SLA.
Ação proposta:

- Revisar critérios de classificação de prioridade com base em impacto e urgência

- Implementar regras automáticas de priorização conforme categoria

2️⃣ Atuação Direcionada nas Categorias Críticas

Problema: Algumas categorias concentram os maiores tempos médios de resolução.
Ação proposta:

- Foco nas categorias com maior impacto no SLA

- Criação de procedimentos padronizados e base de conhecimento

3️⃣ Balanceamento da Carga de Atendimento

Problema: Possível sobrecarga ou má distribuição de chamados entre analistas, 
impactanto diretamente no tempo de resolução dos chamados.
Ação proposta:

- Redistribuição de chamados considerando complexidade e especialização

- Monitoramento do backlog diário

4️⃣ Controle Preventivo de SLA

Problema: Ausência de monitoramento proativo que resulta na detecção tardia de chamados próximos ao vencimento do SLA.
Ação proposta:

- Criação de alertas para chamados próximos do vencimento do SLA

- Uso de dashboards operacionais para acompanhamento em tempo real
---

## Fonte de Dados

Os dados utilizados são simulados, com o objetivo de representar um ambiente realista de atendimento de suporte técnico.

### Estrutura do dataset:
- `id_chamado`
- `data_abertura`
- `data_fechamento`
- `categoria`
- `prioridade`
- `status`
- `tempo_resolucao_horas`

---

## Estrutura do Projeto

- 📂 `dados` — Arquivos de dados em Excel
  - `chamados_suporte.xlsx`
- 📂 `python` — Notebook de análise  
  - `analise_suporte.ipynb`
- 📂 `powerbi` — Arquivo do dashboard Power BI  
  - `dashboard_chamados.pbix`  
- 📂 `imagens` — Print do dashboard
  - ![Dashboard Principal](imagens/dashboard.png)
  
---

## Ferramentas Utilizadas

- **Power BI**
  - Tratamento de dados
  - Criação de medidas com DAX
  - Construção de dashboard interativo

- **SQL**
  - Análises exploratórias
  - Validação de métricas
  - Agregações e filtros por categoria e prioridade

- **Python**
  - Análise exploratória de dados (EDA)
  - Manipulação de dados com Pandas
  - Visualizações com Matplotlib/Seaborn

---

## Dashboard (Power BI)

O dashboard apresenta indicadores estratégicos, como:
- Total de chamados
- Tempo médio de resolução
- Percentual de chamados fora do SLA
- Distribuição por categoria e prioridade

---

## Análises Realizadas em SQL

O SQL foi utilizado para aprofundar a análise dos dados e validar padrões observados no dashboard.

### Exemplos de consultas:

#### Chamados com maior tempo de resolução
```
SELECT TOP 10 id_chamado, categoria, prioridade, tempo_resolucao_horas
FROM chamados
ORDER BY tempo_resolucao_horas DESC
```

Tempo médio de resolução por categoria e prioridade
```
SELECT categoria, prioridade, ROUND(AVG(tempo_resolucao_horas), 2) AS [tempo_medio_resolucao]
FROM chamados
GROUP BY categoria, prioridade
ORDER BY tempo_medio_resolucao DESC
```

Chamados fora do SLA por categoria
```
SELECT categoria, COUNT(*) AS [chamados_fora_sla]
FROM chamados
WHERE tempo_resolucao_horas > 4
GROUP BY categoria
ORDER BY chamados_fora_sla DESC
```
