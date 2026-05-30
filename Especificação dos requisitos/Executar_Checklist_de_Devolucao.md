# CDU07 — Executar Checklist de Devolução

## 1. Nome do caso de uso

**Executar Checklist de Devolução**

## 2. Objetivo

Permitir que o Atendente do CCT confira se o ativo devolvido está em boas condições e acompanhado dos acessórios esperados.

## 3. Classificação

**Concreto reutilizável**, pois pode ser iniciado diretamente pelo Atendente do CCT ou incluído por **Registrar Devolução**.

## 4. Atores

| Ator | Classificação | Participação |
|---|---|---|
| Atendente do CCT | Primário | Executa a conferência |
| Sistema GAC | Secundário | Apresenta itens esperados e registra resultado |

## 5. Pré-condições

- O ativo deve estar em processo de devolução.
- O sistema deve possuir a lista de acessórios vinculados ao ativo.
- O Atendente do CCT deve ter acesso ao ativo físico.

## 6. Fluxo principal

**P1.** O Atendente do CCT seleciona a opção **Executar Checklist de Devolução**.

**P2.** O sistema apresenta os itens esperados para devolução.

**P3.** O sistema apresenta campos para conferência de equipamento, cabo HDMI, fonte, adaptador, identificação numérica dos acessórios e estado físico.

**P4.** O Atendente do CCT confere cada item físico.

**P5.** O Atendente do CCT marca os itens como **Conforme**.

**P6.** O sistema valida se todos os itens obrigatórios foram marcados. **[E1]**

**P7.** O sistema registra o checklist como concluído.

**P8.** O sistema apresenta a mensagem: **IN06 — Checklist concluído com sucesso.**

**P9.** O sistema retorna ao caso de uso chamador.

## 7. Fluxos alternativos

### A1 — Item devolvido com dano

**A1.1.** No passo **P5**, o Atendente do CCT marca um item como **Danificado**.

**A1.2.** O sistema solicita descrição do dano.

**A1.3.** O Atendente do CCT informa a descrição.

**A1.4.** O sistema inclui o caso de uso **Registrar Ocorrência**.

**A1.5.** O sistema registra o checklist como **Concluído com Pendência**.

**A1.6.** O sistema retorna ao caso de uso chamador.

### A2 — Item ausente ou divergente

**A2.1.** No passo **P5**, o Atendente do CCT marca um item como **Ausente** ou **Divergente**.

**A2.2.** O sistema solicita justificativa.

**A2.3.** O Atendente do CCT informa a justificativa.

**A2.4.** O sistema inclui o caso de uso **Registrar Ocorrência**.

**A2.5.** O sistema registra o checklist como **Concluído com Pendência**.

**A2.6.** O sistema retorna ao caso de uso chamador.

## 8. Fluxos de exceção

### E1 — Checklist incompleto

**E1.1.** No passo **P6**, o sistema identifica item obrigatório sem conferência.

**E1.2.** O sistema apresenta a mensagem: **ER14 — Todos os itens obrigatórios devem ser conferidos.**

**E1.3.** O sistema retorna ao passo **P3**.

## 9. Pós-condições

- O checklist fica registrado.
- O resultado da conferência fica vinculado à devolução.
- Pendências geram ocorrência.
- Devolução incompleta pode ser bloqueada ou registrada com pendência, conforme regra definida.

## 10. Requisitos não funcionais aplicáveis

- A tela de checklist deve ser objetiva.
- O sistema deve destacar itens obrigatórios.
- O checklist deve ser auditável.

## 11. Pontos de inclusão

| Ponto | Caso relacionado |
|---|---|
| P1 | Pode ser incluído por **Registrar Devolução** |
| A1.4 / A2.4 | Inclui **Registrar Ocorrência** |

## 12. Frequência

**Alta**, pois deve ocorrer em cada devolução de ativo.
