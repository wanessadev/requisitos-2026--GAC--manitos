# Especificação de Requisitos Funcionais

## Caso de Uso (CDU) - GAC

---

## Histórico de Versões

| Data       | Versão | Descrição | Autor |
|------------|--------|-----------|-------|
| 30/05/2026 | 1.0 | Criação da especificação do caso de uso no padrão do template de CDU | Grupo Manitos |

---
# 1. Nome do Caso de Uso

**Registrar Manutenção**

---

# 2. Objetivo

Permitir que o Atendente do CCT registre a manutenção de um ativo, indicando motivo, situação, responsável pelo registro e alteração de disponibilidade no inventário.

---

# 3. Tipo de Caso de Uso

| Item | Valor |
|---|---|
| Tipo do Caso de Uso | Concreto |

---

# 4. Atores

## 4.1 Primário

| Ator | Descrição |
|---|---|
| Atendente do CCT | Registra manutenção operacional de ativos |

## 4.2 Secundário

| Ator | Descrição |
|---|---|
| Coordenação do CCT | Acompanha ativos em manutenção e histórico |
| Sistema GAC | Registra manutenção e atualiza o inventário |
| Técnico/Setor de Manutenção | Pode ser informado como responsável externo ou destinatário da manutenção |

---

# 5. Precondições

| Código | Descrição |
|---|---|
| PRE01 | O ativo deve estar cadastrado no inventário |
| PRE02 | O Atendente do CCT deve possuir permissão para registrar manutenção |
| PRE03 | O motivo da manutenção deve ser informado |
| PRE04 | O ativo não deve estar com retirada ativa sem devolução registrada, salvo manutenção aberta por ocorrência |

---

# 6. Fluxo Principal

## P1. Acessar manutenção

### P1.1.
O Atendente do CCT seleciona a opção **Registrar Manutenção**.

### P1.2.
O sistema apresenta a tela de registro de manutenção.

---

## P2. Identificar ativo

### P2.1.
O Atendente do CCT informa ou escaneia o patrimônio do ativo.

### P2.2.
O sistema localiza o ativo no inventário. **[E1]**

---

## P3. Informar manutenção

### P3.1.
O Atendente do CCT informa o motivo da manutenção.

### P3.2.
O Atendente do CCT informa descrição, data de início e responsável ou setor de manutenção.

### P3.3.
O Atendente do CCT anexa evidência quando necessário.

---

## P4. Validar registro

### P4.1.
O sistema valida os dados obrigatórios. **[E2]**

### P4.2.
O sistema verifica se o ativo pode ser marcado como **Em Manutenção**. **[E3]**

---

## P5. Registrar manutenção

### P5.1.
O sistema registra a manutenção.

### P5.2.
O sistema altera o status do ativo para **Em Manutenção**.

---

## P6. Atualizar inventário

### P6.1.
O sistema inclui o caso de uso **CDU03 - Atualizar Inventário**.

### P6.2.
O sistema apresenta a mensagem **MSG035 - Manutenção registrada com sucesso**.

### P6.3.
O caso de uso é encerrado.

---

# 7. Fluxos Alternativos

## A1. Manutenção gerada a partir de ocorrência

### A1.1.
No passo **P1.1**, o caso de uso é iniciado a partir de uma ocorrência registrada.

### A1.2.
O sistema preenche automaticamente ativo, motivo e descrição inicial.

### A1.3.
O Atendente do CCT complementa as informações.

### A1.4.
O fluxo segue para o passo **P4.1**.

## A2. Finalizar manutenção

### A2.1.
No passo **P1.1**, o Atendente do CCT seleciona manutenção aberta.

### A2.2.
O Atendente do CCT informa data de finalização e resultado.

### A2.3.
O sistema altera o status do ativo para **Disponível** ou **Com Pendência**.

### A2.4.
O sistema inclui o caso de uso **CDU03 - Atualizar Inventário**.

### A2.5.
O sistema apresenta a mensagem **MSG036 - Manutenção finalizada com sucesso**.

---

# 8. Fluxos de Exceção

## E1. Ativo não encontrado

### E1.1.
No passo **P2.2**, o sistema não encontra o patrimônio informado.

### E1.2.
O sistema apresenta a mensagem **MSG037 - Ativo não encontrado para manutenção**.

### E1.3.
O fluxo retorna ao passo **P2.1**.

## E2. Dados obrigatórios ausentes

### E2.1.
No passo **P4.1**, o sistema identifica ausência de motivo ou descrição.

### E2.2.
O sistema apresenta a mensagem **MSG038 - Informe os dados obrigatórios da manutenção**.

### E2.3.
O fluxo retorna ao passo **P3.1**.

## E3. Ativo não pode ser enviado para manutenção

