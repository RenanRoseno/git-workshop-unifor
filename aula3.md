# Gestão de configuração - Git
## Aula 3: Tags, Hooks e Recuperação

*Objetivos:*

- Compreender como usar tags para marcar pontos específicos no histórico do código como versões importantes.
- Aprender a usar Git Hooks para automatizar tarefas e aprimorar o fluxo de trabalho.
- Aprender a usar git revert e git reset para reverter alterações e recuperar de erros.

*Conteúdos:*

- Criação de tags, tipos de tags (leves e anotadas), visualização de tags, checkout para tags, exclusão de tags.
- Uso de Git Hooks para automatizar tarefas.
- Uso de git revert e git reset para recuperação de desastres.

*Atividades:*

- Prática de criação de tags em pontos importantes do histórico do código.
- Configuração e execução de Git Hooks para automatizar tarefas específicas.
- Exercícios de uso de git revert e git reset para reverter alterações e recuperar de erros.

*Recursos Complementares:*

- Documentação oficial do Git sobre tags, hooks e recuperação.
- Tutoriais online sobre o uso avançado de tags, hooks e recuperação no Git.

## Pré-requisitos

- Conhecimento básico de Git e controle de versão.
- Familiaridade com o uso do terminal ou linha de comando.
- Compreensão dos conceitos de branches e commits no Git.
- Familiaridade com os comandos do Git, como commit, branch e merge.
- Ter um repositório Git configurado localmente.

## Referências

Aqui estão algumas referências úteis sobre Git tag, Git hook, Git reset e Git revert:

