# Changelog

O que mudou em cada versão deste repositório, da mais nova para a mais antiga.
Cada versão tem data (`AAAA-MM-DD`) e as seções que forem usadas: Adicionado, Alterado, Corrigido, Removido.

## 1.4.0 — 2026-11-22

Nesta versão: três skills novas (uma já em uso, duas em teste), mais duas regras no exemplo de campanha, e o exemplo do diário sai.

### Adicionado

- `/faxina`: o Claude junta as ideias, os pedidos, as propostas e os relatórios abertos do projeto, decide o que é óbvio e me pergunta só o que é meu, até não sobrar nada em aberto. Já uso, então ela entra na lista principal.
- Duas skills em "Em teste", porque ainda não usei nenhuma do começo ao fim: `/audio`, para a mensagem que veio de um ditado, e `/retomar`, para continuar de onde parou depois que o limite de uso acabou.
- O exemplo de campanha pede, na preparação da sessão, um resumo de quem entra em cena e uma lista de músicas para buscar.
- O `CLAUDE.md` global de exemplo mostra o `CLAUDE.md` de um canal de vídeo, que é escrita e não software, dentro da pasta de um projeto de software.

### Removido

- O exemplo do diário (`Sites/meu-app/`): ele pedia um diário "para quem está aprendendo a programar", o oposto do foco que o repositório tem hoje. Quem linkava esse arquivo precisa tirar o link. Tratei como exceção, sem subir para a 2.0.0, porque o exemplo contradizia o resto.

## 1.3.0 — 2026-11-22

Nesta versão: o foco do repositório mudou (dominar a própria IA, e não aprender cada coisa a fundo), e as cópias passam a mostrar o jeito de trabalhar de hoje: o Claude decide mais sozinho e entrega em três partes.

### Alterado

- O README e o `CLAUDE.md` global de exemplo dizem o foco novo: dominar a própria IA, corrigindo os erros dela e otimizando como ela trabalha, para melhorar o resultado. Antes, o foco era aprender cada coisa a fundo.
- O `CLAUDE.md` global decide sozinho o que é fácil de desfazer e só pergunta o que é meu de verdade. A entrega tem três partes (o que ficou pronto, o que foi decidido, o que só eu confiro), e o roteiro de teste só vem quando eu peço.
- O global também ganhou o roadmap mantido pelo Claude, com a seção "Pedidos de outros projetos", a regra de um dono por arquivo quando há sessões em paralelo, o limite de 10 itens abertos por projeto ("Nada acumula"), o foco do mês e da semana, e a linha de modelo e esforço em todo prompt para colar em outra sessão.
- O `CLAUDE.md` de software ganhou "Nome do projeto", "O que vai para o ar" e "Projetos que trocam dados", e a regra de botão com ícone. O Claude confere antes de entregar (o bloco "Como testar" só vem a pedido), e ao achar um bug ele mostra como achou, em vez de parar antes de corrigir.
- O de RPG ganhou o Figurante, a quinta categoria de personagem.
- `/celular`: o que só dá para ver na máquina vira uma linha em "Para conferir no computador", e o Claude não para esperando resposta.
- `/independente`: um relatório só por projeto, e o relatório inteiro vai no chat no fim. As ideias que ele não aplicou ficam só no relatório.
- `/checkup`: conta os itens abertos de cada projeto e recomenda limpar quando passam de 10.
- `/limpar`: o prompt da sessão nova vem com o modelo e o esforço sugeridos, numa linha acima do bloco.
- `/desligar` e `/nuvem`: seguem a mesma regra de "Para conferir no computador".
- O README diz o que fazer com uma skill no claude.ai, onde o cabeçalho aceita menos campos.

## 1.2.0 — 2026-10-26

### Alterado

- O `CLAUDE.md` global ganhou "Modelo e esforço": no fim de cada tarefa, o Claude avisa o modelo e o esforço que usou e sugere os da próxima. Se a tarefa for pesada demais para o modelo da sessão, ele para e pergunta antes, e quem troca sou eu.
- O global também ganhou a regra de que pedido entre projetos vai para o roadmap de quem vai fazer, e o mapa da raiz de Projects.
- O `CLAUDE.md` de software ganhou uma seção de UX, os casos de erro padrão no "Como testar", a regra de mostrar como achar o bug antes de corrigir, a linha "Nesta versão" no topo de cada versão do changelog e uma regra para não dar ao `gh` a permissão de apagar repositório.
- O de RPG ganhou "toda falha é interessante".
- `/push`: roda na conversa principal, e não num subagente, para a confirmação do envio aparecer.
- `/celular`: quando a pergunta depende de um texto, o texto vai no chat e as perguntas vão no painel de opções.
- `/independente`: ganhou a seção "Exceções às travas", para tarefa de manutenção, e lê o mapa da raiz de Projects.
- `/nuvem`: o exemplo de projeto sem GitHub ficou mais exato.
- `/independente` saiu de "Em teste" e passou para a lista principal, em `skills/independente/`. Quem linkava o caminho antigo (`skills/em-teste/independente/`) precisa trocar.

## 1.1.0 — 2026-10-17

### Adicionado

- Duas skills numa seção à parte, "Em teste", porque ainda não usei nenhuma do começo ao fim:
  `/independente`, em que o Claude toca a tarefa sozinho e me entrega um relatório no fim, e
  `/nuvem`, que passa o trabalho do computador para uma sessão na nuvem e de volta.

### Alterado

- O `CLAUDE.md` global pede ideias: uma seção nova, "Seja criativo", e a regra de que ideia que vale
  guardar vai para um arquivo, e não fica só no chat.
- O `CLAUDE.md` de software diz como escrever o changelog: para quem usa, e não para quem programa.
- O `CLAUDE.md` de RPG separa os personagens em quatro categorias, e não mais em três.
- O livro de regras ganhou uma regra: apelido não é termo de regra.
- A campanha ganhou o registro de sessão por partes, a regra de que os arquivos da pasta são só do
  mestre, e a preparação aponta onde pode haver rolagem, sem números.
- `/push`: antes de enviar, procura segredo no que vai subir, e não envia nada se achar.
- `/celular`: quando a pergunta depende de um texto que eu preciso ler, texto e perguntas vão no chat.
- `/limpar`: a linha proposta para o `CLAUDE.md` também fica anotada no roadmap.

## 1.0.0 — 2026-09-27

Primeira versão estável. O conteúdo é o mesmo da 1.0.0-rc.1.
Daqui em diante, se um arquivo mudar de caminho, a versão sobe para 2.0.0.

## 1.0.0-rc.1 — 2026-09-25

### Adicionado

- O README: por que eu configurei o Claude Code para me ensinar, e a árvore dos meus `CLAUDE.md`,
  com um link para cada cópia.
- Sete exemplos de `CLAUDE.md`, prontos para copiar e adaptar: o global, a área de software, um site,
  um app com diário, a área de RPG, um livro de regras e uma campanha.
- Cinco skills que eu já usei de verdade: `/celular`, `/checkup`, `/desligar`, `/limpar` e `/push`.
- A licença CC BY 4.0: pode copiar, adaptar e usar para qualquer fim, desde que dê o crédito ao republicar.
