---
name: nuvem
description: Passagem entre o computador e a nuvem. Use só quando eu digitar /nuvem — no computador, prepara o projeto para eu continuar numa sessão na nuvem, ou recebe o que voltou dela; na nuvem, salva tudo e me ensina a voltar para o computador.
argument-hint: "[preparar]"
disable-model-invocation: true
# Existe uma cópia no claude.ai, para funcionar na nuvem. Mudou este arquivo, suba a cópia de novo (o cabeçalho de lá só aceita name, description e allowed-tools).
allowed-tools:
  - Bash(printenv *)
  - Bash(git status)
  - Bash(git status *)
  - Bash(git log *)
  - Bash(git branch *)
  - Bash(git remote *)
  - Bash(git fetch *)
  - Bash(git rev-list *)
  - Bash(ls *)
---

# /nuvem — continuar o trabalho entre o computador e a nuvem

Eu saio do computador com frequência e continuo o trabalho numa sessão na nuvem (claude.ai/code, ou a aba Code do app do Claude). Depois volto para o computador. Quero passar de um lado para o outro **sem perder nada**.

Argumento (pode estar vazio): $ARGUMENTS

## Como a nuvem funciona (fatos da documentação oficial)

- A sessão na nuvem roda numa máquina da Anthropic que **clona o repositório do GitHub**. Ela só enxerga o que está commitado e enviado para lá.
- Ela **não vê** o que fica só no meu computador: `~/.claude/CLAUDE.md`, os CLAUDE.md das áreas (`Sistemas/`, `RPGs/`), `~/.claude/skills`, o `.env`, e arquivos fora do git. Ela **vê** o CLAUDE.md e o `.claude/` commitados no repositório, e as skills que eu ativei no claude.ai.
- As minhas regras chegam lá pelo **script de preparação** do ambiente da nuvem, que escreve `~/.claude/CLAUDE.md` quando a máquina liga. Ele é gerado pelo `/nuvem preparar`. Uso dois ambientes: **Sistemas** e **RPG**.
- Do computador para a nuvem, **a conversa não vai junto**: a nuvem começa uma sessão nova. O que importa tem que estar nos arquivos.
- Da nuvem para o computador, `claude --teleport <id>` traz o ramo **e a conversa inteira**. Ele exige: o computador sem mudança sem commit, a mesma pasta de repositório, o ramo enviado para o GitHub e a mesma conta.
- Na nuvem, a variável `CLAUDE_CODE_REMOTE` vale `true`, e `CLAUDE_CODE_REMOTE_SESSION_ID` guarda o id da sessão.
- A nuvem consegue enviar ramos para o GitHub, mas **não consegue apagar** ramo lá.
- Projeto sem GitHub até pode subir como cópia, mas o trabalho **não volta**. Nesse caso, o caminho é o Remote Control, com o computador ligado.

Se algo aqui não bater com o que você vê (um comando que não existe, uma mensagem diferente), diga e não improvise.

## 1. Qual é o modo?

1. `$ARGUMENTS` é `preparar` → **Preparar**.
2. `printenv CLAUDE_CODE_REMOTE` mostra `true` → **Saída** (estou na nuvem e vou largá-la).
3. No computador, rode `git fetch --prune` e compare:
   - o ramo atual no GitHub tem commits que o computador não tem (`git rev-list --count HEAD..@{u}` maior que zero), ou
   - existe ramo no GitHub com trabalho que ainda não entrou aqui (`git branch -r --no-merged HEAD`; os da nuvem em geral começam com `claude/`)
   → **Chegada**.
4. Nada disso → **Ida**.
5. Se o computador **e** o GitHub têm commits que o outro não tem, ou se não deu para saber, pergunte com a ferramenta de perguntas.

Diga na primeira linha qual modo você escolheu e por quê.

---

## Ida — do computador para a nuvem

### 1. Vale ir para a nuvem?

Uma linha: se o computador vai **ficar ligado**, o Remote Control com `/celular` é mais simples, porque a mesma sessão continua e nada precisa ser movido. A nuvem é para quando o computador vai **desligar**. Siga sem esperar resposta.

### 2. O projeto pode ir?

- Precisa ser repositório git com remoto no GitHub (`git remote -v`).
- Se não for — uma campanha sem repositório no GitHub, a raiz `~/Documents/Projects`, uma pasta sem git —, **pare aqui**. Explique: a nuvem receberia uma cópia, mas o trabalho feito lá não teria como voltar. Recomende o Remote Control.

### 3. O que a nuvem não vai ver

Confira e me diga, em lista curta:

