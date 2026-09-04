---
# ---------------------------------------------------------------------------
# MODELO DE POST
#
# Como usar:
#   1. Copie este arquivo para _posts/
#   2. Renomeie para AAAA-MM-DD-um-slug-curto.markdown
#      (a data e o slug vêm do nome do arquivo; a URL final será /um-slug-curto/)
#   3. Preencha o front matter abaixo e escreva o texto
#
# Pastas iniciadas por "_" que o Jekyll não conhece são ignoradas na build,
# então este arquivo nunca é publicado.
# ---------------------------------------------------------------------------

# OBRIGATÓRIO -------------------------------------------------------------
title: "Título do post"

# OPCIONAIS ---------------------------------------------------------------

# Imagem de capa. Aparece no card da home e no cabeçalho do post.
# Coloque o arquivo em assets/images/ e use o caminho a partir da raiz.
image: /assets/images/exemplo.png

# Categorias: alimentam /categories.html. Use poucas e reaproveite as
# existentes (ex.: linux, redes, windows, desenvolvimento, carreira).
categories: [desenvolvimento]

# Tags: alimentam /tags.html. Duas têm efeito especial no tema:
#   featured -> destaca o post na barra lateral da home
#   sticky   -> fixa o post em um banner no topo da home
tags: [exemplo, tutorial]

# Resumo usado nos cards e nas meta tags. Se omitido, o Jekyll usa o
# primeiro parágrafo do texto.
description: "Uma frase curta explicando do que trata o post."

# Data/hora explícita. Só é necessária para ordenar dois posts do mesmo dia.
# date: 2026-09-04 10:00:00 -0300

# layout: post e author: davi são aplicados automaticamente pelo bloco
# defaults: do _config.yml — não precisa repetir aqui.
---

O primeiro parágrafo é o mais importante: o tema aplica uma capitular
(a primeira letra em corpo grande) e é ele que vira o resumo automático
nos cards da home, caso `description` não esteja preenchido.

## Um subtítulo

Texto normal, com **negrito**, *itálico*, [um link](https://example.com) e
`código inline`.

### Um subtítulo menor

- item de lista
- outro item

1. item numerado
2. outro item

Bloco de código com destaque de sintaxe (informe a linguagem após as crases):

```bash
echo "olá mundo"
```

```ruby
puts "olá mundo"
```

> Uma citação, útil para destacar uma conclusão ou um trecho de documentação.

Imagem no meio do texto:

![Texto alternativo descrevendo a imagem](/assets/images/exemplo.png)

Tabela:

| Coluna A | Coluna B |
| -------- | -------- |
| valor 1  | valor 2  |

---

Para conferir antes de publicar:

```sh
docker compose up      # -> http://localhost:4000
```
