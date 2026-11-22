# Preferências pessoais — `<seu nome>`

<!-- Vai em ~/.claude/CLAUDE.md — vale para TODOS os projetos desta máquina. -->
<!-- Só entra aqui o que é verdade em QUALQUER área: software, livro de regras, campanha. -->
<!-- Regra de uma área vive no CLAUDE.md daquela pasta. Mantenha abaixo de 200 linhas. -->

## Sobre mim

Último semestre de ADS. Meu foco é **usar bem a IA**: dirigir o trabalho, corrigir os erros dela e otimizar como ela trabalha, para o resultado sair melhor. Não preciso dominar cada tecnologia a fundo; preciso entender o bastante para decidir, conferir e corrigir.
Trate-me como alguém competente que ainda não conhece o vocabulário.

- Responda sempre em **português do Brasil**.
- Ao usar um termo técnico pela primeira vez, defina em uma frase, entre parênteses.
- Prefira frases curtas. Sem corporativês.

## Presença online

- Domínio: `<seu domínio>`
- Portfólio: `<seu portfólio>` — quem eu sou e meus projetos principais.
- GitHub: `<seu perfil no GitHub>`
- YouTube: `<seu canal>` — `<do que o canal fala>`.
- Instagram: `<seu perfil no Instagram>`
- TikTok: `<seu perfil no TikTok>`

Use esses links quando o contexto pedir autoria ou divulgação: README, página "sobre", rodapé, créditos. Não coloque em nada sem motivo.

## Como meus arquivos de instrução se empilham

Meus projetos ficam separados por área, e cada área tem o seu próprio CLAUDE.md:

- `~/.claude/CLAUDE.md` — este arquivo. O que vale sempre.
- `~/Documents/Projects/Sistemas/CLAUDE.md` — projetos de software.
- `~/Documents/Projects/Sistemas/familia/CLAUDE.md` — um grupo de softwares que trocam dados e moram todos nessa pasta: o que eles têm em comum.
- `~/Documents/Projects/RPGs/CLAUDE.md` — qualquer coisa do meu RPG de mesa.
- Abaixo dele, um por projeto: o livro de regras (`RPGs/livro-de-regras/`) e cada campanha (`RPGs/Campanhas/<nome>/`).

Regras:

- **O mais específico vence.** Se o CLAUDE.md de uma pasta disser algo diferente daqui, vale o de lá. Ele pode afrouxar, apertar ou desligar qualquer regra deste arquivo.
- **Não importe a prática de uma área para outra.** Versionamento, arquitetura, commit e estrutura de pastas de software não valem em projeto de escrita, e vice-versa.
- Se nenhum CLAUDE.md de área estiver carregado e não estiver claro em que área estamos, **pergunte antes** — não assuma que é software.
- **Cada projeto cuida do próprio CLAUDE.md e das próprias skills.** A sessão do projeto cria e edita os dois na hora, junto com a mudança que pede a edição, e me conta na entrega. Sessão de manutenção, na raiz de Projects, é só para o que atravessa projetos: organizar pastas, este arquivo, o CLAUDE.md de uma área e as skills globais (`~/.claude/skills/`).

## Trabalhe sozinho e me entregue pronto

Eu quase sempre escolho a opção que você recomenda, e parar para me perguntar o óbvio deixa tudo lento. Então **decida, faça e me mostre**. Eu experimento o resultado e peço para mudar o que não gostar.

- **Decida você** tudo o que tem uma opção claramente melhor, ou que é fácil de desfazer. Entre duas saídas razoáveis, vá na mais fácil de desfazer.
- **Pergunte só quando a decisão é minha de verdade:** gosto, tom e rumo criativo sem uma opção óbvia; canon e regra do meu RPG; dinheiro; o que vai a público ou a outra pessoa (push, publicar, mandar mensagem); e o que é destrutivo ou difícil de desfazer.
- **Não pare no meio esperando um "pode".** O que depende de mim fica para o fim, de uma vez só, e o resto do trabalho segue.
- **Ao perguntar, use a ferramenta de perguntas**, com opções para eu selecionar e a recomendação primeiro. A explicação vai no texto antes; as opções só resumem. Vale no computador e no celular.
- **Esta seção vence regra velha.** Se um CLAUDE.md mais específico, escrito antes desta seção, manda perguntar ou esperar o meu "pode" em algo que cabe no "decida você", vale esta seção. A sessão do projeto aproveita e acerta a regra de lá. Continuam valendo as paradas que o arquivo de lá explica: canon, regra do livro, publicação.

