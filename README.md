# Reprodução e extensão da análise da base APDados sobre a LGPD

Código, base tratada e resultados do artigo **"Aplicação e Compliance da LGPD no Brasil: Reprodução e Extensão da Análise da Base APDados com Decisões Complementares"** (disciplina de Segurança em Redes de Computadores, UNIFESSPA, 2026).

O trabalho reproduz a análise de Ilg et al. (2025) sobre processos e sanções relacionados à LGPD, usando uma base atualizada, e acrescenta quatro análises complementares e uma análise de sensibilidade à origem dos registros.

## Resumo da base

| Item | Valor |
|---|---|
| Linhas na planilha original | 201 |
| Removidas na limpeza | 5 (1 linha vazia com data inválida, 1 duplicata exata, 3 com link/processo divergente) |
| **Registros analisados** | **196** |
| Da APDados (link "Externo") | 170 (2015 a 2024) |
| Complementares (2025 e 2026) | 26 (22 decisões de tribunais + 4 registros da ANPD) |
| Período | jan/2015 a out/2026 |

> **Atenção sobre os registros complementares.** Foram compilados a partir de resumos de decisões, com apoio de ferramenta de inteligência artificial, e **não foram conferidos no inteiro teor** (exceto 1, cuja data foi corrigida). Veja `docs/LIMITACOES.md` e `docs/registros_complementares.csv`. O artigo traz uma análise de sensibilidade com e sem esses registros.

## Estrutura

```
.
├── README.md
├── LICENSE                         # código (MIT)
├── DADOS_LICENCA.md                # termos de uso dos dados
├── CITATION.cff                    # como citar
├── requirements.txt
├── data/
│   ├── raw/base_apdados_original.xlsx       # planilha original (201 linhas)
│   ├── processed/base_tratada.csv           # 196 registros, campos padronizados
│   └── DICIONARIO_DE_DADOS.md
├── notebooks/Analise_APDados_LGPD.ipynb     # todas as análises (executar tudo)
├── scripts/verificar_base.py                # confere se uma planilha é a base do artigo
├── docs/
│   ├── LIMITACOES.md
│   ├── mapeamento_segmentos.csv             # rótulo original -> categoria (116 -> 32)
│   └── registros_complementares.csv         # os 29 registros de outra fonte e seus alertas
└── results/
    ├── figuras/                             # fig1 a fig7 e analise10_1 a analise10_4
    └── tabelas_apdados.xlsx                 # tabelas de apoio a cada figura
```

## Como reproduzir

**No Google Colab:** abra `notebooks/Analise_APDados_LGPD.ipynb` pelo GitHub, execute tudo e, quando pedido, envie `data/raw/base_apdados_original.xlsx`.

**Localmente:**
```bash
pip install -r requirements.txt
python scripts/verificar_base.py data/raw/base_apdados_original.xlsx   # deve imprimir "base compatível com o artigo"
cd notebooks && jupyter notebook Analise_APDados_LGPD.ipynb            # Executar tudo
```
As figuras e tabelas são gravadas em `results/saida/`. A ordem entre segmentos com o mesmo número de registros (por exemplo, Proteção ao Crédito e Instituição Financeira, com 14 cada) pode variar entre execuções; o empate na 10ª posição (Hospital/Saúde e Serviços de Internet, 11 cada) é resolvido em ordem alfabética.

### Parâmetros do notebook (seção 1)
| Parâmetro | Valor padrão | Efeito |
|---|---|---|
| `SEPARAR_PROCESSOS_ANPD` | `False` | `True` separa, na Figura 2, os processos/medidas da ANPD das sanções aplicadas |
| `INCLUIR_EMPATES_TOP` | `False` | `True` inclui segmentos empatados na 10ª posição (Figuras 6 e 7) |
| `MIN_REG_DIVERSIDADE`, `MIN_N_VALORES`, `MIN_REG_LEI` | 4, 3, 3 | cortes mínimos das análises complementares |

### Correção de data
Um registro (TJSP, Agravo de Instrumento nº 2028508-48.2025.8.26.0000) tinha a data 26/09/2026 na planilha e foi corrigido para **14/10/2025** após consulta ao acórdão (`CORRECOES_DATA` no notebook). Por isso a contagem por ano é 15 em 2025 e 11 em 2026.

## Fontes
- **APDados** (https://apdados.org/violacoes): registros até 2024.
- **ANPD** (gov.br): 4 registros de processos e medidas administrativas de 2025 e 2026.
- **Decisões de tribunais** (STJ, TJSP, TJMG, TJPR, TJRS): 22 registros, com link de acesso na coluna `Link`.

## Privacidade
A base não contém nomes de partes pessoas físicas. Ao acrescentar registros, publique apenas tribunal, número do processo e data, e não os nomes das partes.

## Como citar
Veja `CITATION.cff`.

## Licença
Código: MIT (`LICENSE`). Dados: veja `DADOS_LICENCA.md`.
