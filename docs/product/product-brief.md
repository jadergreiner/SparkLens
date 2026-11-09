# SparkLens — Product Brief (M0)

**Status:** DRAFT — hipóteses aguardando validação do responsável pelo produto  
**Data:** 2026-11-08  
**Método:** BMad — fase de descoberta; artefato inicial inspirado no fluxo de Product Brief, **não** resultado de execução de agentes locais.

## 1. Contexto e motivação confirmados

- SparkLens será um **produto pessoal, público e incremental**, publicado no GitHub.
- Servirá como **caso de estudo prático do Life Learning**, além de portfólio técnico.
- Deve permitir aplicações de competências de Engenharia de Dados, Spark, AWS, Databricks, arquitetura distribuída, governança, DataOps e IA generativa, sem impor todos esses componentes ao MVP.
- A aprendizagem deve produzir **desafios e evidências reproduzíveis**; o produto precisa ter valor para terceiros, não ser apenas uma coleção de laboratórios.

## 2. Problema a descobrir

**Hipótese H1 (não validada):** engenheiros de dados precisam de uma forma simples de diagnosticar e explicar comportamento de workloads Apache Spark, com recomendações reproduzíveis para análise e melhoria.

O nome SparkLens sugere observabilidade/diagnóstico de Spark, mas **essa interpretação ainda não foi aprovada como definição do produto**. Não implementar soluções antes de validar H1.

### Hipóteses alternativas

- H2: ferramenta educacional que torna planos de execução e trade-offs de Spark compreensíveis.
- H3: ferramenta para organizar evidências e experimentos de otimização de pipelines de dados.

## 3. Público-alvo candidato

- Engenheiros de dados em aprendizado ou evolução profissional.
- Engenheiros que operam pipelines Apache Spark.
- Líderes técnicos que revisam performance e evidências de confiabilidade.

**Pendente:** entrevistar/validar qual segmento tem o problema mais frequente e relevante.

## 4. Proposta de valor candidata

Transformar sinais técnicos de execução Spark em explicações e evidências acionáveis, com entradas de exemplo e documentação reproduzível. **Ainda é uma hipótese**, não promessa de funcionalidade.

## 5. Critérios para aprovação do M0

- [ ] Registrar problema, usuário e frequência/intensidade da dor.
- [ ] Escolher explicitamente uma hipótese e rejeitar/adiar as alternativas.
- [ ] Definir o trabalho que o usuário espera realizar (JTBD).
- [ ] Documentar alternativas existentes e diferencial verificável.
- [ ] Definir uma demonstração mínima de valor e critérios mensuráveis de sucesso.
- [ ] Delimitar o MVP e os **não objetivos**.
- [ ] Revisar privacidade, licenças, custo e acessibilidade da proposta.
- [ ] Obter aprovação explícita do responsável pelo produto para avançar ao PRD.

## 6. Restrições e princípios

1. Usar dados sintéticos por padrão; não publicar credenciais ou dados internos.
2. Preferir execução local no MVP quando tecnicamente possível.
3. Não provisionar recursos AWS/Databricks sem uma decisão separada.
4. Separar **hipótese**, **decisão aprovada**, **implementação** e **evidência validada**.
5. Nenhuma entrega no SparkLens aprova automaticamente competência ou altera cadência Life Learning.

## 7. Perguntas abertas da descoberta

1. Qual cenário real de Spark é mais trabalhoso para o usuário hoje?
2. A primeira versão deve analisar logs/planos, executar experiências didáticas ou organizar diagnósticos?
3. O usuário-alvo aceita operar uma CLI local ou precisa de interface?
4. Que entrada pública e anonimizada reproduz o problema?
5. Qual métrica prova valor em um teste com usuários?

## 8. Próximo gate

**G0 — Aprovar problema e recorte de MVP.** Sem essa aprovação, PRD, arquitetura, backlog e implementação permanecem pendentes.
