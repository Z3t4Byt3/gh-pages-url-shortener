[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
![Total Lines](https://img.shields.io/tokei/lines/github/nelsontky/gh-pages-url-shortener?color=blue)
![GitHub stars](https://img.shields.io/github/stars/Z3t4Byt3/gh-pages-url-shortener?style=social)

# 🔗 GitHub Pages Encurtador de URL

Este é um encurtador de URL simples que pode ser totalmente hospedado no GitHub Pages. Isto quer dizer que  
não precisa da manutenção de nenhum servidor ou banco de dados, e pode ser hospedado
inteiramente no GitHub de graça!

[Yeh! Chegamos ao topo do HN!](https://news.ycombinator.com/item?id=25110879)

<img src="https://i.imgur.com/ZfD7XGt.png" alt="Top of HN" width="240px">

E no GitHub trending!

<img src="https://i.imgur.com/OkYCSOx.png" alt="GitHub Trending" width="240px">

## 👨‍🏫 Demonstração

1. [nlsn.cf/1](https://nlsn.cf/1) deve vincular a este repo.

1. Para adicionar um novo link encurtado, adicione um issue com o title being o link que você quer
   para encurtar (incluindo o `http(s)://`) to
   [https://github.com/nelsontky/gh-pages-url-shortener-db/issues](https://github.com/nelsontky/gh-pages-url-shortener-db/issues).

1. A URL encurtada recém-criada pode ser acessada via `nlsn.cf/{issue_number}`

## ☕️ Reursos

1. Ao contrário de muitos encurtadores de URL, este ~~não precisa de um banco de dados~~ usa um
   "banco de dados" na forma de issues do GitHub e pode ser totalmente hospedado em GitHub
   pages.

1. Não há necessidade do símbolo de sharp - URLs encurtadas aparecem limpos assim:
   `nlsn.cf/1` em vez de ter a seguinte aparência: `nlsn.cf/#1`.

## 💡 Como é que isso funciona?

_Obrigado ao @kidGodzilla pela explicação bem elaborada
[Aqui](https://github.com/nelsontky/gh-pages-url-shortener/issues/5#issuecomment-728040879)._

> 1. 404.html lida com todas as solicitações
> 1. Small javascript snippet busca uma representação JSON do GitHub issue
>    via a API JSON e redireciona para o issue title, como uma URL.
> 1. Profit?

## 😎 Isso é tão legal! Como posso usar isso com meu próprio domínio?

_Isenção de responsabilidade: este método de criação de um encurtador de URL,é hacky e não deve ser
Ser confiável. Continue por sua própria conta e risco!_

1. Fork the repo before cloning your fork.
1. Set up GitHub pages for your forked repo.
   1. In your forked repo, **click the Settings tab** and scroll down to the
      GitHub Pages section.
   1. Em seguida, selecione o **main branch** source and click on the **Save** button.
   1. <img src="https://i.imgur.com/kjinFX9.png" alt="How to create GitHub page" height="176px">
1. Se você estiver usando seu próprio domínio:
   1. [Configure seu domínio para GitHub pages.](https://docs.github.com/en/free-pro-team@latest/github/working-with-github-pages/managing-a-custom-domain-for-your-github-pages-site#configuring-an-apex-domain)
   1. Altere a URL no `CNAME` file para o seu domínio.
1. Se você estiver usando GitHub page's domínio padrão,ou seja,algo como
   `https://<username>.github.io/<repo-name>/`
   1. Delete o `CNAME` file.
   1. Altere `var PATH_SEGMENTS_TO_SKIP = 0;` no topo de `404.html` para
      `var PATH_SEGMENTS_TO_SKIP = 1;`.
      1. Isso ocorre porque os domínios do GitHub têm um segmento de caminho adicional (o repo
         name) depois de host name.
1. Crie um novo repo como um database. (Ou você pode usar o seu forked repo)
   1. Atualize `var GITHUB_ISSUES_LINK = "<your-github-issues-link>";` no topo
      do `404.html` consequentemente depois.
      1. Formato para `GITHUB_ISSUES_LINK`:
         `https://api.github.com/repos/{owner}/{repo}/issues/`
      1. Lembre-se da barra `/`!
1. Envie suas alterações para o seu forked repo, e seu encurtador de URL de baixo custo estará pronto para o uso!

## 🍴 Featured forks

To feature your fork here, edit this section and open a PR!

- [eexit.github.io/s](https://github.com/eexit/s) - Criou um script bash que
  permite o encurtamento de URLs diretamente na linha de comando! Confira o script dele
  
  [Aqui](https://github.com/nelsontky/gh-pages-url-shortener/issues/49#issue-745134937).
- [gh-short-url](https://github.com/mayandev/gh-short-url) - Uma ferramenta de linha de comando npm que usa github pages para converter url curta.
