# Case de liderança financeira: fechar o mês e explicar o resultado

Queremos conhecer seu julgamento financeiro, sua comunicação e como usa IA para analisar e verificar um fechamento.

## Contexto

Você assumiu a liderança de Finance de uma corretora de benefícios. A liderança precisa entender **junho de 2026**, comparando com abril, maio e o orçamento.

A visão gerencial considera recebimentos e pagamentos de caixa. A contabilidade registra receitas e despesas por competência. As duas visões respondem a perguntas diferentes e precisam ser explicadas em conjunto.

Leia o [contexto do negócio e as regras do fechamento](CONTEXTO.md). Consulte o [guia dos arquivos e das colunas](DICIONARIO_DE_DADOS.md) durante a análise. Esses dois documentos explicam o que considerar e os limites das fontes. Não é necessário conhecer regras internas da Pipo.

## Arquivos recebidos

| Arquivo | Para que serve |
|---|---|
| [Detalhamento da receita](dados/detalhamento_receita.csv) | Detalhar faturamento e recebimentos por cliente, tipo de receita e documento |
| [Extrato](dados/extrato.csv) | Apurar entradas e saídas de caixa |
| [Contas a pagar e receber liquidadas](dados/ap_ar_liquidados.csv) | Investigar documentos e classificações ligados às movimentações do período |
| [Saldos bancários](dados/saldos_bancarios.csv) | Conferir a evolução do caixa, com abertura em março |
| [Balancete mensal](dados/balancete.csv) | Apurar o resultado contábil e examinar saldos patrimoniais |
| [Mapa gerencial](dados/mapa_gerencial.csv) | Agrupar categorias do extrato e do orçamento |
| [Mapa contábil](dados/mapa_contabil.csv) | Agrupar contas analíticas do balancete |
| [Orçamento e metas](dados/orcamento_metas.csv) | Comparar realizado com plano de caixa e meta comercial |
| [Vendas](dados/vendas.csv) | Contextualizar novo MRR vendido |
| [Churn de clientes](dados/churn_clientes.csv) | Contextualizar saídas de clientes no período |

Os valores e identificadores foram alterados para este exercício. As bases preservam características de uma rotina financeira real. São arquivos estáticos: não há serviço externo, credencial ou software obrigatório. O pacote não inclui razão contábil.

## O que entregar

Prepare uma entrega que responda às quatro perguntas:

1. **Como foi o fechamento de junho?** Apresente o mês em comparação com o orçamento e os meses anteriores, trazendo insights sobre o negócio. Destaque números que precisam de validação e pontos de atenção para a liderança.
2. **Como você tentaria reconciliar o contábil e o gerencial?** Onde estão as principais diferenças e o que falta para uma análise mais completa?
3. **O que você melhoraria no fechamento de Finance nos próximos meses?** Proponha de uma a três ações e indique quais perguntas gostaria de fazer e a quais informações adicionais gostaria de ter acesso.
4. **Como você usou IA no desafio?** Conte como ela contribuiu para o trabalho e como você avaliou os resultados.

**A entrega precisa ser compreensível por uma pessoa, sem auxílio de IA para interpretar o material.** Organize a apresentação, as análises de apoio e suas conclusões para uma leitura clara e autossuficiente.

Organize a resposta em um **repositório privado na sua conta pessoal do GitHub** e compartilhe com os avaliadores. Inclua os arquivos e as instruções necessários para reproduzir a análise e envie o link, seguindo o [README de entrega](README.md#como-contribuir-e-entregar).

## Tempo e apresentação

**Prazo de entrega: 5 dias. Dedicação estimada: 4 a 6 horas**, incluindo a preparação da apresentação. As datas serão combinadas no convite. Registre eventuais pendências e como continuaria.

A conversa terá **30 minutos de apresentação e 20 minutos de discussão**, com perguntas sobre a origem dos números e suas decisões.

## Como vamos avaliar

| Dimensão | O que queremos observar |
|---|---|
| Rigor financeiro | Critérios corretos, comparações compatíveis e controle de dupla contagem |
| Leitura do negócio | Explicações sustentadas para as variações e conexão entre resultado e caixa |
| Julgamento e liderança | Materialidade, prioridades, tratamento da incerteza e ações úteis |
| Comunicação | Conclusões claras e proporcionais à evidência |
| Uso crítico de IA | Ganho de produtividade, verificação e domínio da entrega |

Avaliamos a qualidade das conclusões e verificações. Volume de código e acabamento visual não aumentam a nota por si só.
