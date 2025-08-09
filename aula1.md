# Gestão de configuração - Git
## Capitulo 1: Introdução ao Controle de Versão

*Objetivos:*
- Compreender os conceitos básicos e a importância do controle de versão.
- Familiarizar-se com a evolução histórica das ferramentas de controle de versão.
- Introdução ao Git

*Conteúdos:*
- Definição e importância do controle de versão em desenvolvimento de software.
- Visão geral histórica das ferramentas de controle de versão: do CVS ao Git.
- Terminologia básica: commit, branch, merge, conflict.
- Laboratório

### Pré-requisitos

- No Windows, instalar WSL.
- No Linux, apenas terminal.

## Visão Geral

1. Qual é a definição e importância do controle de versão em desenvolvimento de software?
2. Quais são os problemas de desenvolvimento de software resolvidos pelo controle de versão?
3. Quais são as vantagens do Git em relação a outras ferramentas de controle de versão?
4. Quais são as desvantagens do Git?
5. Como o Git evoluiu ao longo do tempo em relação a outras ferramentas de controle de versão?
6. Quais são os comandos básicos do Git e como eles são usados?
7. O que é um commit hash e qual é a sua importância no controle de versão?
8. Como você trabalharia com o Git em um laboratório prático?
9. Quais são as principais diferenças entre um sistema de controle de versão centralizado e um sistema de controle de versão distribuído?
10. Como o Git permite o trabalho offline e fornece redundância em caso de falha do servidor central?

## Tópico complementar: Developer Experience (DX) e a Gestão de Configuração

**Developer Experience (DX)** refere-se à qualidade da experiência do desenvolvedor ao interagir com ferramentas, fluxos de trabalho e ambientes de desenvolvimento. Quando bem projetada, a DX aumenta a produtividade, reduz frustrações e melhora a qualidade do software entregue.

### Como a Gestão de Configuração Impacta na DX

A gestão de configuração, especialmente com o uso de ferramentas como Git, afeta diretamente a experiência dos desenvolvedores nos seguintes aspectos:

- ✅ **Previsibilidade e Segurança**  
  Versionamento consistente permite reverter mudanças com confiança, reduzindo o medo de "quebrar algo".

- ✅ **Onboarding Facilitado**  
  Repositórios bem estruturados com histórico claro, mensagens de commit compreensíveis e fluxos definidos aceleram o processo de integração de novos membros.

- ✅ **Integração com Ferramentas Modernas**  
  Git se conecta facilmente a plataformas de CI/CD, revisão de código, análise estática e monitoramento, otimizando o fluxo de trabalho.

- ✅ **Colaboração Assíncrona**  
  Branches, pull requests e comentários promovem colaboração sem necessidade de reuniões ou trabalho síncrono.

- ✅ **Automação e Qualidade de Código**  
  Ferramentas que validam commits, executam testes automáticos e aplicam padrões aumentam a consistência e qualidade.

---

### Ferramentas que Potencializam a DX com Git

| Ferramenta | Função Principal | Benefício para DX |
|-----------|------------------|--------------------|
| **GitHub / GitLab / Bitbucket** | Repositórios + CI/CD | Fluxos de PRs, revisões, automações |
| **Copilot / CodeWhisperer** | IA para sugestão de código | Reduz o tempo de escrita e aprendizado |
| **Husky + lint-staged** | Ganchos de Git locais | Previne erros antes do push |
| **Commitlint + Conventional Commits** | Padronização de mensagens | Facilita changelog e versionamento |
| **Semantic Release** | Versionamento automático | Reduz erros humanos e gera changelog |
| **Nx / TurboRepo** | Gerenciamento de monorepos | DX escalável em grandes projetos |
| **Backstage** | Portal de Dev Interno | Padroniza criação e gestão de serviços |
| **VS Code Live Share** | Colaboração em tempo real | Editar e depurar remotamente |
| **Jupyter + Jupytext** | Notebooks versionáveis | Integra notebooks ao Git de forma limpa |

---

### Recomendações Práticas

- 📘 Adote fluxos de commit semântico (e.g. Conventional Commits)
- 🧪 Execute linters e testes com ganchos (`pre-commit`)
- 🤝 Use pull requests com revisão obrigatória
- 📂 Documente claramente como clonar, instalar e rodar o projeto
- 🚀 Automatize releases com changelog automático

