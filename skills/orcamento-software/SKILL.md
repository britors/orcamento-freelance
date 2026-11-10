---
name: orcamento-software
description: Orça projetos de desenvolvimento de software sob encomenda (freelance) com preço fechado por escopo — decompõe o escopo, estima horas com três pontos, aplica overhead, contingência por risco, impostos e margem, e entrega uma planilha interna de cálculo (.xlsx) e uma proposta comercial formal para o cliente. Use sempre que o usuário pedir orçamento, cotação, estimativa de preço ou de prazo, proposta comercial, "quanto cobrar", "quanto custa fazer", precificação de um sistema, site, app, API, automação ou integração para um cliente, mesmo que ele não use a palavra "orçamento" — por exemplo ao colar um briefing de cliente e perguntar quanto cobrar ou em quanto tempo entrega.
---

# Orçamento de projetos de software (freelance, preço fechado)

Este skill transforma um briefing de cliente em duas entregas:

1. **Planilha interna (.xlsx)** — o cálculo completo: escopo decomposto, horas, custo, contingência, impostos, margem e cronograma de pagamentos. É material de trabalho do freelancer e **nunca** vai para o cliente, porque expõe custo e margem.
2. **Proposta comercial formal** — o documento que o cliente recebe: escopo em linguagem de negócio, exclusões, premissas, marcos, um preço fechado único e condições.

A separação existe porque em preço fechado o cliente compra um resultado, não horas. Mostrar horas convida a negociação item a item e transforma o preço fechado em "banco de horas" disfarçado.

Leia `references/metodologia.md` antes de estimar e `references/proposta.md` antes de redigir a proposta. Os parâmetros do freelancer ficam em `references/parametros.md`. As tabelas de impostos (MEI, Simples Nacional, Lucro Presumido) ficam em `references/impostos.md`.

## Fluxo

### 1. Carregar parâmetros

Leia `references/parametros.md`. Se **custo-hora** ou **alíquota de impostos** estiverem vazios, pergunte ao usuário uma única vez antes de calcular — sem eles o preço é chute. Para a alíquota, pergunte o regime tributário (e, no Simples, a receita dos últimos 12 meses e se o pró-labore chega a 28% do faturamento) e calcule a alíquota efetiva com `references/impostos.md`. Os demais campos têm padrões justificados e só mudam se o usuário pedir.

### 2. Entender o briefing

Extraia do que o usuário trouxe: objetivo do sistema, perfis de usuário, funcionalidades, plataformas (web, mobile, desktop), integrações externas, volume esperado, prazo desejado, quem hospeda e quem fornece conteúdo/design.

Pergunte **apenas o que muda o preço de forma relevante** — no máximo três perguntas por rodada, de preferência com opções clicáveis. Tudo o que não for perguntado vira **premissa explícita** na planilha e na proposta. Isso mantém o fluxo rápido e, ao mesmo tempo, protege o freelancer: premissa escrita é o que permite cobrar mudança de escopo depois.

Perguntas que quase sempre valem a pena quando não estão respondidas:
- Existe design/protótipo pronto ou o design faz parte do escopo?
- Quais integrações externas (pagamento, ERP, APIs de terceiros) e se elas têm documentação/sandbox.
- Web apenas, ou também app mobile (nativo ou híbrido)?

### 3. Avaliar se dá para fechar preço

Preço fechado só é responsável quando o escopo é conhecido o bastante. Se o briefing for vago demais (ex.: "um app tipo Uber", sem telas nem regras), **não force um número**. Proponha em vez disso:
- **Fase 1 — Descoberta paga** (preço fechado pequeno, 1–2 semanas): levantamento de requisitos, fluxos, protótipo de baixa fidelidade e orçamento firme da fase 2.
- **Fase 2 — Construção**: preço fechado calculado após a descoberta, com uma **estimativa indicativa em faixa** apenas para o cliente ter ordem de grandeza.

Explique ao usuário por que escolheu esse caminho.

### 4. Decompor o escopo (EAP)

Monte a estrutura analítica do projeto: **Módulo → Tarefa**. Regras:
- Nenhuma tarefa com estimativa provável acima de **16 h**. Tarefa maior está mal entendida; quebre-a. Tarefas pequenas são estimadas com muito mais precisão.
- Passe pela **checklist de itens esquecidos** em `references/metodologia.md`. Os itens que mais destroem margem em freelance são os que ninguém pediu explicitamente (ambientes, deploy, e-mails transacionais, recuperação de senha, LGPD, responsividade, handoff).

### 5. Estimar cada tarefa (três pontos)

