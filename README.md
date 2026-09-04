# davifigueiredo — blog

Blog pessoal feito com [Jekyll](https://jekyllrb.com/) e hospedado no GitHub
Pages, usando o tema [Mundana](https://www.wowthemes.net/mundana-jekyll-theme/),
da WowThemes.

## Rodando localmente

Com Docker (sem instalar nada na máquina):

```sh
docker compose up          # -> http://localhost:4000
```

Com Ruby instalado (3.0+):

```sh
bundle install
bundle exec jekyll serve    # -> http://localhost:4000
```

O `Gemfile.lock` não é versionado de propósito: a gem `github-pages` fixa todas
as dependências na mesma versão que o GitHub Pages usa, então um `bundle install`
limpo reproduz o ambiente de produção.

## Publicando

O GitHub Pages compila a branch `master` automaticamente a cada push; não há
workflow do Actions para manter. O site é servido em:

    https://dav1app.github.io/blog/

O `_config.yml` precisa corresponder ao endereço onde o site é servido:

```yaml
url: 'https://dav1app.github.io'   # esquema + domínio
baseurl: '/blog'                   # subcaminho, '' na raiz de um domínio
```

`baseurl` é um **caminho**, não uma URL. Colocar uma URL completa nele quebra
todos os links internos — esse era o bug original aqui.

### Migrando para um domínio próprio

1. Registre o domínio e aponte o DNS para o GitHub Pages (registros `A` para os
   quatro IPs do Pages, ou um registro `CNAME` para `dav1app.github.io`).
2. Crie um arquivo `CNAME` na raiz do repositório contendo apenas o domínio.
3. Ajuste `url:` para `https://o-dominio` e `baseurl:` para `''`.

Faça o passo 1 primeiro. Um `CNAME` apontando para um domínio sem registros DNS
faz o Pages redirecionar o site para um endereço que não resolve, o que tira o
blog do ar — foi exatamente o que aconteceu aqui.

## Escrevendo um post

Há um modelo pronto em [`_templates/post.markdown`](_templates/post.markdown)
com todo o front matter comentado. Copie e renomeie:

```sh
cp _templates/post.markdown _posts/$(date +%F)-meu-slug.markdown
```

`_templates/` começa com `_` e não é uma pasta conhecida do Jekyll, então é
ignorada na build — o modelo nunca vai para o ar.

O front matter mínimo é:

```yaml
---
layout: post
title: "Título do post"
image: /assets/images/alguma-imagem.png
categories: [linux, redes]
tags: [debian, vpn]
---
```

`layout: post` e `author: davi` são aplicados automaticamente pelo bloco
`defaults:` do `_config.yml`, então podem ser omitidos.

- `categories` e `tags` alimentam `/categories.html` e `/tags.html`. Posts sem
  nenhum dos dois simplesmente não aparecem nessas páginas.
- A tag `featured` coloca o post na barra lateral da home; a tag `sticky` fixa
  o post em um destaque no topo da home.

## Idioma

O site é escrito em português (`lang: pt-BR`). As datas são renderizadas pelo
include `_includes/data-pt.html`, porque o filtro `date` do Liquid não tem
suporte a locale e sempre emite os meses em inglês.
