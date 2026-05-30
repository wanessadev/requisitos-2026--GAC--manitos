# CDU08 — Registrar Ocorrência

## 1. Nome do caso de uso

**Registrar Ocorrência**

## 2. Objetivo

Permitir o registro de problemas, atrasos, danos, perdas, falta de acessórios ou inconsistências relacionadas a ativos, retiradas ou devoluções.

## 3. Classificação

**Concreto**

## 4. Atores

| Ator | Classificação | Participação |
|---|---|---|
| Atendente do CCT | Primário | Registra ocorrências operacionais |
| Coordenação do CCT | Primário | Registra ou acompanha ocorrências gerenciais |
| Sistema GAC | Secundário | Armazena e vincula a ocorrência |

## 5. Pré-condições

- Deve existir um ativo, retirada, devolução ou usuário relacionado à ocorrência.
- O tipo de ocorrência deve ser identificado.
- O responsável pelo registro deve informar uma descrição mínima.

## 6. Fluxo principal

**P1.** O Atendente do CCT seleciona a opção **Registrar Ocorrência**.

**P2.** O sistema apresenta o formulário de ocorrência.

**P3.** O Atendente do CCT informa o ativo, Professor, retirada ou devolução relacionada.

**P4.** O sistema apresenta os tipos de ocorrência disponíveis: dano, falha, atraso, falta de acessório, extravio, não devolução ou divergência.

**P5.** O Atendente do CCT seleciona o tipo de ocorrência.

**P6.** O Atendente do CCT informa a descrição da ocorrência e, quando necessário, anexa evidência.

**P7.** O sistema valida os dados obrigatórios. **[E1]**

**P8.** O sistema registra a ocorrência com data, hora, responsável e vínculo com o ativo.

**P9.** O sistema atualiza a situação do ativo quando aplicável. **[A1]**

**P10.** O sistema apresenta a mensagem: **IN07 — Ocorrência registrada com sucesso.**

**P11.** O caso de uso é encerrado.

## 7. Fluxos alternativos

### A1 — Ocorrência altera status do ativo

**A1.1.** No passo **P9**, o sistema identifica que a ocorrência impede novo uso do ativo.

**A1.2.** O sistema altera o status do ativo para **Com Pendência** ou **Em Manutenção**.

**A1.3.** O sistema inclui o caso de uso **Atualizar Inventário**.

**A1.4.** O sistema segue para o passo **P10**.

### A2 — Coordenação registra ocorrência gerencial

**A2.1.** No passo **P1**, a Coordenação do CCT seleciona a opção **Registrar Ocorrência**.

**A2.2.** O sistema apresenta o formulário com campos gerenciais.

**A2.3.** A Coordenação do CCT informa a ocorrência.

**A2.4.** O sistema segue para o passo **P7**.

### A3 — Ocorrência aberta automaticamente

**A3.1.** No passo **P1**, o sistema inicia o registro a partir de checklist com pendência ou devolução em atraso.

**A3.2.** O sistema preenche automaticamente os dados já conhecidos.

**A3.3.** O Atendente do CCT complementa a descrição.

**A3.4.** O sistema segue para o passo **P7**.

## 8. Fluxos de exceção

### E1 — Dados obrigatórios ausentes

**E1.1.** No passo **P7**, o sistema identifica ausência de tipo, descrição ou vínculo da ocorrência.

**E1.2.** O sistema apresenta a mensagem: **ER15 — Informe os dados obrigatórios da ocorrência.**

**E1.3.** O sistema retorna ao passo **P2**.

### E2 — Ativo relacionado não encontrado

**E2.1.** No passo **P3**, o sistema não localiza o ativo informado.

**E2.2.** O sistema apresenta a mensagem: **ER16 — Ativo relacionado não encontrado.**

**E2.3.** O sistema retorna ao passo **P3**.

## 9. Pós-condições

- A ocorrência fica registrada.
- A ocorrência fica vinculada ao ativo, retirada, devolução ou usuário relacionado.
- O status do ativo pode ser atualizado.
- A Coordenação do CCT pode consultar a ocorrência em relatórios ou dashboard.

## 10. Requisitos não funcionais aplicáveis

- A ocorrência deve ser rastreável.
- O sistema deve registrar data, hora e usuário responsável.
- O sistema deve permitir consulta posterior para auditoria.

## 11. Pontos de inclusão

| Ponto | Caso relacionado |
|---|---|
| A1.3 | **Atualizar Inventário** |
| A3 | Pode ser acionado por **Executar Checklist de Devolução** ou **Registrar Devolução** |

## 12. Frequência

**Média**, com valor alto para controle patrimonial e auditoria.
