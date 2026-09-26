# Projetos de software

<!-- Vai na pasta que guarda meus projetos de código: ~/Documents/Projects/Sistemas/CLAUDE.md -->
<!-- Carrega junto com ~/.claude/CLAUDE.md. Em conflito, este vence. -->
<!-- Mantenha abaixo de 200 linhas. -->

## Quando estas regras não se aplicam

Este arquivo vale para projeto que eu pretendo manter. Para teste rápido, protótipo descartável ou script de tarefa única, eu aviso — algo como "isso aqui é só um teste" — e as seções de Versionamento e Documentação ficam de fora, sem cerimônia.

Se eu decidir manter o projeto depois, as regras passam a valer dali pra frente. Não precisa voltar e arrumar o que já foi feito antes.

## Roadmap

No `ROADMAP.md` (regras no CLAUDE.md global), **um marco é uma versão alvo**: `0.2.0`, `0.3.0`, `1.0.0-beta.1`, `1.0.0`. Quando um marco fecha, os itens dele viram a entrada daquela versão no `CHANGELOG.md`.

## Depois de implementar — bloco "Como testar" obrigatório

Toda vez que você terminar uma implementação, **encerre a resposta com um bloco "Como testar"**. Sem ele, a tarefa não está entregue.

O bloco tem que ter, nesta ordem:

1. **O comando exato** para rodar, e de qual pasta.
2. **Onde olhar** — a URL, a tela, o arquivo ou a saída do terminal.
3. **O passo a passo numerado**, escrito para alguém que não conhece o código. "Clique em X, digite Y, aperte Z" — não "verifique se a rota responde".
4. **O sinal concreto de que deu certo.** Um valor, uma mensagem, uma tela específica. Nunca "deve funcionar".
5. **Pelo menos um caso de erro:** o que eu faço para provocar a falha de propósito, e o que deve acontecer. Se eu só testar o caminho feliz, não testei nada.

Regras:

- Teste só o que mudou nesta tarefa. Não repita o roteiro do projeto inteiro toda vez.
- Mudança mínima — texto, cor, espaçamento, um typo — não precisa do bloco inteiro. Basta uma frase: o que mudou e como eu vejo que mudou. O bloco completo vale pra tudo que envolve lógica, comportamento ou dado novo.
- Se alguma parte não der para testar manualmente, **diga isso e explique por quê**, em vez de inventar um passo.
- Se o teste depender de algo que eu preciso preparar antes (banco rodando, `.env` preenchido, dado de exemplo), isso é o passo zero.

## Versionamento

Todo projeto tem uma versão em **SemVer** (Semantic Versioning / versionamento semântico — convenção em que cada parte do número muda por um motivo específico e combinado), no formato `MAIOR.MENOR.CORREÇÃO` (em inglês, `MAJOR.MINOR.PATCH`).

- **Fonte única da verdade:** o campo `version` do `package.json` (ou o arquivo equivalente da linguagem). O número **nunca** é escrito à mão em dois lugares — a interface lê de lá.
- **Começa em `0.1.0`.** Enquanto estiver em `0.x`, é permitido quebrar qualquer coisa sem cerimônia; é para isso que serve o zero.
- **Vai para `1.0.0`** quando eu assumir compromisso com a interface — alguém usando de verdade, ou a entrega oficial. Não é "quando compila", é "quando quebrar isso vai incomodar alguém".
- Depois do `1.0.0`:
  - **CORREÇÃO** (PATCH) sobe em conserto de bug, sem mudar comportamento esperado — `1.2.3 → 1.2.4`
  - **MENOR** (MINOR) sobe em funcionalidade nova que não quebra o que existia — `1.2.4 → 1.3.0`
  - **MAIOR** (MAJOR) sobe quando algo que funcionava antes deixa de funcionar do mesmo jeito — `1.3.0 → 2.0.0`
- **Ao subir MAIOR, zera MENOR e CORREÇÃO. Ao subir MENOR, zera CORREÇÃO.** Nunca `1.3.4 → 2.3.4`.
- Mantenha um **`CHANGELOG.md`** na raiz, versão mais nova em cima, com as seções que forem usadas: Adicionado, Alterado, Corrigido, Removido. Uma linha por mudança, escrita para usuário, não para programador. Toda versão tem **data** (`AAAA-MM-DD`) ao lado do número — isso vale para toda versão, inclusive pré-lançamentos.

Ao propor subir a versão, **diga qual parte do número sobe e por quê**. Se estiver em dúvida entre MENOR e MAIOR, pergunte: a diferença é se algo que funcionava antes parou de funcionar.