---

> 💡 Melhorar a Developer Experience com boas práticas de Git não é só sobre produtividade — é também sobre reduzir o atrito, facilitar a colaboração e tornar o trabalho mais agradável para todos os envolvidos.


## Problemas de Desenvolvimento de Software Resolvidos pelo Controle de Versão

![controle-versao](./images/controle-versao.png)

1. **Perda de Código:** O controle de versão permite que você salve diferentes versões do seu código, evitando a perda de trabalho se algo der errado.

2. **Colaboração:** O controle de versão permite que várias pessoas trabalhem no mesmo projeto sem sobrescrever o trabalho umas das outras.

3. **Rastreamento de Alterações:** O controle de versão permite que você veja quem fez uma alteração, quando ela foi feita e por que ela foi feita.

4. **Reverter Alterações:** Se uma alteração introduzir um bug, o controle de versão permite que você reverta para uma versão anterior do código.

5. **Testando Novas Funcionalidades:** O controle de versão permite que você crie uma "branch" para desenvolver e testar novas funcionalidades sem afetar o código principal.

6. **Gerenciamento de Lançamentos:** O controle de versão permite que você mantenha diferentes versões do seu código para diferentes versões do seu software, facilitando o gerenciamento de lançamentos.

## Evolução das Ferramentas de Controle de Versão

### 🧭 Comparativo: Git vs Outras Ferramentas de Controle de Versão

| Ferramenta     | Tipo        | Distribuído | Curva de Aprendizado | Performance | Uso em Equipe | Status Atual |
|----------------|-------------|-------------|-----------------------|-------------|---------------|---------------|
| **Git**        | DVCS        | ✅           | Moderada              | 🔥 Alta      | 🚀 Excelente  | Ativo e dominante |
| **Mercurial**  | DVCS        | ✅           | Baixa                 | Alta        | Muito boa     | Em uso, menor adoção |
| **Bazaar**     | DVCS        | ✅           | Baixa                 | Média       | Boa           | Obsoleto |
| **Fossil**     | DVCS + Wiki | ✅           | Moderada              | Alta        | Boa           | Ativo (projetos pequenos) |
| **Pijul**      | DVCS        | ✅           | Alta (experimental)   | Média       | Incipiente    | Em desenvolvimento |
| **Darcs**      | DVCS        | ✅           | Alta                  | Média       | Limitado      | Pouco usado (acadêmico) |
| **Subversion** | CVCS        | ❌           | Baixa                 | Média       | Boa           | Ativo em ambientes legados |
| **CVS**        | CVCS        | ❌           | Baixa                 | Baixa       | Limitado      | Obsoleto |
| **Perforce**   | CVCS        | ❌           | Alta                  | 🚀 Muito Alta| Excelente     | Ativo (uso corporativo/games) |
| **ClearCase**  | CVCS        | ❌           | Muito Alta            | Média       | Corporativo   | Legado em uso |
| **Plastic SCM**| Híbrido     | ✅/❌        | Moderada              | Alta        | Muito boa     | Ativo (uso em jogos) |


### 🧱 Tipos de Sistemas de Controle de Versão

| Tipo                      | Descrição                                                                 | Exemplos                            | Vantagens                                                                 | Desvantagens                                                               |
|---------------------------|---------------------------------------------------------------------------|-------------------------------------|---------------------------------------------------------------------------|----------------------------------------------------------------------------|
| **Local (LVCS)**          | Armazena versões apenas na máquina do desenvolvedor.                      | RCS, cópias manuais                 | Simples de usar, sem dependência externa.                                 | Risco alto de perda de dados, difícil colaboração.                         |
| **Centralizado (CVCS)**   | Um servidor central gerencia o histórico e os arquivos de código.         | Subversion (SVN), CVS, Perforce     | Boa colaboração, controle centralizado.                                  | Requer conexão, servidor único = ponto único de falha.                     |
| **Distribuído (DVCS)**    | Cada desenvolvedor possui uma cópia completa do repositório.              | Git, Mercurial, Fossil              | Trabalha offline, redundância, ótimo para colaboração e branches.        | Curva de aprendizado maior, complexidade inicial.                          |
| **Híbrido / Comercial**   | Mistura elementos distribuídos e centralizados com ferramentas visuais.   | Plastic SCM, GitHub, GitLab, Azure Repos | Usabilidade moderna, integra CI/CD, controle de acesso granular.     | Pode ser proprietário ou exigir infraestrutura adicional.                  |

