# Feature Specification: Personal Study Topics

**Feature Branch**: `001-personal-study-topics`

**Created**: 2026-11-24

**Status**: Draft

**Input**: User description: "Crie uma lista pessoal de estudos. A pessoa pode
cadastrar um tópico com título obrigatório, marcar e desmarcar sua conclusão e
filtrar todos, pendentes ou concluídos. Os tópicos permanecem após recarregar a
página. Mostrar mensagens quando a lista ou o filtro estiver vazio. Não haverá
contas, compartilhamento ou sincronização. Descreva histórias e critérios de
aceitação verificáveis."

## User Scenarios & Testing *(mandatory)*

### User Story 1 - Cadastrar e acompanhar tópicos (Priority: P1)

Como estudante, quero cadastrar tópicos com um título obrigatório para manter
uma lista pessoal clara do que preciso estudar.

**Why this priority**: Sem cadastro e visualização de tópicos, a lista não
entrega seu valor principal.

**Independent Test**: Pode ser totalmente testada ao criar um tópico válido,
recarregar a página e confirmar que o título e o estado pendente permanecem na
lista.

**Acceptance Scenarios**:

1. **Given** que a lista está disponível, **When** a pessoa informa um título
   válido e confirma o cadastro, **Then** o tópico aparece uma única vez na
   lista como pendente.
2. **Given** que nenhum título foi informado ou que ele contém somente espaços,
   **When** a pessoa tenta cadastrar, **Then** o cadastro é recusado e uma
   mensagem de validação clara é exibida sem criar um tópico.
3. **Given** que existem tópicos cadastrados, **When** a página é recarregada,
   **Then** todos os tópicos permanecem disponíveis com seus títulos e estados
   atuais.

---

### User Story 2 - Marcar e desfazer conclusão (Priority: P1)

Como estudante, quero marcar um tópico como concluído e também reabri-lo para
refletir corretamente meu progresso de estudo.

**Why this priority**: O estado de conclusão é a principal forma de acompanhar
e corrigir o avanço da lista.

**Independent Test**: Pode ser totalmente testada ao alternar um tópico de
pendente para concluído, recarregar a página e retornar o tópico ao estado
pendente.

**Acceptance Scenarios**:

1. **Given** um tópico pendente, **When** a pessoa o marca como concluído,
   **Then** seu estado muda imediatamente para concluído.
2. **Given** um tópico concluído, **When** a pessoa desmarca sua conclusão,
   **Then** seu estado volta para pendente.
3. **Given** um tópico cujo estado foi alterado, **When** a página é recarregada,
   **Then** o estado mais recente permanece.

---

### User Story 3 - Filtrar por estado (Priority: P2)

Como estudante, quero visualizar todos os tópicos, apenas os pendentes ou apenas
os concluídos para concentrar minha atenção no conjunto relevante.

**Why this priority**: Os filtros tornam a lista útil à medida que cresce, mas
dependem do cadastro e dos estados definidos nas histórias prioritárias.

**Independent Test**: Pode ser totalmente testada com tópicos pendentes e
concluídos ao selecionar cada filtro e conferir a coleção exibida.

**Acceptance Scenarios**:

1. **Given** tópicos pendentes e concluídos, **When** o filtro Todos é
   selecionado, **Then** todos os tópicos são exibidos.
2. **Given** tópicos pendentes e concluídos, **When** o filtro Pendentes é
   selecionado, **Then** somente tópicos pendentes são exibidos.
3. **Given** tópicos pendentes e concluídos, **When** o filtro Concluídos é
   selecionado, **Then** somente tópicos concluídos são exibidos.
4. **Given** um filtro ativo, **When** o estado de um tópico deixa de corresponder
   a esse filtro, **Then** o tópico deixa de aparecer no resultado atual.

---

### User Story 4 - Entender estados vazios (Priority: P3)

Como estudante, quero receber mensagens específicas quando a lista estiver
vazia ou quando o filtro atual não tiver resultados para entender que não houve
falha.

**Why this priority**: O estado vazio orienta o próximo passo e evita que a
ausência de itens seja confundida com um problema.

**Independent Test**: Pode ser totalmente testada primeiro com a lista sem
tópicos e depois com um filtro sem tópicos correspondentes.

**Acceptance Scenarios**:

1. **Given** que não existe nenhum tópico cadastrado, **When** a pessoa
   visualiza a lista, **Then** uma mensagem informa que a lista está vazia e
   sugere cadastrar o primeiro tópico.
2. **Given** que existem tópicos na lista, **When** o filtro atual não possui
   correspondências, **Then** uma mensagem específica informa que não há
   tópicos naquele filtro.

