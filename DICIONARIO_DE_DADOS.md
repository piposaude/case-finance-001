# Guia dos arquivos e das colunas

Os valores estão em **reais**, não em milhares. Nos CSVs, o ponto separa os centavos e a vírgula separa as colunas. Datas estão no formato ano-mês-dia. Os arquivos podem ser abertos em planilha ou na ferramenta que você preferir.

Os códigos de identificação são fictícios. Guarde-os como texto. Campo vazio significa informação indisponível, não necessariamente zero. Este guia explica o que cada linha representa e quais colunas ajudam a encontrar a mesma operação em outro arquivo.

## 1. Detalhamento da receita

[Abrir o arquivo](dados/detalhamento_receita.csv) · 2.642 linhas

Cada linha reúne parcelas de receita do controle financeiro. Uma mesma nota pode aparecer em várias linhas, por exemplo por atender a mais de um cliente ou competência.

| Coluna | Como ler |
|---|---|
| `receita_id` | Código exclusivo daquela linha. Preserve-o para mostrar a origem de um número. |
| `cliente_id` | Cliente final que gerou a receita. Não é necessariamente quem efetuou o pagamento. |
| `tipo_receita` | Comissão, Fee por Vida, Agenciamento ou Premiação. |
| `documento_ref` | Referência da nota ou documento, quando disponível. Pode se repetir. |
| `competencia` | Mês de referência da parcela no controle operacional. Pode diferir da competência contábil. |
| `data_emissao`, `data_recebimento` | Quando a nota foi emitida e quando o dinheiro foi recebido, conforme o controle. |
| `nf_bruto`, `nf_liquido` | Valores bruto e líquido informados. |
| `iss`, `iss_retido` | Valor de ISS e indicação de retenção (`sim` ou `não`). ISS não retido não deve ser descontado novamente do recebimento. |
| `irrf`, `csrf` | Retenções informadas. Não são automaticamente uma despesa adicional. |
| `valor_recebido` | Valor recebido até o corte. Para somar recebimentos de junho, use a data de recebimento. |

Para faturamento, use a data de emissão preenchida. Para recebimento, use a data de recebimento. Não troque uma pela outra. Se bruto, retenções e líquido apresentarem diferença, registre-a em vez de alterar a entrada.

Algumas informações indisponíveis no corte foram deixadas vazias. Por isso, duas linhas podem parecer iguais e ainda representar parcelas diferentes. **Não apague linhas por semelhança: cada `receita_id` deve ser preservado.** Uma referência de documento vazia não comprova que houve emissão de nota.

## 2. Extrato

[Abrir o arquivo](dados/extrato.csv) · 1.878 linhas

Cada linha é uma entrada ou saída de uma conta financeira.

| Coluna | Como ler |
|---|---|
| `registro_id`, `movimento_id` | Identificam a linha e o movimento. Nenhum dos dois se repete neste arquivo. |
| `data_pagamento` | Data da entrada ou saída do dinheiro. |
| `conta_id` | Conta bancária ou de aplicação. O mesmo código aparece no arquivo de saldos. |
| `valor` | Entrada positiva; saída negativa. |
| `documento_ref` | Referência documental disponível. Pode ajudar a investigar a operação, mas não identifica sozinha uma linha. |
| `contraparte_id` | Pessoa ou empresa que pagou ou recebeu. Uma operadora, por exemplo, pode pagar comissões de vários clientes finais. |
| `categoria_cf`, `categoria_erp` | Categoria para a visão gerencial e descrição mais detalhada do sistema financeiro. |
| `area`, `macroarea` | Área responsável e seu agrupamento. `Não informada` significa que o campo não veio preenchido. |
| `tipo_movimento` | `Transferência entre contas`, `Intercompany` ou `Outros recebimentos e pagamentos`. Intercompany é uma operação com outra empresa do grupo, não uma instrução para excluir o valor. |

