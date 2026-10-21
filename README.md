# Projeto de Análise de Sentimento em Feedbacks de E-commerce

Este projeto foi desenvolvido para demonstrar um fluxo completo de processamento de linguagem natural (NLP) em textos de comentários de clientes, com foco em:

- limpeza de texto
- remoção de ruído e stop words
- análise de sentimento com IA
- apresentação dos resultados em um DataFrame

## Objetivo

O objetivo principal é transformar comentários reais ou simulados de clientes em dados estruturados, limpar o texto para reduzir ruído e, em seguida, classificar cada comentário como:

- Positivo
- Negativo
- Neutro

Isso pode ser usado em dashboards de atendimento, e-commerce, CRM e análise de reputação de marca.

## O que foi feito no código

### 1. Importação das bibliotecas

O projeto utiliza:

- pandas: para manipular os dados em tabelas
- re: para limpar texto com expressões regulares
- nltk: para usar a lista de stop words em português
- transformers: para carregar o modelo de análise de sentimento

### 2. Criação de um dataset local

Foi montada uma base de exemplos de feedbacks de clientes em e-commerce, contendo:

- comentário original
- contexto de atendimento
- produto
- experiência do cliente

Esses dados são transformados em um DataFrame do pandas para facilitar a manipulação.

### 3. Função de limpeza de texto

A função `limpar_texto_portfolio` faz as seguintes etapas:

- converte o texto para minúsculas
- remove links e URLs
- remove menções (`@usuario`) e hashtags (`#tag`)
- remove pontuações e números
- preserva letras com acentos do português
- remove espaços em excesso
- remove stop words em português
- mantém palavras como "não", "nem" e "nunca" para preservar o sentido emocional do texto

Essa etapa é importante porque modelos de IA tendem a funcionar melhor quando o texto está limpo e padronizado.

### 4. Aplicação da limpeza no DataFrame

A coluna `comentario_original` recebe uma nova coluna chamada `comentario_limpo`, contendo o texto já processado.

### 5. Análise de sentimento com IA

Foi carregado um modelo de classificação de sentimento usando Hugging Face:

```python
pipeline("text-classification", model="cardiffnlp/twitter-xlm-roberta-base-sentiment")
```

Esse modelo analisa cada comentário limpo e retorna:

- label: o sentimento detectado
- score: a confiança da IA na classificação

### 6. Tradução dos rótulos

Como o modelo retorna rótulos em inglês, foi criada uma função para traduzir para português:

- Negative -> Negativo
- Positive -> Positivo
- Neutral -> Neutro

### 7. Resultado final

O DataFrame final inclui:

- comentário original
- comentário limpo
- sentimento detectado
- nível de confiança da IA

Esse resultado é exibido em formato tabular para facilitar a leitura e análise.

## Dependências

Para executar o projeto, é necessário instalar as bibliotecas:

```bash
pip install pandas nltk transformers torch
```

## Como rodar

1. Abra o notebook
2. Certifique-se de que as bibliotecas foram instaladas
3. Execute as células na ordem em que aparecem
4. Veja o resultado da limpeza e da classificação de sentimento

## Conclusão

Este projeto mostra uma aplicação prática de NLP em comentários de clientes, combinando:

- pré-processamento de texto
- remoção de ruído
- uso de IA para análise de sentimento
- organização dos resultados em DataFrame

É uma base útil para portfólio, apresentação acadêmica ou projeto de análise de reputação digital.

## Autor Vinícius Bortoluci

Projeto desenvolvido como exemplo de portfolio em processamento de linguagem natural.
