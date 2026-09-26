---
name: limpar
description: Passagem de sessão. Use só quando eu digitar /limpar — decide se vale dar /clear ou /compact e salva o estado nos arquivos do projeto para eu continuar numa sessão nova sem perder nada.
disable-model-invocation: true
---

# /limpar — preparar a passagem para uma sessão limpa

Quero saber se vale limpar o contexto (a memória desta conversa). Se valer, quero sair desta sessão sem perder nada.

## 1. Vale limpar?

Responda com honestidade, em uma ou duas frases.

- **Vale** quando a sessão já passou por várias tarefas diferentes, arquivos foram lidos e reescritos várias vezes, a tarefa atual chegou num ponto de parada, ou você começou a esquecer ou contradizer algo combinado antes.
- **Não vale agora** quando estamos no meio de uma mudança pela metade, com arquivos inconsistentes. Nesse caso, diga o que falta para chegar num ponto de parada seguro e pare aí.
- Você não sabe o tamanho exato do seu contexto. Se precisar do número, peça que eu rode `/context`.
- Se a sessão é longa mas continua no mesmo assunto, `/compact` (resume a conversa em vez de apagar) pode ser melhor que `/clear`. Diga qual dos dois você recomenda e por quê.

## 2. Salve o estado nos arquivos, não no prompt

Antes de eu limpar, tudo que importa tem que estar em arquivo. Um prompt copiado se perde, um arquivo fica.

- `ROADMAP.md`: reescreva "Onde estou" e "Próximo passo sugerido" com o estado real agora, inclusive o que ficou pela metade e em que ponto exato parou.
- Decisão tomada nesta sessão que ainda não está escrita vai para a seção "Decisões" do mapa do projeto (`ARQUITETURA.md`, `ESTRUTURA.md` ou `CAMPANHA.md`).
- Mudança concluída que ainda não está no histórico vai para o `CHANGELOG.md` ou para o registro de sessão.
- Se combinamos algo nesta conversa que deveria valer sempre, não salve sozinho: me proponha a linha para o CLAUDE.md.
- Se há mudança de código sem commit, me avise e pergunte se quero commitar antes.

Depois, diga numa lista curta quais arquivos você atualizou.

## 3. O prompt de retomada

Me dê um prompt curto, num bloco de código para eu copiar. Ele deve:

- mandar ler o `ROADMAP.md`, e qualquer outro arquivo necessário, pelo caminho;
- dizer qual é o próximo passo;
- incluir **só** o que não coube em arquivo. Em geral, nada ou quase nada.

Se o prompt ficar longo, faltou salvar alguma coisa em arquivo. Volte ao passo 2.
