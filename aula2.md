# Aula 2: Branching e Merging – Git

*Objetivos:*
- Compreender e utilizar o modelo de branching do Git.
- Aprender a mesclar mudanças e resolver conflitos.
- Introdução ao Github

*Conteúdos:*
- Comandos para branching e merging: git branch, git checkout, git merge.
- Resolução de conflitos.
- Trabalhando com Github

## Pré-requisitos

Antes de prosseguir com esta aula, é recomendado ter conhecimento básico do Git e do controle de versão de software. Certifique-se de ter o Git instalado em seu sistema e estar familiarizado com os comandos básicos, como `git init`, `git add`, `git commit`.

Além disso, é útil ter uma compreensão básica de como funciona o fluxo de trabalho de desenvolvimento de software e a importância do controle de versão.

Se você ainda não possui conhecimento prévio sobre esses tópicos, recomendo que você revise os conceitos básicos do Git e do controle de versão antes de prosseguir com esta aula.

## Visão Geral

1. O que é branching e qual é o objetivo de utilizá-lo no controle de versão de software?
2. Como o branching permite que os desenvolvedores trabalhem em novas funcionalidades ou correções de bugs sem interferir no código principal?
3. Quais são os comandos do Git utilizados para criar e alternar entre branches?
4. O que é merging e qual é o seu propósito no controle de versão de software?
5. Como o merging é usado para unir o trabalho feito em uma branch de desenvolvimento de volta para a branch principal?
6. Quais são as vantagens de utilizar branches no Git?
7. Como os branches permitem experimentação segura e facilitam o desenvolvimento paralelo?
8. Como os branches facilitam o controle de versão eficiente e a revisão de código?
9. Quais são as desvantagens de utilizar branches no Git?
10. Como a complexidade de gerenciamento e os conflitos de merge podem ser desafios ao utilizar branches?
11. Como a desatualização de branches e a sobrecarga de processo podem ser desvantagens ao utilizar branches?
12. O que são conflitos no Git e como eles ocorrem durante o processo de mesclagem?
13. Como os conflitos de merge podem ser resolvidos manualmente?
14. Quais são as vantagens de utilizar o GitHub para hospedagem de código-fonte e colaboração?
15. Quais são os recursos avançados do Git e como eles podem ser explorados?
16. Quais são as ferramentas GUI para Git e como elas podem facilitar o trabalho com o controle de versão?
17. Como o Git pode ser integrado com IDEs, como o VSCode?
18. O que é o arquivo .gitignore e como ele é utilizado no controle de versão com Git?
19. Como o GitHub Desktop pode ser utilizado para facilitar a interação com o GitHub?
20. Quais são os benefícios de utilizar o GitHub para compartilhar projetos de código aberto e colaborar com outros desenvolvedores?

## O que é Branching

Branching, no contexto de controle de versão de software, é o processo de criar uma "cópia" do código que pode ser modificada independentemente do código principal. Isso permite que os desenvolvedores trabalhem em novas funcionalidades ou correções de bugs sem interferir no código principal.

![branch](./images/git-branch.png)

> Quantos branches existem na figura?

## ⚖️ Vantagens e Desvantagens de Trabalhar com Branches no Git

| Aspecto                | Vantagens                                                                                   | Desvantagens                                                                                  |
|------------------------|---------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------|
| 🧩 Isolamento           | Permite desenvolver funcionalidades sem afetar o código principal.                        | Pode causar divergência se os branches não forem sincronizados com frequência.               |
| 🤝 Colaboração          | Vários desenvolvedores podem trabalhar em paralelo com segurança.                         | Pode haver conflitos ao integrar mudanças simultâneas.                                        |
| 🧪 Experimentação        | Possibilita testar ideias ou refatorações sem riscos ao projeto principal.               | Branches não usados ou esquecidos acumulam “lixo” no repositório.                             |
| 📈 Fluxo de trabalho     | Suporta metodologias como Git Flow, trunk-based e CI/CD.                                 | Fluxos mal definidos podem gerar confusão e retrabalho.                                       |
| 🔍 Revisão e testes      | Facilita Pull Requests e testes isolados antes da integração.                            | Exige processos e ferramentas para garantir validação consistente.                            |
| 🗂️ Organização de versões | Permite manter branches para produção, desenvolvimento, hotfix, etc.                    | Excesso de branches pode tornar o repositório difícil de navegar e manter.                   |
| ⚠️ Manutenção            | Branches facilitam manutenção de versões antigas em paralelo.                           | Quanto mais branches, maior a necessidade de governança e limpeza periódica.                 |