### Pré-lançamento (alpha, beta, rc) e canal de estabilidade

No caminho até o `1.0.0` (ou até uma versão MAIOR nova), o número pode levar um **identificador de pré-lançamento** — um sufixo depois de um hífen, definido pelo próprio SemVer: `1.0.0-alpha.1` → `1.0.0-beta.1` → `1.0.0-rc.1` → `1.0.0`. Numere sequencialmente (`.1`, `.2`...). Uma versão com esse sufixo sempre conta como "menor" que a versão final equivalente.

- **Alpha**: funcionalidade ainda incompleta. Uso só meu, interno.
- **Beta**: já tem tudo que foi planejado para essa versão, mas ainda pode ter bug. Pode sair pra fora.
- **RC** (release candidate, "candidato a lançamento"): acho que está pronto — só vira a versão final se nada grave aparecer nesse meio-tempo.

Separado disso, existe um **rótulo de estabilidade** (canal de distribuição — não faz parte do número da versão, é uma etiqueta ao lado, como o Debian usa `unstable`/`stable`): use `unstable` / `stable` quando eu quiser sinalizar isso além do SemVer — por exemplo, numa release do GitHub ou no README.

**Registre todo pré-lançamento no `CHANGELOG.md`**, não só quando vira versão final — quero o histórico completo de cada `alpha`, `beta` e `rc` que existiu, não um resumo.

Ao propor um pré-lançamento, diga o que falta para virar a próxima fase.

### Versão e changelog na interface — obrigatório em todo projeto com UI

- **Mostre o número da versão** em local discreto e sempre visível — rodapé, tela "sobre" ou barra lateral —, lendo da fonte única (nunca digitado na tela).
- Se o projeto estiver numa fase de pré-lançamento, mostre o identificador completo (`v1.0.0-beta.2`) — não simplifique para `v1.0.0`.
- **O número da versão é clicável.** Ao clicar, abre uma tela ou aba própria com o **changelog completo**, montado a partir do `CHANGELOG.md`.
- Nessa tela, as versões aparecem **da mais recente para a mais antiga**, cada uma com **data** e a lista de mudanças daquela versão.
- Se o projeto não tiver como ler o `CHANGELOG.md` em tempo real (ex.: front-end estático sem backend), gere esse conteúdo em build a partir do arquivo — não duplique o texto à mão em outro lugar.

## Documentação do projeto — obrigatória

Todo projeto deve ter um arquivo **`ARQUITETURA.md`** na raiz, mantido por você:

1. **Uma tabela com um arquivo por linha**, na ordem em que o código executa, com: caminho do arquivo, o que ele faz em uma frase, e quem chama ele.
2. **Uma seção "Como as peças se conectam"** — 5 a 10 linhas em texto corrido descrevendo o caminho de uma requisição do começo ao fim.
3. **Uma seção "Decisões"** — por que essa biblioteca, por que essa estrutura de pasta. É a parte que eu mais esqueço depois.

Regras de manutenção:

- Crie o `ARQUITETURA.md` na primeira vez que o projeto tiver mais de três arquivos.
- **Atualize junto com a mudança**, na mesma tarefa. Criou, renomeou ou apagou arquivo, a tabela muda no mesmo passo.
- Uma frase por arquivo. Se precisar de parágrafo, a explicação vai como comentário no próprio código.
- Não descreva o que já é óbvio pelo nome (`package.json`, `.gitignore`). Descreva o que eu não adivinharia.

## Código

- Comente o **porquê**, não o quê. `// soma 1` não ajuda; `// a API conta a partir de 1, não de 0` ajuda.
- Nomes de variável e função em inglês; comentários em português.
- Não instale biblioteca nova sem me dizer o que ela resolve e o que aconteceria sem ela.
- Não crie arquivo que eu não pedi. Especialmente README extra, exemplo, teste de demonstração e arquivo de configuração "por precaução".

## Segredos e segurança

- Senha, token e chave de API **nunca** entram no código. Vão em `.env`, e `.env` entra no `.gitignore`.
- Todo projeto tem um `.env.example` com as chaves e **sem** os valores.
- Antes de qualquer `git commit`, confira que nenhum segredo está no que vai subir.
- Em bot ou script que aceita comando de fora, valide **quem** está mandando antes de executar qualquer coisa.

## Git

- Commits pequenos e frequentes, mensagem em português no imperativo ("adiciona rota de login").
- Não faça `git push` sem eu pedir, pergunte se pode primeiro.
- Nunca trabalhe direto na `main` sem me avisar.