🧭 Quando Usar Cada Tipo?

    LVCS: Estudos pessoais, scripts simples.

    CVCS: Projetos corporativos legados, ambientes com regras rígidas de compliance.

    DVCS: Projetos modernos, open-source, times distribuídos.

    Híbrido: DevOps moderno, com integração CI/CD, pipelines, permissões e DX aprimorada.
------

1. **Controle de Versão Local:** No início, os desenvolvedores mantinham versões locais de arquivos de código. Isso era propenso a erros, pois era fácil sobrescrever ou perder versões.

![local-vcs](./images/local-vcs.png)

2. **Controle de Versão Centralizado (CVCS):** Ferramentas como CVS, Subversion e Perforce introduziram um servidor central que mantinha todas as versões do código. Isso facilitou a colaboração, mas a perda do servidor central poderia resultar na perda de todo o histórico de versões.

![local-vcs](./images/centralized-cvs.png)

3. **Controle de Versão Distribuído (DVCS):** Ferramentas como Git, Mercurial e Bazaar permitiram que cada desenvolvedor tivesse uma cópia completa do histórico de versões. Isso tornou possível trabalhar offline e deu aos desenvolvedores a capacidade de ter várias "branches" de trabalho.

![local-vcs](./images/distributed-cvs.png)


> O Git foi criado por Linus Torvalds em 2005 para gerenciar o desenvolvimento do kernel do Linux. Ele introduziu muitos conceitos inovadores em DVCS, como um modelo de dados que garante a integridade do código e a capacidade de manipular facilmente o historico do código.

## Introdução ao Git

![git](./images/git.png)

Video: https://youtu.be/e9lnsKot_SQ

> Git Book Pro https://git-scm.com/book/en/v2

> Historia do Git https://git-scm.com/book/pt-br/v2/Come%C3%A7ando-Uma-Breve-Hist%C3%B3ria-do-Git

```
1.2 Começando - Uma Breve História do Git
Uma Breve História do Git

Como muitas coisas na vida, o Git começou com um pouco de destruição criativa e uma ardente controvérsia.

O núcleo (kernel) do Linux é um projeto de código aberto com um escopo bastante grande. A maior parte da vida da manutenção do núcleo o Linux (1991-2002), as mudanças no código eram compartilhadas como correções e arquivos. Em 2002, o projeto do núcleo do Linux começou usar uma DVCS proprietária chamada BitKeeper.

Em 2005, a relação entre a comunidade que desenvolveu o núcleo do Linux e a empresa que desenvolveu BitKeeper quebrou em pedaços, e a ferramenta passou a ser paga. Isto alertou a comunidade que desenvolvia o Linux (e especialmente Linus Torvalds, o criador do Linux) a desenvolver a sua própria ferramenta baseada em lições aprendidas ao usar o BitKeeper. Algumas metas do novo sistema era os seguintes:

    Velocidade

    Projeto simples

    Forte suporte para desenvolvimento não-linear (milhares de ramos paralelos)

    Completamente distribuído

    Capaz de lidar com projetos grandes como o núcleo o Linux com eficiência (velocidade e tamanho dos dados)

Desde seu nascimento em 2005, Git evoluiu e amadureceu para ser fácil de usar e ainda reter essas qualidades iniciais. Ele é incrivelmente rápido, é muito eficiente com projetos grandes, e ele tem um incrível sistema de ramos para desenvolvimento não linear (Veja [ch03-git-branching]).
```

## ⚖️ Vantagens e Desvantagens do Git

