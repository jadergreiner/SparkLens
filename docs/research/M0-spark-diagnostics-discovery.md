# M0 — Descoberta crítica: diagnóstico e otimização Apache Spark

- **Data:** 2026-11-08
- **Status:** Pesquisa preliminar concluída; **hipótese priorizada, escopo NÃO aprovado**
- **Método de referência:** BMad — explorar e validar uma ideia; avaliação crítica inspirada em `bmad-forge-idea`. Nenhum agente BMad local foi executado.
- **Decisão do responsável:** priorizar diagnóstico e otimização de workloads Spark, contestando a hipótese antes de fechar o escopo.

## 1. Problema candidato

> Engenheiros de dados gastam esforço para transformar sinais fragmentados da execução Spark em hipóteses de causa raiz, intervenções seguras e comprovação objetiva de melhoria.

**Essa formulação é hipótese de problema, não resultado de pesquisa com usuários.** Não há nesta fase evidência de frequência, severidade ou disposição de adoção.

### Usuários candidatos

1. Engenheiro de dados intermediário/sênior que investiga jobs lentos.
2. Líder técnico que revisa justificativas para tuning.
3. Engenheiro em aprendizado que precisa interpretar evidência antes de alterar parâmetros.

**Não incluir os três segmentos no MVP sem validação.**

## 2. Concorrência e alternativas já disponíveis

| Alternativa | Capacidade constatada | Implicação |
|---|---|---|
| Spark UI / History Server | Jobs, stages, tasks, executors, event logs e análise posterior | Reproduzir dashboards não cria diferencial |
| Spark SQL EXPLAIN / métricas AQE | Planos e estatísticas de execução | Recomendações precisam considerar otimizações já aplicadas |
| Databricks Spark UI / Query Profile | Diagnóstico de gargalos, detalhes operacionais | Posicionamento 'diagnostica Spark' sozinho é insuficiente |
| Databricks Query Performance Insights | Recomendações já priorizadas e, em alguns casos, assistência de otimização | IA e sugestões não constituem diferencial por si só |
| Qubole Sparklens | Profiling, paralelismo, skew, simulação de executores, análise via event history | **Conflito nominal e sobreposição funcional** com o nome SparkLens |

### Risco específico de nome

Existe um produto open source anterior **Qubole Sparklens** em https://github.com/qubole/sparklens. O repositório atual **jadergreiner/SparkLens** usa nome praticamente idêntico e também propõe otimização Spark. **Não pressupor exclusividade de nome nem emitir conclusão jurídica**. Realizar avaliação de marca, pesquisa de disponibilidade e decisão de identidade antes de lançar publicamente.

## 3. Argumentos a favor e contra

| Afirmação | Contestação | Como testar |
|---|---|---|
| Há demanda por diagnósticos Spark mais simples | Ferramentas existentes já apresentam métricas e guias | Entrevistas com casos recentes e comparação com fluxo atual |
| Um diagnóstico automático economiza tempo | Pode gerar falsos positivos e transferir custo à verificação | Teste cego com eventos conhecidos e medição de tempo |
| Recomendações produzem melhora | Tuning pode piorar custo, latência ou estabilidade; AQE pode corrigir sozinho | Experimentos controlados antes/depois, mesma carga e ambiente |
| Ferramenta independente de nuvem é valiosa | Integrações locais podem perder métricas específicas da plataforma | Comparar cobertura Local / AWS / Databricks e necessidades reais |
| Um assistente IA diferencia produto | Soluções já usam recomendações e IA; risco de alucinação | Baseline determinístico antes de LLM; exigir rastreio das evidências |
| Há material suficiente para ensinar Spark | Material educacional é abundante | Testar valor incremental em tarefas objetivas de diagnóstico |

## 4. Proposta de posicionamento a testar (não aprovada)

> **Diagnóstico explicável e verificável de workloads Spark:** para cada suspeita, apresentar sinais observados, hipótese de causa raiz, grau de confiança, próximos testes e comparação antes/depois.

**Hipótese de diferenciação:** transformar observabilidade em uma cadeia de evidência auditável, com resultados reproduzíveis, sem prometer tuning automático universal.

## 5. Três recortes alternativos de MVP

### A — Analisador offline de event logs (preferência de investigação)

- Entrada candidata: logs de eventos Spark gerados localmente com dados sintéticos.
- Saída candidata: relatório textual/JSON com sintomas de skew, spill ou paralelismo insuficiente e provas extraídas das métricas.
- **Riscos:** diversidade de versões/formato, logs incompletos, falsos positivos, ferramenta existente com função semelhante.
- **Critério de escolha:** usuários conseguirem resolver um caso mais rapidamente do que usando Spark UI/History Server ou Qubole Sparklens.

### B — Explicador de planos SQL/DataFrame

- Entrada candidata: saída de `explain` e contexto de consulta.
- Saída candidata: leitura orientada de nós relevantes e experimentos recomendados.
- **Riscos:** plano sem métricas reais não comprova gargalo; benefício restrito a formação.

