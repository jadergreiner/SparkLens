# SparkLens — Brainstorming M0 (sessão aberta)

- Data: 2026-11-08
- Estado: **ABERTA — divergência, sem seleção/aprovação de solução**
- Persona hipotética: engenheiro de dados em aprendizado de diagnóstico e otimização Spark
- Objetivo: encontrar valor educacional demonstrável que não seja mera repetição da Spark UI, cursos ou documentação
- Método: facilitação inspirada em `bmad-brainstorming`; **skill não instalada nem executada dentro do repositório**
- Estilo inicial: Creative Partner; usuário pode alterar para Facilitator ou Ideate for Me
- Gate do produto: M0/G0 aberto; não autoriza PRD, arquitetura, infraestrutura nem implementação

## Pergunta central

Por que um engenheiro que já dispõe de Spark UI, documentação e cursos escolheria aprender com o SparkLens?

## Rodada 1 — três campos de exploração

1. **Investigação:** entregar um job lento e evidências fragmentadas; aluno formula hipótese antes do feedback.
2. **Experimentação:** alterar código/configuração e comparar efeitos sob condições controladas.
3. **Mentoria socrática:** exigir explicação causal e contestar certezas infundadas.

## Ideias-semente para divergência (não priorizadas)

1. Caso-mistério sem indicação do gargalo.
2. Simulação de incidente com diagnóstico incompleto.
3. Pistas graduais liberadas por hipótese do aprendiz.
4. Revisor que só pergunta por evidências, sem revelar solução.
5. Biblioteca de interpretações erradas frequentes.
6. Desafio em que a intervenção piora o desempenho.
7. Comparação de duas execuções com parâmetros controlados.
8. Cenário que muda a distribuição de dados e quebra a solução decorada.
9. Cartão de defesa técnica: sinal → hipótese → contraexemplo → experimento.
10. Rubrica de qualidade argumentativa independente do acerto final.
11. Diagnóstico com falta deliberada de métricas; aprender a dizer 'não sei'.
12. Explicação visual de mudanças do plano físico com AQE.

## Objeções a manter abertas

- Conteúdo convencional pode ser igualmente eficaz.
- Excesso de orientação pode aumentar dependência.
- Treinar em três cenários não garante transferência de competência.
- Produto educacional pode exigir conteúdo e revisão especializada contínuos.
- Sobreposição de nome e funcionalidade com Qubole Sparklens requer tratamento próprio.

## Próximo exercício de brainstorming

**Inversão:** 'Como construiríamos uma ferramenta que faz alguém parecer competente em Spark, sem realmente aprender a diagnosticar?'  
Usar respostas para derivar princípios de desenho que evitem aprendizagem superficial.

## Registro de decisões

Nenhum conceito foi aprovado. A sessão ainda precisa de contribuições do usuário, outras técnicas divergentes e convergência somente quando ele solicitar.

## Contexto e referências

