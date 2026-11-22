---
name: celular
description: Modo longe do computador. Use só quando eu digitar /celular — estou no celular via Remote Control e não consigo fazer os testes que exigem estar na frente da máquina.
disable-model-invocation: true
---

# /celular — estou longe do computador

Estou usando o Remote Control pelo celular. O computador continua ligado e você continua rodando comandos nele normalmente. O que eu não consigo é **olhar a tela da máquina** nem mexer nela: abrir o navegador do PC, clicar na interface, ver um app rodando localmente.

Isso vale até o fim desta sessão, ou até eu dizer que cheguei.

## Conferir muda

**Você mesmo verifica** tudo o que dá para confirmar rodando comando na máquina: testes automatizados, build, `curl` numa rota, ler um log, conferir um arquivo gerado, abrir a tela num navegador sem janela. Rode e me conte o resultado em uma linha. Não me passe como tarefa o que você consegue fazer sozinho.

**O que só eu consigo conferir**, olhando a tela ou mexendo na máquina, não vira roteiro de teste: vira **uma linha por mudança** na seção `## Para conferir no computador`, no topo do `ROADMAP.md`, acima de "Onde estou". A linha diz o que olhar e o que eu deveria ver ("o cartão acende quando a peça passa por cima"). Se dá para ver pelo celular (uma URL pública), a linha traz o endereço. Na resposta, só avise: "N linhas novas em Para conferir no computador".

Em projeto sem testes (livro de regras, campanha), vale só a parte de como escrever as respostas.

## Respostas pelo celular

Eu **ouço** as respostas pelo celular, como um podcast. Por isso:

- **Longas e detalhadas.** Explique o que fez, por que fez, e o que isso muda. Não corte o detalhe esperando eu pedir.
- **Escreva para ser ouvido.** Prosa corrida, com começo, meio e fim. O resultado vem primeiro, e a explicação vem depois.
- Evite tabela, bloco de código longo e lista de símbolos. Lido em voz alta, isso vira ruído. Se eu precisar ver código, mostre só o trecho que mudou e diga em palavras o que ele faz.
- **Não pare esperando resposta.** No `/celular` eu estou sempre ocupado: ouço e anoto as ideias para a `/faxina`, mas não respondo no meio. Dúvida vira decisão anotada, com a sua recomendação e o porquê (no relatório, se houver um, ou no `ROADMAP.md`), e você segue. Entre duas saídas razoáveis, escolha a mais fácil de desfazer. O que só eu posso decidir, e o que é destrutivo ou difícil de desfazer, não se faz: fica anotado nos arquivos, à minha espera.

## Quando eu voltar

Quando eu disser que cheguei, me mostre a lista "Para conferir no computador" numa mensagem só. Eu olho o que quiser e digo o que achei: o que eu confirmar ou dispensar sai da lista, e o que falhar vira item no roadmap. Roteiro de teste, só se eu pedir.