### C — Comparador reprodutível antes/depois

- Entrada candidata: métricas de duas execuções da mesma aplicação.
- Saída candidata: comparação de duração, volume processado, shuffle, spill e contexto de execução.
- **Riscos:** confusão por variação de carga, cluster, cache, AQE e aquecimento; necessidade de normalização.

Nenhuma opção foi escolhida formalmente. **A é apenas o primeiro experimento sugerido**, não o escopo fechado.

## 6. Experimentos de descoberta e critérios

**E1 — Entrevistas exploratórias.** Conversar com pelo menos 5 engenheiros de dados que tenham investigado lentidão Spark recentemente. Coletar caso concreto, processo atual, tempo, dificuldade e artefatos usados. **Critério proposto:** ao menos 3 de 5 relatarem dificuldade recorrente e demonstrarem um caso específico, sem perguntas indutivas. Amostra exploratória: não inferir mercado total.

**E2 — Benchmark de diagnóstico.** Construir (somente após autorização para implementação) três workloads sintéticos com sintomas controlados: skew, spill e subparalelismo. Comparar Spark UI/History Server, Qubole Sparklens (onde tecnicamente compatível) e protótipo. **Critério proposto:** evidência correta em pelo menos 2 de 3 casos, nenhum diagnóstico assertivo sem sinal verificável; registrar resultados ambíguos. Não afirmar ganho de tempo sem medição.

**E3 — Teste de utilidade.** Pedir a 3 usuários-alvo para interpretar um relatório estático versus workflow atual. Medir acerto na hipótese de gargalo e tempo de decisão; registrar diferença e confiança. **Critério proposto:** maioria prefere o novo formato por uma razão observável, sem degradar acerto.

**E4 — Naming e legitimidade.** Pesquisar conflito com Qubole Sparklens, usos públicos, documentação e eventual registro de marca nas jurisdições pertinentes. **Gate:** nome aprovado ou plano de renomeação antes de divulgação ampla.

## 7. Matriz de riscos preliminar

| Risco | Impacto | Resposta inicial |
|---|---|---|
| Colisão de identidade com Qubole Sparklens | Alto | Gate E4; não inferir direito de uso |
| Ausência de diferencial sobre UI/Databricks | Alto | Benchmark competitivo E2/E3 |
| Diagnóstico incorreto levar a tuning danoso | Alto | Justificativa observável, incerteza e revisão humana |
| Métricas ausentes/incompatíveis | Médio/alto | Suportar somente versões testadas e explicitar limitações |
| Exposição de logs operacionais sensíveis | Alto | Sintéticos por padrão, análise local, política de sanitização |
| Overengineering e gasto de nuvem | Médio | Sem provisão; resolver um cenário local primeiro |
| Uso prematuro de LLM | Médio | Diagnóstico determinístico como baseline |

## 8. Perguntas que impedem fechar o escopo

1. **Quem exatamente sofre o problema primeiro?** Usuário educacional ou engenheiro em produção?
2. **Qual decisão precisa ficar melhor?** Identificar gargalo, recomendar intervenção ou demonstrar melhoria?
3. **Quais dados os usuários conseguem compartilhar?** Event logs reais podem conter nomes, caminhos e metadados sensíveis.
4. **Qual métrica define sucesso?** Redução do tempo de investigação, aumento de acerto ou prevenção de mudanças ruins?
5. **Qual limitação concreta das ferramentas existentes é insuportável?**
6. **Manter ou mudar o nome SparkLens?** Risco real de confusão com Qubole Sparklens.

## 9. Gate M0/G0

**Resultado: NÃO APROVADO PARA ENCERRAMENTO.** Existe base técnica para investigar, mas não para fechar PRD, arquitetura, funcionalidades ou promessas de performance.

**Próxima ação recomendada:** realizar E1 e decidir recorte de persona/JTBD; em paralelo validar E4. Só então comparar A/B/C e aprovar ou descartar a proposta.

## Fontes consultadas

- BMad, Explore and Validate an Idea: https://docs.bmad-method.org/plan/explore-and-validate-an-idea/
- Apache Spark, Monitoring and Instrumentation: https://spark.apache.org/docs/latest/monitoring
- Apache Spark, Performance Tuning: https://spark.apache.org/docs/latest/sql-performance-tuning
- Databricks, Diagnose Cost and Performance Issues: https://docs.databricks.com/aws/en/optimizations/spark-ui-guide
- Databricks, Query Performance Insights (2026-09-02): https://docs.databricks.com/aws/en/sql/user/queries/performance-insights
- Qubole Sparklens: https://github.com/qubole/sparklens
- Qubole Sparklens documentation: https://docs.qubole.com/en/latest/user-guide/engines/spark/sparklens.html

Fontes cobrem **capacidades de ferramentas**; não validam necessidade dos usuários nem viabilidade comercial.
