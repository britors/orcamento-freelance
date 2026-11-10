<p align="center">
  <img src=".claude-plugin/icon.svg" alt="Ícone do orcamento-freelance: um recibo com R$" width="128">
</p>

# orcamento-freelance

[Português](#português) · [English](#english)

## Português

Plugin do [Claude Code](https://claude.com/claude-code) que orça projetos de software sob encomenda com **preço fechado**. Você cola o briefing do cliente; o Claude devolve o cálculo interno numa planilha e a proposta comercial que vai para o cliente.

### O que ele faz

- **Decompõe o escopo** em módulos e tarefas de até 16 h e passa por uma checklist do que costuma ser esquecido (ambientes, deploy, recuperação de senha, LGPD, handoff).
- **Estima em três pontos:** esperado = (otimista + 4 × provável + pessimista) ÷ 6.
- **Monta o preço:** overhead (gestão, QA, deploy, documentação), contingência pelo nível de risco, custos diretos, e impostos e margem por gross-up, sobre o preço e não sobre o custo.
- **Calcula o imposto** pelo seu regime: MEI, Simples Nacional (Anexo III ou V pelo Fator R) ou Lucro Presumido.
- **Entrega dois arquivos:** a planilha `.xlsx` interna, com fórmulas vivas, e a proposta comercial, que mostra um preço único sem horas nem margem.
- **Não força número** quando o escopo é vago: propõe descoberta paga antes da construção.

### Instalação

No Claude Code 2.1.275 ou mais novo, dentro de uma sessão:

```
/plugin install orcamento-freelance --marketplace britors/orcamento-freelance
```

Em versões anteriores:

```
/plugin marketplace add britors/orcamento-freelance
/plugin install orcamento-freelance@orcamento-freelance
```

### Uso

Peça um orçamento ou cole um briefing e pergunte quanto cobrar:

> Um cliente quer um sistema web de agendamento para a clínica dele, com área do paciente, painel do administrador e pagamento online. Quanto cobro e em quanto tempo entrego?

Na primeira vez, o Claude pergunta o seu custo-hora e o regime tributário. Para não responder sempre, preencha `skills/orcamento-software/references/parametros.md`.

### Parâmetros

`references/parametros.md` traz os padrões, todos ajustáveis: margem de 20%; overhead de 12% (gestão), 20% (QA), 8% (deploy) e 5% (documentação); contingência de 10%, 20% ou 35% por risco; 30 horas por semana; pagamento 30/40/30.

As tabelas de impostos ficam em `references/impostos.md`, com valores de 2026. Confirme a alíquota final com o seu contador.

### Estrutura

```
.claude-plugin/plugin.json                              manifesto
.claude-plugin/marketplace.json                         marketplace de um plugin só
skills/orcamento-software/SKILL.md                      fluxo do orçamento
skills/orcamento-software/references/metodologia.md     checklist, calibração e risco
skills/orcamento-software/references/parametros.md      seus parâmetros
skills/orcamento-software/references/impostos.md        MEI, Simples e Lucro Presumido
skills/orcamento-software/references/proposta.md        modelo da proposta
```

## English

[Claude Code](https://claude.com/claude-code) plugin that prices custom software projects at a **fixed price** for Brazilian freelancers. Paste a client brief and Claude returns:

- an internal `.xlsx` with live formulas: scope breakdown, three-point estimates, overhead, risk contingency, taxes and margin (grossed up on the price);
- a formal client proposal showing a single price, without hours or margin.

Taxes cover MEI, Simples Nacional (Annex III/V, Fator R) and Lucro Presumido, with 2026 figures. Skill content is in Portuguese.

Install:

```
/plugin install orcamento-freelance --marketplace britors/orcamento-freelance
```

On older versions, run `/plugin marketplace add britors/orcamento-freelance` and then `/plugin install orcamento-freelance@orcamento-freelance`.

Usage: paste a client brief and ask how much to charge. On first use, Claude asks for your hourly cost and tax regime; to skip that, fill in `skills/orcamento-software/references/parametros.md`.

## Licença / License

[GPL-3.0](LICENSE)
