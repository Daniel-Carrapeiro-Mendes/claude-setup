---
name: independente
description: Modo autônomo. Use só quando eu digitar /independente — você toca a tarefa sozinho, decide e aplica as próprias ideias sem me pedir permissão, e no fim me entrega um relatório completo para eu revisar.
argument-hint: "[a tarefa]"
disable-model-invocation: true
# Existe uma cópia no claude.ai, para funcionar na nuvem. Mudou este arquivo, suba a cópia de novo (o cabeçalho de lá só aceita name, description e allowed-tools).
---

# /independente — trabalhe sozinho e me conte tudo no fim

Quero que você toque esta tarefa sozinho. Decida, aplique as suas ideias e siga em frente sem me pedir licença a cada passo. No fim, me entregue um relatório completo, para eu revisar, corrigir e acrescentar o que eu quiser.

Tarefa (pode estar vazia): $ARGUMENTS

Se estiver vazia, a tarefa é o "Próximo passo sugerido" do `ROADMAP.md`. Diga que foi isso na primeira mensagem.

Isso vale até o fim desta tarefa. Depois, voltam as regras de sempre.

## 1. Antes de começar

1. Leia o `ROADMAP.md`, o mapa do projeto (`ARQUITETURA.md`, `ESTRUTURA.md` ou `CAMPANHA.md`) e os CLAUDE.md da pasta e da área. As regras da área continuam valendo: "Como testar", `ARQUITETURA.md`, `CHANGELOG.md`, versão, canon.
2. Se o projeto tem git e há **mudança sem commit**, pare e me pergunte o que fazer com ela, com a ferramenta de perguntas. É a única pergunta permitida, e só aqui: o meu trabalho pela metade não pode se misturar com o seu.
3. Monte a rede de segurança (seção 4).
4. Mande **uma** mensagem curta: o que você entendeu da tarefa, o seu plano em poucas linhas e onde o relatório vai ficar. Não espere resposta. Comece.

## 2. O que fica liberado

- **Decidir sem perguntar.** Dúvida vira decisão anotada no relatório. Entre duas saídas razoáveis, escolha a mais fácil de desfazer.
- **Aplicar as suas ideias, em qualquer parte do projeto**, mesmo fora da tarefa: corrigir o bug que você viu de passagem, melhorar um texto confuso, reorganizar o que estiver atrapalhando. Cada ideia aplicada entra no relatório com o porquê.
- Criar, renomear e reorganizar arquivos do projeto.
- Instalar biblioteca **no projeto**. No relatório, diga o que ela resolve e o que aconteceria sem ela.
- A ferramenta de perguntas fica de lado até o fim (com a exceção do passo 1.2).

## 3. O que continua travado

Mesmo com a liberdade acima, **não faça**:

- Nada destrutivo ou difícil de desfazer: apagar o que não está no git, `git reset --hard`, rebase, reescrever histórico, apagar dados de banco.
- Nada que saia da máquina: `git push`, deploy, publicar, mandar mensagem ou e-mail, abrir PR ou issue.
- `sudo`, nem instalar ou remover programa na máquina.
- Senha, token ou chave no código.
- Mudar o **canon** de um projeto de RPG. Trama, regra ou personagem novo entra marcado no próprio texto como sugestão sua.
- Mudar a ordem, o escopo ou a prioridade dos marcos do roadmap. Marcar item concluído e reescrever "Onde estou" e "Próximo passo" pode. Mudança de plano vira proposta no relatório.
- Mexer fora deste projeto: em outro projeto, nos CLAUDE.md, nas skills ou na configuração do Claude.

Quando a tarefa esbarrar num desses, **pule só essa parte**, anote em "Esperando você" com a sua recomendação e siga com o resto.

## 4. Rede de segurança

Tudo o que você fizer precisa poder ser desfeito, ideia por ideia.

- **Projeto de software com git:** crie a branch `independente/<nome-curto-da-tarefa>` a partir da atual e avise na primeira mensagem (nada direto na `main`). Faça **um commit por decisão ou ideia**, com a mensagem dizendo o porquê. Assim cada uma se desfaz sozinha com `git revert <hash>`.
- **Projeto de RPG com git:** commits pequenos no ramo atual, um por decisão ou ideia. A área não usa branch.
- **Projeto sem git:** prefira as ferramentas de edição a comandos de terminal para mudar arquivo. O `/rewind` do Claude Code desfaz o que elas fizeram nesta sessão, mas não o que um comando de terminal fez. O relatório lista cada arquivo criado ou alterado.

## 5. Durante o trabalho

- **Escreva o relatório enquanto trabalha**, não só no fim. Se a sessão cair ou a conversa for resumida, nada se perde.
- Rode tudo o que dá para rodar sem mim: testes, build, verificador, um `curl`. O que só se confere olhando a tela vai para "Como conferir".
- Se a tarefa se mostrar bem maior do que parecia — mudaria a arquitetura, ou levaria várias sessões —, pare num ponto consistente e relate. Um pedaço inteiro vale mais que tudo pela metade.
- Ideia que você teve e decidiu **não** aplicar vai para as "Ideias soltas" do `ROADMAP.md`, marcada como sugestão sua e com a data.

## 6. O relatório

**Onde:** `RELATORIO-independente-AAAA-MM-DD.md`, na raiz do projeto. Se o projeto tem git, garanta que a linha `RELATORIO-independente-*.md` está em `.git/info/exclude` (a exclusão local, que não sobe para o GitHub nem aparece no `.gitignore`). Se já existir um relatório com a mesma data, acrescente `-2`, `-3`.

**Tamanho:** sem limite. Quero tudo.

**Estilo:** escrito para ser **lido e ouvido**. Eu posso pedir para ouvir o relatório pelo celular, como um podcast. Prosa, frases curtas, sem tabela e sem bloco de código longo. Hash, caminho de arquivo e comando ficam juntos na última parte.

**Ordem:**

1. **Resumo** — até 5 linhas: o que foi feito, como o projeto ficou e o que precisa de mim.
2. **Esperando você** — o que só eu posso decidir ou fazer, cada item com a sua recomendação.
3. **O que foi feito** — passo a passo: o quê, por quê e quais alternativas você descartou.
4. **Ideias que eu apliquei sem você pedir** — em destaque, porque são as que eu mais preciso revisar.
5. **Ideias que eu não apliquei** — e por quê. Elas também estão nas Ideias soltas.
6. **Suposições** — o que você supôs sem conseguir confirmar.
7. **Como conferir** — no formato da área: "Como testar" em software, "o que conferir antes de levar pra mesa" em RPG.
8. **Para desfazer** — branch, cada commit com hash curto e uma linha, e os arquivos tocados.

## 7. No fim

Atualize o `ROADMAP.md` ("Onde estou", "Próximo passo", itens concluídos) e faça o último commit.

Na sua última mensagem vão **só**: o resumo, o caminho do relatório e o "Como conferir". **O relatório inteiro vai para o chat só quando eu pedir.** Aí vai na íntegra, sem cortar nada.

**Na nuvem** (quando `printenv CLAUDE_CODE_REMOTE` mostra `true`): lá, arquivo fora do git some quando a máquina da nuvem é desligada. Por isso, na nuvem, mande também o relatório inteiro na última mensagem — a conversa fica guardada em claude.ai/code. Diga que foi por isso.

Termine com o que eu faço depois de revisar, cada comando explicado: juntar a branch na `main`, desfazer uma ideia com `git revert`, ou descartar tudo. Quem decide sou eu.
