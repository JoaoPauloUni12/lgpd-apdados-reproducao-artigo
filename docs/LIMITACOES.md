# Limitações

1. **Registros complementares não conferidos.** Dos 26 registros complementares (2025 e 2026), 22 vêm de decisões de tribunais, compiladas a partir de resumos com apoio de IA, e 4 vêm de páginas oficiais da ANPD (conferidas). Das decisões de tribunais, só 1 foi conferida no inteiro teor, e nela a data estava errada (corrigida). A coluna "Alertas" de `registros_complementares.csv` lista as ressalvas que a própria planilha registra (números de processo parcialmente ocultos, "confirmar no inteiro teor", segmento ou lei não identificados).
2. **Cobertura da base.** A base não contém todos os processos relacionados à LGPD no Brasil; a frequência de registros não mede a taxa real de violações.
3. **Série temporal.** A APDados utilizada termina em 2024; os registros de 2025 e 2026 são todos complementares, de outra coleta. A queda após 2022 pode refletir defasagem na inclusão de casos recentes.
4. **Valores.** Só 86 dos 196 registros (44%) têm valor em reais interpretável. O maior valor (R$ 72 milhões, TJMA, 2023) é dano moral coletivo de sentença de primeira instância, e não é comparável aos valores individuais.
5. **Agrupamento de segmentos.** Feito por regras textuais (116 rótulos em 32 categorias). A categoria "Poder Público" também agrega ações de controle de constitucionalidade.
6. **Instâncias superiores.** Não se acompanhou o resultado de recursos.
7. **Sanções administrativas.** Dos 8 registros administrativos, 4 são processos ou medidas em andamento da ANPD, e não sanções aplicadas.
