# O negócio e a leitura do fechamento

A Empresa Case é uma corretora de benefícios. Ela recebe comissões pela carteira de clientes, fees de serviço, agenciamento e premiações. A liderança quer entender o resultado de **junho de 2026**, comparando com abril, maio e o orçamento.

Você lidera uma equipe financeira enxuta e trabalha com a contabilidade e as áreas de negócio. Seu papel é explicar o mês, investigar o que importa e indicar o que já permite decidir e o que ainda precisa ser confirmado.

## Estamos olhando uma empresa

Os arquivos representam uma única entidade jurídica. Há negócios com empresas do mesmo grupo, mas não estamos consolidando o grupo inteiro.

Isso importa para o caixa: **um serviço pago a outra empresa do grupo continua sendo despesa da empresa analisada**. Já uma transferência entre duas contas bancárias próprias apenas muda o dinheiro de lugar. A coluna `tipo_movimento` diferencia essas situações. Os pagamentos intercompany deste pacote estão classificados como serviços.

## Três números, três perguntas

| Visão | O que queremos entender | Como apurar no case |
|---|---|---|
| Variação do caixa | Quanto dinheiro entrou ou saiu? | Some todos os valores do extrato do mês e compare com a mudança dos saldos bancários. Use março como abertura de abril. |
| Resultado gerencial em caixa | Como ficaram os recebimentos e pagamentos considerados no resultado? | Use o extrato e os grupos do mapa gerencial. Inclua receitas e despesas financeiras e os serviços intercompany. Deixe de fora transferências próprias, compras de ativos/carteiras e adiantamentos a clientes. Apresente separadamente qualquer item sem classificação. |
| Resultado contábil | Quais receitas e despesas foram reconhecidas naquele mês? | Use os movimentos mensais das contas de resultado do balancete. O saldo final dessas contas inclui meses anteriores. Não some subtotais junto com as contas detalhadas. |

O resultado gerencial acima é uma medida específica do case. Não é automaticamente lucro contábil, EBITDA ou fluxo de caixa livre. O orçamento fornecido usa essa mesma visão de recebimentos e pagamentos; a linha de Capex e M&A é acompanhada à parte.

## Por que as visões podem ser diferentes

Uma despesa pode pertencer a junho e ser paga em julho. Um recebimento de junho pode liquidar uma receita de maio. Uma compra de carteira pode gerar desembolso agora e amortização ao longo do tempo. Impostos retidos também fazem o recebimento líquido diferir do valor bruto da receita.

Esses são critérios para interpretar os números, não explicações prontas para cada diferença. O balancete mostra despesas de provisão e amortização, mas a variação de um saldo patrimonial pode incluir pagamentos, baixas e reclassificações. Não atribua uma causa sem a evidência necessária.

## O papel de cada base

- **Extrato e saldos:** mostram a movimentação do dinheiro. O caixa deve conciliar por conta e mês.
- **Detalhamento da receita:** abre faturamento e recebimentos por cliente e tipo de receita. Compare com o banco, mas não some as duas bases. Comissão e Fee por Vida compõem a receita recorrente; Agenciamento e Premiação são apresentados separadamente.
- **Contas a pagar e receber:** ajudam a investigar documentos relacionados aos pagamentos e recebimentos. O arquivo reúne registros movimentados no trimestre, não todas as contas em aberto. Pode haver movimentos bancários sem documento correspondente e vice-versa.
- **Balancete:** apresenta a prévia contábil. Não há razão ou memória completa das contas para comprovar cada lançamento.
- **Vendas e churn:** ajudam a contextualizar a receita. MRR vendido não é faturamento nem recebimento do mês. O churn fornecido é a saída de clientes, sem valor de MRR perdido ou cancelamentos parciais de apólices.

## O que os arquivos permitem concluir

O movimento financeiro vai até **30/06/2026**. O detalhamento da receita inclui também parcelas de outros meses quando houve recebimento no trimestre. Recebimentos posteriores ao corte não foram fornecidos. As datas e valores informados pelo controle não comprovam, sozinhos, o reconhecimento contábil.

Não há vínculo de cada venda com sua implantação e primeira receita, nem histórico suficiente para calcular churn percentual de MRR. Receber de um cliente depois de sua saída pode significar cobrança de períodos anteriores.

A ponte deve comparar receitas e despesas por categoria, usando as descrições do extrato e as contas detalhadas do balancete. Os mapas resumem a apresentação; você pode abrir os grupos para investigar. Algumas contas contábeis reúnem despesas de diferentes categorias do financeiro. Nesses casos, indique a composição que falta, sem repartir valores por suposição ou buscar dados internos por conta própria.

[Voltar ao enunciado](CASE.md) · [Consultar as colunas dos arquivos](DICIONARIO_DE_DADOS.md)