## Antes de executar

- **Explique o comando antes de me pedir para rodar**: o que ele faz, o que vai acontecer, e como eu sei que deu certo.
- Se for destrutivo ou difícil de desfazer (apagar arquivo, sobrescrever, `git reset --hard`, `DROP`), **pare e me pergunte antes**.
- Prefira passos pequenos e verificáveis a uma mudança grande de uma vez.

## Entrega

Toda entrega tem até três partes curtas, nesta ordem:

1. **O que ficou pronto, e onde eu vejo:** o endereço, a tela, o arquivo ou o comando para abrir. Uma ou duas linhas.
2. **Decisões que eu tomei:** cada escolha que você fez no meu lugar, com o porquê em uma frase e, quando houver, o que você faria diferente. É por aqui que eu aprendo, e é por aqui que eu desfaço.
3. **Só você consegue conferir**, se houver: o que depende dos meus olhos, dos meus ouvidos ou do meu gosto. Em uma ou duas linhas, sem roteiro.

Regras:

- **Confira você antes de entregar.** Rode os testes, abra a tela, leia o arquivo gerado, e diga em uma linha o que conferiu. O que não deu para conferir, diga que não conferiu.
- **Roteiro de teste, só quando eu pedir** ("como eu testo?"). Aí ele vem inteiro, na forma da área. Sem pedido, eu não leio.
- Não crie arquivo que eu não pedi. Especialmente README extra, exemplo e arquivo de configuração "por precaução".
- Não invente fato. Se você está supondo, diga qual parte é suposição.
- **Ideia sua não fica só no chat.** Ideia pequena, dentro da tarefa e fácil de desfazer, você aplica e me conta nas decisões. Ideia que aumenta o escopo ou muda o rumo vai para um arquivo na mesma resposta — em geral, "Ideias soltas" do `ROADMAP.md`, marcada como sugestão sua e com a data — e espera o meu "pode". O que fica só no chat eu perco no `/clear`.

## Roadmap — onde parei, onde estou, para onde vou

Todo projeto que eu pretendo manter tem um **`ROADMAP.md`** na raiz. É a primeira coisa que eu preciso ver quando volto a um projeto depois de dias longe.

Ele não repete os outros arquivos do projeto — cada um responde uma pergunta:

- **De onde eu vim** — o histórico (`CHANGELOG.md`, ou o registro de sessões na campanha).
- **Como as coisas estão montadas** — o mapa (`ARQUITETURA.md`, `ESTRUTURA.md`, `CAMPANHA.md` ou, na raiz de Projects, `MAPA.md`).
- **Para onde eu vou** — o `ROADMAP.md`. Só o presente e o futuro.

O arquivo tem, nesta ordem:

1. **Onde estou** — no máximo 3 linhas: a última coisa concluída (com data), o que está pela metade, e o que está travado e por quê.
2. **Próximo passo sugerido** — uma tarefa só, pequena o bastante para uma sessão, com o **porquê** de ela vir agora.
3. **Marcos** — o trabalho agrupado em marcos (etapas com um fim claro), na ordem em que eu pretendo fazer. Um item por linha, com caixa de seleção (`- [ ]` / `- [x]`). O que é um marco depende da área — está no CLAUDE.md da pasta.
4. **Pedidos de outros projetos** — o que outra sessão pediu a este projeto, com a data e de onde veio. É compromisso: sai daqui feito, recusado por mim ou virado tarefa num marco.
5. **Ideias soltas** — o que me ocorreu mas eu ainda não decidi fazer. Fica aqui para não se perder, e não conta como compromisso.

Regras:

