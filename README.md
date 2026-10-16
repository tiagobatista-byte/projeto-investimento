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

- **VF** (`FV`): `=FV(Taxa_mensal; Quantidade_anos*12; Aport*-1)` calcula o patrimônio acumulado com aportes mensais. A taxa é mensal, por isso os anos são multiplicados por 12. Os cenários usam a mesma fórmula com os anos da coluna A (`$A26`, `$A27`...).
- **Dividendo mensal**: `Patrimonio * rendimento_carteira`.
- **PROCV** (`VLOOKUP`): `=VLOOKUP($C$32&"-"&B36; Planilha2.$A:$D; 4; FALSE)` monta a chave `PERFIL-TIPO` (ex.: `MODERADO-PAPEL`), procura na Planilha2 e devolve o percentual. O valor em reais é percentual × aporte.

## Intervalos nomeados

Todos apontam para a **Planilha1** e são usados nas fórmulas:

| Nome | Célula |
|---|---|
| `Salario` | `C13` |
| `rendimento_carteira` | `C14` |
| `Sugestao_investimento` | `C15` |
| `Aport` | `C19` |
| `Quantidade_anos` | `C20` |
| `Taxa_mensal` | `C21` |
| `Patrimonio` | `C22` |

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

## Ajustes feitos nesta versão

- Intervalos nomeados recriados (estavam com `#REF!`) e aplicados nas fórmulas.
- Referências dos cenários padronizadas (`$A26` em todas as linhas).
- Célula "Por quantos anos?" formatada como número, não moeda.
- Erros de digitação corrigidos nos rótulos.
- Removida a célula de teste da Planilha2.

## Aviso

Projeto educacional. Não é recomendação de investimento.
