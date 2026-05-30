# CDU04 — Retirar Ativo

## 1. Nome do caso de uso

**Retirar Ativo**

## 2. Objetivo

Permitir que um Professor retire um ativo do CCT, vinculando o item ao responsável, sala, bloco, turno, data, horário e termo de responsabilidade.

## 3. Classificação

**Concreto**

## 4. Atores

| Ator | Classificação | Participação |
|---|---|---|
| Professor | Primário | Solicita ou confirma a retirada do ativo |
| Atendente do CCT | Secundário | Apoia a validação e libera o ativo |
| Sistema GAC | Secundário | Registra a retirada e atualiza o inventário |

## 5. Pré-condições

- O Professor deve possuir dados cadastrados.
- O ativo deve estar cadastrado no inventário.
- O ativo deve estar disponível.
- O Professor deve informar sala, bloco e turno.

## 6. Fluxo principal

**P1.** O Professor seleciona a opção **Retirar Ativo**.

**P2.** O sistema apresenta a tela de retirada.

**P3.** O Professor informa sala, bloco, turno e tipo de ativo desejado.

**P4.** O sistema consulta ativos disponíveis. **[E1]**

**P5.** O Professor seleciona o ativo ou solicita apoio do Atendente do CCT.

**P6.** O sistema inclui o caso de uso **Validar Patrimônio e Acessórios**. **[E2]**

**P7.** O sistema gera o termo de responsabilidade.

**P8.** O Professor assina digitalmente o termo.

**P9.** O sistema registra a retirada com data, hora, responsável, sala, bloco, turno e acessórios vinculados.

**P10.** O sistema inclui o caso de uso **Atualizar Inventário**.

**P11.** O sistema apresenta a mensagem: **IN03 — Ativo retirado com sucesso.**

**P12.** O caso de uso é encerrado.

## 7. Fluxos alternativos

### A1 — Atendente registra retirada em nome do Professor

**A1.1.** No passo **P1**, o Atendente do CCT seleciona a opção **Retirar Ativo**.

**A1.2.** O Atendente do CCT localiza o cadastro do Professor.

**A1.3.** O sistema apresenta os dados do Professor.

**A1.4.** O Atendente do CCT informa os dados da retirada.

**A1.5.** O sistema segue para o passo **P4**.

### A2 — Professor precisa atualizar dados

**A2.1.** No passo **P3**, o sistema identifica dados cadastrais desatualizados.

**A2.2.** O sistema solicita atualização cadastral.

**A2.3.** O sistema inclui o caso de uso **Cadastrar Dados**.

**A2.4.** O sistema retorna ao passo **P3**.

## 8. Fluxos de exceção

### E1 — Nenhum ativo disponível

**E1.1.** No passo **P4**, o sistema não encontra ativo disponível.

**E1.2.** O sistema apresenta a mensagem: **ER07 — Não há ativo disponível para retirada.**

**E1.3.** O caso de uso é encerrado.

### E2 — Patrimônio ou acessórios inválidos

**E2.1.** No passo **P6**, o sistema identifica divergência na validação do patrimônio ou dos acessórios.

**E2.2.** O sistema apresenta a mensagem: **ER08 — Patrimônio ou acessórios divergentes.**

**E2.3.** O sistema retorna ao passo **P5**.

### E3 — Termo não assinado

**E3.1.** No passo **P8**, o Professor não assina o termo de responsabilidade.

**E3.2.** O sistema apresenta a mensagem: **ER09 — A retirada depende do aceite do termo de responsabilidade.**

**E3.3.** O caso de uso é encerrado.

## 9. Pós-condições

- A retirada fica registrada.
- O ativo fica vinculado ao Professor.
- O inventário é atualizado para **Emprestado**.
- O termo de responsabilidade fica armazenado.

## 10. Requisitos não funcionais aplicáveis

- O registro deve ser rápido para reduzir filas.
- O sistema deve manter rastreabilidade entre Professor, ativo, sala, data, horário e acessórios.
- O termo assinado deve ser armazenado com segurança.

## 11. Pontos de inclusão

| Ponto | Caso incluído |
|---|---|
| P6 | **Validar Patrimônio e Acessórios** |
| P10 | **Atualizar Inventário** |

## 12. Frequência

**Alta**, pois representa uma das principais operações do GAC.
