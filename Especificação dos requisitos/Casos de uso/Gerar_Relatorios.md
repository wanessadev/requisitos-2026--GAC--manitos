# Especificação de Requisitos Funcionais

## Caso de Uso (CDU) - GAC

---

## Histórico de Versões

| Data       | Versão | Descrição | Autor |
|------------|--------|-----------|-------|
| 30/05/2026 | 1.0 | Criação da especificação do caso de uso no padrão do template de CDU | Grupo Manitos |

---
# 1. Nome do Caso de Uso

**Gerar Relatórios**

---

# 2. Objetivo

Permitir que a Coordenação do CCT gere relatórios sobre inventário, retiradas, devoluções, ocorrências, manutenções, atrasos e histórico de movimentações dos ativos.

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
| Coordenação do CCT | Solicita e consulta relatórios gerenciais |

## 4.2 Secundário

| Ator | Descrição |
|---|---|
| Sistema GAC | Consolida dados e gera relatórios |
| Atendente do CCT | Pode gerar relatórios operacionais quando autorizado |

---

# 5. Precondições

| Código | Descrição |
|---|---|
| PRE01 | O usuário deve possuir permissão para gerar relatórios |
| PRE02 | Deve existir base de dados com inventário ou movimentações |
| PRE03 | O tipo de relatório deve ser selecionado |
| PRE04 | O período de consulta deve ser informado quando exigido |

---

# 6. Fluxo Principal

## P1. Acessar relatórios

### P1.1.
A Coordenação do CCT seleciona a opção **Gerar Relatórios**.

### P1.2.
O sistema apresenta os tipos de relatório disponíveis.

---

## P2. Selecionar relatório

### P2.1.
A Coordenação do CCT seleciona o tipo de relatório.

### P2.2.
O sistema apresenta os filtros disponíveis para o relatório selecionado.

---

## P3. Informar filtros

### P3.1.
A Coordenação do CCT informa período, tipo de ativo, status, responsável, local ou ocorrência.

### P3.2.
O sistema valida os filtros informados. **[E1]**

---

## P4. Gerar relatório

### P4.1.
O sistema consulta os dados correspondentes.

### P4.2.
O sistema gera o relatório com os dados consolidados. **[E2]**

---

## P5. Apresentar resultado

### P5.1.
O sistema apresenta o relatório em tela.

### P5.2.
A Coordenação do CCT consulta os dados apresentados.

---

## P6. Exportar relatório

### P6.1.
A Coordenação do CCT seleciona a opção de exportação.

### P6.2.
O sistema gera o arquivo no formato selecionado.

### P6.3.
O sistema disponibiliza o relatório para download.

---

# 7. Fluxos Alternativos

## A1. Visualizar relatório sem exportar

### A1.1.
No passo **P6.1**, a Coordenação do CCT opta por não exportar o relatório.

### A1.2.
O sistema mantém o relatório disponível em tela.

### A1.3.
O caso de uso é encerrado.

## A2. Gerar relatório a partir do dashboard

### A2.1.
No passo **P1.1**, o caso de uso é iniciado a partir do **CDU11 - Consultar Dashboard**.

### A2.2.
O sistema preenche automaticamente os filtros selecionados no dashboard.

### A2.3.
O fluxo segue para o passo **P4.1**.

---

# 8. Fluxos de Exceção

## E1. Filtros inválidos

### E1.1.
No passo **P3.2**, o sistema identifica filtros inválidos ou período inconsistente.

### E1.2.
O sistema apresenta a mensagem **MSG033 - Filtros inválidos para geração do relatório**.

### E1.3.
O fluxo retorna ao passo **P3.1**.

## E2. Nenhum dado encontrado

### E2.1.
No passo **P4.2**, o sistema não encontra dados para os filtros informados.

### E2.2.
O sistema apresenta a mensagem **MSG034 - Nenhum dado encontrado para os filtros selecionados**.

### E2.3.
O fluxo retorna ao passo **P3.1**.

---

# 9. Pós-condições

| Código | Descrição |
|---|---|
| POS01 | O relatório é apresentado em tela |
| POS02 | O arquivo de relatório é disponibilizado quando exportado |
| POS03 | Nenhum dado operacional é alterado pela geração |
| POS04 | A Coordenação do CCT pode usar o relatório para auditoria e gestão |

---

# 10. Requisitos Não Funcionais

| Código | Requisito |
|---|---|
| RNF01 | A geração de relatório simples deve ocorrer em até 5 segundos na maior parte das consultas |
| RNF02 | O sistema deve controlar acesso aos relatórios por perfil |
| RNF03 | O relatório exportado deve preservar os filtros aplicados |
| RNF04 | O sistema deve permitir exportação em formato adequado para consulta e compartilhamento |

---

# 11. Ponto de Extensão

Não se aplica.

---

# 12. Frequência de Utilização

| Item | Informação |
|---|---|
| Frequência | Média |
| Perfil de Uso | Consultas gerenciais e auditorias periódicas |
| Informações mais acessadas | Inventário, retiradas, devoluções, atrasos, ocorrências e manutenção |

---

# 13. Interface Visual

## IV1. Tela de geração de relatórios

| Campo | Tipo/Formato | Obrigatório | Descrição | Regra de Negócio |
|---|---|---|---|---|
| Tipo de relatório | Lista | Sim | Define o relatório desejado | Deve ser selecionado |
| Período | Data inicial/final | Condicional | Intervalo dos dados | Obrigatório para relatórios temporais |
| Tipo de ativo | Lista | Não | Categoria do ativo | Filtra resultado |
| Status | Lista | Não | Situação do ativo | Filtra resultado |
| Responsável | Busca | Não | Professor ou atendente relacionado | Filtra resultado |
| Botão “Gerar” | Botão | Sim | Gera relatório | Habilitado após filtros mínimos |
| Botão “Exportar” | Botão | Não | Exporta relatório | Disponível após geração |

---

# 14. Observações

| Código | Observação |
|---|---|
| OBS01 | Relatórios podem ser usados em auditorias e reuniões da Coordenação |
| OBS02 | Novos tipos de relatório podem ser adicionados conforme necessidade do CCT |

---

# 15. Referências

| Código | Referência |
|---|---|
| REF01 | Documento de Visão da Demanda do Projeto GAC |
| REF02 | Glossário do Projeto GAC |
| REF03 | CDU11 - Consultar Dashboard |
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
