# ADR-002 — Uso de janelas temporais para correlação e agregação de alertas

**Status:** Aceita  
**Data:** 2026-02-05

## Contexto
Sensores IDS em ambientes de Provedores de Internet de Pequeno Porte (PPPs) geram alto volume de alertas, muitos deles redundantes ou relacionados ao mesmo evento de ataque. A correlação precisa reduzir ruído operacional sem perder a capacidade de detecção, mantendo simplicidade e baixo custo computacional.

## Decisão
A correlação de alertas será baseada em **janelas temporais deslizantes**, combinadas com critérios de agregação como:
- intervalo de tempo
- origem/destino (IP, porta, protocolo)
- tipo de alerta/regra
- frequência de ocorrência

As janelas serão inicialmente configuradas com valores fixos (ex.: 10s, 30s, 60s), podendo ser ajustadas conforme resultados experimentais.

## Justificativa
- **Eficiência operacional:** janelas temporais reduzem rapidamente alertas repetitivos relacionados ao mesmo evento.
- **Baixo custo computacional:** abordagem simples, adequada a execução local.
- **Controle e explicabilidade:** parâmetros claros e ajustáveis facilitam entendimento e auditoria.
- **Aderência ao cenário real:** ataques DDoS e varreduras apresentam forte correlação temporal.

## Alternativas consideradas
1. **Correlação global sem janelas temporais**  
2. **Janelas adaptativas complexas (baseadas em LLM ou modelos avançados)**  
3. **Correlação exclusivamente baseada em regras estáticas**

## Consequências
- ✅ Redução significativa de ruído operacional
- ✅ Base sólida para aplicação posterior de IA clássica (clustering/classificação)
- ✅ Facilidade de experimentação e comparação de parâmetros
- ⚠️ Janelas mal ajustadas podem ocultar eventos de baixa frequência (mitigável por análise experimental)

## Relação com o projeto
Esta decisão define o mecanismo central de consolidação de alertas da “caixa-preta” e orienta o desenho dos experimentos, métricas de avaliação e ajustes operacionais.
