---
name: celular
description: Modo longe do computador. Use só quando eu digitar /celular — estou no celular via Remote Control e não consigo fazer os testes que exigem estar na frente da máquina.
disable-model-invocation: true
---

# /celular — estou longe do computador

Estou usando o Remote Control pelo celular. O computador continua ligado e você continua rodando comandos nele normalmente. O que eu não consigo é **olhar a tela da máquina** nem mexer nela: abrir o navegador do PC, clicar na interface, ver um app rodando localmente.

Isso vale até o fim desta sessão, ou até eu dizer que cheguei.

## O bloco "Como testar" muda

Separe cada teste em três grupos:

1. **Você mesmo verifica**: tudo que dá para confirmar rodando comando na máquina. Testes automatizados, build, `curl` numa rota, ler um log, conferir um arquivo gerado. Rode e me mostre o resultado resumido. Não me passe como tarefa o que você consegue fazer sozinho.
2. **Dá pra fazer pelo celular**: só se existir de verdade. Por exemplo, uma URL pública que eu consigo abrir no celular. Se não houver nenhum, diga "nenhum" e não invente.
3. **Só no computador**: tudo que depende de ver a tela ou mexer na máquina. Esses **não** vão para a resposta. Vão para o `ROADMAP.md`.

Em projeto sem testes (livro de regras, campanha), vale só a parte de como escrever as respostas. O que precisar ser conferido na máquina vai para os pendentes do mesmo jeito.

## Testes pendentes no ROADMAP.md

Mantenha no topo do `ROADMAP.md`, acima de "Onde estou", a seção `## Testes pendentes no computador`:

- Um bloco por mudança, com data e o nome do que mudou.
- Cada bloco no formato completo do "Como testar": comando, onde olhar, passo a passo, sinal de que deu certo e caso de erro. Ele tem que dar pra ler de uma vez, sem precisar desta conversa.
- Os blocos ficam na ordem em que devem ser feitos. Se um teste depende de outro, diga.

Na resposta pelo celular, só avise em uma linha: "N testes adicionados aos pendentes do ROADMAP.md".

## Respostas pelo celular

Eu **ouço** as respostas pelo celular, como um podcast. Por isso:

- **Longas e detalhadas.** Explique o que fez, por que fez, e o que isso muda. Não corte o detalhe esperando eu pedir.
- **Escreva para ser ouvido.** Prosa corrida, com começo, meio e fim. O resultado vem primeiro, e a explicação vem depois.
- Evite tabela, bloco de código longo e lista de símbolos. Lido em voz alta, isso vira ruído. Se eu precisar ver código, mostre só o trecho que mudou e diga em palavras o que ele faz.
- Pode fazer quantas perguntas precisar. Sempre no formato de opções para eu selecionar (regra do CLAUDE.md global).

## Quando eu voltar

Quando eu disser que cheguei, comece pelos **Testes pendentes no computador**, na ordem. Conforme eu confirmo cada teste, remova o bloco dele. Teste que falhou vira item no roadmap, não some.
