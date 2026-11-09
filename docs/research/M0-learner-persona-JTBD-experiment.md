# M0 — Persona aprendiz e validação do JTBD (EXP-M0-01)

**Data:** 2026-11-08  
**Status:** Proposta de descoberta, **não validada**. Nenhuma entrevista, participante, protótipo ou teste foi executado.  
**Contexto:** continuação de [M0 — diagnóstico Spark](./M0-spark-diagnostics-discovery.md). Persona priorizada pelo responsável: **engenheiro de dados em aprendizado**.  
**Referência metodológica:** BMad Forge Idea (questionamento crítico; sem executar agente instalado).

## 1. Definição de persona (hipótese)

Engenheiro de dados com fundamentos de DataFrames/SQL/PySpark, mas pouca experiência em interpretar Spark UI, stages, tasks, shuffle, spill, skew, planos físicos e AQE. Estuda com cenários reais para adquirir autonomia de diagnóstico.

**Critérios de triagem propostos:** já criou/executou um job Spark; sabe explicar ações/transforms em nível básico; não diagnostica rotineiramente aplicações Spark em produção de forma independente. Registrar autoavaliação e exercício de entrada, sem usar senioridade/título como proxy suficiente.

**Excluídos da amostra primária:** iniciantes absolutos em programação ou Spark e especialistas em tuning (podem ser avaliados em pesquisas separadas).

**Distinção:** usuário = aprendiz; influenciador = mentor/Tech Lead; comprador/pagador = ainda desconhecido. Não presumir monetização.

## 2. JTBD hipotético

> **Quando** tenho um job Spark lento e não consigo interpretar os sinais de execução, **quero** formar e testar hipóteses a partir de evidências reais, **para** explicar a causa provável, justificar uma intervenção e verificar seu efeito em um problema novo — sem depender de receita de parâmetros ou resposta pronta.

**Funcional:** localizar gargalo e evidência; **cognitivo:** entender causalidade e incerteza; **profissional:** defender decisão fundamentada.

**Resultados desejados candidatos:** maior acerto de diagnóstico independente em caso novo; melhor justificativa; menos mudanças sem evidência. Não confundir velocidade de completar exercícios, satisfação e aprendizagem transferível.

## 3. Contestação explícita

| Objeção adversarial | Como a hipótese pode ser falsificada |
| --- | --- |
| A dor é falta de prática, não falta de produto | Acompanhamento humano, exercícios estáticos e Spark UI geram resultado igual ou superior |
| Guias dão a resposta e geram dependência | Melhor desempenho durante treino, mas nenhuma melhora no caso novo sem dicas |
| Learning-by-doing existe em cursos gratuitos e docs oficiais | Usuários não encontram diferença significativa ou preferem alternativas existentes |
| Métricas são ambíguas | Casos aceitam múltiplas hipóteses; tutor força diagnóstico falso ou simplista |
| O estudante não tem acesso a clusters/event logs reais | Não consegue reproduzir atividade nem interpretar artefatos |
| AQE já resolve parte do problema | Recomendações de tuning ignoram otimizações automáticas ou contexto |
| Ferramenta vira plataforma educacional genérica | Alto custo de conteúdo/UX sem vantagem mensurável |
| Aprendizado aparente é efeito de familiaridade com cenário | Acerto cai ao mudar dataset, mecanismo e sintoma |
| Produto perde para material gratuito | Guia estático causa mesmo ganho sem custo de desenvolvimento |

**Hipótese diferencial mais estreita a testar:** um ciclo guiado de *hipótese → evidência → experimento → defesa → feedback* melhora a capacidade de diagnosticar um caso não visto, em relação a estudar com materiais convencionais.

## 4. Alternativas de intervenção antes de construir software

A. Material oficial Spark UI + roteiro de investigação escrito.  
B. Exercício guiado de papel/Markdown com pistas graduais e rubrica de avaliação.  
C. Protótipo manual do fluxo com tutor humano ('concierge'), sem IA, sem backend.  
D. Aplicativo completo.

