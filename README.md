# TOTVS Chef Web — Base de Conhecimento

Base de conhecimento sobre o **TOTVS Food Service – Linha Chef**, com foco no
**TOTVS Chef Web** (retaguarda web / Gestão Web), construída para servir de
contexto a um agente de IA que apoia a operação do restaurante: tirar dúvidas,
criar tarefas e planejar implementações/integrações.

## Estrutura

| Arquivo | Conteúdo |
|---|---|
| `docs/01-visao-geral.md` | O que é o produto, componentes da Linha Chef, público-alvo, arquitetura |
| `docs/02-modulos-retaguarda.md` | Detalhe dos módulos do Chef Web: cadastros, estoque, financeiro, fiscal, relatórios |
| `docs/03-pdv-e-frente-de-loja.md` | Chef PDV, comanda eletrônica, autoatendimento, KDS |
| `docs/04-integracoes-e-apis.md` | iFood/delivery, TEF, APIs, pontos de integração |
| `docs/05-requisitos-tecnicos.md` | Instalação, requisitos, sincronização nuvem/local |
| `docs/06-releases-e-novidades.md` | Evolução do produto e novidades recentes |
| `docs/99-fontes.md` | Todas as fontes oficiais consultadas |
| `AGENT.md` | Instruções para o agente que usará esta base |

## Como usar com um agente

1. Aponte o agente (Claude Project, CLAUDE.md, RAG etc.) para a pasta `docs/`.
2. Use `AGENT.md` como system prompt / instruções base.
3. Ao criar tarefas ou especificar implementações, cite o módulo e a tela do
   Chef Web envolvidos, conforme a nomenclatura desta base.

> Fontes: documentação pública da TOTVS (TDN — tdn.totvs.com, espaço TChef),
> Central de Atendimento TOTVS e páginas oficiais do produto. Esta base não
> substitui a documentação oficial; em caso de divergência, vale o TDN.