| Aspecto                         | Vantagens                                                                 | Desvantagens                                                                 |
|----------------------------------|---------------------------------------------------------------------------|------------------------------------------------------------------------------|
| **Distribuição**                | Cada desenvolvedor tem o repositório completo, permitindo trabalho offline. | Pode gerar múltiplas versões divergentes se mal coordenado.                |
| **Desempenho**                  | Operações locais (commit, diff, merge) são rápidas e eficientes.          | Repositórios grandes com muitos arquivos binários podem impactar a performance. |
| **Branching e Merging**         | Criação e fusão de branches é leve, rápida e encorajada.                  | Conflitos mal resolvidos podem causar confusão e retrabalho.               |
| **Integridade dos dados**       | Usa SHA-1 para garantir integridade de commits e histórico.               | A manipulação de histórico (ex: rebase, reset) exige cuidado.              |
| **Flexibilidade**               | Suporta diversos fluxos de trabalho (Git Flow, trunk-based, forking).     | Pode ser difícil padronizar em times grandes sem boas práticas.           |
| **Comunidade e ecossistema**    | Ampla adoção, compatibilidade com IDEs, CI/CD, e plataformas como GitHub. | Necessidade de ferramentas adicionais para controle de permissões granulares. |
| **Aprendizado**                 | Amplo material de apoio, cursos, cheat sheets.                            | Curva de aprendizado pode ser íngreme para iniciantes.                     |
| **Colaboração**                 | Ótimo para trabalho em equipe e projetos open-source.                     | Exige cultura e disciplina para manter um histórico limpo e compreensível. |

> "Para que uma tecnologia escale entre os desenvolvedores, é necessário que sua complexidade seja compensada por ganhos significativos e boas experiências de uso. Exemplos: Git, Kubernetes." Autor: Rodrigo Galba.

## Fundamentos do Git

*Objetivos:*
- Instalar e configurar o Git.
- Aprender comandos básicos do Git.

*Conteúdos:*
- Instalação do Git e configuração inicial.
- Repositórios Git: locais e remotos.
- Comandos básicos: git init, git clone, git add, git commit, git push, git pull.

*Atividades:*
- Criação de um novo repositório Git e clonagem de um repositório existente.
- Prática dos comandos básicos com exercícios simples.

## Estágios do Git


![stages](./images/0202-git-commands.png)

> O Git tem três estados principais nos quais seus arquivos podem estar: modificado, preparado e confirmado:

- Modificado significa que você alterou o arquivo, mas ainda não o confirmou no seu banco de dados.
- Preparado significa que você marcou um arquivo modificado em sua versão atual para entrar na próxima captura de commit.
- Confirmado significa que os dados estão armazenados com segurança no seu banco de dados local.

Isso nos leva às três principais seções de um projeto Git: a árvore de trabalho, a área de preparação e o diretório Git.

A árvore de trabalho é um único checkout de uma versão do projeto. Esses arquivos são retirados do banco de dados compactado no diretório Git e colocados no disco para você usar ou modificar.

A área de preparação é um arquivo, geralmente contido no diretório Git, que armazena informações sobre o que será incluído no seu próximo commit. Seu nome técnico na terminologia do Git é o "índice", mas a frase "área de preparação" também funciona bem.

O diretório Git é onde o Git armazena os metadados e o banco de dados de objetos do seu projeto. Esta é a parte mais importante do Git e é o que é copiado quando você clona um repositório de outro computador.

Referencia: https://bytebytego.com/guides/how-does-git-work/

### 🔍 Tipos de objeto

| Tipo       | Conteúdo                                             |
| ---------- | ---------------------------------------------------- |
| **blob**   | Conteúdo bruto de um arquivo                         |
| **tree**   | Estrutura de diretórios (referencia blobs e trees)   |
| **commit** | Metadados, mensagem, autor, hash da árvore (tree)    |
| **tag**    | Marca simbólica para um commit (ou outro objeto Git) |

### 🧩 Entendendo com analogia

- Um commit aponta para uma tree
- A tree aponta para blobs (arquivos) e outras trees (subdiretórios)
- Cada objeto tem um hash SHA-1 (ou SHA-256 no Git moderno)

## Git Commands Cheat Sheet

![cheat-sheet](./images/0201-git-commands-cheat-sheet.png)

### Comandos Principais do Git

1. `git init`: Inicializa um novo repositório Git. 
    - Exemplo: `git init`
    - Caso de uso: Quando você quer começar a rastrear um novo projeto com o Git.

2. `git clone`: Clona um repositório Git existente.
    - Exemplo: `git clone https://github.com/usuario/projeto.git`
    - Caso de uso: Quando você quer trabalhar em um projeto que já está sendo rastreado pelo Git.

3. `git add`: Adiciona arquivos ao índice do Git para serem rastreados.
    - Exemplo: `git add .` (adiciona todos os arquivos modificados) ou `git add arquivo.txt` (adiciona um arquivo específico)
    - Caso de uso: Quando você fez alterações em um ou mais arquivos e quer que essas alterações sejam rastreadas pelo Git.

