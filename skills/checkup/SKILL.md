---
name: checkup
description: Check-up de retomada. Use só quando eu digitar /checkup — dentro de um projeto, confere o roadmap contra a realidade e diz onde parei e para onde vou; na raiz ou numa pasta de área, mostra um painel de todos os projetos e sugere qual retomar.
argument-hint: "[caminho opcional de um projeto ou de uma pasta de área]"
disable-model-invocation: true
allowed-tools:
  - Read
  - Grep
  - Glob
  - Bash(ls *)
  - Bash(git log *)
  - Bash(git status *)
  - Bash(git branch *)
  - Bash(git -C * log *)
  - Bash(git -C * status *)
  - Bash(git -C * branch *)
---

# /checkup — onde eu parei, onde estou, para onde vou

Voltei a mexer em algo depois de dias longe e não lembro onde parei. Quero um check-up que **não confie cegamente no roadmap**: ele pode estar desatualizado justamente porque eu sumi.

Pasta pedida (pode estar vazia; se vazia, use a pasta atual): $ARGUMENTS

## Regra de ouro: só leitura

Este comando **não edita nada**. Nem roadmap, nem código, nem arquivo de histórico. Quando algo estiver errado ou faltando, proponha a correção e espere eu aprovar. O roadmap é meu.

Toda afirmação sobre o estado do projeto vem com a fonte: o arquivo ou o commit (hash curto) de onde saiu. Se é dedução sua, diga que é dedução.

## 1. Qual modo?

- **Panorama** — a pasta é `~/Documents/Projects` ou uma pasta que agrupa projetos (uma área como `Sistemas/` ou `RPGs/`, ou uma categoria como `Sistemas/Sites/` ou `RPGs/Campanhas/`).
- **Projeto** — qualquer outra pasta com `ROADMAP.md`, `.git` ou `CLAUDE.md` próprio.
- Se não der para saber, pergunte com a ferramenta de perguntas.

---

## Modo projeto

### 1.1 Leia o contexto

- O `CLAUDE.md` da pasta e o da área acima dela. É lá que está o que conta como marco, qual é o mapa e qual é o histórico nesta área — não assuma que é software.
- `ROADMAP.md`.
- O mapa: `ARQUITETURA.md`, `ESTRUTURA.md` ou `CAMPANHA.md`, o que existir.
- O histórico: `CHANGELOG.md` ou o registro de sessões da campanha. Só as entradas mais recentes.

Se o projeto for grande (muito código para ler), delegue a varredura do passo 1.2 ao subagente `Explore` e peça só as conclusões, para não encher o contexto.

### 1.2 Confira o roadmap contra a realidade

Com git:

- Data da última mudança do roadmap: `git log -1 --format='%h %cs' -- ROADMAP.md`.
- O que aconteceu depois: `git log --oneline <hash>..HEAD`.
- Trabalho esquecido: `git status --short` e `git branch` (branch além da principal pode ser trabalho parado).

Sem git: use `ls -lt` para comparar a data do `ROADMAP.md` com a dos outros arquivos.

Depois, cruze:

- Item marcado `- [ ]` que os commits ou o histórico mostram como feito.
- Item marcado `- [x]` sem sinal nenhum de ter sido feito.
- Trabalho recente (commits, arquivos mudados) que não corresponde a item nenhum do roadmap.
- "Onde estou" que não bate com o último commit ou com a última entrada do histórico.

### 1.3 Responda

**Topo — curto, cabe numa tela:**

1. **Onde parei** — a última coisa concluída, com data e fonte.
2. **Onde estou** — o que está pela metade e o que está travado.
3. **Próximo passo sugerido** — uma tarefa, pequena o bastante para uma sessão.
4. **Por quê** — e qual critério você usou: primeiro o que destrava outras tarefas; depois o que fecha o marco atual; por último o resto.

Se o roadmap estiver desatualizado, abra o topo com um alerta de uma linha: há quanto tempo e quantos commits de diferença. Nesse caso, as quatro partes seguem **a realidade**, não o roadmap.

**Embaixo — o detalhe, para ler se eu quiser:**

- **O que é o projeto** — duas linhas, tiradas do mapa ou do README.
- **O que já foi feito** — o que fechou recentemente, pelo histórico.
- **Marcos** — cada um com quantos itens feitos de quantos.
- **Pendências soltas** — mudança sem commit, branch parada, TODO recente.
- **Divergências** — cada item do passo 1.2, com a fonte.
- **Correção proposta** — se o roadmap precisa mudar, mostre o trecho novo de "Onde estou" e "Próximo passo" num bloco, pronto para eu aprovar. Não grave.

### 1.4 Projeto sem roadmap

Faça o check-up com o que existir (git, histórico, mapa) e, no fim, proponha um `ROADMAP.md` no formato do meu CLAUDE.md global. Só grave se eu aprovar — e a gravação acontece fora deste comando, numa resposta seguinte.

---

## Modo panorama

### 2.1 Ache os projetos

Use `Glob` a partir da pasta pedida, procurando `**/ROADMAP.md`, `**/.git/HEAD` e `**/CLAUDE.md`.

- Um projeto é a pasta que contém um desses marcadores.
- O `CLAUDE.md` de uma área ou categoria (ex.: `Sistemas/CLAUDE.md`, `RPGs/CLAUDE.md`) não faz daquela pasta um projeto.
- Ignore o que estiver dentro de `node_modules`, `.venv`, `vendor` ou de outro projeto já encontrado.
- O `ROADMAP.md` da própria raiz `~/Documents/Projects` é o de manutenção. Ele entra na tabela como "Manutenção".

### 2.2 Colete, por projeto

- **Última atividade:** `git -C <pasta> log -1 --format=%cs`; sem git, `ls -lt <pasta>`.
- **Onde parou:** a seção "Onde estou" do roadmap, resumida em uma linha. Leia só o começo do arquivo.
- **Pendências:** `git -C <pasta> status --short` (conte os arquivos, não liste).
- **Sinal:**
  - 🟢 roadmap em dia (sem commits depois da última mudança dele);
  - 🟡 roadmap desatualizado (diga quantos commits atrás);
  - ⚪ sem roadmap.

Se passar de uns quinze projetos, delegue a coleta ao subagente `Explore`.

### 2.3 Responda

1. Uma tabela: projeto (caminho curto) · última atividade · onde parou · sinal · pendências. Ordene da atividade mais recente para a mais antiga.
2. **Sugestão de qual retomar** — um projeto só, com o porquê e o critério usado, nesta ordem:
   1. o que destrava outro projeto (um roadmap que depende de outro);
   2. o que tem trabalho pela metade ou mudança sem commit — trabalho interrompido esfria rápido;
   3. o que está mais perto de fechar um marco.
   
   É sugestão. Prioridade entre projetos é decisão minha.
3. Uma linha dizendo que, para o check-up completo, basta rodar `/checkup` dentro da pasta do projeto.

---

## Fim

Termine sempre com **como eu confiro**: quais arquivos ou comandos eu abro para verificar as duas ou três afirmações mais importantes que você fez.
