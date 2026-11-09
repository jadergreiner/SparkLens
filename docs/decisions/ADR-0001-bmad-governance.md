# ADR-0001 — BMad como processo de entrega do SparkLens

- **Data:** 2026-11-08
- **Status:** Proposta (requer validação do responsável pelo projeto)

## Contexto

SparkLens é um produto público em estágio inicial, também utilizado como cenário prático do Life Learning. É necessário separar decisões de produto/engenharia da governança de aprendizagem.

## Decisão proposta

Adotar BMad v6.12 estável como referência para descoberta, planejamento, arquitetura, implementação e revisão, com gates explícitos; começar por Product Brief antes de PRD e código. Manter Life Learning como autoridade das competências e seus critérios de aprovação.

## Consequências positivas

- Rastreabilidade entre problema, requisitos, implementação e evidências.
- Menor risco de transformar o produto em exercícios desconexos.
- Separação de responsabilidades entre engenharia e ensino.

## Trade-offs e riscos

- Excesso de processo em um projeto solo: manter artefatos proporcionais.
- Divergência futura entre versões BMad: registrar versão e migração.
- Confundir artefatos preparatórios com agentes instalados: declarar estados explicitamente.

## Alternativas consideradas

1. Desenvolver sem metodologia formal — mais rápido inicialmente, mas com menor rastreabilidade.
2. Instalar BMad v7 alpha imediatamente — rejeitado por ora devido à instabilidade declarada.
3. Aplicar Life Learning como processo único — rejeitado por misturar avaliação pedagógica e evolução de produto.

## Condições de aprovação

Validar versão-alvo, compatibilidade com a IDE e política de PRs. Este ADR não autoriza provisionamento.
