# DIO Invest – Projeto de Investimento em FIIs

Planilha (`Projeto_Investimento.ods`) que simula o aporte mensal em fundos imobiliários e sugere a divisão do valor por tipo de FII, conforme o perfil do investidor.

## Como usar

1. Abra `Projeto_Investimento.ods` no LibreOffice Calc (ou importe no Excel / Google Planilhas).
2. Na **Planilha1**, preencha: salário (`C13`), rendimento da carteira (`C14`), aporte mensal (`C19`), anos (`C20`) e taxa mensal (`C21`).
3. Escolha o perfil em `C32` (CONSERVADOR, MODERADO ou AGRESSIVO) na lista suspensa.
4. Veja os resultados nos blocos de investimento mensal, cenários e distribuição por tipo de FII.

## O que a ferramenta responde

| Pergunta | Onde |
|---|---|
| Quanto investir por mês (sugestão de 30% do salário)? | `C15` |
| Quanto terei ao final de N anos? Qual o dividendo mensal? | `C22` e `C23` |
| Como fica em 2, 5, 10, 20 e 30 anos? | `C26:D30` |
| Como dividir o aporte entre os tipos de FII? | `C32:D42` |

## Como `VF` e `PROCV` entram nos cálculos

- **VF** (`FV`): `=FV(C21; C20*12; C19*-1)` calcula o patrimônio acumulado com aportes mensais. A taxa é mensal, por isso os anos são multiplicados por 12. Os cenários usam a mesma fórmula com os anos da coluna A.
- **Dividendo mensal**: patrimônio × rendimento da carteira (`C14`).
- **PROCV** (`VLOOKUP`): `=VLOOKUP($C$32&"-"&B36; Planilha2.$A:$D; 4; FALSE)` monta a chave `PERFIL-TIPO` (ex.: `MODERADO-PAPEL`), procura na Planilha2 e devolve o percentual. O valor em reais é percentual × aporte.

## Intervalos nomeados

`Salario`, `rendimento_carteira`, `Sugestao_investimento`, `Aport`, `Quantidade_anos`, `Taxa_mensal` e `Patrimonio`.

> Atenção: no arquivo atual todos apontam para `#REF!` e nenhuma fórmula os utiliza. Devem ser recriados apontando para `C13`, `C14`, `C15`, `C19`, `C20`, `C21` e `C22` da Planilha1.

## Percentuais por perfil (Planilha2)

| Tipo de FII | Conservador | Moderado | Agressivo |
|---|---|---|---|
| Papel | 30% | 32% | 50% |
| Tijolo | 50% | 35% | 10% |
| Híbridos | 10% | 8% | 5% |
| FOFs | 10% | 5% | 5% |
| Desenvolvimento | 0% | 10% | 20% |
| Hotelarias | 0% | 10% | 10% |

Os valores estão digitados manualmente; cada perfil soma 100%. _Origem/justificativa: (preencher)._

## O que foi alterado em relação à ferramenta do Expert

_(Preencher com as suas alterações.)_

## Aviso

Projeto educacional. Não é recomendação de investimento.