**Escolha para experimento:** comparar A versus B/C. **D está bloqueado**. Criar conteúdo e protótipo estático exige decisão de execução posterior, não é autorização automática para construir app.

## 5. EXP-M0-01 — Teste de aprendizagem e transferência

### Pergunta falsificável

A orientação baseada em evidências melhora **diagnóstico independente em um caso inédito**, em comparação com estudo convencional de duração equivalente?

### Amostra e recrutamento (meta, não coleta concluída)

- 8–12 engenheiros de dados aprendizes; amostra de conveniência exploratória.
- Triar experiência prévia; registrar tempo de estudo, experiência Spark e familiaridade com UI.
- Consentimento voluntário; pseudonimizar relatos; não coletar logs de produção ou dados de clientes.
- Número insuficiente para inferência estatística robusta ou alegação de eficácia populacional; reportar resultados descritivos e intervalos quando apropriados.

### Materiais e ambientes

- Três casos sintéticos distinguíveis: skew; shuffle/spill; baixo paralelismo. Preparar **pares equivalentes** por dificuldade para evitar que teste repita o treino.
- Pacote estático: resumo de contexto, plano, métricas e capturas de Spark UI/eventos sintéticos, com gabarito auditado por revisor experiente.
- Incluir casos em que uma hipótese inicialmente plausível é refutada por outra métrica; registrar versão Spark e AQE.
- Verificar que exemplos não dependem de comportamento específico não reproduzível.
- Sem provisionar AWS/Databricks e sem logs internos.

### Design do piloto

1. **Triagem + pré-teste independente** (5–10 min): mesmo nível de dificuldade para todos, sem ajuda; mede nível inicial.
2. **Treino** (15–20 min) dividido aleatoriamente em A (referências oficiais + UI + roteiro convencional) e B (fluxo guiado progressivo), com tarefas de complexidade semelhante e **mesmo tempo**.
3. **Teste de transferência não visto** (15 min): caso diferente e equivalente, sem pistas ou feedback, para ambos os grupos. Trocar variantes entre participantes e, se possível, equilibrar ordem.
4. **Defesa técnica curta** (5 min): pedir evidências, hipóteses alternativas, teste e limitações.
5. **Preferência e dificuldades** (5 min): entrevista breve depois da avaliação.
6. Se viável, **retenção em 7 dias**, caso novo e sem ajuda, como extensão opcional previamente declarada.

**Risco de validade:** com 8–12 pessoas, diferença individual pode dominar. Não apresentar relação causal definitiva. Uma segunda rodada com amostra ampliada é necessária se os sinais forem promissores.

### Rubrica independente — pontuação 0–10

| Critério | Pontos | Definição |
| --- | ---: | --- |
| Identificação da hipótese principal | 0–2 | Coerência com gabarito e ambiguidade documentada |
| Identificação de métricas pertinentes | 0–3 | Nomeia números/sinais corretos; sem inventar métricas |
| Diferenciação de causas alternativas | 0–2 | Reconhece o que as métricas não demonstram |
| Experimento de validação | 0–2 | Intervenção testável com controle de condições |
| Cautela/limitações | 0–1 | Não declara certeza ou ganho não demonstrado |

Avaliação por dois revisores cegos para condição quando possível; resolver discordâncias com critérios prévios. Publicar exemplos de pontuação sem dados pessoais.

### Métrica primária

**Pontuação de transferência (0–10) no caso não visto, sem ajuda**, ajustando interpretação pelo pré-teste. Registrar distribuição por grupo, diferença descritiva e casos individuais, sem exagerar significância.

### Métricas secundárias

- Tempo até justificativa final;
- taxa de hipóteses sem suporte e falsas certezas;
- qualidade da defesa técnica;
- taxa de desistência/conclusão;
- percepção de utilidade (não substitui resultado);
- retenção em 7 dias, se executada.