Para cada tarefa, estime **Otimista (O)**, **Mais provável (M)** e **Pessimista (P)** em horas e calcule:

> Esperado = (O + 4M + P) / 6

Use as faixas de calibração de `references/metodologia.md` como sanidade, não como tabela fixa. O pessimista deve refletir um problema real plausível (API mal documentada, regra de negócio que muda), não catástrofe.

### 6. Classificar o risco e calcular

Classifique o risco do projeto (baixo / médio / alto) com os critérios de `references/metodologia.md` e aplique, nesta ordem:

1. **Horas de desenvolvimento** = soma dos esperados.
2. **Overhead** sobre as horas de desenvolvimento: gestão e comunicação, QA/testes, deploy/infra, documentação/handoff (percentuais em `parametros.md`).
3. **Contingência** sobre (desenvolvimento + overhead), conforme o risco.
4. **Custo do trabalho** = horas totais × custo-hora.
5. **Custos diretos** repassados (licenças, domínio, infra no período de desenvolvimento, serviços de terceiros, assets pagos).
6. **Preço** = (custo do trabalho + custos diretos) ÷ (1 − alíquota de impostos − margem).
7. **Arredondar para cima** conforme a regra de `parametros.md`.

A fórmula do passo 6 é *gross-up*: imposto e margem incidem sobre o preço final, não sobre o custo. Somar percentuais sobre o custo (custo × 1,20 × 1,10…) subestima o preço e corrói a margem real — é o erro mais comum em orçamento de freelancer.

Calcule também, para conferência: **valor-hora efetivo** (preço ÷ horas totais), **prazo** (horas totais ÷ horas semanais dedicadas, arredondado para cima em semanas) e **valor-hora para mudanças de escopo** (o valor-hora efetivo, arredondado para cima para múltiplo de R$ 10).

### 7. Gerar a planilha interna

Leia o SKILL.md de **xlsx** antes de criar o arquivo. Estrutura obrigatória, em abas:

| Aba | Conteúdo |
|---|---|
| **Parâmetros** | Custo-hora, alíquota, margem, percentuais de overhead, tabela de contingência por risco, risco escolhido, horas semanais, regra de arredondamento. Células de entrada destacadas. |
| **Escopo** | Módulo, tarefa, O, M, P, Esperado (fórmula), observação. Subtotais por módulo. |
| **Custos diretos** | Item, valor, observação. |
| **Precificação** | Cascata do passo 6 inteira, cada linha uma fórmula referenciando Parâmetros/Escopo/Custos, terminando em preço arredondado, valor-hora efetivo, prazo e valor-hora de mudança. |
| **Pagamentos** | Marcos, percentual, valor (fórmula sobre o preço), evento que libera o pagamento. |
| **Premissas e exclusões** | Tudo o que foi assumido e tudo o que está fora do escopo. |

Tudo com **fórmulas vivas**, nunca valores colados: o usuário vai ajustar margem, risco ou uma estimativa e o preço precisa recalcular sozinho. Nome do arquivo: `orcamento-interno-<cliente>-<projeto>.xlsx`.

### 8. Gerar a proposta comercial

Siga o modelo de `references/proposta.md`. Formato:
- Se a sessão oferece documentos editáveis do Claude (Claude Docs), crie a proposta como Doc — o usuário edita, compartilha e exporta para PDF ou Word.
- Se o usuário pedir Word/.docx explicitamente, ou não houver Claude Docs, gere `.docx` seguindo o SKILL.md de **docx**.

A proposta mostra **um preço fechado único** e as condições de pagamento. Não mostra horas, custo-hora, margem, contingência nem a decomposição por tarefa.

### 9. Resumo no chat

Termine com um resumo curto, em prosa: preço proposto, prazo, horas totais, valor-hora efetivo, nível de risco e o porquê, as duas ou três premissas que mais afetam o preço e qualquer ponto que o usuário deva confirmar com o cliente antes de enviar.

## Princípios

- **Premissa explícita vale mais que pergunta extra.** O orçamento sai rápido e o escopo fica protegido.
- **Não negocie contra si mesmo.** Se o preço calculado parecer alto, mostre de onde ele vem e ofereça cortes de escopo (MVP, fases), nunca cortes silenciosos de horas ou margem.
- **Tudo rastreável.** Qualquer número da proposta deve ser explicável a partir de uma linha da planilha.
- **A proposta não é contrato.** Ela pode virar anexo de um contrato, mas recomende ao usuário revisão jurídica do contrato de prestação de serviços em projetos de valor relevante.
