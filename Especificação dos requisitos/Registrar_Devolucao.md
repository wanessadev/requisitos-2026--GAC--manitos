# CDU06 — Registrar Devolução

## 1. Nome do caso de uso

**Registrar Devolução**

## 2. Objetivo

Permitir que o Atendente do CCT registre o retorno de um ativo ao CCT, encerrando o ciclo de retirada e atualizando a situação do item.

## 3. Classificação

**Concreto**

## 4. Atores

| Ator | Classificação | Participação |
|---|---|---|
| Atendente do CCT | Primário | Registra a devolução |
| Professor | Secundário | Entrega o ativo |
| Sistema GAC | Secundário | Atualiza registros e inventário |

## 5. Pré-condições

- Deve existir uma retirada ativa para o ativo.
- O Professor deve apresentar o ativo para devolução.
- O ativo deve estar identificado por patrimônio, QR Code, NFC ou seleção manual.

## 6. Fluxo principal

**P1.** O Atendente do CCT seleciona a opção **Registrar Devolução**.

**P2.** O sistema apresenta a tela de busca de retirada ativa.

**P3.** O Atendente do CCT informa ou escaneia o patrimônio do ativo.

**P4.** O sistema localiza a retirada ativa vinculada ao ativo. **[E1]**

**P5.** O sistema apresenta os dados da retirada: Professor, sala, bloco, turno, data, horário e acessórios esperados.

**P6.** O sistema inclui o caso de uso **Executar Checklist de Devolução**. **[E2]**

**P7.** O Atendente do CCT confirma a devolução.

**P8.** O sistema registra data e hora da devolução.

**P9.** O sistema inclui o caso de uso **Atualizar Inventário**.

**P10.** O sistema apresenta a mensagem: **IN05 — Devolução registrada com sucesso.**

**P11.** O caso de uso é encerrado.

## 7. Fluxos alternativos

### A1 — Devolução com pendência

**A1.1.** No passo **P6**, o checklist identifica pendência.

**A1.2.** O sistema registra a devolução com status **Com Pendência**.

**A1.3.** O sistema inclui o caso de uso **Registrar Ocorrência**.

**A1.4.** O sistema segue para o passo **P8**.

### A2 — Devolução fora do prazo

**A2.1.** No passo **P5**, o sistema identifica atraso na devolução.

**A2.2.** O sistema informa o atraso ao Atendente do CCT.

**A2.3.** O sistema inclui o caso de uso **Registrar Ocorrência**.

**A2.4.** O sistema segue para o passo **P6**.

## 8. Fluxos de exceção

### E1 — Retirada ativa não encontrada

**E1.1.** No passo **P4**, o sistema não encontra retirada ativa para o ativo.

**E1.2.** O sistema apresenta a mensagem: **ER12 — Não existe retirada ativa para este ativo.**

**E1.3.** O caso de uso é encerrado.

### E2 — Checklist não concluído

**E2.1.** No passo **P6**, o checklist não é concluído.

**E2.2.** O sistema apresenta a mensagem: **ER13 — A devolução depende da conclusão do checklist.**

**E2.3.** O sistema retorna ao passo **P6**.

## 9. Pós-condições

- A devolução fica registrada.
- O ciclo de retirada é encerrado.
- O inventário é atualizado.
- Pendências, atrasos ou danos ficam registrados como ocorrência.

## 10. Requisitos não funcionais aplicáveis

- O registro de devolução deve ser rápido.
- O sistema deve manter histórico de devoluções.
- O sistema deve permitir rastrear responsável, ativo e horário da devolução.

## 11. Pontos de inclusão

| Ponto | Caso incluído |
|---|---|
| P6 | **Executar Checklist de Devolução** |
| P9 | **Atualizar Inventário** |
| A1.3 / A2.3 | **Registrar Ocorrência** |

## 12. Frequência

**Alta**, pois toda retirada deve terminar com uma devolução.