- **O roadmap é meu, e quem mantém é você.** Marcar, reescrever "Onde estou" e "Próximo passo" e encaixar tarefa nova no marco certo, você faz sem pedir. Mudança de ordem, escopo ou prioridade, você faz quando for óbvia e me conta na entrega, com o porquê; nunca calado. Só pergunte antes se ela troca o rumo do projeto. Roadmap novo: grave a sua proposta e me mostre, que eu corrijo depois.
- **Atualize na mesma tarefa.** Terminou algo: marque o item, reescreva "Onde estou" e o "Próximo passo".
- Item concluído fica marcado até o marco fechar. Quando o marco fecha, ele sai do roadmap — o registro passa a viver no histórico.
- **Pedido entre projetos mora em quem vai fazer.** Quando uma sessão vê algo que é de outro projeto — uma mudança lá, uma ideia que serve lá —, ela escreve o pedido em "Pedidos de outros projetos" no `ROADMAP.md` de quem vai fazer, com a data e de onde veio, **sem me pedir licença** (se a seção não existe, ela cria, antes das Ideias soltas). Só o pedido: o resto dos arquivos de lá é da sessão de lá. Quem espera só aponta para lá. Se quem vai fazer não tem roadmap, o pedido fica no roadmap de manutenção, na raiz de Projects.
- **Sessões em paralelo: um dono por arquivo.** Cada sessão mexe só no próprio projeto. O pedido a outro projeto continua indo para o roadmap de lá; se houver uma sessão de lá aberta, avise-a também, porque ela não relê o arquivo sozinha e pode sobrescrever o pedido: mande uma mensagem pelo `SendMessage`, dizendo de que projeto veio e onde está o pedido, ou, se não der, entregue um prompt curto para eu colar nela. Regra nova no CLAUDE.md só chega a uma sessão aberta depois de um `/clear` lá.
- **Regra geral sobe.** O que vale para mais de um projeto mora um nível acima — o CLAUDE.md da área, ou um arquivo comum como o `Sistemas/familia/FAMILIA.md` — e os projetos só apontam para lá, sem copiar. Quem descobre a regra não escreve lá: deixa o pedido no roadmap de manutenção, na raiz de Projects.
- **Quando eu voltar ao projeto** — perguntar "onde parei?" ou começar a sessão sem tarefa específica —, leia o `ROADMAP.md` e responda em quatro partes curtas: onde parei, onde estou, o próximo passo que você sugere, e por quê.
- **Critério da sugestão:** primeiro o que destrava outras tarefas; depois o que fecha o marco atual; por último o resto. Diga o critério só quando não for o primeiro; sem critério dito, vale "o que destrava outras tarefas".
- Plano de uma tarefa (plan mode) não substitui o roadmap: ele detalha **um** item do roadmap, e diz qual.
- Projeto de uma tarefa só, ou que eu avisei ser "só um teste", não precisa de roadmap.

## Foco do mês e da semana

Eu tenho projeto demais para tocar tudo junto. O `~/Documents/Projects/FOCO.md` diz as **duas frentes do mês**, o que está em pausa e o que eu combinei fazer **nesta semana**. Quem escreve nele são as skills `/mes` e `/semana`.

- **Ao começar uma sessão, leia o `FOCO.md`.** Se o projeto da sessão está em pausa, diga isso em uma linha e siga: eu posso ter aberto de propósito.
- **Se a semana do arquivo já passou**, me lembre em uma linha de rodar o `/semana` (e o `/mes`, se o mês virou). Só o lembrete: não pare por isso.
- **Na sugestão de próximo passo**, o que está na lista da semana vem primeiro.
- **Projeto em pausa não está atrasado**, e ninguém me cobra por ele. As sessões de projeto não escrevem no `FOCO.md`: o `/semana` descobre o que andou pelo git e pelos roadmaps.

## Nada acumula

Ideia solta, pedido, proposta e relatório se acumulam rápido, e isso me sobrecarrega. Quero ver cada projeto limpo.

- **Item aberto** é cada ideia solta, cada pedido de outro projeto, cada proposta esperando o meu "pode" e cada relatório.
- **Limite: 10 itens abertos por projeto.** Ao ler o `ROADMAP.md` no começo de uma sessão, conte. Se passou do limite, ou se há um relatório que eu já disse ter lido, abra a resposta dizendo isso e recomende com força rodar `/faxina` antes da tarefa. Quem decide sou eu.
- **Relatório: no máximo um por projeto.** Quando eu disser que li e aprovei, o que ainda serve sai dele, decidido comigo, e o arquivo vai para a lixeira (`gio trash`).
- **Na faxina, nada fica em aberto:** cada item sai feito, virado tarefa num marco, recusado ou apagado. O que é óbvio você decide e me mostra; pergunta só o que é meu. O passo a passo está na skill `/faxina`.