4. `git commit`: Cria um novo commit com as alterações rastreadas.
    - Exemplo: `git commit -m "Mensagem do commit"`
    - Caso de uso: Quando você quer salvar um ponto específico no histórico do projeto.

5. `git branch`: Lista, cria ou deleta branches.
    - Exemplo: `git branch` (lista branches), `git branch nova_branch` (cria nova branch), `git branch -d branch_antiga` (deleta branch)
    - Caso de uso: Quando você quer trabalhar em uma nova funcionalidade ou corrigir um bug sem afetar o código principal.

6. `git merge`: Une as alterações de uma branch em outra.
    - Exemplo: `git merge branch_fonte`
    - Caso de uso: Quando você terminou de trabalhar em uma branch e quer unir as alterações na branch principal.

7. `git status`: Mostra o estado atual do repositório.
    - Exemplo: `git status`
    - Caso de uso: Quando você quer ver quais arquivos foram modificados e quais alterações estão prontas para serem commitadas.

# 🧪 Laboratório: Instalação e Configuração Básica do Git no Windows

## ✅ Etapas Básicas

### 1. Instalar o Git no Windows
1. Acesse o site oficial: https://git-scm.com/downloads
2. Baixe o instalador para Windows.
3. Execute o instalador:
   - Mantenha as opções padrão nas telas.
   - Use o **Git Bash** como terminal recomendado.

### 2. Verificar instalação

Abra o **Git Bash** e execute:

```bash
git --version
````

Você verá a versão instalada, como:

```
git version 2.44.0.windows.1
```

---

### 3. Configurar nome de usuário e e-mail

```bash
git config --global user.name "Seu Nome"
git config --global user.email "seu@email.com"
```

Verifique com:

```bash
git config --list
```

---

### 4. Criar um repositório local

```bash
mkdir git-workshop
cd git-workshop
git init
```

Você verá:

```
Initialized empty Git repository in C:/Users/SeuUsuario/git-workshop/.git/
```

---

### 5. Criar um arquivo `README.md`

```bash
echo "# Meu Projeto Git" > README.md
```

Visualize com:

```bash
cat README.md
```

### 6. Adicionar e fazer o primeiro commit

```bash
git add README.md
git commit -m "Adiciona README inicial"
```

---

### 📝 Resultado Esperado

* Git instalado e funcional no terminal.
* Configuração global feita (`user.name` e `user.email`).
* Repositório local com um commit inicial e o arquivo `README.md`.

## ⚙️ Como funciona o `git config`

O comando `git config` é utilizado para **definir ou consultar configurações do Git**, como nome do autor, e-mail, editor padrão, aliases, e comportamento de merge ou push.

Essas configurações podem ser aplicadas em **três níveis diferentes**:

| Nível        | Escopo                        | Comando exemplo                                | Arquivo afetado                         |
|--------------|-------------------------------|------------------------------------------------|------------------------------------------|
| **System**   | Para todos os usuários do sistema | `git config --system user.name "Nome"`         | `C:\Program Files\Git\etc\gitconfig`     |
| **Global**   | Para o usuário atual           | `git config --global user.name "Nome"`         | `~/.gitconfig` ou `C:\Users\SeuUser\.gitconfig` |
| **Local**    | Apenas para um repositório     | `git config user.name "Nome"`                  | `.git/config` dentro do repositório     |

> 💡 O nível **local** sobrescreve o **global**, que por sua vez sobrescreve o **system**.

---

### 📌 Exemplos Práticos

```bash
# Definir o nome do usuário globalmente
git config --global user.name "João da Silva"

# Definir o e-mail do usuário globalmente
git config --global user.email "joao@email.com"

# Definir editor padrão
git config --global core.editor "code --wait"

# Ver todas as configurações ativas
git config --list

