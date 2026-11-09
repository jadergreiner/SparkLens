# Adoção do BMad — SparkLens

**Status:** iniciado por documentação; instalação do runtime/agentes ainda **não verificada**.

## Baseline de versão

- **BMad v6.12 (estável)** como versão inicial.
- A documentação da versão 7 foi identificada como preview alpha em 2026-11-08; migração deve ser decisão separada.
- Fonte: https://docs.bmad-method.org/start/install-bmad/
- Consultar a documentação correspondente à versão instalada antes de executar comandos ou customizações.

## Instalação local (a executar pelo desenvolvedor)

Pré-requisitos informados para v6.12: Node.js 20.12+, Python 3.10+ e uv.

Na raiz do repositório:

```bash
npx bmad-method install
```

Selecionar a IDE/agente compatível durante a instalação e validar a estrutura gerada segundo a documentação de **v6.12**.

**Importante:** este commit **não executa** o instalador e não incorpora arquivos oficiais dos agentes BMad. Não executar scripts de terceiros sem revisar seu conteúdo e permissões.

## Fluxo inicial de trabalho

| Gate | Perspectiva BMad | Entrega | Estado |
| --- | --- | --- | --- |
| M0 / G0 | Analyst | Product Brief validado | Rascunho |
| M1 / G1 | Product Manager | PRD e métricas de sucesso | Bloqueado por G0 |
| M1 / G2 | Architect | Arquitetura e ADRs | Bloqueado por PRD |
| M2 / G3 | Product Owner | Histórias, priorização e aceite | Bloqueado por PRD |
| M2 / G4 | Developer | Implementação, testes, review e demo | Bloqueado por histórias |

Os nomes de agentes representam papéis do método; não significa que os agentes tenham sido executados neste ambiente.

## Fronteira com Life Learning

- **SparkLens:** código, decisões de produto, issues, PRs e evidências públicas.
- **Life Learning:** trilhas e avaliação de competências, com decisão pelo conselho.
- **Notion e Google Drive:** registros canônicos de aprendizagem.
- **Recall:** flashcards de revisão.
- Ao final de uma sessão do Life Learning, identificar aplicação conceitual ou prática ao SparkLens; só transformar em tarefa de produto se houver benefício e critérios de aceite.
- Manter práticas obrigatórias Local/AWS/Databricks no contexto das competências sem forçar infraestrutura de nuvem no produto.

## Regras de mudança

- Abrir PR para mudanças relevantes de escopo, arquitetura e implantação.
- Não tratar hipóteses do Product Brief como requisitos aprovados.
- Atualizar status, decisões e links de evidências após cada gate.
- Evitar duplicar conteúdo governado pelo Life Learning.

## Referências

- https://docs.bmad-method.org/
- https://docs.bmad-method.org/start/install-bmad/
- https://docs.bmad-method.org/reference/skills-and-agents/
