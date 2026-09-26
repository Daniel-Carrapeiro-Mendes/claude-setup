---
name: push
description: Envia os commits locais para o repositório remoto, com checagens de segurança antes. Acionada apenas pelo usuário com /push.
argument-hint: "[instruções extras opcionais]"
disable-model-invocation: true
context: fork
model: haiku
background: false
allowed-tools:
  - Bash(git status)
  - Bash(git status *)
  - Bash(git branch *)
  - Bash(git log *)
  - Bash(git remote *)
  - Bash(git diff *)
---

Sua tarefa é enviar os commits locais deste repositório para o remoto, com segurança.

## Passo 1 — Diagnóstico

Rode, nesta ordem, e leia o resultado antes de decidir qualquer coisa:

- `git status -sb`
- `git branch --show-current`
- `git log --oneline -5`

## Passo 2 — Checagens de segurança

Pare e apenas relate (sem tentar consertar) se qualquer uma destas condições for verdadeira:

1. **Não é um repositório git.** Avise e encerre.
2. **Há mudanças não commitadas.** Liste os arquivos afetados e encerre. Nunca crie um commit: isso é decisão do usuário.
3. **Não há nada novo para enviar** (a branch já está em dia com o remoto). Avise e encerre.
4. **Não existe um remoto configurado.** Explique como configurar e encerre.

Se a branch atual for `main` ou `master`, pode continuar, mas destaque isso com clareza no relatório final.

## Passo 3 — Push

- Se a branch já acompanha uma branch remota: `git push`
- Se ainda não acompanha: `git push -u origin <branch-atual>`
- **Nunca** use `--force`, `--force-with-lease`, `--delete` ou `--mirror`. Se achar que algum deles é necessário, pare e explique o motivo, deixando a decisão para o usuário.
- Se o push for rejeitado (por exemplo, "non-fast-forward" ou "fetch first"), **não tente resolver sozinho**. Relate o erro exatamente como apareceu e sugira que o usuário avalie um `git pull --rebase`.

## Passo 4 — Relatório final

Seja curto e objetivo:

- Branch de origem e destino (remoto)
- Quantos commits foram enviados, com uma linha por commit
- Ou, se nada foi enviado, o motivo

## Instruções extras do usuário

Podem estar vazias. Se houver algo aqui, respeite, desde que não contrarie as regras acima:

$ARGUMENTS