# Ver configurações de um nível específico
git config --global --list
git config --local --list
```

## 📚 Trabalhando com o Histórico no Git

| Conceito                         | Descrição                                                                                     | Comando(s) Principal(is)                        |
|----------------------------------|-----------------------------------------------------------------------------------------------|--------------------------------------------------|
| **Commit**                       | Unidade de alteração no Git; armazena autor, data, mensagem e um `commit hash` único.        | `git commit`, `git log`                         |
| **Histórico de Commits**         | Lista completa das alterações realizadas em ordem cronológica reversa.                       | `git log`                                        |
| **Commit Hash**                  | Identificador SHA-1 único gerado para cada commit, usado para referenciar mudanças.           | Visível em `git log`                            |
| **Checkout de versão anterior**  | Permite navegar para um commit antigo ou outro branch.                                        | `git checkout <hash>` ou `git checkout <branch>`|
| **Reversão de alterações**       | Cria um novo commit que desfaz mudanças de um commit anterior.                               | `git revert <hash>`                              |
| **Branch**                       | Linha de desenvolvimento separada usada para isolar funcionalidades ou correções.            | `git branch`, `git checkout -b`                 |
| **Mudança de branch**            | Alterna o diretório de trabalho para outro branch existente.                                 | `git checkout <branch>`                          |
| **Merge**                        | Une alterações de uma branch (ex: feature) na branch principal (ex: main/master).            | `git merge <branch>`                             |
| **Desenvolvimento colaborativo**| Permite que múltiplos desenvolvedores trabalhem em paralelo sem conflito direto.             | Uso combinado de branches e merges              |

![git-log](./images/git-log.png)

----

## 🧾 Tabela: Entendendo o Commit Hash no Git

| Aspecto                          | Descrição                                                                                       |
|----------------------------------|---------------------------------------------------------------------------------------------------|
| **Definição**                    | Sequência única de caracteres (SHA-1) que identifica um commit de forma exclusiva.               |
| **Formato**                      | Composto por 40 caracteres hexadecimal (ex: `a1b2c3d4e5f6...`).                                  |
| **Finalidade**                   | Rastrear alterações, referenciar commits em comandos (`merge`, `checkout`, `revert`, etc).       |
| **Geração**                      | Calculado com base no conteúdo do commit: snapshot dos arquivos, metadata, autor, mensagem.      |
| **Unicidade**                    | Qualquer alteração — mesmo mínima — gera um novo hash, garantindo identificação exclusiva.       |
| **Uso prático**                  | Permite voltar a um estado anterior do projeto, desfazer mudanças específicas, comparar versões. |
| **Visualização**                 | Através do comando `git log`, que exibe o hash e demais informações do commit.                   |
| **Integridade**                  | Hash protege contra alterações não autorizadas — qualquer corrupção no histórico é detectável.  |
| **Truncamento**                  | É comum usar apenas os primeiros 7 a 10 caracteres para referência curta (ex: `git checkout a1b2c3d`). |
| **Importância**                  | Essencial para o controle de versão distribuído; é a base da segurança e rastreabilidade do Git. |

![hash](./images/git-commit-hash.png)

## 🧠 Como funciona o `HEAD` no Git

O `HEAD` é um ponteiro especial no Git que **representa o estado atual do repositório**, ou seja, **o commit que está "checado" no momento**.

### 📌 Conceito

- O `HEAD` geralmente aponta para o **último commit no branch atual** (ex: `main`, `dev`).
- Quando você faz um novo commit, o `HEAD` se move automaticamente para esse novo commit.
- Ao alternar entre branches com `git checkout`, o `HEAD` também é atualizado para apontar para o novo branch.

### 🔄 Navegação com `HEAD`

| Comando                  | Significado                                          |
|--------------------------|------------------------------------------------------|
| `HEAD`                   | Último commit no branch atual                        |
| `HEAD~1`                 | Commit anterior ao `HEAD`                            |
| `HEAD~2`, `HEAD~3`...    | Commits anteriores em sequência                      |
| `HEAD^`                  | Pai direto do commit atual (igual a `HEAD~1`)        |
| `HEAD^^` ou `HEAD~2`     | Avô do commit atual                                  |
| `git checkout HEAD`      | Recupera a versão atual do repositório               |
| `git checkout HEAD~1`    | Muda para a versão do commit anterior (modo detached)|

### 🧪 Exemplo prático

```bash
git log --oneline
# d4e5f6b (HEAD -> main) Adiciona rodapé
# a1b2c3d Adiciona seção de uso
````

* `HEAD` aponta para `d4e5f6b`
* `HEAD~1` seria `a1b2c3d`

---

### ⚠️ Modo Detached HEAD

Quando você faz `git checkout` em um commit específico (e não em um branch), o `HEAD` entra em modo **detached**. Isso significa que ele não está mais vinculado a um branch. Commits feitos neste estado **não serão mantidos** se você mudar de branch sem salvá-los.

