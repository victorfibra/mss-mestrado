# ADR-003 — Política de dados, privacidade e reprodutibilidade

**Status:** Aceita  
**Data:** 2026-02-05

## Contexto
O projeto utiliza dados provenientes de ambientes reais de Provedores de Internet de Pequeno Porte (PPPs), incluindo alertas de IDS e metadados de tráfego. Esses dados podem conter informações sensíveis (IPs, topologia, padrões de uso), exigindo cuidados com privacidade, ética e conformidade, sem comprometer a reprodutibilidade científica.

## Decisão
Será adotada uma política explícita de separação entre:
- **Dados reais sensíveis** (nunca versionados no Git)
- **Dados anonimizados ou agregados**
- **Dados sintéticos ou simulados**, utilizados para experimentos reproduzíveis

O repositório conterá apenas:
- código
- documentação
- scripts de processamento
- descrições metodológicas dos dados

## Justificativa
- **Privacidade e ética:** protege informações do provedor e de usuários finais.
- **Conformidade acadêmica:** evita riscos legais e institucionais.
- **Reprodutibilidade:** scripts e descrições permitem replicar experimentos com dados sintéticos.
- **Segurança operacional:** reduz superfície de exposição de dados reais.

## Alternativas consideradas
1. **Versionar dados reais anonimizados**  
2. **Versionar subconjuntos reais reduzidos**  
3. **Manter apenas dados reais, fora de versionamento, com documentação do processo**

## Consequências
- ✅ Repositório seguro para compartilhamento acadêmico
- ✅ Clareza metodológica para banca e artigos
- ✅ Possibilidade de abertura futura do código
- ⚠️ Requer esforço adicional para geração de dados sintéticos e documentação

## Relação com o projeto
Esta decisão orienta toda a estratégia de experimentação, publicação de resultados, escrita da dissertação e eventual disponibilização pública do artefato tecnológico.