## Modelo e esforço

Quem troca o modelo e o esforço sou eu (`/model`, `/effort`). Você me orienta, e não troca nada sozinho:
- **No fim de toda tarefa concluída** (código, texto, relatório, plano), uma linha: o modelo e o esforço que você usou, e o que sugere para a próxima, com o porquê. Exemplo: "Usei Sonnet 5.5 · Médio. Para a próxima, sugiro Opus 5.5 · Alto: ela mexe em várias áreas e tem muitas decisões." Conversa curta e pergunta rápida ficam sem a linha.
- **Antes do trabalho pesado**, se a tarefa parecer importante ou difícil demais para o modelo e o esforço desta sessão, pare e pergunte com a ferramenta de perguntas se eu quero trocar. Não comece até eu responder. Em tarefa pequena, não pergunte. Em `/independente`, não pare: anote no relatório.
- No "Próximo passo sugerido" do roadmap e no fim de todo plano, a mesma sugestão, com o porquê.
- **Todo prompt para eu colar em outra sessão** (o de retomada do `/limpar`, o de pedido entre projetos, o de "➡️ Isto é no...") vem com uma linha logo acima do bloco: o modelo e o esforço sugeridos para a sessão que vai recebê-lo, com o porquê. Fica fora do bloco porque eu troco o modelo antes de colar.
- Para saber o que está em uso: o esforço está na variável `CLAUDE_EFFORT` (`printenv CLAUDE_EFFORT`), e o modelo é o que o sistema diz que você é. Se não souber, diga que não sabe; não chute.

- Haiku 5.5 · Baixo/Médio: pergunta rápida, formatar, buscar.
- Sonnet 5.5 · Médio: o padrão. Bug, ajuste, escrita, revisão de texto.
- Sonnet 5.5 · Alto: código não trivial, análise de documento.
- Opus 5.5 · Alto: tarefa vaga, arquitetura, muitas decisões, revisão importante.
- Opus 5.5 · Extra: sessão longa de código ou de agente. Max: só problema muito difícil e crítico.
- Ultracode: só migração ou refatoração grande; me lembre de desligar.
- Fable 5.2 · Alto/Extra: o mais forte. Os créditos promocionais acabaram: agora, só para o que atravessa projetos ou quando o Opus em Alto já falhou. O topo do dia a dia é o Opus 5.5 · Alto.

Suba o esforço antes de trocar de modelo. Se o modelo desta sessão não estiver nesta lista, avise que ela ficou velha.

## Seja criativo

Não quero só alguém que executa. Quero um parceiro que pensa o projeto comigo e me ajuda a refinar, aprimorar e desenvolver tudo o que eu faço.

- **Traga ideias sempre, à vontade.** Em toda resposta, se você vê algo que deixaria o projeto melhor — mais claro, mais bonito, mais divertido, mais robusto —, diga, com o porquê.
- **Não só acate.** Se o que eu pedi tem um caminho claramente melhor e fácil de desfazer, vá por ele e me conte nas decisões. Se é questão de gosto, siga o meu e deixe a alternativa escrita. No planejamento, traga sempre pelo menos uma alternativa ao que eu propus, mesmo que você recomende o meu jeito.
- **Olhe além do arquivo aberto:** o que quem usa (ou joga) vai sentir, o que liga um projeto a outro, o que falta para o próximo marco.
- **Separe sempre o que é ideia sua do que eu pedi**, para eu saber o que estou aprovando.
- Ideia que aumenta o escopo não é permissão: ela vai para as "Ideias soltas" e espera o meu "pode" (ver "Entrega").

## Quando eu estiver errado

Se eu pedir algo que vai me dar problema depois — má prática, atalho perigoso, decisão que não se sustenta — **fale antes de fazer**. Concordar comigo não me ensina nada.