---

> ✅ **Resumo:** trabalhar com branches é poderoso e essencial no Git, mas exige disciplina, processos claros e colaboração eficiente para evitar desorganização e conflitos.


## O que é Merging

Merging, no contexto de controle de versão de software, é o processo de combinar as alterações de uma branch em outra. Isso é comumente usado para unir o trabalho feito em uma branch de desenvolvimento de volta para a branch principal.

### 🔀 Vantagens e Desvantagens de Realizar Merges no Git

| Aspecto               | Vantagens                                                                                  | Desvantagens                                                                                     |
|------------------------|--------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------|
| 🔄 Integração de código | Permite consolidar mudanças de diferentes branches em um único ponto.                     | Pode gerar conflitos se o histórico estiver muito divergente.                                   |
| 📚 Preservação do histórico | Mantém a linha do tempo real com todos os commits e contextos originais.               | Pode deixar o histórico mais complexo e difícil de visualizar.                                  |
| 🤝 Colaboração         | Facilita o trabalho em equipe e a fusão de contribuições paralelas.                        | Exige alinhamento prévio entre desenvolvedores para minimizar conflitos.                        |
| ✅ Estabilidade         | Permite unir apenas branches testadas e revisadas ao código principal.                    | Commits mal documentados dificultam entender a origem de mudanças durante o merge.             |
| 🧩 Flexibilidade        | Suporta fluxos diversos (ex: Git Flow, trunk-based), com branches curtos ou longos.       | Merges mal coordenados podem quebrar o código ou introduzir bugs difíceis de rastrear.         |
| 📈 CI/CD e automação    | Integração contínua pode ser ativada ao mesclar em branches protegidos.                   | Se políticas de merge não forem aplicadas (ex: PR review), pode comprometer a qualidade do código. |

---

> 💡 **Resumo:** merges são essenciais para consolidar trabalho em equipe, mas exigem coordenação, boas práticas e revisão de código para evitar regressões.

![branch](./images/0203-git-merge-git-rebase.jpg)


## 🔄 Tabela Comparativa: `git merge` vs `git rebase`

| Aspecto                  | `git merge`                                                                 | `git rebase`                                                             |
|--------------------------|------------------------------------------------------------------------------|---------------------------------------------------------------------------|
| 📌 O que faz             | Une o histórico de duas branches, criando um commit de merge.               | Reescreve o histórico aplicando commits de um branch sobre outro.       |
| 🕘 Histórico             | Preserva o histórico completo, incluindo pontos de divergência.             | Cria um histórico linear e limpo, omitindo os merges.                   |
| 🧩 Uso típico            | Colaboração entre times, onde a integridade do histórico é importante.       | Manter histórico limpo antes de integrar a um branch principal.         |
| 🤝 Quando usar           | Ao integrar branches compartilhados com outros desenvolvedores.             | Ao atualizar sua branch com mudanças do main antes de um pull request. |
| ⚠️ Riscos                | Histórico pode ficar mais complexo com muitos merges.                      | Altera hashes dos commits (não recomendado em branches públicos).       |
| 🌳 Visual no `git log`   | Ramificações visíveis (grafo divergente).                                   | Linha do tempo linear (mais legível).                                   |
| 📦 Commit automático     | Cria commit automático de merge (pode ser personalizado).                   | Reaplica os commits um por um (reorganiza).                             |
| 💬 Recomendação geral    | Use para preservar contexto e facilitar debugging coletivo.                 | Use para limpar o histórico antes de mesclar via PR.                    |

---

### 🧠 Dica prática

- Prefira `merge` para **projetos com colaboração simultânea**.
- Prefira `rebase` para **trabalho individual e limpeza de histórico antes de contribuir com o main**.

> ⚠️ **Nunca rebase branches que já foram compartilhados com outros desenvolvedores.**

O Git suporta **diferentes tipos de merge**, dependendo do contexto, do histórico dos branches e das opções usadas no comando. Abaixo estão os **principais tipos de merge suportados pelo Git**:

