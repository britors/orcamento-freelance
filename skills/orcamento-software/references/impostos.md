# Impostos sobre o faturamento (Brasil)

Use este arquivo para chegar na **alíquota efetiva** que entra no preço (passo 6 do SKILL.md). Os números valem para **2026**. Lei tributária muda todo ano: diga ao usuário que confira a alíquota final com o contador dele, e trate a alíquota como premissa na planilha.

A alíquota que entra no gross-up é a soma do que incide **sobre a nota fiscal**. Encargos sobre o pró-labore (INSS) são custo fixo do negócio e entram no custo-hora, não aqui.

## Qual regime o freelancer usa

| Regime | Quem cabe | Teto de faturamento |
|---|---|---|
| MEI | Pessoa sozinha, sem sócio, com ocupação permitida | R$ 81.000 por ano |
| Simples Nacional | ME e EPP | R$ 4,8 milhões por ano (ISS dentro do DAS até R$ 3,6 milhões) |
| Lucro Presumido | Qualquer empresa até o teto | R$ 78 milhões por ano |

Se o usuário não souber o regime, pergunte. Se ele estiver como pessoa física (RPA ou carnê-leão), avise que a tributação vai até 27,5% de IR mais INSS e que abrir empresa costuma compensar a partir de poucos projetos por ano.

## MEI

- **Desenvolvimento de software não é ocupação permitida no MEI.** Programador, desenvolvedor, analista de sistemas e consultor de TI ficam de fora. Se o usuário fatura software como MEI, avise do risco de desenquadramento e recomende conversar com o contador.
- Imposto fixo mensal (DAS), independente do faturamento: INSS de 5% do salário mínimo (R$ 81,05 com o mínimo de R$ 1.621) + R$ 5 de ISS para serviços = **R$ 86,05 por mês**.
- Alíquota efetiva para o orçamento: DAS anual ÷ faturamento anual previsto. Ex.: R$ 1.032,60 ÷ R$ 81.000 ≈ 1,3%.
- Estourou o teto em até 20% (até R$ 97.200): paga DAS de ME sobre o excesso e vira ME no ano seguinte. Acima de 20%: desenquadramento retroativo a janeiro. Se o projeto orçado faz o faturamento do ano passar de R$ 81 mil, avise antes de calcular.

## Simples Nacional

Desenvolvimento de software (CNAEs 6201-5/01 sob encomenda, 6202-3/00 customizável, 6204-0/00 consultoria em TI) fica no **Anexo V**, ou no **Anexo III** quando o **Fator R** é de pelo menos 28%.

> **Fator R** = folha de salários dos últimos 12 meses (inclui pró-labore e encargos) ÷ receita bruta dos últimos 12 meses (RBT12).

Na prática, o freelancer que tira pró-labore de pelo menos 28% do faturamento paga pelo Anexo III, bem mais barato. Esse pró-labore paga 11% de INSS e IRPF pela tabela, e isso entra no custo-hora.

### Alíquota efetiva

> Alíquota efetiva = (RBT12 × alíquota nominal − parcela a deduzir) ÷ RBT12

Use a RBT12 que a empresa terá **nos meses em que vai faturar o projeto**, incluindo o próprio projeto quando ele for grande. Empresa com menos de 12 meses: RBT12 = média mensal × 12.

**Anexo III** (Fator R ≥ 28%)

| Faixa | RBT12 | Alíquota nominal | Parcela a deduzir |
|---|---|---:|---:|
| 1 | até R$ 180.000 | 6,00% | 0 |
| 2 | até R$ 360.000 | 11,20% | R$ 9.360 |
| 3 | até R$ 720.000 | 13,50% | R$ 17.640 |
| 4 | até R$ 1.800.000 | 16,00% | R$ 35.640 |
| 5 | até R$ 3.600.000 | 21,00% | R$ 125.640 |
| 6 | até R$ 4.800.000 | 33,00% | R$ 648.000 |

**Anexo V** (Fator R < 28%)