- **Mudança sem commit e arquivo fora do git:** `git status --short`. Tudo isso fica para trás se não for commitado.
- **Arquivo ignorado que importa:** o `.env` nunca sobe (é segredo). Se a tarefa na nuvem precisar dele, a chave tem que ser cadastrada no ambiente da nuvem, não no código. Arquivo de bastidor em `.git/info/exclude` também não vai.
- **As minhas regras:** mostre a data da última mudança do CLAUDE.md global e do CLAUDE.md da área deste projeto (`ls -l --time-style=+%F`). Se algum mudou depois da última vez que eu rodei `/nuvem preparar`, me lembre de rodar de novo e de colar o script no ambiente.
- **Skills:** só vão as que estão ativadas no claude.ai.

### 4. Salve o estado nos arquivos

A conversa não vai para a nuvem. Antes de sair, faça como no passo 2 do `/limpar`:

- `ROADMAP.md`: reescreva "Onde estou" e "Próximo passo sugerido" com o estado real agora, inclusive o que ficou pela metade e em que ponto exato.
- Decisão desta sessão que ainda não está escrita vai para "Decisões" do mapa do projeto.
- Mudança concluída que ainda não está no histórico vai para o `CHANGELOG.md` ou para o registro de sessões.

### 5. Commit e push

Pergunte se pode commitar o que falta. Depois, explique e peça para enviar: o `git push` manda os commits daqui para o GitHub, que é de onde a nuvem clona. Sem ele, a nuvem começa sem o trabalho de hoje. Lembre que o `/push` faz isso com a busca de segredos antes, e sugira que eu o rode.

### 6. Como começar lá

Na **última mensagem** — não no texto de uma pergunta —, me dê:

1. **O passo a passo:** no app do Claude, aba **Code** (ou em claude.ai/code), escolho o repositório `<nome>` e o ambiente **Sistemas** ou **RPG**, conforme a área deste projeto. Se o repositório não aparecer, a nuvem ainda não tem acesso a ele. Explique as duas saídas da documentação: instalar o app do Claude no repositório pelo GitHub, ou rodar `/web-setup` uma vez aqui no terminal (ele envia o token do `gh` para a minha conta).
2. **O prompt pronto**, num bloco de código para copiar. Ele manda ler o `ROADMAP.md`, diz qual é o próximo passo e inclui **só** o que não coube em arquivo.
3. **A alternativa pelo terminal**, antes de sair: `claude --cloud "<o prompt>"` cria a sessão na nuvem daqui mesmo, clonando o ramo atual do GitHub. Depois eu acompanho pelo celular.
4. Uma linha: se eu for desligar o computador, rodo `/desligar` antes.

---

## Saída — na nuvem, antes de largar

### 1. As minhas regras vieram?

Confira se `~/.claude/CLAUDE.md` existe e leia a primeira linha: ela diz de que dia é a cópia. Se não existir, avise logo no começo: esta sessão rodou **sem** as minhas regras, e o trabalho dela merece uma revisão mais atenta. A correção é rodar `/nuvem preparar` no computador e colar o script no ambiente.

### 2. Salve o estado

- Conforme a área: `ROADMAP.md` ("Onde estou", "Próximo passo", itens concluídos), `CHANGELOG.md` ou registro de sessões, e "Decisões" do mapa.
- O que só dá para testar no computador (olhar a tela, abrir no navegador do PC, mexer na máquina) vai para a seção `## Testes pendentes no computador`, no topo do `ROADMAP.md`, acima de "Onde estou". Um bloco por mudança, com data, no formato completo do "Como testar" da área, legível sem esta conversa.

### 3. Commit

Commite tudo no ramo desta sessão (`git branch --show-current`).

### 4. Como eu quero voltar?

Pergunte com a ferramenta de perguntas, com estas duas opções:

- **Levar para a `main` agora** (recomendado quando o trabalho terminou; é o que o meu livro de regras já faz): junte o ramo na `main` e envie direto, sem pull request. Explique cada comando antes. No computador, depois, basta `git pull`.
- **Continuar esta conversa no computador:** envie o ramo (`git push -u origin <ramo>`). No computador, o `claude --teleport <id>` traz o ramo e a conversa inteira. Monte o comando com o id de `printenv CLAUDE_CODE_REMOTE_SESSION_ID`, trocando o prefixo `cse_` por `session_` se for o caso. Se não tiver certeza do formato, diga que digitar `/teleport` aqui na nuvem mostra o comando exato.

### 5. Última mensagem

- O que foi salvo e onde.
- O que eu faço no computador, com cada comando explicado: o que faz, de qual pasta rodar, e como sei que deu certo.
- "Quando chegar, rode `/nuvem` no computador, dentro da pasta do projeto."

