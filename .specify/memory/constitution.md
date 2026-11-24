<!--
Sync Impact Report
- Version change: 0.0.0 → 1.0.0
- Modified principles: Template placeholders → five project principles
- Added sections:
  - Core Principles
  - Quality and Delivery Constraints
  - Development Workflow
  - Governance
- Removed sections: None
- Follow-up TODOs: None
-->

# My Project Constitution

## Core Principles

### I. Simple and Justified Solutions

Implementações MUST preferir a solução mais simples que atenda integralmente aos
requisitos. Toda nova dependência MUST possuir justificativa explícita e MUST
ser evitada quando a funcionalidade existente ou uma implementação local
equivalente for suficiente, confiável e mais fácil de manter.

**Racional**: simplicidade reduz custo cognitivo, superfície de falhas e esforço
de manutenção.

### II. Clear and Stable Interfaces

As ações principais expostas pelo projeto MUST seguir contratos coerentes e
previsíveis. Interfaces, argumentos, resultados e mensagens de erro MUST manter
o padrão adotado pelo projeto, e alterações incompatíveis MUST ser documentadas
e versionadas.

**Racional**: contratos consistentes permitem uso confiável e evitam
comportamentos específicos de implementação.

### III. Validation-Ready and Unambiguous Input

Entradas MUST ser explícitas, inequívocas e acompanhadas de mensagens claras
quando inválidas. Regras de validação MUST ser definidas no limite das
interfaces antes do processamento principal, sem conversões silenciosas ou
valores substitutos que ocultem erros.

**Racional**: mensagens objetivas e rejeição antecipada tornam falhas
compreensíveis e reproduzíveis.

### IV. Automated Validation, Rules, and Filtering

Alterações MUST ser acompanhadas de testes automatizados para as regras de
negócio e os filtros aplicados aos dados ou resultados. Casos válidos,
inválidos e de fronteira relevantes MUST ser cobertos antes que a alteração seja
considerada concluída.

**Racional**: automação impede regressões e demonstra que validação e filtros
preservam o comportamento esperado.

### V. Continuous Requirement and Implementation Coherence

Requisitos, implementação, testes e documentação MUST permanecer consistentes.
Toda alteração de comportamento MUST atualizar as superfícies afetadas no mesmo
ciclo de entrega; divergências detectadas MUST bloquear a conclusão do trabalho
até serem resolvidas ou formalmente registradas como dívida aprovada.

**Racional**: coerência contínua mantém o projeto compreensível e reduz
discrepâncias entre a especificação e o sistema entregue.

## Quality and Delivery Constraints

- Nenhuma alteração pode introduzir dependência sem justificar sua necessidade,
  avaliar alternativas existentes e registrar o impacto de manutenção.
- A implementação deve expor falhas de forma explícita; silenciosamente ignorar
  erros, usar retornos bem-sucedidos para falhas ou produzir valores parciais
  inválidos é proibido.
- Regras de validação e filtragem MUST possuir testes automatizados reproduzíveis.
- Comentários, documentação e mensagens ao usuário MUST estar alinhados ao
  comportamento efetivamente implementado.
- Complexidade adicional MUST ser sustentada por requisito mensurável ou
  restrição técnica demonstrada.

## Development Workflow

1. Definir requisitos e critérios de aceitação antes da implementação.
2. Projetar ou ajustar a interface, incluindo entradas inválidas e mensagens de
   erro.
3. Implementar testes automatizados que demonstrem os resultados esperados.
4. Realizar a menor implementação simples que satisfaça testes e requisitos.
5. Executar validação focada e, quando aplicável, a suíte completa do projeto.
6. Revisar requisitos, código, testes e documentação em conjunto antes da
   conclusão.

Revisões MUST verificar explicitamente aderência aos cinco princípios desta
constituição. Exceções MUST registrar requisito, impacto, responsáveis e plano
de remoção ou revisão.

## Governance

Esta constituição prevalece sobre práticas locais conflitantes. Alterações
constitucionais MUST ser realizadas por meio de proposta documentada contendo
motivação, impacto e, quando necessário, plano de migração. A revisão de
conformidade MUST ocorrer em toda proposta ou alteração que afete requisitos,
interfaces, dependências, validações ou filtros.

O versionamento segue semver para governança:

- MAJOR: remoção ou redefinição incompatível de princípio ou obrigação;
- MINOR: novo princípio, seção ou expansão material de orientação;
- PATCH: esclarecimento, correção textual ou refinamento sem mudança semântica.

Toda revisão concluída MUST confirmar a aderência ou registrar as exceções
aprovadas. A data da última alteração MUST acompanhar qualquer emenda.

**Version**: 1.0.0 | **Ratified**: 2026-11-24 | **Last Amended**: 2026-11-24
