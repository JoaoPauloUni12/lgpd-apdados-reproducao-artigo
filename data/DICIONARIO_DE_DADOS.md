# Dicionário de dados

## `raw/base_apdados_original.xlsx` (201 linhas, 14 colunas)

| Coluna | Descrição |
|---|---|
| Data | Data da decisão ou do fato. Uma linha tem data inválida (01/01/1970) e é removida na limpeza. |
| Estado | UF do tribunal ou órgão. |
| Sanções | Tipo de sanção (judicial, administrativa), com grafias variadas. |
| Emissor | Tribunal ou órgão que emitiu a decisão (por exemplo TJSP, STJ, ANPD). |
| Status | Situação do processo (primeira ou segunda instância, em andamento etc.). |
| Penalidade | Descrição da penalidade ou do resultado. |
| Valor [R$] | **Texto livre** com o valor. Pode conter `200 UFESPs`, `3 salários`, pedidos não concedidos, multas diárias com teto. |
| Condenações | Tipo de condenação (indenização por danos morais, obrigação de fazer etc.). |
| Segmento | Setor da parte demandada, com cerca de 116 rótulos distintos. |
| Lei | Lei invocada (LGPD, CDC, Marco Civil etc.). |
| Artigo | Artigos citados (texto livre). |
| Descrição | Resumo do caso. |
| Observações | Notas de quem compilou o registro (inclui alertas como "confirmar no inteiro teor"). |
| LINK | `Externo` para registros da APDados; URL para os 29 registros complementares. |

## `processed/base_tratada.csv` (196 linhas)

| Coluna | Descrição |
|---|---|
| ID | Identificador sequencial (1 a 196). |
| Data | Data em formato AAAA-MM-DD (um registro com data corrigida, ver README). |
| Ano | Ano da data. |
| Estado | UF. |
| Emissor | Tribunal ou órgão. |
| **Fonte** | `APDados` (170) ou `Complementar` (26). |
| Sancao | `Judiciais`, `Administrativas` ou `Desconhecido`. Em `Administrativas` entram 4 sanções e 4 processos/medidas da ANPD (os 4 complementares). |
| Lei | Lei padronizada (LGPD, CDC, Constituição Federal, Marco Civil da Internet etc.). |
| Artigos_LGPD | Números dos artigos da LGPD citados, separados por `;`. |
| Condenacao | Tipo de condenação padronizado. |
| Segmento | Categoria de segmento padronizada (32 categorias; ver `docs/mapeamento_segmentos.csv`). |
| Valor_categoria | `Valor em R$`, `Sem valor informado`, `Multa diária/teto ou valor ambíguo`, `Não monetário (UFESP/salários)` ou `Pedido não concedido`. |
| Valor_R$ | Valor numérico, preenchido só quando `Valor_categoria` = `Valor em R$` (86 registros). |
| Link | `Externo` (APDados) ou URL do registro complementar. |

Os campos de texto livre da planilha (Descrição, Observações, Penalidade) **não** foram incluídos na base tratada.
