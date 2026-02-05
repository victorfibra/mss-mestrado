# ADR-001 — Não usar IA generativa (LLM) para correlação de alertas

**Status:** Aceita  
**Data:** 2026-02-05

## Contexto
O projeto visa um Modelo de Serviço de Segurança Gerenciada (MSS) de baixo custo para Provedores de Internet de Pequeno Porte (PPPs), com alto volume de alertas provenientes de sensores IDS (ex.: Suricata). A etapa de correlação precisa operar em escala, com custo previsível, baixa latência e possibilidade de execução em infraestrutura modesta (on-prem/VM barata).

## Decisão
A correlação e consolidação de alertas será realizada com técnicas de IA clássica e métodos determinísticos (heurísticas), por exemplo:
- janelas temporais e agregação
- clustering/agrupamento
- classificação supervisionada quando aplicável
- regras e filtros de pós-processamento

Modelos de linguagem (LLMs) não serão utilizados como mecanismo principal de correlação.

## Justificativa
- **Custo previsível:** correlação via LLM envolve tokenização de grandes volumes (entradas longas e repetitivas), resultando em custo variável e potencialmente inviável para PPPs.
- **Adequação técnica:** correlação é majoritariamente um problema de padrões/tempo/frequência, geralmente bem atendido por técnicas clássicas.
- **Operação e controle:** métodos clássicos tendem a ser mais explicáveis, auditáveis e fáceis de ajustar com base em métricas operacionais.

## Alternativas consideradas
1. **LLM como correlacionador principal**  
2. **LLM apenas como etapa auxiliar opcional** (ex.: sumarização/enriquecimento após correlação clássica)  
3. **Somente regras heurísticas (sem ML)**

## Consequências
- ✅ Solução mais barata e escalável no cenário alvo  
- ✅ Maior previsibilidade operacional e facilidade de auditoria  
- ✅ Facilita execução local e reprodutibilidade do artefato  
- ⚠️ Perde flexibilidade de linguagem natural na etapa de correlação (pode ser compensado com camada opcional de sumarização pós-correlação)

## Relação com o projeto
Esta decisão define o núcleo da “caixa-preta” (motor de correlação) e orienta escolhas de arquitetura, métricas e experimentos.
