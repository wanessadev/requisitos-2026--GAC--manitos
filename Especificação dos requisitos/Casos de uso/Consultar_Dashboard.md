# Especificação de Requisitos Funcionais

## Caso de Uso (CDU) - GAC

---

## Histórico de Versões

| Data       | Versão | Descrição | Autor |
|------------|--------|-----------|-------|
| 30/05/2026 | 1.0 | Criação da especificação do caso de uso no padrão do template de CDU | Grupo Manitos |

---
# 1. Nome do Caso de Uso

**Consultar Dashboard**

---

# 2. Objetivo

Permitir que a Coordenação do CCT consulte indicadores consolidados sobre ativos, retiradas, devoluções, pendências, ocorrências e disponibilidade do inventário.

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
| Coordenação do CCT | Consulta indicadores e acompanha a situação operacional dos ativos |

## 4.2 Secundário

| Ator | Descrição |
|---|---|
| Sistema GAC | Consolida e apresenta os indicadores do dashboard |
| Atendente do CCT | Pode consultar indicadores operacionais quando autorizado |

---

# 5. Precondições

| Código | Descrição |
|---|---|
| PRE01 | A Coordenação do CCT deve possuir permissão para consultar o dashboard |
| PRE02 | O Sistema GAC deve possuir dados de inventário e movimentações |
| PRE03 | Os indicadores devem estar disponíveis para consolidação |
| PRE04 | O período de consulta deve estar definido ou assumir período padrão |

---

# 6. Fluxo Principal

## P1. Acessar dashboard

### P1.1.
A Coordenação do CCT seleciona a opção **Consultar Dashboard**.

### P1.2.
O sistema apresenta a tela inicial do dashboard.

---

## P2. Definir filtros

### P2.1.
A Coordenação do CCT informa filtros de período, tipo de ativo, status ou local.

### P2.2.
O sistema valida os filtros informados. **[E1]**

---

## P3. Consultar indicadores

### P3.1.
O sistema consolida dados de ativos, retiradas, devoluções, ocorrências e manutenções.

### P3.2.
O sistema apresenta indicadores de disponibilidade, ativos em uso, pendências, atrasos e ocorrências.

---

## P4. Detalhar indicador

### P4.1.
A Coordenação do CCT seleciona um indicador para detalhamento.

### P4.2.
O sistema apresenta a lista de registros relacionados ao indicador.

---

## P5. Encerrar consulta

### P5.1.
A Coordenação do CCT finaliza a consulta.

### P5.2.
O caso de uso é encerrado.

---

# 7. Fluxos Alternativos

## A1. Consulta sem filtros

### A1.1.
No passo **P2.1**, a Coordenação do CCT não informa filtros.

### A1.2.
O sistema aplica o período e os filtros padrão.

### A1.3.
O fluxo segue para o passo **P3.1**.

## A2. Exportar visão do dashboard

### A2.1.
No passo **P4.2**, a Coordenação do CCT seleciona a opção de exportar dados.

### A2.2.
O sistema gera arquivo com os dados apresentados.

### A2.3.
O sistema disponibiliza o arquivo para download.

---

# 8. Fluxos de Exceção

## E1. Filtros inválidos

### E1.1.
No passo **P2.2**, o sistema identifica período inválido ou filtro inconsistente.

### E1.2.
O sistema apresenta a mensagem **MSG031 - Filtros inválidos para consulta do dashboard**.

### E1.3.
O fluxo retorna ao passo **P2.1**.

## E2. Dados indisponíveis

### E2.1.
No passo **P3.1**, o sistema não consegue consolidar os dados.

### E2.2.
O sistema apresenta a mensagem **MSG032 - Dados temporariamente indisponíveis**.

### E2.3.
O caso de uso é encerrado.

---

# 9. Pós-condições

| Código | Descrição |
|---|---|
| POS01 | Os indicadores são apresentados à Coordenação do CCT |
| POS02 | Os dados filtrados podem ser detalhados |
| POS03 | A visão exportada fica disponível quando solicitada |
| POS04 | Nenhum dado operacional é alterado pela consulta |

---

# 10. Requisitos Não Funcionais

| Código | Requisito |
|---|---|
| RNF01 | O dashboard deve carregar os principais indicadores em até 5 segundos na maior parte das consultas |
| RNF02 | O sistema deve restringir acesso aos indicadores conforme perfil |
| RNF03 | A interface deve ser responsiva |
| RNF04 | Os indicadores devem ser atualizados com dados consistentes do inventário e movimentações |

---

# 11. Ponto de Extensão

## PE1. Gerar Relatórios

Permite gerar relatório detalhado a partir de indicadores ou filtros selecionados no dashboard.

---

# 12. Frequência de Utilização

| Item | Informação |
|---|---|
| Frequência | Média |
| Perfil de Uso | Consultas gerenciais pela Coordenação do CCT |
| Informações mais acessadas | Disponibilidade, ativos em uso, atrasos, pendências e ocorrências |

---

# 13. Interface Visual

## IV1. Tela de dashboard gerencial

| Campo/Componente | Tipo/Formato | Obrigatório | Descrição | Regra de Negócio |
|---|---|---|---|---|
| Período | Filtro de data | Não | Intervalo da consulta | Usa período padrão quando vazio |
| Tipo de ativo | Lista | Não | Categoria de ativo | Filtra os indicadores |
| Status do ativo | Lista | Não | Disponível, Em Uso, Em Manutenção ou Com Pendência | Filtra dados apresentados |
| Indicadores | Cards/Gráficos | Sim | Resumo operacional | Calculado pelo sistema |
| Lista detalhada | Tabela | Não | Registros do indicador selecionado | Exibida sob demanda |
| Botão “Exportar” | Botão | Não | Exporta visão atual | Disponível para perfil autorizado |

---

# 14. Observações

| Código | Observação |
|---|---|
| OBS01 | O dashboard deve apoiar decisões da Coordenação do CCT |
| OBS02 | Indicadores podem evoluir conforme novas necessidades gerenciais |

---

# 15. Referências

| Código | Referência |
|---|---|
| REF01 | Documento de Visão da Demanda do Projeto GAC |
| REF02 | Glossário do Projeto GAC |
| REF03 | CDU12 - Gerar Relatórios |
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
