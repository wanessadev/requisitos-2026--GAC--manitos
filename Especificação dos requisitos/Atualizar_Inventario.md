# CDU03 — Atualizar Inventário

## 1. Nome do caso de uso

**Atualizar Inventário**

## 2. Objetivo

Permitir que o Atendente do CCT ou a Coordenação do CCT atualize informações dos ativos, como status, localização, estado de conservação, disponibilidade e vínculo com acessórios.

## 3. Classificação

**Concreto**

## 4. Atores

| Ator | Classificação | Participação |
|---|---|---|
| Atendente do CCT | Primário | Atualiza dados operacionais dos ativos |
| Coordenação do CCT | Primário | Atualiza ou acompanha dados patrimoniais |
| Sistema GAC | Secundário | Valida, salva e registra alterações |

## 5. Pré-condições

- O ativo deve estar cadastrado no sistema.
- O usuário deve possuir permissão para alterar dados de inventário.
- O motivo da atualização deve estar definido quando houver alteração de status.

## 6. Fluxo principal

**P1.** O Atendente do CCT seleciona a opção **Atualizar Inventário**.

**P2.** O sistema apresenta a tela de consulta de ativos.

**P3.** O Atendente do CCT pesquisa o ativo por patrimônio, QR Code, NFC, tipo ou localização.

**P4.** O sistema apresenta os dados atuais do ativo. **[E1]**

**P5.** O Atendente do CCT altera as informações necessárias, como status, localização, acessórios vinculados ou estado físico.

**P6.** O sistema valida os dados alterados.

**P7.** O sistema salva a atualização.

**P8.** O sistema registra histórico de alteração.

**P9.** O sistema apresenta a mensagem: **IN02 — Inventário atualizado com sucesso.**

**P10.** O caso de uso é encerrado.

## 7. Fluxos alternativos

### A1 — Atualização automática após retirada

**A1.1.** No passo **P1**, o caso de uso é iniciado pelo sistema após a retirada de ativo.

**A1.2.** O sistema altera o status do ativo para **Emprestado**.

**A1.3.** O sistema vincula o ativo ao professor responsável.

**A1.4.** O sistema segue para o passo **P8**.

### A2 — Atualização automática após devolução

**A2.1.** No passo **P1**, o caso de uso é iniciado pelo sistema após registro de devolução.

**A2.2.** O sistema altera o status do ativo para **Disponível**, **Com Pendência** ou **Em Manutenção**.

**A2.3.** O sistema segue para o passo **P8**.

### A3 — Ativo enviado para manutenção

**A3.1.** No passo **P5**, o Atendente do CCT informa que o ativo apresenta defeito.

**A3.2.** O sistema altera o status para **Em Manutenção**.

**A3.3.** O sistema remove o ativo da lista de disponíveis.

**A3.4.** O sistema segue para o passo **P8**.

## 8. Fluxos de exceção

### E1 — Ativo não encontrado

**E1.1.** No passo **P4**, o sistema não localiza ativo com os critérios informados.

**E1.2.** O sistema apresenta a mensagem: **ER05 — Ativo não encontrado.**

**E1.3.** O sistema retorna ao passo **P2**.

### E2 — Alteração inválida de status

**E2.1.** No passo **P6**, o sistema identifica alteração incompatível com a situação do ativo.

**E2.2.** O sistema apresenta a mensagem: **ER06 — Status incompatível com a situação atual do ativo.**

**E2.3.** O sistema retorna ao passo **P5**.

## 9. Pós-condições

- O inventário fica atualizado.
- O histórico da alteração fica registrado.
- O status do ativo passa a refletir sua condição real.
- Ativos indisponíveis deixam de aparecer para retirada.

## 10. Requisitos não funcionais aplicáveis

- A consulta ao inventário deve responder rapidamente.
- As alterações devem ser auditáveis.
- O sistema deve evitar inconsistência entre status, localização e responsável.

## 11. Pontos de inclusão

| Ponto | Caso relacionado |
|---|---|
| A1 | Pode ser acionado por **Retirar Ativo** |
| A2 | Pode ser acionado por **Registrar Devolução** |
| A3 | Pode ser acionado por **Registrar Ocorrência** |

## 12. Frequência

**Alta**, pois o inventário sustenta a rastreabilidade e a disponibilidade dos ativos.
