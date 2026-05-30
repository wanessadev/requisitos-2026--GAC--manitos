# CDU02 — Cadastrar Dados

## 1. Nome do caso de uso

**Cadastrar Dados**

## 2. Objetivo

Permitir o cadastro de informações necessárias para operação do GAC, incluindo dados de usuários, professores e registros básicos vinculados ao controle de ativos.

## 3. Classificação

**Concreto**

## 4. Atores

| Ator | Classificação | Participação |
|---|---|---|
| Professor | Primário | Cadastra ou atualiza seus dados básicos |
| Atendente do CCT | Primário | Cadastra dados operacionais quando autorizado |
| Coordenação do CCT | Secundário | Pode validar dados administrativos |
| Sistema GAC | Secundário | Valida e armazena os dados |

## 5. Pré-condições

- O usuário deve acessar a opção de cadastro.
- Os dados mínimos exigidos devem estar disponíveis.
- O perfil a ser cadastrado deve estar definido.

## 6. Fluxo principal

**P1.** O Professor seleciona a opção **Cadastrar Dados**.

**P2.** O sistema apresenta o formulário de cadastro.

**P3.** O Professor informa nome, matrícula, setor, e-mail institucional e contato.

**P4.** O Professor seleciona a opção **Salvar**.

**P5.** O sistema verifica se os campos obrigatórios foram preenchidos. **[E1]**

**P6.** O sistema inclui o caso de uso **Validar Dados e Ativar Conta**.

**P7.** O sistema armazena os dados cadastrados.

**P8.** O sistema apresenta a mensagem: **IN01 — Dados cadastrados com sucesso.**

**P9.** O caso de uso é encerrado.

## 7. Fluxos alternativos

### A1 — Atendente cadastra dados de usuário

**A1.1.** No passo **P1**, o Atendente do CCT seleciona a opção **Cadastrar Dados**.

**A1.2.** O sistema apresenta o formulário administrativo.

**A1.3.** O Atendente do CCT informa os dados do usuário.

**A1.4.** O sistema segue para o passo **P5**.

### A2 — Usuário atualiza dados existentes

**A2.1.** No passo **P2**, o sistema identifica que já existem dados cadastrados.

**A2.2.** O sistema apresenta os dados atuais preenchidos.

**A2.3.** O usuário altera as informações permitidas.

**A2.4.** O sistema segue para o passo **P4**.

## 8. Fluxos de exceção

### E1 — Campos obrigatórios não preenchidos

**E1.1.** No passo **P5**, o sistema identifica ausência de campo obrigatório.

**E1.2.** O sistema apresenta a mensagem: **ER03 — Preencha todos os campos obrigatórios.**

**E1.3.** O sistema retorna ao passo **P2**.

### E2 — Dados duplicados

**E2.1.** No passo **P6**, o sistema identifica matrícula ou e-mail já cadastrado.

**E2.2.** O sistema apresenta a mensagem: **ER04 — Dados já cadastrados no sistema.**

**E2.3.** O sistema retorna ao passo **P2**.

## 9. Pós-condições

- Os dados ficam cadastrados ou atualizados.
- A conta fica ativa ou pendente de validação.
- O registro fica disponível para uso nos fluxos de retirada, devolução e auditoria.

## 10. Requisitos não funcionais aplicáveis

- O formulário deve ser simples e objetivo.
- Os dados pessoais devem ser protegidos.
- O sistema deve evitar duplicidade de usuários.

## 11. Pontos de inclusão

| Ponto | Caso incluído |
|---|---|
| P6 | **Validar Dados e Ativar Conta** |

## 12. Frequência

**Média**, conforme a visão do GAC para cadastro de dados do professor.
