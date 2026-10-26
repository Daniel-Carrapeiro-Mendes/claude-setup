---
name: push
description: Envia os commits locais para o repositório remoto, depois de checar o estado do repositório e procurar segredos no que vai subir. Acionada apenas pelo usuário com /push.
argument-hint: "[instruções extras opcionais]"
disable-model-invocation: true
model: haiku
background: false
# Sem "context: fork": num subagente, a caixa de aprovação do git push não aparecia e o push era recusado. Na conversa principal ela existe.
# git push fica de fora de propósito: a regra "ask" do settings.json global vence o allowed-tools, e aqui liberaria até --force se ela sair.
# Existe uma cópia no claude.ai. Mudou este arquivo, suba a cópia de novo (o cabeçalho de lá só aceita name, description e allowed-tools).
allowed-tools:
  - Bash(git status)
  - Bash(git status *)
  - Bash(git branch *)
  - Bash(git log *)
  - Bash(git remote *)
  - Bash(git diff *)
  - Bash(gitleaks git *)
  - Bash(gitleaks stdin *)
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

## Passo 3 — Busca de segredos

Procure senhas, tokens e chaves nos commits que ainda não estão em nenhum remoto, ou seja, no que vai subir. Rode os dois comandos, exatamente assim:

- `gitleaks git --log-opts="HEAD --not --remotes" --redact --no-banner -v .` — olha o conteúdo dos arquivos em cada commit.
- `git log --format=%B HEAD --not --remotes | gitleaks stdin --redact --no-banner -v` — olha as mensagens dos commits.

Só siga para o push se **os dois** terminarem com `no leaks found`. Em qualquer outro caso (`leaks found`, erro, `gitleaks` não encontrado), **não suba nada**:

- Para cada achado, relate o arquivo, a linha, o commit e a regra (`RuleID`). Nas mensagens de commit não há arquivo: diga só a regra e o trecho mostrado.
- Nunca rode sem `--redact` e nunca tente descobrir o valor escondido.
- Não tente consertar. Tirar um segredo de um commit exige reescrever o histórico, e isso é decisão do usuário.
- Se achar que é alarme falso, diga isso no relatório, mas não suba mesmo assim.

## Passo 4 — Push

- Se a branch já acompanha uma branch remota: `git push`
- Se ainda não acompanha: `git push -u origin <branch-atual>`
- O push vai pedir confirmação ao usuário. Isso é esperado: é a última checagem, feita por ele.
- **Nunca** use `--force`, `--force-with-lease`, `--delete` ou `--mirror`. Se achar que algum deles é necessário, pare e explique o motivo, deixando a decisão para o usuário.
- Se o push for rejeitado (por exemplo, "non-fast-forward" ou "fetch first"), **não tente resolver sozinho**. Relate o erro exatamente como apareceu e sugira que o usuário avalie um `git pull --rebase`.

## Passo 5 — Relatório final

Seja curto e objetivo:

- Branch de origem e destino (remoto)
- Resultado da busca de segredos: quantos commits foram olhados e se algo foi encontrado
- Quantos commits foram enviados, com uma linha por commit
- Ou, se nada foi enviado, o motivo

## Instruções extras do usuário

Podem estar vazias. Se houver algo aqui, respeite, desde que não contrarie as regras acima:

$ARGUMENTS
