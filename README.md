# ETL & People Insights

Pipeline de dados aplicado à área de People Analytics, simulando um fluxo real de 
ingestão, tratamento e análise de dados de RH — do dado bruto ao insight estratégico.

## Sobre o projeto

Este projeto replica a arquitetura de um pipeline de dados de Talent Acquisition, 
construído com base em experiência real de People Analytics. Utiliza duas fontes de 
dados distintas, aplica transformações e normalizações, faz o append das bases e 
persiste o resultado em banco de dados relacional para análise via SQL.

## Arquitetura do pipeline

Fonte 1 (IBM HR Dataset) → Normalização → Lookup → Append → SQLite → Análise SQL
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

## Principais insights

- Funcionários com até 25 anos têm taxa de desligamento de 35.8% — o triplo da faixa 36-45
- Cargos técnicos e de RH concentram as maiores taxas de rotatividade (~24%)
- Funcionários elegíveis (6+ meses no cargo) ganham 60% mais e saem menos
- Liderança tem a menor taxa de desligamento: 5.2%

## Stack

Python · Pandas · SQLite · SQL

## Contexto

Projeto desenvolvido como portfólio, baseado em pipeline real criado e mantido por mim 
na área de People Analytics de uma multinacional de grande porte. O pipeline original 
integra APIs REST do Workday, múltiplas fontes de dados e automações, suportando uma 
operação de Talent Acquisition com mais de 1.100 contratações anuais.

Este repositório replica a arquitetura e a lógica de tratamento usando dados públicos 
(IBM HR Analytics Dataset) para fins de demonstração.