- [M0, investigação crítica](../research/M0-spark-diagnostics-discovery.md)
- [Persona, JTBD e experimento EXP-M0-01](../research/M0-learner-persona-JTBD-experiment.md)
- [BMad — Explore and Validate an Idea](https://docs.bmad-method.org/plan/explore-and-validate-an-idea/)

## Rodada 1 — Contribuição do responsável (técnica de inversão)

> "Respostas prontas e redução e otimização sem sustentar o que ocorre tecnicamente (sorte de principiante)."

### Interpretação e contestação

- **Antipadrão A1 — resposta pronta:** o estudante replica ajustes sugeridos sem formular hipótese nem ler métricas.
- **Antipadrão A2 — otimização sem mecanismo:** o job fica mais rápido, mas o estudante não consegue explicar quais operações físicas, dados, partições ou recursos provocaram a mudança.
- **Antipadrão A3 — sorte de principiante:** um ganho isolado pode ocorrer por cache, aquecimento, ruído de execução, variação de entrada, AQE ou sorte, não necessariamente por uma intervenção correta.

**Cuidado de desenho:** explicação convincente também pode ser memorizada. Exigir explicação é necessário, mas não suficiente para evidenciar competência. A verificação deve testar previsão e transferência.

### Princípios candidatos derivados (ainda não aprovados)

1. **Hipótese antes da solução:** o estudante declara qual sintoma espera alterar e por quê, antes de executar mudança.
2. **Mecanismo observável:** conectar o ajuste a plano físico, distribuição de tarefas, métricas e comportamento do Spark.
3. **Contrafactual:** exigir explicação sobre o que deveria acontecer se a hipótese estiver incorreta.
4. **Repetibilidade:** repetir medições controlando carga, recursos, cache, versões e configurações; reportar variação, não apenas o melhor tempo.
5. **Transferência:** entregar um caso novo com sintoma semelhante e causa diferente para medir compreensão independente.
6. **Falsificação explícita:** uma redução de tempo sem causalidade sustentada não constitui aprovação da competência.

### Ideias divergentes novas (não selecionadas)

- **I13 — Otimização placebo:** um ajuste aparenta acelerar por ruído; o aluno precisa detectar falta de evidência.
- **I14 — Diagnóstico ao contrário:** o aluno prevê métricas antes de executar e confronta o resultado.
- **I15 — Tribunal de evidências:** um avaliador adversarial contesta explicações causais e pede testes discriminantes.
- **I16 — Mesmo tempo, outra causa:** workloads com duração semelhante, mas gargalos diferentes, para impedir diagnóstico por tempo total.
- **I17 — Relatório de inconclusão:** premiar a decisão fundamentada de não recomendar tuning quando as métricas são insuficientes.

### Próxima provocação — rodada 2 (ainda aberta)

**Se o job ficou 30% mais rápido após uma mudança de `spark.sql.shuffle.partitions`, quais provas mínimas o estudante deveria apresentar antes de afirmar que entendeu e resolveu o gargalo?** Considerar métricas, explicação causal, execuções comparáveis e hipóteses alternativas. O número 30% é hipotético, não benchmark do produto.

**Status:** brainstorming aberto; sem MVP ou arquitetura aprovados, sem experimentos executados.

## Rodada 2 — Descoberta sobre a jornada de aprendizagem

**Contribuição do responsável:** "Não tenho estas respostas (eu também preciso delas)."

### Aprendizado de produto

A hipótese de persona também se aplica ao próprio criador: a experiência precisa ensinar **como identificar evidências** antes de exigir defesa técnica. Não interpretar ausência de resposta como falha no aluno nem como prova de demanda de mercado.

### Exemplo para ensino

Cenário hipotético: execução de 10 para 7 minutos com `spark.sql.shuffle.partitions` de 200 para 80. A redução observada é de 30%, mas uma execução isolada não estabelece causalidade.

- Observar: verificar plano físico, partições realmente aplicadas, métricas de tarefas, shuffle, spill e variabilidade.
- Investigar: avaliar AQE, cache, volume, concorrência e diferenças de ambiente.
- Comprovar: repetir testes comparáveis, formular hipótese falsificável e registrar resultados contrários.
- Aprendizado: justificativa coerente e resultado inconclusivo podem demonstrar mais competência do que ganho fortuito.

### Três níveis candidatos (não aprovados)

1. **Aprender a observar:** conceitos e interpretação de métricas e planos.
2. **Aprender a investigar:** hipóteses e escolha de evidências.
3. **Aprender a comprovar:** testes controlados, explicação causal e defesa técnica.

**Risco a testar:** transformar o produto em curso genérico; diferencial exigirá efeito sobre desempenho independente em casos novos. Não avançar o M0 com base apenas nessa observação.

### Próxima pergunta acessível ao aprendiz

Em vez de pedir imediatamente todos os critérios técnicos, perguntar: **"O tempo de 7 minutos aconteceu uma vez ou várias vezes?"** A resposta guiará o ensino de variabilidade e repetição sem antecipar toda a solução.

**Status:** sessão de brainstorming aberta. Nenhum MVP ou arquitetura aprovado.

## Rodada 2 — Resposta sobre repetibilidade

**Contribuição do responsável (literal):** "mais execucoes distingue ambiente quente/frio, disponibilidade de maquinas/workers, rede e os proprios dados. Reduzo as variavis externas quanto a sua incerteza/variabilidade"

### Análise técnica

O participante identificou fatores de variação relevantes: warm-up/cache/JIT, disponibilidade/concorrência de workers, rede e características dos dados.

**Precisão essencial:** repetições permitem **estimar** dispersão e robustez do resultado; não garantem controle dos fatores externos nem causalidade. Comparar blocos de configurações sem randomização pode confundir mudança de parâmetros com horário, carga do cluster ou cache.

### Princípios de laboratório candidatos (não aprovados)

- Manter dataset e configuração de recursos equivalentes, registrando diferenças inevitáveis.
- Alternar ou randomizar a ordem dos tratamentos A e B e observar aquecimento.
- Repetir medições e analisar mediana/dispersão, não escolher apenas melhor tempo.
- Registrar métricas de CPU, memória, shuffle, spill, executores, tarefas, skew e presença de AQE conforme pertinência.
- Não usar ganho isolado como certificação de causa técnica.
- Exigir tanto a argumentação sobre mecanismo quanto a investigação de explicações alternativas.

**Ideia-semente I18 — Laboratório de causalidade de performance:** comparar duas configurações em execuções repetidas, introduzindo variação de cache e concorrência para ensinar diferença entre **observação, variabilidade e causalidade**. Um resultado inconclusivo fundamentado é aceitável.

### Próxima provocação

Se duas configurações apresentarem distribuições de tempo sobrepostas, **qual decisão responsável seria possível?** Dar ao aluno opção de: manter baseline, realizar novo experimento ou propor mudança com ressalvas, justificando o custo da incerteza.

**Status:** brainstorming aberto, nenhum experimento executado, nenhum escopo aprovado.

## Rodada 3 — Decisão sob incerteza (contribuição do responsável)

> "Manter a configuração atual até existir evidência suficiente."

### Avaliação

A escolha é tecnicamente defensável para os dados fictícios apresentados: A = [8.5, 7.9, 8.2, 7.7, 8.3] min, média 8.12; B = [8.1, 8.4, 7.8, 8.0, 8.2] min, média 8.10; diferença média 0.02 min (=1.2 s, ~0.25% de A). Cinco observações não demonstram superioridade, especialmente sem controle de carga, pareamento ou ambiente. Manter baseline não prova que baseline seja superior: registra **insuficiência de evidência para troca**.

### Contestação

- **Custo de inação:** baseline pode ser muito caro; investigar mais também custa.
- **Custo de mudança:** regressão, rollback, riscos de disponibilidade e operação.
- **Decisão contextual:** a mesma evidência pode justificar decisões diferentes conforme impacto e tolerância a risco.

### I19 — Decisão técnica sob incerteza

Cenário didático: aprendiz escolhe manter, investigar ou experimentar uma mudança reversível, defendendo risco, custo, incerteza, critério de aprovação e rollback. Avaliar julgamento técnico, não premiar uma resposta única.

### Nova provocação — Rodada 4: decisão com impacto financeiro

Dois jobs equivalentes são executados diariamente. Configuração atual custa R$ 100/dia. Alternativa estima economia de R$ 20/dia, **mas** em uma medição ocorreu regressão de 30% de duração. Os valores são inteiramente fictícios. Como o aprendiz deveria planejar um experimento de baixo risco para distinguir economia real de ruído? Deve definir uma métrica de custo, um limite de regressão, repetição e possibilidade de voltar à configuração original.

**Status:** brainstorming aberto, sem escopo aprovado nem experiência executada.

## Rodada 4 — Contrato prévio de número de execuções

**Contribuição literal do responsável:** "um acordo sobre o numero de execucoes com a config alternativa para avaliar o resultado"

### Avaliação

A ideia introduz pré-compromisso de medição, reduzindo a tentação de escolher uma amostra conveniente depois de observar resultados. **Contestação:** o número de execuções isoladamente não garante segurança, comparação justa ou poder estatístico. Exige também baseline sob condições equivalentes, condições de parada, métricas de custo e latência, e incerteza.

### I20 — Contrato de experimento (ideia-semente, não escopo aprovado)

Antes de executar, aprendiz define: hipótese e métrica principal; mínimo de execuções por variante (10 por configuração apenas como exemplo didático, não tamanho amostral validado); comparação sob mesmos dados/carga/recursos; ordem alternada/randomizada; limiar de regressão operacional e condição de interrupção; procedimento de rollback; tratamento de resultados inconclusivos.

**Falha instrutiva:** se uma execução ameaçar SLA, o contrato deve prever interrupção antecipada em vez de exigir completar todas as repetições.

### Próxima provocação

"Se a alternativa ficar mais barata, mas uma execução ameaçar o SLA, você continuaria o teste? Que limite acordaria para interrompê-lo?" A resposta pode ser qualitativa e não requer fórmula estatística.

**Estado:** brainstorming ainda aberto; hipótese educacional não validada; nenhuma execução real ou provisionamento.