---

## Chegada — de volta ao computador

1. **O computador está limpo?** `git status --short`. O `git pull` e o teleport precisam disso. Se houver mudança sem commit, explique por quê e pergunte o que fazer. Não faça stash nem commit por conta própria.
2. **O que veio da nuvem:** `git log --oneline HEAD..@{u}`, e os ramos do GitHub que ainda não entraram aqui, cada um com o último commit.
3. **Trazer o trabalho** (explique o comando e peça antes):
   - Se a `main` do GitHub avançou: `git pull --ff-only`. O `--ff-only` só avança; nunca mistura histórias. Se ele recusar, é porque o computador também mudou. Pare e explique.
   - Se o trabalho está num ramo da nuvem e eu quero a conversa junto: numa janela nova de terminal, na pasta do projeto, `claude --teleport` mostra a lista de sessões da nuvem. Depois de trazer, a sessão da nuvem pode ser arquivada em claude.ai/code, para eu não continuar nas duas.
4. **Testes pendentes no computador:** se o `ROADMAP.md` tiver essa seção, comece por ela, na ordem. Conforme eu confirmo cada teste, remova o bloco. Teste que falhou vira item no roadmap, não some.
5. **Ramo velho no GitHub:** ramo da nuvem que já entrou na `main` fica lá, porque a nuvem não consegue apagá-lo. Ofereça apagar (`git push origin --delete <ramo>`), explicando o comando. Só com a minha licença.
6. Atualize "Onde estou" no `ROADMAP.md`.

---

## Preparar — os scripts das minhas regras na nuvem (`/nuvem preparar`)

Só roda no computador. Na nuvem, explique que este modo precisa dos arquivos do computador e pare.

### 1. Gere os scripts

**Não redigite** os CLAUDE.md: copie os arquivos de verdade com este comando, explicando antes o que ele faz (cria dois scripts em `~/Downloads/claude-nuvem/`, uma pasta comum, que não some quando o computador reinicia — no `/tmp`, um reinício antes de colar já apagou os scripts uma vez):

```bash
gerar() {  # $1 = nome do ambiente, $2 = CLAUDE.md da área
  {
    echo '#!/bin/bash'
    echo "# Ambiente $1 — gerado pelo /nuvem preparar em $(date +%F). Escreve as minhas regras na máquina da nuvem."
    echo 'mkdir -p ~/.claude'
    echo "cat > ~/.claude/CLAUDE.md <<'FIM_CLAUDE_MD'"
    echo "<!-- Cópia para a nuvem, ambiente $1, de $(date +%F). As pastas citadas abaixo não existem aqui: o CLAUDE.md da área vem logo depois do global, e o do projeto vem com o repositório. -->"
    cat ~/.claude/CLAUDE.md
    printf '\n---\n\n'
    cat "$2"
    echo 'FIM_CLAUDE_MD'
  } > ~/Downloads/claude-nuvem/"$1.sh"
}
mkdir -p ~/Downloads/claude-nuvem
gerar Sistemas ~/Documents/Projects/Sistemas/CLAUDE.md
gerar RPG ~/Documents/Projects/RPGs/CLAUDE.md
```

### 2. Confira antes de me entregar

- `grep -c FIM_CLAUDE_MD ~/Downloads/claude-nuvem/*.sh` precisa dar **2** em cada arquivo (a abertura e o fecho). Mais que isso, algum CLAUDE.md contém essa palavra e o script quebraria: pare e me avise.
- `bash -n` em cada script não pode mostrar erro.
- Rode cada um numa pasta de teste descartável (`H=$(mktemp -d); HOME=$H bash <script>`) e confira que o `CLAUDE.md` gerado contém o global e o da área, sem nada faltando.

### 3. Entregue

Na última mensagem:

1. O caminho dos dois scripts e como copiá-los: `code ~/Downloads/claude-nuvem/Sistemas.sh`, selecionar tudo, copiar. Depois de colar os dois, a pasta pode ser apagada.
2. O passo a passo: em claude.ai/code, criar (ou editar) os ambientes **Sistemas** e **RPG** e colar cada script no campo do script de preparação. Não sei os nomes exatos dos botões. Se você também não souber, diga isso em vez de inventar.
3. Como conferir: numa sessão nova na nuvem, `/context` tem que listar `/root/.claude/CLAUDE.md` em "Memory files".
4. Uma linha: o script é uma cópia. Mudou o CLAUDE.md global ou o de uma área, rode `/nuvem preparar` de novo e cole outra vez.
