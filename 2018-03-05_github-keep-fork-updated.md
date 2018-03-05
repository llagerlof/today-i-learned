# Como atualizar um fork do github quando houver alterações no branch original

Dentro do seu fork, listar os repositórios vinculados:

```$ git remote -v```

Adicionar o repositório do owner original:

```$ git remote add upstream https://github.com/shermangray/tabuada.git```

Conferir se o repositório entrou na configuração do seu fork:

```$ git remote -v```

Atualizar o seu fork com os dados do repositório do owner:

```$ git fetch upstream```

Atualizar o seu fork com as atualização do branch master do owner original:

```$ git merge upstream/master```

Enviar para o seu fork no github as atualizações:

```$ git push```

---

*keywords: github, fork, tutorial*

*reference: https://help.github.com/articles/syncing-a-fork/*
