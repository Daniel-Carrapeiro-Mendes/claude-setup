# `<nome do sistema>` — Livro de Regras

<!-- Carrega junto com ~/.claude/CLAUDE.md e ~/Documents/Projects/RPGs/CLAUDE.md. Em conflito, este vence. -->

## Regras de todo livro de regras

### Versionamento do livro

O livro tem uma versão em **SemVer** (Semantic Versioning / versionamento semântico — cada parte do número muda por um motivo combinado), no formato `MAIOR.MENOR.CORREÇÃO`. Traduzido para regra de jogo:

- **CORREÇÃO** — errata que não muda a intenção da regra: redação confusa, exemplo errado, número que contradizia o texto. A mesa não precisa reaprender nada. `1.2.3 → 1.2.4`
- **MENOR** — conteúdo novo que não invalida o que já existia: subsistema novo, mais opções, mais exemplos. Quem já jogava continua jogando igual. `1.2.4 → 1.3.0`
- **MAIOR** — uma regra que funcionava de um jeito passou a funcionar de outro. **A mesa precisa reaprender.** `1.3.0 → 2.0.0`

Na dúvida entre MENOR e MAIOR, a pergunta é: *alguém que decorou a regra antiga vai jogar errado agora?* Se sim, é MAIOR.

- **Ao subir MAIOR, zera MENOR e CORREÇÃO. Ao subir MENOR, zera CORREÇÃO.**
- **Fonte única da verdade:** um único lugar guarda o número — `VERSAO.md` na raiz, ou o cabeçalho do documento principal. Capa, rodapé e PDF leem de lá na hora de gerar. Nunca digitado à mão em dois lugares.
- **Começa em `0.1.0`.** Em `0.x` eu quebro o que quiser sem cerimônia.
- **Vai para `1.0.0`** quando uma mesa que não sou eu jogar com ele. Não é "quando terminei de escrever", é "quando mudar isso vai atrapalhar a mesa de alguém".

#### Playtest: alpha, beta, rc

No caminho até uma versão, o número pode levar um identificador de pré-lançamento (sufixo depois de um hífen):

- `1.0.0-alpha.N` — **playtest interno.** Ainda falta conteúdo. Só eu e quem topa testar coisa quebrada.
- `1.0.0-beta.N` — **playtest aberto.** Todo o conteúdo planejado existe, mas pode estar desbalanceado.
- `1.0.0-rc.N` — **candidata a edição.** Acho que fechou; só vira `1.0.0` se nada grave aparecer na mesa.

Ao propor um pré-lançamento, diga o que falta para virar a próxima fase.

#### CHANGELOG.md — a errata

Na raiz, versão mais nova em cima, cada versão com **data** (`AAAA-MM-DD`) e as seções que forem usadas: Adicionado, Alterado, Corrigido, Removido.

- Uma linha por mudança, **escrita para quem joga**, não para quem escreve: "dano de queda agora é 1d6 a cada 3m, era a cada 1,5m" — não "ajuste na tabela 4.2".
- Toda versão entra, **inclusive os pré-lançamentos** (`1.0.0-beta.2` tem a sua própria entrada). Quero o histórico completo, não um resumo.
- Mudança que exige reaprender (MAIOR) ganha uma linha a mais dizendo **o que fazer com a ficha antiga**.

### Roadmap

No `ROADMAP.md` (regras no CLAUDE.md global), **um marco é uma versão ou fase de playtest**: `0.3.0`, `1.0.0-alpha.1`, `1.0.0-beta.1`, `1.0.0`. Quando um marco fecha, os itens dele viram a entrada daquela versão no `CHANGELOG.md`.

### ESTRUTURA.md — o mapa das regras

Mantenha um **`ESTRUTURA.md`** na raiz, atualizado junto com a mudança, na mesma tarefa:

1. **Uma tabela com uma regra ou capítulo por linha**, na ordem em que aparecem no livro: nome, o que faz em uma frase, e **quais outras regras dependem dela**.
2. **Uma seção "Como as peças se conectam"** — 5 a 10 linhas em texto corrido descrevendo uma rodada de jogo do começo ao fim, passando pelos subsistemas na ordem em que entram.
3. **Uma seção "Decisões"** — por que essa mecânica e não outra, o que eu já testei e descartei, e por quê. É a parte que eu mais esqueço depois.

A coluna de dependência é a que importa: é ela que me diz o que vai quebrar quando eu mexer numa regra.

### Termos

- Cada termo de regra é definido **uma vez**, no lugar dele, e usado igual no livro inteiro.
- Ao introduzir termo novo, me diga onde ele ficou definido e em que outros lugares ele aparece.

### Depois de escrever ou mudar uma regra — bloco "Como playtestar"

Toda mudança de regra termina com um bloco "Como playtestar":

1. **A cena de teste** — a situação mínima de mesa que exercita essa regra: quem está lá, o que está acontecendo, o que os personagens querem fazer.
2. **O que rolar e o que comparar** — os números concretos, e o resultado esperado.
3. **O sinal de que está funcionando** — nada de "parece equilibrado". Algo observável: quantos acertos em dez tentativas, quantas rodadas até o combate acabar, quantas opções reais o jogador tem no turno.
4. **Como quebrar de propósito** — a combinação que abusa da regra. Se eu não tentar quebrar, não testei.
5. **O que observar na mesa** — se travou o ritmo, se alguém precisou reler o texto, se virou conta demais.

Mudança só de redação (typo, clareza, exemplo novo) não precisa do bloco. Basta uma frase dizendo o que mudou e onde.