- Documentação oficial do Git sobre tags: [Git Tag Documentation](https://git-scm.com/book/en/v2/Git-Basics-Tagging)
- Documentação oficial do Git sobre hooks: [Git Hooks Documentation](https://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks)
- Documentação oficial do Git sobre reset: [Git Reset Documentation](https://git-scm.com/docs/git-reset)
- Documentação oficial do Git sobre revert: [Git Revert Documentation](https://git-scm.com/docs/git-revert)

Além disso, você pode encontrar tutoriais online sobre esses tópicos em sites como:

- [Atlassian Git Tutorial](https://www.atlassian.com/git/tutorials)
- [Git SCM Documentation](https://git-scm.com/doc)
- [GitHub Guides](https://guides.github.com/)
- [Geeksforgeeks](https://www.geeksforgeeks.org/git-hooks/)

> Essas referências devem fornecer informações detalhadas sobre como usar Git tags, Git hooks, Git reset e Git revert em seu fluxo de trabalho de desenvolvimento.

## Visão Geral

1. Como criar uma tag leve no Git?
2. Qual a diferença entre uma tag leve e uma tag anotada no Git?
3. Como visualizar todas as tags em um repositório Git?
4. Como fazer o checkout para uma tag específica no Git?
5. Como excluir uma tag no Git?
6. Quais são os tipos de Git Hooks disponíveis?
7. Como configurar um Git Hook para ser executado antes de cada commit?
8. Como usar o Git revert para desfazer um commit específico?
9. Qual a diferença entre o Git revert e o Git reset?
10. Como usar o Git reset para desfazer um commit e descartar as alterações?
11. Se um commit for perdido, a tag sera perdida?

## Git Tag

As tags são usadas no Git para marcar pontos específicos no histórico do código como versões importantes. Existem dois tipos de tags: tags leves e tags anotadas.

![git-tags](./images/git-tag.png)

### Tags Leves

Uma tag leve é apenas um ponteiro para um commit específico. Para criar uma tag leve, você pode usar o comando `git tag <nome_da_tag>`. Por exemplo, para criar uma tag chamada "v1.0", você pode executar `git tag v1.0`.

### Tags Anotadas

Uma tag anotada é um objeto completo no Git, que inclui informações como o nome do autor, data e mensagem. Para criar uma tag anotada, você pode usar o comando `git tag -a <nome_da_tag> -m "<mensagem_da_tag>"`. Por exemplo, para criar uma tag anotada chamada "v1.0" com a mensagem "Versão 1.0 lançada", você pode executar `git tag -a v1.0 -m "Versão 1.0 lançada"`.


### 📌 Comparativo: Tag Leve vs Tag Anotada

| Tipo de Tag     | Armazena Metadados? | Tem mensagem? | Hash próprio? | Ideal para...          |
|-----------------|---------------------|---------------|---------------|-------------------------|
| Tag leve        | ❌ Não               | ❌ Não         | ❌ Não         | Marcação rápida         |
| Tag anotada     | ✅ Sim               | ✅ Sim         | ✅ Sim         | Versões formais/lancamentos |


### Visualizando Tags

Para visualizar todas as tags em um repositório Git, você pode usar o comando `git tag`. Isso listará todas as tags existentes.

### Checkout para uma Tag

Para fazer o checkout para uma tag específica no Git, você pode usar o comando `git checkout <nome_da_tag>`. Por exemplo, para fazer o checkout para a tag "v1.0", você pode executar `git checkout v1.0`.

### Excluindo uma Tag

Para excluir uma tag no Git, você pode usar o comando `git tag -d <nome_da_tag>`. Por exemplo, para excluir a tag "v1.0", você pode executar `git tag -d v1.0`.

---
### 🧪 Laboratório: Gerenciamento de Tags entre Branches

1. Crie tags em `main`:
```bash
git checkout main
git tag -a v1.0 -m "Versão 1.0 em main"
````

2. Promova para `test` e crie nova tag:

```bash
git checkout test
git merge main -m "Merge v1.0 para test"
git tag -a v1.0-test -m "Versão 1.0 testada"
```

3. Promova para `prod`:

```bash
git checkout prod
git merge test -m "Merge v1.0-test para prod"
git tag -a v1.0-prod -m "Versão 1.0 em produção"
```

4. Ver tags:

```bash
git tag --list
```

### 💡 Laboratorio parte 2

#### O que acontece ao fazer checkout de uma tag do branch prod estando no branch main?

> Ao executar `git checkout <tag>` enquanto está no branch `main` (ou qualquer outro), o Git:

1. O Git **Sai do branch atual** e entra em modo **detached HEAD**.
2. O repositório passa a exibir o conteúdo exato do commit referenciado pela **tag** (ex: uma versão em `prod`).
3. **Você não está mais em nenhum branch**, então qualquer commit feito nesse estado **não ficará em um branch rastreável** (a menos que você crie um novo branch a partir daí).

```bash
git checkout v1.0-prod
# HEAD agora está "solto" no commit da tag
```

> ✅ Ideal para inspeção ou build de versões (cicd).
> ⚠️ Crie um branch (`git checkout -b`) se quiser desenvolver a partir da tag.

---

## Git Reset

O comando `git reset` é usado para desfazer commits e alterar a posição do branch atual. Existem três formas principais de usar o `git reset`:

1. Soft Reset: `git reset --soft HEAD~1`
    - Este tipo de reset desfaz os commits, mas mantém as alterações no diretório de trabalho e no índice. Os arquivos alterados serão mantidos como alterações não adicionadas.
    - O *reset soft* é útil para fazer correções antes do *push*.

2. Mixed Reset (padrão): `git reset <commit>`
    - Este tipo de reset desfaz os commits e remove as alterações do índice, mas mantém as alterações no diretório de trabalho. Os arquivos alterados serão mantidos como alterações não rastreadas.

3. Hard Reset: `git reset --hard <commit>`
    - Este tipo de reset desfaz os commits e descarta todas as alterações, tanto no diretório de trabalho quanto no índice. Os arquivos alterados serão perdidos permanentemente.

É importante ter cuidado ao usar o `git reset`, pois ele pode reescrever o histórico do projeto. Certifique-se de ter um backup adequado antes de executar um reset.

Exemplo de uso do `git reset`:

- Desfazer o último commit e manter as alterações no diretório de trabalho:
  ```
  git reset --soft HEAD~1
  ```

- Desfazer o último commit e remover as alterações do índice:
  ```
  git reset HEAD~1
  ```

- Desfazer o último commit e descartar todas as alterações:
  ```
  git reset --hard HEAD~1
  ```

Lembre-se de substituir `<commit>` pelo hash do commit que você deseja desfazer.

## Git Revert

O comando `git revert` é usado para desfazer um commit específico, criando um novo commit que desfaz as alterações feitas no commit especificado. Esta é uma maneira segura de desfazer alterações, pois não reescreve o histórico do projeto.

Para usar o `git revert` e desfazer um commit específico, você pode usar o comando `git revert` <hash_do_commit>. Por exemplo, para desfazer o commit com o hash "abc123", você pode executar `git revert` abc123.

Quando você executa o `git revert`, o Git criará um novo commit que desfaz as alterações feitas no commit especificado. Este novo commit terá as alterações opostas, efetivamente cancelando o commit anterior.

É importante observar que o `git revert` não exclui ou remove o commit original. Em vez disso, ele adiciona um novo commit que desfaz as alterações. Isso significa que o histórico de commits permanece intacto e você ainda pode ver o commit original e suas alterações.

Usar o `git revert` é uma maneira segura de desfazer alterações, pois não afeta outros branches ou commits. Ele permite desfazer seletivamente commits específicos sem afetar o restante do histórico do projeto.

Lembre-se de substituir <hash_do_commit> pelo hash real do commit que você deseja desfazer.

---

### 🔁 Comparativo: `git reset` vs `git revert`

| Comando       | O que faz                                        | Impacta histórico? | Uso recomendado             |
|---------------|--------------------------------------------------|--------------------|------------------------------|
| `git reset`   | Move o ponteiro HEAD para outro commit           | ✅ Sim              | Reescrever histórico local   |
| `git revert`  | Cria um novo commit que desfaz alterações        | ❌ Não              | Desfazer commits publicados  |

---

## Git Hooks

Git Hooks são scripts que podem ser executados antes ou depois de certos eventos do Git, como commit, push ou merge. Eles permitem automatizar tarefas e aprimorar seu fluxo de trabalho. Os Git Hooks são armazenados no diretório `.git/hooks` do seu repositório Git.

Existem vários tipos de Git Hooks disponíveis, incluindo:

- `pre-commit`: Executado antes de criar um commit.
- `prepare-commit-msg`: Executado antes de editar a mensagem do commit.
- `commit-msg`: Executado depois de editar a mensagem do commit.
- `post-commit`: Executado depois de criar um commit.
- `pre-rebase`: Executado antes de fazer um rebase em um branch.
- `post-checkout`: Executado depois de fazer checkout em um branch.
- `post-merge`: Executado depois de realizar um merge.
- `pre-push`: Executado antes de fazer um push.
- `post-receive`: Executado depois de receber um push.


### 📘 Tabela: Tipos de Git Hooks

| Hook                 | Quando é executado                            |
|----------------------|-----------------------------------------------|
| `pre-commit`         | Antes de criar um commit                      |
| `prepare-commit-msg` | Antes de editar a mensagem de commit         |
| `commit-msg`         | Após editar a mensagem de commit             |
| `post-commit`        | Após criar um commit                         |
| `pre-rebase`         | Antes de fazer um rebase                     |
| `post-checkout`      | Após mudar de branch                         |
| `post-merge`         | Após um merge ser concluído                  |
| `pre-push`           | Antes de enviar commits para o repositório   |
| `post-receive`       | Após receber um push no repositório remoto   |


![git-hooks](./images/git-hooks.png)

Para configurar um Git Hook, você pode criar um arquivo com o nome do hook no diretório `.git/hooks` do seu repositório Git. Por exemplo, para configurar um hook pre-commit, você pode criar um arquivo chamado `pre-commit` no diretório `.git/hooks` e adicionar o código desejado.

Os Git Hooks podem ser escritos em qualquer linguagem de script, como Bash, Python ou Ruby. Eles podem ser usados para impor padrões de codificação, executar testes, realizar análises de código ou qualquer outra tarefa personalizada que você deseja automatizar em seu fluxo de trabalho do Git.

É importante observar que os Git Hooks não são compartilhados entre repositórios. Cada repositório tem seu próprio conjunto de hooks.

---

Claro! Aqui está uma seção explicativa em **Markdown** sobre **publicação de repositórios Git** com foco no uso do **GitHub como serviço de hospedagem**, cobrindo os comandos `git push`, `git clone`, e contexto geral.

---

# ☁️ Publicação de Repositórios com GitHub

## 🧠 O que é publicar um repositório?

Publicar um repositório significa **enviar seu código local para um servidor online**, como o **GitHub**, para:

- Compartilhar com outras pessoas
- Fazer backup do seu código
- Trabalhar de forma colaborativa
- Integrar com pipelines CI/CD, GitHub Actions, etc.

---

## 🧰 Pré-requisitos

1. Ter uma conta no [github.com](https://github.com)
2. Ter o Git configurado localmente com seu usuário:

```bash
git config --global user.name "Seu Nome"
git config --global user.email "seu@email.com"
````

---

## 🚀 Passos para publicar um repositório existente no GitHub

### 1. Crie um repositório vazio no GitHub (sem README)

Acesse [https://github.com/new](https://github.com/new)
Escolha um nome, deixe **vazio**, e clique em **Create Repository**.

---

### 2. No terminal, dentro do seu projeto local:

Adicione o repositório remoto:

```bash
git remote add origin https://github.com/SEU_USUARIO/NOME_DO_REPO.git
```

Empurre o repositório para o GitHub:

```bash
git push -u origin main
```

> A flag `-u` cria o vínculo entre a branch local `main` e a `origin/main`.

---

## 🌍 Clonando um repositório existente

Se você quiser **baixar um repositório que está no GitHub**, use:

```bash
git clone https://github.com/usuario/repositorio.git
```

Isso cria uma cópia local do repositório e já configura o `origin` para o repositório remoto.

---

## 📌 Comandos relacionados

| Comando                  | O que faz                                            |
| ------------------------ | ---------------------------------------------------- |
| `git remote -v`          | Lista os repositórios remotos configurados           |
| `git push origin main`   | Envia commits da branch `main` para o GitHub         |
| `git push origin --tags` | Envia todas as tags locais para o GitHub             |
| `git clone <url>`        | Baixa o repositório remoto e cria uma cópia local    |
| `git pull`               | Puxa atualizações do GitHub para o repositório local |

---

## 🔐 Dica: Autenticação com HTTPS ou SSH

O GitHub exige autenticação para `push`. Você pode usar:

* **Token de acesso pessoal** (PAT) com HTTPS
* **Chaves SSH** para configurar acesso mais seguro (avançado)

---

## Resumo

1. Para criar uma tag leve no Git, você pode usar o comando `git tag <nome_da_tag>`. Por exemplo, para criar uma tag chamada "v1.0", você pode executar `git tag v1.0`.

2. A diferença entre uma tag leve e uma tag anotada no Git é que a tag leve é apenas um ponteiro para um commit específico, enquanto a tag anotada é um objeto completo no Git, que inclui informações como o nome do autor, data e mensagem. Para criar uma tag anotada, você pode usar o comando `git tag -a <nome_da_tag> -m "<mensagem_da_tag>"`.

3. Para visualizar todas as tags em um repositório Git, você pode usar o comando `git tag`. Isso listará todas as tags existentes.

4. Para fazer o checkout para uma tag específica no Git, você pode usar o comando `git checkout <nome_da_tag>`. Por exemplo, para fazer o checkout para a tag "v1.0", você pode executar `git checkout v1.0`.

5. Para excluir uma tag no Git, você pode usar o comando `git tag -d <nome_da_tag>`. Por exemplo, para excluir a tag "v1.0", você pode executar `git tag -d v1.0`.

6. Os tipos de Git Hooks disponíveis são: pre-commit, prepare-commit-msg, commit-msg, post-commit, pre-rebase, post-checkout, post-merge, pre-push e post-receive.

7. Para configurar um Git Hook para ser executado antes de cada commit, você pode criar um arquivo com o nome do hook na pasta `.git/hooks` do seu repositório Git. Por exemplo, para configurar um hook pre-commit, você pode criar um arquivo chamado `pre-commit` na pasta `.git/hooks` e adicionar o código desejado.

8. Para usar o Git revert e desfazer um commit específico, você pode usar o comando `git revert <hash_do_commit>`. Por exemplo, para reverter o commit com o hash "abc123", você pode executar `git revert abc123`.

9. A diferença entre o Git revert e o Git reset é que o Git revert cria um novo commit que desfaz as alterações do commit especificado, enquanto o Git reset move o branch atual para um commit específico, descartando os commits posteriores.

10. Para usar o Git reset e desfazer um commit e descartar as alterações, você pode usar o comando `git reset <hash_do_commit> --hard`. Por exemplo, para desfazer o commit com o hash "abc123" e descartar as alterações, você pode executar `git reset abc123 --hard`.

11. Se um commit que possui uma tag é perdido durante uma resolução de conflito, a tag não é perdida. A tag ainda apontará para o commit original, mesmo que esse commit não esteja mais no branch atual após a resolução do conflito. No entanto, se o commit for removido do histórico do Git (por exemplo, através de um comando como git rebase), a tag ainda existirá, mas apontará para um commit que não está mais no histórico do branch. Nesse caso, a tag pode ser considerada "perdida" no sentido de que não aponta para um commit no histórico do branch atual.