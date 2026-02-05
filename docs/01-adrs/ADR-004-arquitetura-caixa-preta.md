# ADR-004 — Arquitetura da “Caixa-Preta” do MSS

**Status:** Aceita  
**Data:** 2026-02-05

## Contexto
O projeto propõe um Modelo de Serviço de Segurança Gerenciada (MSS) para Provedores de Internet de Pequeno Porte (PPPs), baseado em sensores IDS (ex.: Suricata) e um mecanismo central de correlação de alertas. É necessário definir uma arquitetura clara, modular e de baixo custo, que permita operação contínua, experimentação controlada e evolução incremental.

## Decisão
A solução será estruturada como uma **arquitetura em camadas**, denominada “caixa-preta”, composta pelos seguintes blocos lógicos:

1. **Camada de Coleta**
   - Sensores IDS (Suricata) posicionados na borda ou em pontos estratégicos da rede.
   - Geração de alertas em formato estruturado (ex.: EVE JSON).

2. **Camada de Pré-processamento**
   - Normalização e filtragem inicial dos alertas.
   - Remoção de eventos claramente redundantes ou irrelevantes.
   - Preparação dos dados para correlação.

3. **Camada de Correlação**
   - Consolidação de alertas usando janelas temporais (ADR-002).
   - Aplicação de heurísticas e IA clássica para agrupamento e classificação (ADR-001).
   - Identificação de eventos correlacionados que representem incidentes.

4. **Camada de Enriquecimento e Análise**
   - Cálculo de métricas (frequência, duração, impacto).
   - Possível enriquecimento com informações externas simples (ex.: listas de IPs conhecidos).

5. **Camada de Saída**
   - Geração de incidentes acionáveis.
   - Exportação de resultados para visualização, relatório ou integração futura com outras ferramentas.

## Justificativa
- **Modularidade:** permite testar e evoluir cada camada de forma independente.
- **Baixo custo:** arquitetura compatível com execução local ou em VMs simples.
- **Reprodutibilidade:** facilita experimentos controlados e comparação de abordagens.
- **Aderência ao MSS:** separa claramente coleta, análise e entrega de valor ao operador.

## Alternativas consideradas
1. **Arquitetura monolítica sem separação de camadas**  
2. **Arquitetura fortemente dependente de serviços cloud/LLMs**  
3. **Pipeline complexo com múltiplas ferramentas externas**

## Consequências
- ✅ Clareza arquitetural para implementação e defesa acadêmica
- ✅ Facilidade de fatiar o projeto em experimentos e artigos
- ✅ Evolução incremental sem refatorações grandes
- ⚠️ Exige disciplina na definição de interfaces entre camadas

## Relação com o projeto
Esta decisão define a estrutura global da solução, orientando implementação, experimentos, métricas e a escrita da dissertação.
