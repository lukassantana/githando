Principais comandos do terminal: https://goo.gl/DqpEBa

Git: trabalha com os estados dos arquivos (outros sistemas trabalham com as diferenças)

Snapshots: estados dos arquivos, todos os estados levam os arquivos daquele momento. http://easycaptures.com/3419459554.

História (linus torvalds): bitkeeper; mesmo criador do linux (indignação); melhorias: velocidade, design, não linear, grandes projetos.

CONFIGURATION
git.config, git.config.user and git.config.project
- git config --global user.name "Ral Oliver"

CICLO DE VIDA DOS STATUS DOS ARQUIVOS (https://goo.gl/HrS4LF)
- untracked (não marcado): arquivo acabou de ser adicionado, mas não visto pelo git
- unmodified: existe, mas não foi modificado
- modified: arquivo modificado
- staged: área pra onde será criada versão
- commit: pegue todos os arquivos staged e crie uma imagem, snapshot, uma versão git commit -m "Add readme.md"
- git status, git add, git log, git log decorate, git log --author="Oliver", git shortlog, git shortlog -sn, git log --graph, git show, git diff, git diff --name-only, git commit -am, git reset

VOLTAR A VERSÃO
- git checkout (voltar o que foi feito antes sem commit)
- git reset HEAD (remover do stage)
- DEU RUIM: commitei e preciso voltar (volte sempre o commit anterior ao desejado)
- git reset --soft: voltar o commit e o arquivo fica em stage
- git reset --mixed: voltar o commit e o arquivo fica em modified
- git reset --hard: ignorar a existência do commit e das alterações (MUITO CALMA NESSA ALMA)

GITHUB
git remote add origin https://github.com/raloliver/githando.git
- origin nome default pra origem do remoto
git push -u origin master (trackear repositorio)
- num primeiro momento é interessante  usar tudo com -u para nas próximas vezes  digitar apenas gut push
git remote -v
- mais detalhes da origem do repositório remoto

master: brunch inicial
git clone: url SSH para clonar o repo local, não pode modificar e realizar push
fork: fazer uma copia pra depois enviar as modificações (pull-request)

BRANCH
um ponteiro movel que leva um commit. pra cada hash, é criada um snapshot e o branch aponta para um determinado commit, que inicialmente se chama master.
e um novo branch pode apontar para um mesmo commit, ou você pode ter um novo branch apontando para um novo commit (http://easycaptures.com/4388317726)
vantagens: modificar sem alterar o master / facilmente desligável / melhor para equipes / evita conflitos e posso trabalhar com o mesmo arquivo.
- git checkout -b israel (criação do brunch) - git branch (lista) - git checkout master (entra)
DELETAR BRUNCH git branch -D branch-name

MERGE (cria um commit novo, pra unir as diferenças)
exemplo de merge: http://easycaptures.com/4825685558 e http://easycaptures.com/3984703625 (ciclo da forma diamante, [vértice])
PRO: merge é uma operação não destrutiva
CONTRA: merge precisa de um commit extra e deixa o histórico poluído

REBASE (joga as mudanças para o início da fila)
exemplo de rebase: http://easycaptures.com/4814535745 e http://easycaptures.com/2156899863 (fast-forward) git pull --rebase
PRO: rebase evita o commit extra e permanece o histórico linear
CONTRA: perda da ordem cronológica por conta da mudança de histórico

MERGE x REBASE
evite o chamado "guitar-hero" usando o merge, preferencialmente use o rebase.
- git merge branch-name

GIT STASH
- Responsável por guardar num arquivo, modificações que ainda não foram commitadas e que eu posso chamar depois.
- git stash (WIP: work in progress)
- git stash apply

ALIAS
- git config --global alias.s status

TAGS
- Delimitador com base em vários commits ou em novas versões que foram criadas.
- git tag -a 0.0.1 -m "Versão Beta Tester"