```bash
git checkout a1b2c3d  # HEAD agora está "solto"
```

> 💡 Sempre que possível, crie uma branch antes de trabalhar em estado detached:
> `git checkout -b hotfix-antigo a1b2c3d`

---

O `HEAD` é essencial para entender como o Git rastreia seu estado atual e como ele gerencia o histórico. Manipular corretamente o `HEAD` é a base para comandos como `reset`, `revert`, `checkout`, e `rebase`.

## 🔁 Tabela: HEAD vs Detached HEAD

| Estado               | O que é?                                                              | Quando ocorre?                                                    | Quando usar?                                                       |
|----------------------|----------------------------------------------------------------------|--------------------------------------------------------------------|--------------------------------------------------------------------|
| `HEAD` normal        | Ponteiro para o último commit do branch atual                        | Ao trabalhar normalmente em um branch (ex: `main`)                | No fluxo comum de desenvolvimento e commits contínuos              |
| `HEAD~N`, `HEAD^`    | Referência relativa ao commit anterior ao `HEAD`                     | Ao navegar no histórico ou usar comandos como `git diff HEAD~1`   | Comparar versões, visualizar histórico, fazer rollback pontual     |
| `Detached HEAD`      | `HEAD` aponta diretamente para um commit, **não para um branch**      | Ao usar `git checkout <commit-hash>` ou tag diretamente           | Testes, build temporário, inspeção de versão antiga sem alterar branches |
| `HEAD -> <branch>`   | Estado normal indicando qual branch o `HEAD` está rastreando          | Exibido em `git log --oneline` ou `git status`                    | Para confirmar em qual branch você está trabalhando atualmente     |

## 🎯 Por que usar o modo Detached HEAD?

Usar o modo **detached HEAD** no Git pode parecer arriscado, mas tem aplicações práticas importantes quando bem compreendido.

### 🧠 Situações comuns e benefícios

| Situação                                   | Vantagem                                                                                    |
| ------------------------------------------ | ------------------------------------------------------------------------------------------- |
| 🔍 **Testar código antigo**                | Permite compilar, rodar ou depurar uma versão específica sem alterar o branch atual.        |
| 🧪 **Builds/Hotfixes temporários**         | Ideal para gerar uma build rápida de um commit passado (ex: para cliente ou CI/CD).         |
| 🧬 **Benchmark ou experimentação isolada** | Você pode testar uma mudança sem criar branch (desde que não precise manter o histórico).   |
| 💥 **Investigar bugs regressivos**         | Facilita voltar no tempo (`git checkout <hash>`) para inspecionar o código antes de um bug. |
| 🔖 **Verificar uma tag de versão**         | `git checkout v1.0.0` entra em detached para explorar aquela release.                       |

### ⚠️ Cuidados

- Commits feitos nesse estado **não ficam vinculados a um branch**.
- Para preservar, crie um branch antes de sair:
  ```bash
  git checkout -b minha-experiencia
  ```

> 💡 Detached HEAD é útil para **observar, testar ou compilar**, mas **não para desenvolver continuamente sem salvar**.

---

## 🧪 Exercício: Usando `git diff` no Histórico de Alterações

Neste exercício, você usará o repositório criado anteriormente com o `README.md` e seus 5 commits incrementais (`v1` a `v5`) para explorar o comando `git diff`.

### 🔍 Etapas

1. **Simule uma nova alteração (sem commit):**

