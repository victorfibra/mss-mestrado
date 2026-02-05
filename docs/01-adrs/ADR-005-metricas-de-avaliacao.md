# ADR-005 — Métricas de avaliação do Modelo de Serviço de Segurança Gerenciada (MSS)

**Status:** Aceita  
**Data:** 2026-02-05

## Contexto
A proposta do MSS busca reduzir o ruído operacional de alertas IDS em Provedores de Internet de Pequeno Porte (PPPs), mantendo capacidade de detecção e viabilidade operacional. Para validar a eficácia da solução, é necessário definir métricas claras, objetivas e mensuráveis, alinhadas ao contexto real de operação.

## Decisão
A avaliação do MSS será baseada em um conjunto de métricas quantitativas e qualitativas, organizadas em quatro dimensões principais:

### 1. Redução de Ruído Operacional
- Número total de alertas antes e depois da correlação.
- Percentual de redução de alertas.
- Relação alerta/incidente após a consolidação.

### 2. Qualidade da Detecção
- Taxa de falsos positivos.
- Taxa de falsos negativos (quando possível).
- Capacidade de agrupar corretamente alertas relacionados ao mesmo evento.

### 3. Impacto Operacional
- Tempo médio para identificação de um incidente.
- Redução do esforço manual de análise (proxy operacional).
- Número de eventos acionáveis gerados por período.

### 4. Custo Computacional
- Consumo médio de CPU e memória.
- Latência do processo de correlação.
- Viabilidade de execução em hardware de baixo custo.

## Justificativa
- **Aderência prática:** métricas refletem problemas reais enfrentados por PPPs.
- **Objetividade:** evita avaliação subjetiva ou puramente qualitativa.
- **Comparabilidade:** permite comparar configurações (ex.: janelas temporais diferentes).
- **Defensabilidade acadêmica:** métricas claras facilitam validação e argumentação em banca.

## Alternativas consideradas
1. **Avaliação apenas qualitativa (percepção do operador)**  
2. **Métricas genéricas de IDS sem foco operacional**  
3. **Avaliação centrada apenas em desempenho computacional**

## Consequências
- ✅ Avaliação clara do ganho operacional do MSS
- ✅ Base sólida para experimentos controlados
- ✅ Material direto para seção de resultados e discussão
- ⚠️ Algumas métricas dependem de rotulação manual ou dados de referência

## Relação com o projeto
Este conjunto de métricas orienta o desenho dos experimentos, a coleta de dados, a análise dos resultados e a escrita da dissertação e de artigos científicos.
