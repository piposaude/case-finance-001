# Como usar o repositório e entregar

O desafio começa no [enunciado](CASE.md), que reúne os links para o contexto, o guia das colunas e os arquivos recebidos. Este README descreve apenas a organização do repositório e o fluxo de contribuição.

## Estrutura

```text
CASE.md                    Enunciado e entregas
CONTEXTO.md                Negócio e regras do fechamento
DICIONARIO_DE_DADOS.md     Como ler cada arquivo e coluna
dados/                     Arquivos de entrada
entrega/                   Pasta que você criará para seu trabalho
```

## Como contribuir e entregar

1. Aceite o convite do GitHub e clone [este repositório privado](https://github.com/piposaude/case-finance-001) com `git clone https://github.com/piposaude/case-finance-001.git`. Abra a pasta clonada antes de continuar.
2. Crie uma branch, por exemplo `git switch -c entrega-case`.
3. Preserve `dados/` e organize seus materiais em `entrega/`. Inclua a apresentação, a análise/ponte com fórmulas ou código e o registro do uso de IA.
4. Crie `entrega/README.md` com a ordem de leitura, ferramentas e versões, passos de reprodução, premissas e limites. Para planilhas, explique como importar os arquivos e recalcular. Para scripts ou notebooks, documente comandos e dependências.
5. Faça commits, envie a branch com `git push -u origin entrega-case` e abra um pull request de `entrega-case` para `main`. Indique no PR o ponto de entrada da entrega e como reproduzir os números principais.

O número de commits e o volume de código não são critérios de avaliação. Se tiver dificuldade com Git, avise a equipe para combinar uma forma equivalente de entrega. Não é necessário publicar seu trabalho em um repositório público.

Links externos podem complementar os arquivos, mas inclua uma versão que possa ser revisada sem contratar um serviço. Não inclua credenciais ou dados reais de terceiros.