```bash
echo "linha extra" >> README.md
````

2. **Verifique a diferença com o último commit (`HEAD`):**

```bash
git diff
```

3. **Adicione a mudança ao stage e compare com o último commit:**

```bash
git add README.md
git diff --cached
```

4. **Compare a versão atual com 2 commits atrás:**

```bash
git diff HEAD~2
```

5. **Compare dois commits anteriores entre si (ver hashes com `git log --oneline`):**

```bash
git diff <commit-antigo> <commit-mais-novo>
```

---

### ✅ Comandos úteis

| Comando                    | Descrição                                                   |
| -------------------------- | ----------------------------------------------------------- |
| `git diff`                 | Mostra diferenças entre o diretório atual e o último commit |
| `git diff --cached`        | Mostra o que está staged em comparação ao último commit     |
| `git diff HEAD~1`          | Compara com o commit anterior ao atual                      |
| `git diff <hash1> <hash2>` | Compara diretamente dois commits específicos                |

---

> 💡 O `git diff` é ideal para revisar mudanças antes de commitá-las ou para investigar o que foi alterado entre versões específicas.

---


## Resumo

1. A definição do controle de versão em desenvolvimento de software é a prática de rastrear e gerenciar alterações no código-fonte ao longo do tempo. Ele é importante porque permite que os desenvolvedores trabalhem de forma colaborativa, revertam alterações, testem novas funcionalidades e gerenciem lançamentos.

2. Os problemas de desenvolvimento de software resolvidos pelo controle de versão incluem a perda de código, a colaboração entre desenvolvedores, o rastreamento de alterações, a reversão de alterações, o teste de novas funcionalidades e o gerenciamento de lançamentos.

3. As vantagens do Git em relação a outras ferramentas de controle de versão incluem a distribuição, o desempenho, o sistema eficiente de branching e merging, a integridade dos dados e a flexibilidade.

4. As desvantagens do Git incluem a curva de aprendizado íngreme, a complexidade dos comandos, a falta de controle de acesso granular e a dificuldade de lidar com arquivos binários grandes.

5. O Git evoluiu ao longo do tempo em relação a outras ferramentas de controle de versão, introduzindo o modelo de dados que garante a integridade do código e a capacidade de manipular facilmente a história do código.

6. Os comandos básicos do Git incluem git init, git clone, git add, git commit, git push, git pull, git branch, git merge e git status. Eles são usados para inicializar um novo repositório, clonar um repositório existente, adicionar arquivos ao índice, criar um novo commit, enviar alterações para um repositório remoto, obter alterações de um repositório remoto, gerenciar branches, unir alterações de uma branch em outra e verificar o estado atual do repositório.

7. Um commit hash é uma sequência única de caracteres gerada pelo sistema de controle de versão para identificar de forma exclusiva um commit específico. Ele é importante no controle de versão porque permite referenciar commits ao realizar operações como merge, revert e checkout de versões específicas do código.

8. Para trabalhar com o Git em um laboratório prático, você pode seguir os seguintes passos:
    - Crie um novo diretório em seu computador e navegue até ele no terminal.
    - Inicialize um novo repositório Git com `git init`.
    - Crie um novo arquivo ou adicione arquivos existentes ao repositório com `git add`.
    - Crie um novo commit com as alterações rastreadas usando `git commit`.
    - Crie branches para desenvolver novas funcionalidades ou corrigir bugs com `git branch`.
    - Una as alterações de uma branch em outra com `git merge`.
    - Verifique o estado atual do repositório com `git status`.

9. As principais diferenças entre um sistema de controle de versão centralizado e um sistema de controle de versão distribuído são:
    - No sistema centralizado, há um servidor central que mantém todas as versões do código, enquanto no sistema distribuído, cada desenvolvedor tem uma cópia completa do histórico de versões.
    - No sistema centralizado, é necessário estar conectado ao servidor para realizar operações, enquanto no sistema distribuído, é possível trabalhar offline e sincronizar as alterações posteriormente.
    - No sistema centralizado, a perda do servidor central pode resultar na perda de todo o histórico de versões, enquanto no sistema distribuído, cada cópia do repositório contém todo o histórico.
    - No sistema centralizado, as operações são mais lentas, pois dependem da conexão com o servidor, enquanto no sistema distribuído, as operações são mais rápidas e eficientes.

10. O Git permite o trabalho offline e fornece redundância em caso de falha do servidor central através do seu modelo de dados distribuído. Cada desenvolvedor tem uma cópia completa do histórico de versões, o que permite trabalhar offline e realizar operações localmente. Além disso, as alterações podem ser sincronizadas entre os repositórios locais e remotos, fornecendo redundância em caso de falha do servidor central.


**Nota:** Este laboratório pressupõe que você está trabalhando localmente e não está fazendo push das alterações para um repositório remoto.

### Histórico do Git

O Git mantém um histórico completo de todas as alterações feitas em um projeto. Cada alteração é registrada como um commit, que contém informações sobre as alterações feitas, o autor, a data e um identificador único chamado commit hash. Isso permite que você acompanhe todas as alterações feitas no código ao longo do tempo e navegue pelo histórico usando comandos como `git log`, `git checkout` e `git revert`.