### E3.1.
No passo **P4.2**, o sistema identifica situação incompatível com abertura de manutenção.

### E3.2.
O sistema apresenta a mensagem **MSG039 - O ativo não pode ser enviado para manutenção nesta situação**.

### E3.3.
O caso de uso é encerrado.

---

# 9. Pós-condições

| Código | Descrição |
|---|---|
| POS01 | A manutenção fica registrada |
| POS02 | O ativo fica com status **Em Manutenção** quando a manutenção é aberta |
| POS03 | O ativo deixa de aparecer como disponível para retirada |
| POS04 | O histórico de manutenção fica disponível para consulta |
| POS05 | O inventário é atualizado |

---

# 10. Requisitos Não Funcionais

| Código | Requisito |
|---|---|
| RNF01 | O registro de manutenção deve ser rastreável |
| RNF02 | O sistema deve registrar data, hora e usuário responsável |
| RNF03 | O sistema deve impedir retirada de ativo em manutenção |
| RNF04 | O histórico de manutenção deve ficar disponível para relatórios |

---

# 11. Ponto de Extensão

## PE1. Atualizar Inventário

Permite atualizar a disponibilidade e o status do ativo após abertura ou conclusão de manutenção.

---

# 12. Frequência de Utilização

| Item | Informação |
|---|---|
| Frequência | Baixa a média |
| Perfil de Uso | Utilizado quando há falha, dano ou necessidade de reparo |
| Informações mais acessadas | Patrimônio, motivo, status, data de abertura e histórico |

---

# 13. Interface Visual

## IV1. Tela de registro de manutenção

| Campo | Tipo/Formato | Obrigatório | Descrição | Regra de Negócio |
|---|---|---|---|---|
| Patrimônio | QR/NFC/Texto | Sim | Identificação do ativo | Deve existir no inventário |
| Status atual | Texto | Sim | Situação do ativo | Obtido automaticamente |
| Motivo | Lista | Sim | Defeito, dano, preventiva ou outro | Deve ser selecionado |
| Descrição | Texto longo | Sim | Detalhamento da manutenção | Deve ser informado |
| Responsável/Setor | Texto/Lista | Não | Responsável pelo reparo | Opcional |
| Evidência | Arquivo/Imagem | Não | Foto ou documento de apoio | Opcional |
| Data de início | Data/Hora | Sim | Início da manutenção | Gerada ou informada |
| Botão “Registrar Manutenção” | Botão | Sim | Confirma registro | Habilitado após validação |

---

# 14. Observações

| Código | Observação |
|---|---|
| OBS01 | A manutenção pode ser aberta manualmente ou a partir de uma ocorrência |
| OBS02 | A gestão de chamados externos pode ser detalhada em integração futura |

---

# 15. Referências

| Código | Referência |
|---|---|
| REF01 | Documento de Visão da Demanda do Projeto GAC |
| REF02 | Glossário do Projeto GAC |
| REF03 | CDU03 - Atualizar Inventário |
| REF04 | CDU08 - Registrar Ocorrência |
---

# 16. Checklist de Validação do Artefato (CDU)

## 16.1 Estrutura mínima

- [x] Nome do caso de uso iniciado com verbo no infinitivo.
- [x] Objetivo claro, direto e com foco em um objetivo principal.
- [x] Tipo do caso de uso informado.
- [x] Atores primário e secundários identificados corretamente.
- [x] Precondições registradas.
- [x] Fluxo principal completo e coerente com o objetivo.
- [x] Fluxos alternativos e de exceção definidos.
- [x] Pós-condições registradas.
- [x] Requisitos não funcionais registrados.
- [x] Pontos de extensão identificados quando aplicável.
- [x] Frequência de utilização estimada.

## 16.2 Qualidade da especificação

- [x] Passos escritos com linguagem simples e objetiva.
- [x] Ações descritas com verbos no presente do indicativo.
- [x] Alternância entre ação do ator e ação da solução está clara.
- [x] Não há ambiguidade relevante.
- [x] Regras de negócio e mensagens estão referenciadas quando necessário.

## 16.3 Consistência e rastreabilidade

- [x] Pontos de entrada e saída dos fluxos alternativos estão explícitos.
- [x] Fluxos de exceção estão vinculados aos passos corretos da solução.
- [x] Referências internas entre passos estão corretas.
- [x] Interface visual está coerente com o fluxo descrito.
- [x] Referências para visão da demanda, glossário e CDUs relacionados estão atualizadas.

## 16.4 Revisão final

- [x] Não há contradições entre seções do artefato.
- [x] Links internos e externos foram validados quando aplicável.
- [x] Documento pronto para revisão por pares.
- [x] Artefato pronto para uso em desenvolvimento e testes.
