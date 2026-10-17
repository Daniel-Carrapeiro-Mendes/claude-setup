# Campanha — `<nome>`

<!-- Vai na raiz da pasta de cada campanha: ~/Documents/Projects/RPGs/Campanhas/<nome>/CLAUDE.md -->
<!-- Carrega junto com ~/.claude/CLAUDE.md e ~/Documents/Projects/RPGs/CLAUDE.md. Em conflito, este vence. -->

## Regras de toda campanha

### Campanha não tem versão

Aqui **não** se usa SemVer nem `CHANGELOG.md`. Campanha não é versionada, é **cronológica**: ela não volta atrás e não tem "correção de bug" — o que aconteceu em mesa, aconteceu. O registro é por sessão, em ordem, com data.

Isso vale só para a campanha. O livro de regras é versionado normalmente.

### CAMPANHA.md — o mapa da campanha

Mantenha um **`CAMPANHA.md`** na raiz, atualizado **na mesma tarefa** em que algo muda:

1. **Uma tabela por tipo** — personagens principais e coadjuvantes, lugares, facções, itens de peso. Uma linha cada: nome, o que é em uma frase, e **a quem está ligado** (qual gancho ele alimenta, de quem depende).
2. **Uma seção "Onde a trama está agora"** — 5 a 10 linhas em texto corrido: o que os jogadores acabaram de fazer, o que está em movimento fora de cena, e o que deve cobrar resposta na próxima sessão.
3. **Uma seção "Ganchos em aberto"** — o que eu plantei e ainda não colhi, com a sessão em que foi plantado.
4. **Uma seção "Decisões"** — por que eu matei aquele coadjuvante, por que mudei a rota, o que eu descartei e por quê. É a parte que eu mais esqueço depois.

Uma frase por linha de tabela. Não descreva o óbvio; descreva o que eu não lembraria daqui a dois meses.

### Registro de sessões

Um arquivo por sessão, numerado e datado (`sessao-01-2025-10-04.md`): o que aconteceu, o que os jogadores decidiram, e o que ficou pendente.

- Escreva o que **aconteceu na mesa**, não o que eu tinha planejado. Quando os dois divergirem, vale o que aconteceu.
- Ao registrar uma sessão, atualize o `CAMPANHA.md` no mesmo passo — tabelas, trama atual e ganchos.
- **Registro por partes.** Quando o mestre conta a sessão por partes, cada parte entra no registro assim que é contada, com commit. O que ela muda em outros arquivos (fichas, ideia geral, linha do tempo) fica listado no fim do registro, em "O que esta parte mexe nos outros arquivos", e só é aplicado depois, com a decisão do mestre. O que a mesa não sabe vai marcado com 🔒 SEGREDO, separado do que foi jogado.

### Roadmap

No `ROADMAP.md` (regras no CLAUDE.md global), **um marco é a próxima sessão ou o arco atual**.

O roadmap da campanha é sobre **o meu trabalho de preparação** — personagens para escrever, mapas, encontros, handouts —, não sobre o que vai acontecer na história. Quem decide a história é a mesa; eu preparo. Nunca escreva no roadmap "os jogadores vão fazer X".

Quando um marco fecha, o que foi usado em mesa entra no registro da sessão; o que não foi usado volta para "Ideias soltas".

### Canon, rascunho e segredo

Três estados, e eu preciso enxergar qual é qual:

- **Canon** — aconteceu em mesa, ou eu declarei fechado. Não muda.
- **Rascunho** — escrito, mas ainda não foi pra mesa. Pode mudar à vontade.
- **Segredo** — é canon, mas os jogadores ainda não sabem.

**Os arquivos desta pasta são só do mestre.** Nenhum jogador lê estes documentos: escreva tudo por inteiro, sem aviso de spoiler e sem etapa ou pergunta só para esconder informação dos jogadores. Segredo é um estado da história, não um cuidado com o arquivo.

O que sai desta pasta é outra coisa: texto lido em voz alta, artifact de jogador e handout. Ao gerar esse material, diga que ele é **da mesa**, e nada de segredo dentro — nem em nota de rodapé, nem em nome de arquivo.

### Antes da sessão — bloco "Como levar isso pra mesa"

Toda preparação termina com:

1. **O que eu leio em voz alta** — já pronto, sem eu precisar reescrever na hora.
2. **Onde pode precisar de rolagem** — os momentos, sem números. A mecânica é do mestre; sugestão de mecânica vem curta e marcada como opcional.
3. **O que provavelmente vai sair do roteiro** — a decisão que os jogadores podem tomar e que você não previu, e o que eu faço se tomarem.
4. **O que pode ficar pra próxima** se o tempo acabar.
