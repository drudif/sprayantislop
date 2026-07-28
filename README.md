# sprayantislop

Skill de agente (`deslopar`) que elimina AI slop de textos e apresentações de marketing/publicidade em pt-BR — landing pages, posts, e-mails, press releases e decks de venda/pitch.

## O que ela faz

- **Entrevista de briefing antes de gerar** (Passo 0): até 5 perguntas, toda pergunta com opção de pular — objetivo, público, ativos reais e o que só essa marca pode dizer. Especificidade nasce do insumo, não da revisão.
- **Regra inegociável de claims:** número, métrica ou depoimento que não veio do briefing entra como `[CONFIRMAR]`, nunca como dado plausível inventado. Depoimento fabricado (a fôrma "— Nome A., profissão, cidade" em granularidade idêntica) é cortado, não reescrito.
- **Decks: o slop mora no slot.** Auditoria de layout antes do texto — teste de existência de cada elemento, regra do eco vertical (eyebrow/título/subtítulo), simetria fabricada, títulos-afirmação e teste do fio (os títulos em sequência contam o argumento?).
- **Camada léxico-estrutural** para pt-BR: famílias de frases e padrões estruturais medidos em corpus (contraste binário, gerúndio pós-vírgula, molduras, fôrmas de gênero, autenticidade fabricada).
- **Score em 6 dimensões**, incluindo distintividade (a headline serviria para o concorrente?) e integridade de claims.

## Instalação

Copie o diretório para a pasta de skills do seu agente:

```bash
git clone https://github.com/drudif/sprayantislop.git ~/.claude/skills/deslopar
```

No Claude Code, a skill dispara pelo gatilho da descrição ou via `/deslopar`.

## Estrutura

```
SKILL.md                    # princípios, fluxos, checklist, pontuação
references/
  briefing.md               # Passo 0: entrevista (5 perguntas → regra que alimentam)
  decks.md                  # auditoria de slots, teste do fio, clichês de pitch
  frases.md                 # famílias de frases a remover (Zero-Lero, vendorizado)
  estruturas.md             # padrões estruturais e de ritmo (Zero-Lero, vendorizado)
  exemplos.md               # transformações antes/depois (Zero-Lero, vendorizado)
```

## Crédito e licença

A camada léxico-estrutural (`references/frases.md`, `estruturas.md`, `exemplos.md`) é vendorizada de [Zero-Lero](https://github.com/ViniciusStanula/Zero-Lero), de Vinicius Stanula, sob licença MIT — ver [LICENSE-zero-lero](LICENSE-zero-lero). Os módulos de briefing, decks e claims são originais deste repositório.