| Faixa | RBT12 | Alíquota nominal | Parcela a deduzir |
|---|---|---:|---:|
| 1 | até R$ 180.000 | 15,50% | 0 |
| 2 | até R$ 360.000 | 18,00% | R$ 4.500 |
| 3 | até R$ 720.000 | 19,50% | R$ 9.900 |
| 4 | até R$ 1.800.000 | 20,50% | R$ 17.100 |
| 5 | até R$ 3.600.000 | 23,00% | R$ 62.100 |
| 6 | até R$ 4.800.000 | 30,50% | R$ 540.000 |

Exemplo com RBT12 de R$ 240.000: Anexo III = (240.000 × 11,2% − 9.360) ÷ 240.000 = **7,30%**; Anexo V = (240.000 × 18% − 4.500) ÷ 240.000 = **16,13%**.

O DAS já inclui IRPJ, CSLL, PIS, COFINS, CPP (INSS patronal) e ISS, então a alíquota efetiva é a alíquota inteira do orçamento. Acima de R$ 3,6 milhões de RBT12, o ISS sai do DAS e é pago à parte ao município.

## Lucro Presumido (serviços)

Sobre o faturamento:

| Tributo | Cálculo | Sobre a nota |
|---|---|---:|
| IRPJ | 15% sobre presunção de 32% | 4,80% |
| Adicional de IRPJ | 10% sobre o lucro presumido acima de R$ 60.000 por trimestre (faturamento acima de R$ 187.500 por trimestre) | 0 a 3,20% |
| CSLL | 9% sobre presunção de 32% | 2,88% |
| PIS (cumulativo) | | 0,65% |
| COFINS (cumulativo) | | 3,00% |
| ISS | Alíquota do município (2% a 5%) | 2% a 5% |
| **Total sem adicional** | | **13,33% a 16,33%** |

- **LC 224/2025:** a parcela da receita bruta anual acima de R$ 5 milhões tem presunção 10% maior (32% → 35,2%). Só afeta empresas acima desse faturamento, e a regra está sendo questionada no STF.
- **INSS patronal:** 20% sobre o pró-labore, fora do faturamento. Entra no custo-hora.
- **Retenções na fonte** quando o cliente é empresa: IRRF de 1,5% e PIS/COFINS/CSLL de 4,65% podem ser retidos na nota. Não é custo a mais (abate dos tributos devidos), mas reduz o caixa de cada parcela. Vale citar na proposta que o valor é bruto.

Compare com o Simples: abaixo de alguns milhões de faturamento, o Simples no Anexo III quase sempre sai mais barato. O Presumido costuma compensar só no Anexo V sem Fator R e com faturamento mais alto. Decisão de regime é do contador.

## Distribuição de lucros

Desde janeiro de 2026 (Lei 15.270/2025), lucros acima de R$ 50 mil por mês, de uma mesma empresa para uma mesma pessoa física, têm retenção de 10% de IR na fonte, em qualquer regime. A aplicação ao Simples está sendo contestada no STF. Não entra na alíquota do orçamento, mas avise o usuário quando o projeto for grande o bastante para isso.

## Reforma tributária

- **2026:** fase de teste. A nota destaca CBS de 0,9% e IBS de 0,1%, compensáveis com PIS/COFINS; para quem cumpre as obrigações acessórias, não há custo a mais. O Simples segue igual.
- **2027:** a CBS substitui PIS e COFINS para empresas fora do Simples. Em projeto do Lucro Presumido com parcelas faturadas a partir de 2027, recomende ao usuário rever a alíquota com o contador e prever na proposta o reajuste do preço por mudança de legislação tributária.
- **2029 a 2033:** o IBS substitui ISS e ICMS aos poucos.

## Na planilha

Na aba Parâmetros, registre: regime, anexo (no Simples), RBT12 usada, alíquota efetiva calculada e a fonte (cálculo do skill ou número do contador). A alíquota efetiva é a célula que alimenta a Precificação.