---

### Edge Cases

- Títulos com espaços no início ou no fim são normalizados para evitar títulos
  visualmente ambíguos.
- Títulos muito longos permanecem identificáveis sem alterar ou perder o valor
  informado pela pessoa.
- Títulos duplicados são permitidos porque não há requisito de unicidade e cada
  cadastro representa um tópico independente.
- Se todos os tópicos pendentes forem concluídos enquanto o filtro Pendentes
  estiver ativo, o filtro permanece selecionado e exibe sua mensagem vazia.
- Se todos os tópicos concluídos forem reabertos enquanto o filtro Concluídos
  estiver ativo, o filtro permanece selecionado e exibe sua mensagem vazia.
- Se os dados salvos forem inválidos ou não puderem ser lidos, a pessoa recebe
  uma mensagem clara em vez de uma confirmação falsa de sucesso ou conteúdo
  parcialmente incorreto.

## Requirements *(mandatory)*

### Functional Requirements

- **FR-001**: O sistema MUST permitir que uma pessoa cadastre um tópico
  informando seu título.
- **FR-002**: O sistema MUST exigir um título não vazio e MUST rejeitar valores
  formados somente por espaços.
- **FR-003**: Cada tópico recém-cadastrado MUST iniciar no estado pendente.
- **FR-004**: O sistema MUST permitir marcar um tópico pendente como concluído.
- **FR-005**: O sistema MUST permitir retornar um tópico concluído ao estado
  pendente.
- **FR-006**: O sistema MUST oferecer filtros para todos, pendentes e
  concluídos.
- **FR-007**: O filtro Todos MUST incluir todos os tópicos, e os demais filtros
  MUST incluir somente tópicos com o estado correspondente.
- **FR-008**: Alterações em filtros e estados MUST atualizar imediatamente a
  coleção visível.
- **FR-009**: O sistema MUST preservar tópicos, títulos e estados após
  recarregar a página.
- **FR-010**: Quando a lista completa estiver vazia, o sistema MUST exibir
  mensagem específica de lista vazia.
- **FR-011**: Quando o filtro selecionado não tiver correspondências, o sistema
  MUST exibir mensagem específica de filtro vazio.
- **FR-012**: O sistema MUST exibir uma mensagem clara quando o cadastro for
  recusado ou os dados persistidos não puderem ser lidos.
- **FR-013**: O sistema MUST manter a experiência restrita a uma lista pessoal,
  sem contas, login, compartilhamento entre pessoas ou sincronização entre
  dispositivos.
- **FR-014**: O sistema MUST operar sem exibir gráficos e MUST concentrar a
  experiência no cadastro, no acompanhamento de conclusão e na filtragem.

### Key Entities *(include if feature involves data)*

- **Tópico de estudo**: Item de estudo identificado por um título informado e
  por um estado de conclusão (pendente ou concluído).
- **Filtro de estado**: Preferência temporária de visualização que limita a
  lista a todos os itens, somente aos pendentes ou somente aos concluídos.

## Success Criteria *(mandatory)*

### Measurable Outcomes

- **SC-001**: Pelo menos 95% das pessoas conseguem cadastrar o primeiro tópico
  válido em até 30 segundos, sem ajuda externa.
- **SC-002**: 100% dos tópicos cadastrados mantêm título e estado corretos após
  um recarregamento da página nos testes de aceitação.
- **SC-003**: 100% dos resultados exibidos correspondem ao filtro selecionado
  em cenários com tópicos pendentes e concluídos.
- **SC-004**: Em 100% das tentativas com título vazio ou apenas espaços, nenhum
  tópico é criado e uma mensagem de validação é apresentada.
- **SC-005**: Pelo menos 90% das pessoas identificam, sem instrução adicional,
  se a lista está vazia ou se apenas o filtro atual não possui resultados.
- **SC-006**: A troca entre os estados pendente e concluído é percebida pela
  pessoa na mesma interação, sem necessidade de recarregar a página.

## Assumptions

- A lista é de uso individual neste navegador ou ambiente de uso e não depende
  de identidade, autenticação ou perfil de usuário.
- A persistência ocorre entre recarregamentos da mesma instância de uso; acesso a
  partir de outros dispositivos ou navegadores não compartilha dados.
- Não existe exclusão, edição, priorização, ordenação manual, categorias, prazos
  ou histórico temporal nesta versão.
- A seleção do filtro pode retornar ao estado padrão ao recarregar; somente os
  tópicos precisam permanecer.
- O título aceito preserva o conteúdo textual informado, com remoção apenas de
  espaços redundantes nas extremidades.
