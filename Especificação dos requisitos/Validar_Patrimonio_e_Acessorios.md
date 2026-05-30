# CDU05 — Validar Patrimônio e Acessórios

## 1. Nome do caso de uso

**Validar Patrimônio e Acessórios**

## 2. Objetivo

Permitir a validação do patrimônio do ativo e de seus acessórios, garantindo que o item físico corresponda ao registro do sistema.

## 3. Classificação

**Concreto reutilizável**, pois pode ser iniciado pelo Atendente do CCT ou incluído por outro caso de uso, como **Retirar Ativo**.

## 4. Atores

| Ator | Classificação | Participação |
|---|---|---|
| Atendente do CCT | Primário | Realiza a conferência física |
| Sistema GAC | Secundário | Consulta e compara dados |
| Leitor QR/NFC | Secundário | Lê o identificador do ativo |

## 5. Pré-condições

- O ativo deve estar fisicamente disponível para conferência.
- O ativo deve possuir identificação patrimonial cadastrada.
- Os acessórios vinculados devem estar registrados no sistema.

## 6. Fluxo principal

**P1.** O Atendente do CCT seleciona a opção **Validar Patrimônio e Acessórios**.

**P2.** O sistema solicita leitura do QR Code, NFC ou inserção manual do patrimônio.

**P3.** O Atendente do CCT informa ou escaneia o identificador do ativo.

**P4.** O sistema consulta o registro do ativo no inventário. **[E1]**

**P5.** O sistema apresenta tipo, patrimônio, status, localização e acessórios esperados.

**P6.** O Atendente do CCT confere o ativo físico e os acessórios.

**P7.** O Atendente do CCT confirma que o patrimônio e os acessórios estão corretos. **[A1] [E2]**

**P8.** O sistema registra a validação.

**P9.** O sistema apresenta a mensagem: **IN04 — Patrimônio e acessórios validados.**

**P10.** O caso de uso é encerrado ou retorna ao caso de uso chamador.

## 7. Fluxos alternativos

### A1 — Validação manual sem QR Code ou NFC

**A1.1.** No passo **P3**, o Atendente do CCT informa que a leitura automática não está disponível.

**A1.2.** O sistema habilita campo para digitação manual do patrimônio.

**A1.3.** O Atendente do CCT informa o código patrimonial.

**A1.4.** O sistema segue para o passo **P4**.

### A2 — Acessório substituído

**A2.1.** No passo **P7**, o Atendente do CCT identifica que um acessório foi substituído por outro equivalente.

**A2.2.** O sistema solicita justificativa.

**A2.3.** O Atendente do CCT informa a justificativa.

**A2.4.** O sistema registra a alteração e segue para o passo **P8**.

## 8. Fluxos de exceção

### E1 — Patrimônio não encontrado

**E1.1.** No passo **P4**, o sistema não encontra o patrimônio informado.

**E1.2.** O sistema apresenta a mensagem: **ER10 — Patrimônio não encontrado no inventário.**

**E1.3.** O sistema retorna ao passo **P2**.

### E2 — Acessório divergente ou ausente

**E2.1.** No passo **P7**, o Atendente do CCT identifica acessório ausente, divergente ou danificado.

**E2.2.** O sistema apresenta a mensagem: **ER11 — Acessório ausente, divergente ou danificado.**

**E2.3.** O sistema solicita registro de ocorrência.

**E2.4.** O sistema inclui o caso de uso **Registrar Ocorrência**.

**E2.5.** O caso de uso é encerrado.

## 9. Pós-condições

- O patrimônio é confirmado como válido.
- Os acessórios são confirmados ou a divergência é registrada.
- A validação fica vinculada à retirada ou devolução correspondente.

## 10. Requisitos não funcionais aplicáveis

- A leitura por QR Code ou NFC deve ser rápida.
- A validação deve funcionar também por entrada manual.
- O sistema deve manter histórico de validações.

## 11. Pontos de inclusão

| Ponto | Caso relacionado |
|---|---|
| P1 | Pode ser incluído por **Retirar Ativo** |
| E2.4 | Inclui **Registrar Ocorrência** |

## 12. Frequência

**Alta**, pois a validação ocorre nas retiradas e pode ocorrer nas devoluções.
