# Como listar os arquivos de uma pasta de um projeto do GitHub usando a API.

Fazer uma requisição GET para a URL abaixo. É possível solicitar a lista de arquivos e diretórios de forma recursiva:

```https://api.github.com/repos/usuario-do-git/projeto-do-usuario/git/trees/branch-do-projeto?recursive=1```

Exemplo:

```https://api.github.com/repos/llagerlof/today-i-learned/git/trees/master?recursive=0```

---

*keywords: github, api, tutorial*

*reference: https://stackoverflow.com/a/25485782/2539521*