### Critérios de decisão propostos (heurísticas, não valores validados)

- **Avançar para novo experimento, NÃO diretamente para MVP:** diferença mediana de **≥ 2 pontos / 10** a favor de B no teste independente, nenhum aumento relevante de afirmações infundadas, e feedback qualitativo consistente de pelo menos 3 participantes sobre valor específico. Exigir replicação e examinar pré-teste.
- **Iterar:** sinal positivo fraco, barreiras de compreensão, heterogeneidade alta, ou diferença de 1–<2 pontos; revisar materiais e repetir.
- **Pivotar para conteúdo aberto/guia:** material convencional empata ou supera fluxo guiado, ou melhoria aparece apenas durante o treino, sem transferência.
- **Abandonar ou redefinir persona:** dificuldade não é relevante para maioria triada; ninguém relata situações concretas; conteúdo básico basta.

**Nunca** apresentar esses limiares como validação estatística ou prova causal; eles são gates de decisão do projeto.

## 6. Hipóteses priorizadas

| ID | Afirmação | Evidência mínima | Status |
| --- | --- | --- | --- |
| H-L1 | Aprendizes encontram dificuldade concreta em interpretação de execução | ≥5 entrevistas sobre casos passados e artefatos usados | Não testada |
| H-L2 | Dificuldade permanece apesar das alternativas gratuitas | Descrição de lacuna específica perante Spark UI/docs/cursos | Não testada |
| H-L3 | Guia melhora transferência independente | EXP-M0-01 comparativo | Não testada |
| H-L4 | O guia ensina a argumentar sem respostas automáticas | Rubrica de defesa, análise de falsas certezas | Não testada |
| H-L5 | Produto vale mais que conteúdo estático | Preferência sustentada por resultado e tarefas reais | Não testada |

## 7. Entrevistas exploratórias: perguntas sem indução

- Conte sobre a última vez que teve dificuldade com um job Spark lento. O que você fez primeiro?
- Quais métricas ou telas consultou? Qual foi a primeira hipótese e como você a testou?
- O que você não conseguiu explicar? Como resolveu ou encerrou?
- Que curso, ferramenta ou pessoa ajudou? O que continuou difícil?
- Se encontrasse um caso semelhante amanhã, como saberia que consegue resolvê-lo sozinho?

**Evitar:** 'Você gostaria de uma IA que detectasse o problema?'; sondar comportamento passado, não intenção hipotética.

## 8. Separação de iniciativas

- **Produto SparkLens:** personas, JTBD, diferenciação, experimentos e eventual software.
- **Life Learning:** metodologia pessoal, competências, avaliações e três esferas Local/AWS/Databricks. Resultados do piloto não aprovam competências automaticamente.
- **M0 aberto:** ainda são necessários prova de dor, benchmark, testes, avaliação de nome (há Qubole Sparklens) e decisão explícita do responsável antes de PRD.

## 9. Fontes e limites da evidência

- BMad Explore and Validate: https://docs.bmad-method.org/plan/explore-and-validate-an-idea/
- Spark Web UI: https://spark.apache.org/docs/latest/web-ui
- Spark Monitoring: https://spark.apache.org/docs/latest/monitoring
- Spark Performance / AQE: https://spark.apache.org/docs/latest/sql-performance-tuning
- Databricks Free Edition: https://www.databricks.com/learn/free-edition
- Qubole Sparklens: https://github.com/qubole/sparklens
- McDermott, 2021, retrieval practice: https://doi.org/10.1146/annurev-psych-010419-051019
- Evidence on worked examples and transfer: https://pubmed.ncbi.nlm.nih.gov/23964423/

Estas fontes informam a fundamentação de *competição, conteúdo e método pedagógico*. Nenhuma mede ainda a eficácia ou adoção do SparkLens.
