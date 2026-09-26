---
name: desligar
description: Checa se é seguro desligar o computador agora. Use só quando eu digitar /desligar — depois eu desligo a máquina por um comando remoto.
disable-model-invocation: true
---

# /desligar — posso desligar o computador?

Vou desligar esta máquina por um comando remoto, para poupar energia. Antes, quero saber se isso vai estragar alguma coisa.

**Você nunca desliga, reinicia ou suspende a máquina**, nem se eu pedir durante esta skill. Quem desliga sou eu, pelo comando remoto, depois da sua resposta.

## O que acontece quando eu desligar

- Esta sessão acaba. O que está só nesta conversa se perde.
- O Remote Control cai. Só volto a falar com você quando ligar o PC de novo.
- Qualquer processo rodando é interrompido no meio.

## 1. Verifique

Use os comandos do sistema operacional desta máquina. Não chute: se não conseguir verificar algo, diga.

1. **Processos desta sessão**: servidor de desenvolvimento, build, testes, instalação de pacote, download, container. Para cada um que ainda está rodando, veja se dá pra interromper sem dano.
   - Pode cortar: servidor de dev, modo watch, teste que só lê.
   - Não pode cortar no meio: instalação de pacote, migração de banco, escrita em arquivo ou banco, download que eu preciso. Espere terminar ou pare de forma limpa.
2. **Trabalho pela metade**: se você estava no meio de uma edição que deixa o projeto inconsistente (código que não compila, arquivo pela metade), termine ou volte ao último ponto consistente.
3. **Banco de dados e containers**: se há banco com escrita em andamento, pare de forma limpa. Se está parado ou só lendo, tudo bem.
4. **Git**: mudança sem commit e commit sem push não se perdem ao desligar, porque estão no disco. Só avise quantos são e pergunte se quero commitar. Nunca faça `push` sem eu pedir.

## 2. Salve o estado da sessão

A conversa vai sumir. Se o projeto tem `ROADMAP.md`:

- Atualize "Onde estou" e "Próximo passo sugerido" com o estado real agora.
- Teste que eu ainda preciso fazer no computador vai para "Testes pendentes no computador".
- Decisão tomada nesta sessão que ainda não está escrita vai para "Decisões" do mapa do projeto.

## 3. O que você não consegue ver

Do terminal, você não enxerga tudo. Diga em uma linha o que fica por minha conta. Por exemplo: arquivo não salvo num editor aberto, download no navegador, atualização do sistema em andamento, programa rodando fora do terminal.

## 4. Responda curto, porque estou no celular

A primeira linha é um destes três vereditos:

- ✅ **Pode desligar.**
- ⏳ **Pode, depois de:** o que falta, e mais ou menos quanto tempo.
- ⛔ **Não desligue agora:** o motivo, em uma frase.

Depois, no máximo 5 linhas: o que você verificou, o que você salvou e o que você não conseguiu ver.

Se o veredito for ⏳ e o que falta estiver ao seu alcance e for seguro, faça, e me dê o veredito de novo quando terminar.