---

## 🔀 Tipos de Merge no Git

| Tipo de Merge                                   | Descrição                                                                                    | Quando ocorre?                                                                       |
| ----------------------------------------------- | -------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------ |
| **Merge automático (Fast-forward)**             | O branch de destino pode avançar diretamente para o commit do branch de origem.              | Quando não há commits divergentes (ex: `main` ainda está “atrasado”).                |
| **Merge com commit de merge (Three-way merge)** | Git cria um commit especial unindo dois históricos diferentes.                               | Quando os branches têm commits distintos e divergiram em algum ponto.                |
| **Merge manual com conflitos**                  | Ocorre quando Git não consegue resolver automaticamente — precisa de intervenção humana.     | Quando ambos os branches modificaram a mesma linha ou arquivo de forma incompatível. |
| **Squash merge**                                | Une as alterações de uma branch como **um único commit**, descartando o histórico detalhado. | Com `git merge --squash`; comum antes de integrar PRs limpos no `main`.              |
| **Octopus merge** (multi-branch)                | Combina **3 ou mais branches** em um único commit de merge.                                  | Com `git merge branch1 branch2 branch3`; usado em integração automatizada.           |
| **No-ff (sem fast-forward)**                    | Força a criação de commit de merge mesmo quando seria possível um fast-forward.              | Com `git merge --no-ff`; usado para preservar o ponto de merge no histórico.         |

---

## 📌 Exemplos de comandos

```bash
git merge feature               # merge normal (pode ser fast-forward ou three-way)
git merge --no-ff feature       # força commit de merge, mesmo se puder avançar direto
git merge --squash feature      # combina todos os commits como um único commit
git merge branch1 branch2       # octopus merge (usado para múltiplos branches ao mesmo tempo)
```

---

### 🧠 Dica

* Use `--squash` para manter o histórico do `main` limpo.
* Use `--no-ff` quando quiser preservar o ponto onde o merge foi feito.

---

### 🧩 Resolução de Conflitos no Git

Conflitos acontecem quando dois branches modificam a mesma linha de um arquivo ou arquivos simultaneamente. O Git não consegue decidir qual mudança manter, então pede intervenção manual.

### 🔥 Quando ocorre?

- Dois branches editam a mesma linha.
- Um branch edita e outro remove a mesma linha.
- Um arquivo é modificado em dois lugares sem histórico comum recente.

### 💥 Exemplo de conflito típico:

```plaintext
<<<<<<< HEAD
linha do branch atual
=======
linha do branch que está sendo mesclado
>>>>>>> feature
````

### ✅ Como resolver

1. Edite o arquivo conflitado e escolha ou combine o conteúdo.
2. Salve o arquivo.
3. Marque como resolvido:

   ```bash
   git add nome-do-arquivo
   git commit -m "Resolve conflito entre main e feature"
   ```

### 🧪 Dica: Ferramentas úteis

* `git status` mostra arquivos com conflito.
* GUI: GitHub Desktop, VSCode, GitKraken ajudam na visualização e resolução.
* CLI: `git mergetool` integra editores visuais como Meld ou Beyond Compare.

> 💡 Resolução rápida evita bloqueios no fluxo de integração.

## 🔧 Tabela: Resolução de Conflitos no Git

| Situação que Gera Conflito          | Exemplo                                                     | Solução                                                   |
|-------------------------------------|-------------------------------------------------------------|------------------------------------------------------------|
| Mesma linha modificada em 2 branches | `main` e `feature` alteram a mesma linha do mesmo arquivo   | Editar manualmente e escolher qual linha manter           |
| Um branch edita, outro deleta       | Um branch remove uma linha que o outro alterou              | Decidir se mantém a linha modificada ou remove            |
| Ordem de commits diferente          | Commits similares aplicados em ordem diferente              | Rebase interativo ou merge manual                         |
| Merge automático falha              | Git não consegue decidir entre dois conteúdos conflitantes  | Abrir o arquivo, resolver e `git add` + `git commit`      |
| Conflitos ao usar rebase            | `git rebase` reescreve histórico e encontra diferenças      | Resolver como em merge, usar `git rebase --continue`      |

---

### 🛠️ Ferramentas para auxiliar

| Ferramenta          | Tipo          | Observação                                                  |
|---------------------|---------------|--------------------------------------------------------------|
| `git status`        | CLI           | Mostra arquivos com conflitos pendentes                      |
| `git diff`          | CLI           | Exibe as diferenças e áreas de conflito                      |
| `git mergetool`     | CLI + GUI     | Abre ferramenta visual configurada (ex: Meld, KDiff3)       |
| VSCode              | IDE/GUI       | Interface integrada com destaque visual e botões de merge   |
| GitHub Desktop      | GUI           | Exibe arquivos conflitantes com opções de resolução visual  |
| GitKraken, Sourcetree | GUI         | Interfaces visuais com resolução de conflito integrada       |

---

> 💡 Sempre revise bem os arquivos antes de finalizar a resolução com `git add` e `git commit`.

---
### Ferramentas Gráficas de Controle de Versão

*Objetivos:*
- Explorar recursos avançados do Git.
- Introdução ao uso de GUIs para Git.

*Conteúdos:*
- Ferramentas GUI para Git: SourceTree, GitHub Desktop.
- Integração do Git com IDEs (VSCode).
- Trabalhando com Gitignore

*Atividades:*
- Prática dos comandos avançados através de cenários complexos.
- Exploração de uma ferramenta GUI Git em um projeto exemplo.

### Introdução ao GitHub

O GitHub é uma plataforma de hospedagem de código-fonte e colaboração que permite que desenvolvedores trabalhem juntos em projetos de software. Ele fornece recursos avançados de controle de versão, gerenciamento de problemas, revisão de código e integração contínua.

Com o GitHub, você pode criar repositórios para armazenar seu código-fonte, colaborar com outros desenvolvedores por meio de pull requests, gerenciar problemas e tarefas, e implantar seu software em serviços de hospedagem.

Além disso, o GitHub oferece uma interface amigável e intuitiva, facilitando a navegação pelos repositórios, visualização do histórico de commits e revisão de alterações.

O GitHub também é amplamente utilizado pela comunidade de desenvolvedores para compartilhar projetos de código aberto, permitindo que outros desenvolvedores contribuam, aprendam e colaborem em projetos de software.

Se você é novo no GitHub, é altamente recomendável explorar seus recursos e aprender a usá-lo para melhorar sua produtividade e colaboração no desenvolvimento de software.

### Introdução ao GitHub Desktop

O GitHub Desktop é uma ferramenta GUI (Interface Gráfica do Usuário) para o Git que facilita o controle de versão e a colaboração em projetos hospedados no GitHub. Ele fornece uma interface intuitiva e amigável para realizar tarefas comuns do Git, como clonar repositórios, criar branches, fazer commits, mesclar alterações e sincronizar com o repositório remoto.

Com o GitHub Desktop, você pode visualizar facilmente o histórico de commits, comparar alterações entre branches e resolver conflitos de mesclagem de forma visual. Ele também oferece recursos avançados, como o uso de submódulos, rebase interativo e cherry-pick.

Além disso, o GitHub Desktop é altamente integrado com o ecossistema do GitHub, permitindo que você crie pull requests, revise e comente em código, e acompanhe as atividades do repositório diretamente na interface.

Se você está começando com o Git ou prefere uma abordagem mais visual para o controle de versão, o GitHub Desktop é uma ótima opção para você. Ele está disponível para Windows e macOS e pode ser baixado gratuitamente no site oficial do GitHub.

### Recursos do GitHub Desktop

O GitHub Desktop oferece uma variedade de recursos para facilitar o controle de versão e a colaboração em projetos. Alguns dos recursos principais incluem:

- Interface intuitiva e amigável: O GitHub Desktop possui uma interface fácil de usar, com menus e botões claros que facilitam a realização de tarefas comuns do Git.

- Visualização do histórico de commits: Você pode visualizar facilmente o histórico de commits do seu repositório, verificando as mensagens de commit, as alterações feitas e os autores.

- Comparação de alterações entre branches: O GitHub Desktop permite que você compare as alterações feitas em diferentes branches, facilitando a identificação de diferenças e conflitos.

- Resolução visual de conflitos de mesclagem: Quando ocorrem conflitos de mesclagem, o GitHub Desktop fornece uma interface visual para ajudar na resolução desses conflitos, permitindo que você escolha quais alterações devem prevalecer.

- Integração com o ecossistema do GitHub: O GitHub Desktop está integrado ao GitHub, permitindo que você crie pull requests, revise e comente em código e acompanhe as atividades do repositório diretamente na interface.

- Recursos avançados: Além das funcionalidades básicas do Git, o GitHub Desktop oferece recursos avançados, como o uso de submódulos, rebase interativo e cherry-pick.

Esses são apenas alguns dos recursos oferecidos pelo GitHub Desktop. Experimente a ferramenta e descubra como ela pode facilitar o seu trabalho com controle de versão e colaboração em projetos hospedados no GitHub.

## Ignorando arquivos no Git

O arquivo .gitignore é usado para especificar quais arquivos e diretórios devem ser ignorados pelo Git. Isso significa que o Git não rastreará as alterações nesses arquivos e diretórios, evitando que eles sejam incluídos nos commits e enviados para o repositório remoto.

### 📄 Tabela: Utilização do Arquivo `.gitignore`

| Tipo de Arquivo/Diretório            | Exemplo                                | Por que ignorar?                                                       |
|--------------------------------------|----------------------------------------|------------------------------------------------------------------------|
| **Arquivos de build/compilação**     | `*.class`, `*.exe`, `dist/`, `build/`  | Gerados automaticamente; não precisam ser versionados.                |
| **Dependências externas**            | `node_modules/`, `vendor/`, `venv/`    | Recriáveis via gerenciadores de pacotes (`npm`, `pip`, etc.).         |
| **Configurações locais do editor/IDE**| `.vscode/`, `.idea/`, `*.sublime-*`    | Preferências pessoais que não afetam o funcionamento do projeto.      |
| **Arquivos temporários/sistema**     | `*.log`, `*.tmp`, `Thumbs.db`, `.DS_Store` | Arquivos criados pelo sistema operacional ou durante execução.    |
| **Credenciais e arquivos sensíveis** | `.env`, `secrets.json`, `*.pem`        | Contêm dados privados que **nunca devem ser versionados**.            |
| **Arquivos de cache**                | `__pycache__/`, `.cache/`, `.pytest_cache/` | Dados temporários, inúteis no versionamento.                      |
| **Logs e arquivos de debug**         | `*.log`, `debug/`                      | Não são relevantes para outros desenvolvedores ou para produção.      |


## 📄 Casos de Uso do `.gitignore`

O `.gitignore` é usado para evitar que arquivos desnecessários, sensíveis ou gerados automaticamente sejam versionados. Entre os principais casos de uso:

* **Builds e executáveis:** arquivos compilados ou intermediários não precisam ser rastreados.
* **Configurações locais:** arquivos de IDE, chaves de API e ambientes pessoais devem ser ignorados.
* **Arquivos temporários:** logs, cache e arquivos de frameworks poluem o repositório.
* **Dependências:** pastas como `node_modules/` ou `venv/` podem ser recriadas com o gerenciador de pacotes.
* **Dados sensíveis:** senhas e credenciais não devem ir para o repositório.

> 🔧 Use curingas (`*`, `?`) e revise o `.gitignore` com frequência para evitar versionar conteúdo desnecessário ou perigoso.

### 🧠 Dica: Gerando .gitignore com base na tecnologia

Para gerar um arquivo `.gitignore` personalizado para seu projeto, você pode usar o site [https://gitignore.io](https://gitignore.io).  

Basta digitar as tecnologias utilizadas (ex: `python`, `node`, `vscode`) e o site gerará automaticamente um `.gitignore` com as regras apropriadas para ignorar arquivos comuns dessas stacks.

---

### 🔄 Comparativo: `git merge` vs `git rebase`

| Comando     | O que faz                            | Quando usar                                   | Considerações                         |
|-------------|---------------------------------------|-----------------------------------------------|----------------------------------------|
| `git merge` | Une dois branches mantendo histórico | Ideal para colaboração e histórico claro      | Pode gerar commits de merge           |
| `git rebase`| Reescreve histórico aplicando commits | Ideal para manter histórico linear            | Evite em branches compartilhados      |

> ⚠️ Use `git rebase` com cuidado — ele altera o histórico do repositório.

---

### Resumo

1. Branching é o processo de criar uma ramificação do código principal em um controle de versão de software. O objetivo é permitir que os desenvolvedores trabalhem em novas funcionalidades ou correções de bugs sem interferir no código principal.

2. O branching permite que os desenvolvedores trabalhem em novas funcionalidades ou correções de bugs sem interferir no código principal. Isso é possível porque cada branch é uma cópia independente do código principal.

3. Os comandos do Git utilizados para criar e alternar entre branches são:
    - `git branch`: cria um novo branch.
    - `git checkout`: alterna para um branch existente.
> 💡 Dica: O comando `git switch` pode ser usado como alternativa moderna ao `git checkout` para alternar entre branches.


4. Merging é o processo de combinar as alterações de uma branch em outra. Seu propósito no controle de versão de software é unir o trabalho feito em uma branch de desenvolvimento de volta para a branch principal.

5. O merging é usado para unir o trabalho feito em uma branch de desenvolvimento de volta para a branch principal. Isso permite que as alterações feitas em uma branch sejam incorporadas ao código principal.

6. As vantagens de utilizar branches no Git são:
    - Isolamento de código.
    - Experimentação segura.
    - Facilita o desenvolvimento paralelo.
    - Controle de versão eficiente.
    - Revisão de código e integração contínua.
    - Desacoplamento de releases e desenvolvimento.

7. Os branches permitem experimentação segura e facilitam o desenvolvimento paralelo, pois cada branch é um ambiente isolado onde os desenvolvedores podem trabalhar em diferentes funcionalidades ou correções de bugs.

8. Os branches facilitam o controle de versão eficiente e a revisão de código, pois cada alteração pode ser revisada e testada antes de ser mesclada no código principal.

9. As desvantagens de utilizar branches no Git são:
    - Complexidade de gerenciamento.
    - Conflitos de merge.
    - Desatualização de branches.
    - Sobrecarga de processo.
    - Divergência de código.

10. A complexidade de gerenciamento e os conflitos de merge podem ser desafios ao utilizar branches. É importante ter um bom fluxo de trabalho e comunicação entre os desenvolvedores para lidar com essas questões.

11. A desatualização de branches e a sobrecarga de processo podem ser desvantagens ao utilizar branches. É importante manter os branches atualizados e ter um fluxo de trabalho eficiente para evitar esses problemas.

12. Conflitos no Git ocorrem quando duas ou mais pessoas modificam a mesma parte do código em branches diferentes e tentam mesclar essas alterações. Os conflitos precisam ser resolvidos manualmente, decidindo qual alteração deve prevalecer.

13. Os conflitos de merge podem ser resolvidos manualmente editando o arquivo em conflito e decidindo qual código deve prevalecer ou se uma combinação dos dois é necessária.

14. As vantagens de utilizar o GitHub para hospedagem de código-fonte e colaboração são:
     - Facilita o compartilhamento de projetos de código aberto.
     - Permite colaboração entre desenvolvedores.
     - Oferece recursos avançados de controle de versão.
     - Integração com outras ferramentas e serviços.

15. Os recursos avançados do Git podem ser explorados para melhorar o controle de versão, como o uso de tags, ramificações remotas, rebase, entre outros.

16. Existem várias ferramentas GUI para Git, como Sourcetree, GitKraken e GitHub Desktop, que facilitam o trabalho com o controle de versão, fornecendo uma interface gráfica para executar comandos do Git.

17. O Git pode ser integrado com IDEs, como o VSCode, por meio de extensões que fornecem recursos avançados de controle de versão diretamente na interface da IDE.

18. O arquivo .gitignore é utilizado no controle de versão com Git para especificar quais arquivos e diretórios devem ser ignorados pelo Git. Isso é útil para evitar que arquivos desnecessários sejam incluídos no repositório.

19. O GitHub Desktop é uma ferramenta que facilita a interação com o GitHub, permitindo que os desenvolvedores gerenciem repositórios, criem branches, façam commits e realizem outras operações diretamente em uma interface gráfica.

20. Os benefícios de utilizar o GitHub para compartilhar projetos de código aberto e colaborar com outros desenvolvedores incluem a facilidade de compartilhamento, a visibilidade da comunidade, a possibilidade de receber contribuições e a integração com outras ferramentas e serviços.