---
name: faxina
description: Faxina do projeto. Use só quando eu digitar /faxina — junta tudo o que está aberto (pedidos de outros projetos, ideias soltas, propostas esperando o meu "pode" e relatórios), decide o que é óbvio, me pergunta só o que é meu, e não deixa nada em aberto.
argument-hint: "[caminho opcional do projeto]"
disable-model-invocation: true
---

# /faxina — nada fica em aberto

Meu projeto acumulou ideias, pedidos, propostas e relatórios. Quero sair daqui com o projeto limpo: você decide o óbvio, e eu decido o resto com você. A regra que leva a esta faxina é a "Nada acumula", do meu CLAUDE.md global.

Pasta (pode estar vazia; se vazia, use a pasta atual): $ARGUMENTS

## 1. Junte tudo o que está aberto

Leia o `ROADMAP.md` e os CLAUDE.md da pasta e da área. Monte uma lista numerada com:

- cada item de "Pedidos de outros projetos";
- cada item de "Ideias soltas" (um item por linha de topo; os subitens vão junto do item deles);
- cada proposta esperando o meu "pode" que o roadmap cita: um plano em `~/.claude/plans/`, um arquivo em `~/Downloads/`;
- cada `RELATORIO-*.md` da raiz do projeto e, dentro dele, cada item de "Esperando você" e de "Ideias que eu não apliquei".

Pedido que ainda está nas Ideias soltas (de antes da seção "Pedidos de outros projetos" existir) conta como pedido.

Antes de perguntar, confira cada item contra a realidade: o git, o histórico e os próprios arquivos. O que já foi feito entra na lista como "já feito", com a fonte.

Mande uma mensagem curta: quantos itens, de que tipo, e quantos parecem já feitos. Não espere resposta. Comece.

## 2. Decida o óbvio, e pergunte só o que é meu

**Você decide sozinho, aplica e me mostra numa tabela curta** (item, o que você fez, por quê):

- o que já foi feito, com a fonte: fecha;
- o pedido de outro projeto com o texto já decidido por mim: aplica, ou vira tarefa no marco certo;
- a duplicata, e o que perdeu o sentido (a data passou, o projeto mudou): sai, com uma linha no histórico se a decisão importa;
- a sua própria sugestão antiga: se é pequena e fácil de desfazer, aplica; se ficou velha, sai.

**Você me pergunta**, com a ferramenta de perguntas, até quatro itens por vez: as minhas próprias ideias quando o projeto continua acima do limite, o que é gosto ou rumo, canon e regra do RPG, e apagar um relatório. Itens parecidos podem ir numa pergunta só, se a decisão for a mesma para todos.

- No texto antes das perguntas, cada item em duas ou três frases: o que é, de quando, de onde veio, e a sua recomendação com o porquê. As opções também precisam fazer sentido sozinhas, porque o texto pode não aparecer para mim.
- As opções, com a sua recomendação primeiro:
  - **Fazer agora** — se é pequeno e cabe nesta sessão;
  - **Vira tarefa** — entra num marco do roadmap (diga qual);
  - **Já feito / fechar** — sai do roadmap;
  - **Apagar** — sai sem registro.
- O relatório tem uma pergunta própria, depois que os itens de dentro dele foram decididos: "Li e aprovo: pode apagar".

## 3. Aplique depois de cada rodada

A minha resposta é o "pode" daquele item. Aplique antes da rodada seguinte, para nada se perder se a sessão cair.

- **Vira tarefa:** o item entra no marco como uma linha `- [ ]` e sai de onde estava.
- **Fazer agora:** faça depois que a lista acabar, a não ser que o item destrave outro.
- **Já feito / fechar:** sai. Se a decisão importa, ganha uma linha no histórico da área (`CHANGELOG.md`, `HISTORICO.md` ou o registro de sessões).
- **Relatório aprovado:** antes do `gio trash`, todo trecho do relatório que uma decisão cita sem transcrever vai, palavra por palavra, para o registro. Depois, mande o arquivo para a lixeira com `gio trash <arquivo>` (dá para recuperar pela lixeira) e confira com `ls` que ele saiu da pasta.
- **Pedido recusado:** se o roadmap de quem pediu aponta para o pedido, deixe lá um pedido curto dizendo que foi recusado e por quê.

## 4. No fim

- Depois de gravar um pedido no roadmap de outro projeto, releia o arquivo no fim da faxina e confirme que o pedido continua lá.
- Diga quantos itens abertos havia e quantos sobraram. O que sobra é só o "fazer agora" que ainda não foi feito.
- Se as decisões mudam o "Onde estou" ou o "Próximo passo", reescreva os dois e me mostre o trecho novo na entrega. Se a mudança troca o rumo do projeto, pergunte antes.
- Projeto com git: um commit só, no fim, com o roadmap e o histórico ("faxina: N itens decididos").
- Termine com **como eu confiro**: a seção "Ideias soltas" e a "Pedidos de outros projetos" do `ROADMAP.md` só com o que eu escolhi manter, e `ls RELATORIO-*` sem nenhum relatório aprovado.
