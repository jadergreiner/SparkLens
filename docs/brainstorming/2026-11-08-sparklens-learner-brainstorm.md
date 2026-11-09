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