Todos os movimentos entram na conferência do saldo bancário. Para o resultado gerencial, siga o [contexto](CONTEXTO.md#três-números-três-perguntas) e o mapa de categorias.

## 3. Contas a pagar e receber

[Abrir o arquivo](dados/ap_ar_liquidados.csv) · 3.011 linhas

Cada linha é um registro documental movimentado no trimestre. Não é uma lista completa de contas em aberto. Os códigos `movimento_id` e `documento_ref` podem se repetir, pois um pagamento pode reunir vários documentos ou divisões de classificação.

As colunas de identificação, data de pagamento, contraparte, categoria, área e tipo de movimento têm o significado descrito no extrato.

| Coluna específica | Como ler |
|---|---|
| `natureza` | `AP`: contas a pagar. `AR`: contas a receber. |
| `origem_id` | Referência do registro no sistema financeiro. Pode aparecer em mais de uma linha. |
| `data_emissao`, `data_vencimento` | Datas do documento. Não comprovam, sozinhas, quando a despesa foi reconhecida. |
| `status` | Situação informada: PAGO ou RECEBIDO. |
| `valor_bruto` | Valor antes das deduções, positivo tanto em AP quanto em AR. |
| `valor_liquido` | Valor líquido: negativo em contas a pagar, positivo em contas a receber. |
| `ir`, `iss`, `inss`, `csll`, `pis`, `cofins` | Valores tributários informados. Não os some novamente ao líquido para apurar caixa. |

Para conferir com o banco, reúna as linhas com o mesmo `movimento_id` e compare seu total com o movimento do extrato. **Não repita o valor do banco a cada documento.** Podem existir diferenças de valor, classificação e cobertura entre os arquivos; ausência de correspondente não comprova, por si só, erro. Não há percentuais de rateio ou contratos no pacote.

## 4. Saldos bancários

[Abrir o arquivo](dados/saldos_bancarios.csv) · 98 linhas

Cada linha informa o `saldo_fechamento` de uma `conta_id` em um `mes`. Março é a abertura de abril. Confira, por conta: saldo anterior + entradas e saídas do extrato = saldo final. Uma conta/mês ausente do arquivo não deve ser considerada zero sem conferência.

## 5. Balancete

[Abrir o arquivo](dados/balancete.csv) · 685 linhas

Cada linha mostra uma conta contábil em um mês. Algumas são contas detalhadas; outras são subtotais dessas contas.

| Coluna | Como ler |
|---|---|
| `mes` | Mês da movimentação contábil. |
| `conta_contabil`, `descricao` | Código e nome da conta. |
| `nivel` | `analitica`: conta detalhada. `sintetica`: subtotal. Some apenas as analíticas. |
| `saldo_inicial`, `saldo_final` | Saldo devedor positivo e credor negativo. Incluem períodos anteriores. |
| `debitos`, `creditos` | Movimentos do mês, ambos apresentados como valores positivos. |

Para conferir uma conta: **saldo inicial + débitos - créditos = saldo final**.

Para apurar o resultado do mês: some **créditos - débitos** das contas analíticas que começam com `3.` e `4.`. O cálculo apresenta receitas positivas e despesas/deduções negativas. Não use o saldo final como resultado mensal.

Contas `1` são ativo; contas `2` são passivo e patrimônio líquido. O balancete não fornece o documento de cada lançamento.

## 6. Mapas de categorias

- [Mapa gerencial](dados/mapa_gerencial.csv), 34 linhas: informa em qual `grupo_gerencial` cada `categoria_cf` entra. `tratamento = resultado` indica inclusão no indicador gerencial; `fora_resultado` indica acompanhamento separado. Transferências próprias ficam fora do resultado em qualquer caso.
- [Mapa contábil](dados/mapa_contabil.csv), 147 linhas: agrupa contas analíticas em `grupo_contabil`. `entra_resultado = 1` identifica contas de resultado; `0`, contas patrimoniais.

Esses mapas servem para organizar a análise. Para investigar uma categoria, use também `categoria_erp` no extrato e `conta_contabil` e `descricao` no balancete. Grupos com nomes parecidos não são necessariamente equivalentes e não comprovam que os documentos foram contabilizados na mesma conta.

## 7. Orçamento e metas

[Abrir o arquivo](dados/orcamento_metas.csv) · 36 linhas

Cada linha contém um `indicador`, em um `mes`, com seu `valor` planejado. `tipo = caixa` é o orçamento dos grupos gerenciais; `meta_comercial` é a meta de novo MRR. `unidade` é BRL e `versao` identifica o plano do exercício. Recebimentos são positivos e desembolsos negativos. Não há subtotais duplicados. Capex e M&A são acompanhados separadamente do resultado gerencial.

## 8. Vendas e churn

- [Vendas](dados/vendas.csv), 18 linhas: cada `venda_id` identifica uma venda. `data_gongo` é a data de confirmação comercial, já no horário local; `porte` é o tamanho do cliente; `novo_mrr` é o valor mensal vendido. Não há relação fornecida entre cada venda e seu primeiro recebimento.
- [Churn](dados/churn_clientes.csv), 8 linhas: cada `saida_id` identifica uma saída de cliente em `data_saida`. `cliente_id` pode ser procurado no detalhamento da receita. Se não aparecer, isso não prova que nunca houve receita desse cliente. O arquivo não informa MRR perdido nem saídas parciais de apólices.

[Voltar ao enunciado](CASE.md) · [Voltar ao contexto](CONTEXTO.md)
