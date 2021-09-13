[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
![Total Lines](https://img.shields.io/tokei/lines/github/nelsontky/gh-pages-url-shortener?color=blue)
![GitHub stars](https://img.shields.io/github/stars/Z3t4Byt3/gh-pages-url-shortener?style=social)

# 🔗 GitHub Pages Encurtador de URL

Este é um encurtador de URL simples que pode ser totalmente hospedado no GitHub Pages. Isto quer dizer que  
não precisa da manutenção de nenhum servidor ou banco de dados, e pode ser hospedado
inteiramente no GitHub de graça!

[Yay! We got to the top of HN!](https://news.ycombinator.com/item?id=25110879)

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

1. Não há necessidade do símbolo de libra - URLs encurtadas aparecem limpos assim:
   `nlsn.cf/1` em vez de ter a seguinte aparência: `nlsn.cf/#1`.

## 💡 Como é que isso funciona?

_Thanks to @kidGodzilla for the pretty neat explanation
[here](https://github.com/nelsontky/gh-pages-url-shortener/issues/5#issuecomment-728040879)._

> 1. 404.html handles all requests
> 1. Small javascript snippet fetches a JSON representation of the GitHub issue
>    via the JSON API, and redirects to the issue title, as a URL.
> 1. Profit?

## 😎 This is so cool! How can I use this with my own domain?!

_Isenção de responsabilidade: este método de criação de um encurtador de URL,é hacky e não deve ser
Ser confiável. Continue por sua própria conta e risco!_

1. Fork the repo before cloning your fork.
1. Set up GitHub pages for your forked repo.
   1. In your forked repo, **click the Settings tab** and scroll down to the
      GitHub Pages section.
   1. Then select the **main branch** source and click on the **Save** button.
   1. <img src="https://i.imgur.com/kjinFX9.png" alt="How to create GitHub page" height="176px">
1. If you are using your own domain:
   1. [Set your domain up for GitHub pages.](https://docs.github.com/en/free-pro-team@latest/github/working-with-github-pages/managing-a-custom-domain-for-your-github-pages-site#configuring-an-apex-domain)
   1. Change the URL in `CNAME` file to your domain.
1. If you are using GitHub page's default domain i.e. Something like
   `https://<username>.github.io/<repo-name>/`
   1. Delete the `CNAME` file.
   1. Change `var PATH_SEGMENTS_TO_SKIP = 0;` at the top of `404.html` to
      `var PATH_SEGMENTS_TO_SKIP = 1;`.
      1. This is as GitHub domains have an additional path segment (the repo
         name) after the host name.
1. Crie um novo repo como um database. (Or you could use your forked repo)
   1. Update `var GITHUB_ISSUES_LINK = "<your-github-issues-link>";` at the top
      of `404.html` accordingly afterwards.
      1. Formato para `GITHUB_ISSUES_LINK`:
         `https://api.github.com/repos/{owner}/{repo}/issues/`
      1. Lembre-se da trailing `/`!
1. Push your changes to your forked repo, and your low cost and cool as heck URL
   shortener will be ready for use!

## 🍴 Featured forks

To feature your fork here, edit this section and open a PR!

- [eexit.github.io/s](https://github.com/eexit/s) - Created a bash script that
  allows for shortening of URLs straight on the command line! Check out his
  script
  [here](https://github.com/nelsontky/gh-pages-url-shortener/issues/49#issue-745134937).
- [gh-short-url](https://github.com/mayandev/gh-short-url) - A npm command line
  tool that use github pages to convert short url.
