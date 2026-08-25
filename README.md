# ETL & People Insights

Pipeline de dados aplicado à área de People Analytics — do dado bruto ao insight 
estratégico, incluindo modelagem preditiva de desligamento.

## Sobre o projeto

Este projeto replica a arquitetura de um pipeline de dados de Talent Acquisition, 
construído com base em experiência real criada e mantida por mim em uma multinacional 
de grande porte. O pipeline original integra APIs REST do Workday, múltiplas fontes 
de dados e automações, suportando uma operação com mais de 2.100 contratações anuais.

Este repositório demonstra a mesma arquitetura e lógica de tratamento usando dados 
públicos (IBM HR Analytics Dataset) para fins de portfólio.

## Arquitetura do pipeline

Fonte 1 (IBM HR Dataset) → Normalização → Lookup → Append → SQLite → Análise SQL → Modelo Preditivo
Fonte 2 (Implantação)   ↗

## O que o pipeline faz

- Extração: leitura de CSV simulando consumo de API REST
- Seleção de colunas: filtra apenas os campos relevantes para análise
- Normalização: tradução de valores, mapeamento de categorias, padronização de tipos
- Lookup por keyword: classificação de cargos por categoria usando lista de prioridade
- Faixa etária e tempo no cargo: criação de variáveis categóricas para segmentação
- Append de fontes: união de duas bases com estruturas diferentes
- Persistência: salvamento em banco SQLite
- Análise SQL: queries para extração de insights de rotatividade, elegibilidade e perfil
- Modelagem preditiva: Random Forest para predição de risco de desligamento

## Principais insights — Análise Exploratória

- Funcionários com até 25 anos têm taxa de desligamento de 35.8% — o triplo da faixa 36-45
- Cargos técnicos e de RH concentram as maiores taxas de rotatividade (~24%)
- Liderança tem a menor taxa de desligamento: 5.2%
- Estado civil influencia retenção independentemente da idade: solteiros têm taxa de 
  desligamento de 26%, mais que o dobro de casados (12%) e divorciados (10%)

## Principais insights — Modelo Preditivo (Random Forest)

- Acurácia: 83%
- Quem sai ganha em média 30% menos do que quem fica (R$4.780 vs R$6.835)
- Quem sai é 4 anos mais jovem em média (33.6 vs 37.5 anos)
- Quem sai tem 35% menos tempo no cargo (2.9 vs 4.5 anos)
- Perfil de maior risco: jovem + pouco tempo de casa + salário abaixo da média
- Salário é o fator de maior importância preditiva (38%), seguido de idade (25%) 
  e tempo no cargo (14%)

## Stack

Python · Pandas · Scikit-learn · SQLite · SQL

## Dataset

IBM HR Analytics Employee Attrition & Performance — Kaggle (público)
