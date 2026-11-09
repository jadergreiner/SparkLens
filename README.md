# SparkLens

**SparkLens** é um projeto público e incremental de Engenharia de Dados, usado como produto de portfólio e como cenário prático de aprendizagem do método **Life Learning**.

> Estado: concepção / inicialização do repositório. Este README descreve intenções e critérios; não representa funcionalidades já implementadas.

## Objetivos

- Construir um produto útil e demonstrável, não apenas uma coleção de laboratórios.
- Evoluir competências de engenharia de dados e arquitetura em direção a responsabilidades de nível Staff.
- Incorporar progressivamente Apache Spark, AWS, Databricks, arquitetura distribuída, governança, DataOps e IA generativa quando houver justificativa de produto.
- Demonstrar decisões arquiteturais, testes, limites, trade-offs e evidências verificáveis.

## Integração com Life Learning

SparkLens é o **caso de estudo e aplicação**, não a fonte da verdade sobre o aprendizado.

1. A competência e a trilha de estudos são governadas pelo Life Learning; o histórico de competências, pontos fortes e lacunas permanece em Notion e Google Drive.
2. Ao concluir uma sessão de estudo, identificar uma aplicação **didática ou prática** da competência ao SparkLens.
3. Quando fizer sentido implementar, criar uma tarefa com requisitos, critérios de aceitação, testes e evidências reproduzíveis.
4. Registrar no histórico de aprendizagem o vínculo com issue, commit ou PR do SparkLens; não confundir explicação teórica com implementação validada.
5. Flashcards e revisões permanecem centralizados no Recall, no deck do Life Learning.

O conselho do Life Learning aprova mudanças na trilha de conteúdo; contribuições ao produto não promovem competências automaticamente. Preservar a prática nas três esferas **Local, AWS e Databricks** quando exigida pela competência, sem assumir que os três ambientes precisam ser provisionados para cada funcionalidade do produto.

## Princípios de evolução

- **Produto antes de ferramenta:** esclarecer problema, usuários e resultados esperados antes de escolher componentes.
- **MVP pequeno:** escolher uma fatia vertical validável e publicar evidência de funcionamento.
- **Local primeiro quando viável:** desenvolver sem custo de nuvem obrigatório.
- **Arquitetura evolutiva:** documentar ADRs e evitar complexidade antecipada.
- **Qualidade observável:** testes automatizados, dados sintéticos, instruções de reprodução e decisões explícitas.
- **Segurança e custos:** não publicar credenciais ou dados sensíveis; não provisionar AWS/Databricks sem decisão explícita.

## Próximos marcos propostos

| Marco | Entregável | Evidência |
| --- | --- | --- |
| M0 — Definição | Problema, persona, proposta de valor e recorte de MVP | PRD inicial revisado |
| M1 — Fundação | Estrutura de projeto, execução local e CI básica | Execução e testes reproduzíveis |
| M2 — Primeira capacidade | Fluxo funcional end-to-end alinhado ao MVP | Demonstração, testes e documentação |
| M3 — Evolução | Observabilidade, governança e integrações com AWS/Databricks conforme necessidade | Métricas, ADRs e avaliação de trade-offs |

Esses marcos são propostas, não aprovações do conselho nem entregas concluídas.

## Organização futura

A estrutura de código será criada conforme a primeira fatia de produto for definida. Não foram escolhidos ainda stack de interface, serviços gerenciados ou modelo de monetização.

## Referências de governança

- [Repositório SparkLens](https://github.com/jadergreiner/SparkLens) — código e evidências públicas do produto.
- **Life Learning** — trilhas, critérios de competência, prática e avaliação.
- **Notion / Google Drive** — fontes de verdade dos registros de aprendizagem.
- **Recall** — flashcards e revisão espaçada.

## Status da sincronização

Documento-base inicial: 2026-11-08. Não representa sincronização bidirecional automática entre repositórios ou aplicativos.
