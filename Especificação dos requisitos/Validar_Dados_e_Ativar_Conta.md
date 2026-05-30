# CDU01 — Validar Dados e Ativar Conta

## 1. Nome do caso de uso

**Validar Dados e Ativar Conta**

## 2. Objetivo

Permitir que o sistema valide os dados informados no cadastro e ative a conta do usuário somente quando as informações obrigatórias estiverem corretas e consistentes.

## 3. Classificação

**Abstrato**, pois é incluído por outro caso de uso, principalmente **Cadastrar Dados**.

## 4. Atores

| Ator | Classificação | Participação |
|---|---|---|
| Sistema GAC | Primário técnico | Executa a validação e ativa a conta |
| Professor | Secundário | Recebe a conta ativa após cadastro |
| Atendente do CCT | Secundário | Pode ter seus dados validados pela Coordenação |
| Coordenação do CCT | Secundário | Pode validar contas administrativas |

## 5. Pré-condições

- O caso de uso deve ter sido instanciado por outro caso de uso.
- Os dados mínimos do usuário devem ter sido preenchidos.
- O tipo de usuário deve estar informado: Professor, Atendente do CCT ou Coordenação do CCT.

## 6. Fluxo principal

**P1.** O sistema recebe os dados cadastrados pelo usuário ou pelo responsável administrativo.

**P2.** O sistema verifica se os campos obrigatórios foram preenchidos.

**P3.** O sistema valida o formato dos dados informados, como nome, matrícula, e-mail institucional, setor e perfil de acesso.

**P4.** O sistema verifica se já existe conta cadastrada com a mesma matrícula ou e-mail institucional. **[E1]**

**P5.** O sistema verifica se o perfil selecionado está compatível com o tipo de usuário.

**P6.** O sistema registra a conta como validada.

**P7.** O sistema ativa a conta do usuário.

**P8.** O sistema apresenta mensagem de confirmação.

**P9.** O sistema retorna ao caso de uso chamador.

## 7. Fluxos alternativos

### A1 — Conta exige aprovação administrativa

**A1.1.** No passo **P6**, o sistema identifica que o perfil solicitado exige aprovação da Coordenação do CCT.

**A1.2.** O sistema registra a conta com status **Pendente de Aprovação**.

**A1.3.** O sistema notifica a Coordenação do CCT.

**A1.4.** O caso de uso é encerrado.

### A2 — Dados incompletos podem ser corrigidos

**A2.1.** No passo **P2**, o sistema identifica campos obrigatórios não preenchidos.

**A2.2.** O sistema apresenta os campos pendentes.

**A2.3.** O usuário corrige os dados.

**A2.4.** O sistema retorna ao passo **P2**.

## 8. Fluxos de exceção

### E1 — Conta já cadastrada

**E1.1.** No passo **P4**, o sistema identifica matrícula ou e-mail já existente.

**E1.2.** O sistema apresenta a mensagem: **ER01 — Já existe uma conta cadastrada com estes dados.**

**E1.3.** O caso de uso é encerrado.

### E2 — Perfil inválido

**E2.1.** No passo **P5**, o sistema identifica perfil incompatível com o tipo de usuário.

**E2.2.** O sistema apresenta a mensagem: **ER02 — Perfil de acesso incompatível com o tipo de usuário.**

**E2.3.** O sistema retorna ao caso de uso chamador.

## 9. Pós-condições

- A conta é ativada quando os dados são válidos.
- A conta fica pendente quando exige aprovação administrativa.
- A tentativa de cadastro inválida fica registrada para auditoria.

## 10. Requisitos não funcionais aplicáveis

- A validação deve ocorrer em tempo adequado para não gerar filas no atendimento.
- O sistema deve proteger os dados pessoais cadastrados.
- O sistema deve registrar data, hora e responsável pela ativação da conta.

## 11. Pontos de inclusão

| Ponto | Caso de uso relacionado |
|---|---|
| P1 | Incluído por **Cadastrar Dados** |

## 12. Frequência

**Alta**, pois toda conta precisa ser validada antes do uso do sistema.
