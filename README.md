# claude-setup

Configurei o [Claude Code](https://claude.com/claude-code) para me ensinar, e não para fazer por
mim: em cada projeto, eu quero entender o que foi feito, não só ter o resultado pronto. Isso está
escrito em arquivos `CLAUDE.md`, que o Claude Code lê sozinho ao trabalhar numa pasta. Eu tenho um
por nível, do que vale sempre até o que só vale num projeto, e quando dois discordam, o mais
específico vence. As cópias aqui se chamam `CLAUDE.exemplo.md`, para o Claude Code não as ler como
instrução de verdade. Para usar uma, renomeie para `CLAUDE.md` e troque os marcadores entre `<>`
pelos seus dados. Leia inteiro antes: são as **minhas** regras, e várias só fazem sentido para o
meu jeito de trabalhar.

## Os `CLAUDE.md`

Cada item mostra onde o arquivo fica na minha máquina. O link abre a cópia.

- [`~/.claude/CLAUDE.md`](exemplo/claude-global/CLAUDE.exemplo.md) — o que vale sempre: como me
  explicar as coisas, o que fazer antes de executar, como entregar.
- `~/Documents/Projects/`
  - [`Sistemas/CLAUDE.md`](exemplo/Projects/Sistemas/CLAUDE.exemplo.md) — projetos de software:
    bloco "Como testar", versão, `ARQUITETURA.md`, segredos e git.
    - [`Sites/meu-site/CLAUDE.md`](exemplo/Projects/Sistemas/Sites/meu-site/CLAUDE.exemplo.md) —
      aperta uma regra: push na `main` publica o site, então tudo passa por branch e prévia.
    - [`Sites/meu-app/CLAUDE.md`](exemplo/Projects/Sistemas/Sites/meu-app/CLAUDE.exemplo.md) —
      acrescenta uma: ao fim de cada sessão, uma entrada no diário do projeto.
  - [`RPGs/CLAUDE.md`](exemplo/Projects/RPGs/CLAUDE.exemplo.md) — RPG de mesa é escrita, não
    software: desliga as práticas de código e diz como escrever.
    - [`livro-de-regras/CLAUDE.md`](exemplo/Projects/RPGs/livro-de-regras/CLAUDE.exemplo.md) —
      traduz as práticas de software: a versão vira errata, "Como testar" vira "Como playtestar".
    - [`Campanhas/minha-campanha/CLAUDE.md`](exemplo/Projects/RPGs/Campanhas/minha-campanha/CLAUDE.exemplo.md)
      — campanha não tem versão: registro por sessão e bloco "Como levar isso pra mesa".

## As skills

Uma skill é um roteiro que o Claude Code segue quando eu digito o comando dela. As minhas ficam em
`~/.claude/skills/<nome>/SKILL.md`, nenhuma roda sem eu chamar, e todas estas eu já usei de verdade.

- [`/celular`](skills/celular/SKILL.md) — modo longe do computador: o que precisa da tela vira
  teste pendente, e as respostas vêm escritas para eu ouvir.
- [`/checkup`](skills/checkup/SKILL.md) — "onde eu parei?": confere o roadmap contra o git, em vez
  de confiar nele. `checkup` também é apelido do `/doctor` embutido; nos meus testes a skill
  venceu, mas se na sua versão abrir o `/doctor`, renomeie.
- [`/desligar`](skills/desligar/SKILL.md) — posso desligar a máquina agora? Confere o que está
  rodando, salva o estado e responde com um veredito.
- [`/limpar`](skills/limpar/SKILL.md) — passagem para uma sessão nova: salva o estado em arquivo e
  diz se vale `/clear` ou `/compact`.
- [`/push`](skills/push/SKILL.md) — envia os commits depois de conferir o git. Nunca força, nunca
  commita por mim, e não procura segredo: essa conferência vem antes, no commit.

## Autor

Daniel Carrapeiro Mendes — [portfólio](https://toca.maxymuxzs.com.br) ·
[GitHub](https://github.com/Daniel-Carrapeiro-Mendes)

Os textos daqui são meus e estão sob a licença [CC BY 4.0](LICENSE): pode copiar, adaptar e usar
para qualquer fim. Se republicar, dê o crédito, linke a licença e diga o que mudou.
