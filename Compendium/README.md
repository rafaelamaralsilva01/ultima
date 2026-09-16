# Compendium — mapa geral pra navegar Avadon

Complementa `Builds/` (o que treinar) com o resto do mundo (onde ir, o que vestir, como não perder tudo, como ganhar gold). Pensado pra quem tá começando e o mundo parece grande demais.

- [`world-map.md`](world-map.md) — cidades, dungeons, como viajar, regra de recall dentro de dungeon
- [`content-and-risk.md`](content-and-risk.md) — status de notoriedade, zona segura vs perigosa, progressão de conteúdo, kit de sobrevivência
- [`gear-progression.md`](gear-progression.md) — material de armadura/arma por fase, Aspect system, checklist de bolsa
- [`economy.md`](economy.md) — de onde vem gold, onde gastar, por fase

## Timeline única — você tá aqui → faça isso → leia isso

| Marco | O que fazer | Doc de apoio |
|---|---|---|
| **Personagem criado** | Escolher template, entender Shelter Island | `Builds/*.md` Fase 0 + `world-map.md` |
| **Skill primária ~30-50, ainda na ilha** | Treinar de graça nos Battle Trainers, guardar gold básico | `Builds/*.md` Fase 1 + `economy.md` |
| **Saiu da ilha, skill 50-80** | Dummies públicos (Dexxer) ou craft de tier baixo (Blacksmith); primeiro gear leather/chain | `Builds/*.md` Fase 2 + `gear-progression.md` |
| **Skill 80-100 (GM)** | Dungeon intermediária, primeiro runebook marcado, potion básica sempre na bolsa | `content-and-risk.md` + `economy.md` |
| **Pronto pra minerar sem medo de PK** | Chivalry/Magery de escape configurado **E** testado fora de dungeon (dentro não tem recall) | `content-and-risk.md` (regra de dungeon) + `reference-scripts/magery-escape/` |
| **Pronto pra automatizar** | Scripts revisados rodando (miner, blacksmith queue, dexxer autopilot) — sempre passar pelo `TESTING_CHECKLIST.md` antes | `reference-scripts/README.md` |
| **100+ e Power Scroll** | Considerar Champion Spawn, build avançada (720 pts) | `content-and-risk.md` (Champion Spawns) + `Builds/*.md` Fase 4 |
| **Endgame** | Aspect system, dungeon de risco alto, casa/vendor | `gear-progression.md` (Aspect) + `economy.md` |

## Como isso se encaixa com o resto do repo

```
Ultima Outlands/
  Builds/              → QUAL skill treinar, em que ordem
  Compendium/          → ONDE ir, O QUE vestir, COMO não morrer/quebrar, de onde vem gold
  reference-scripts/   → Scripts prontos + como escrever/revisar novo (COMMANDS.md, PATTERNS.md, TESTING_CHECKLIST.md)
```

## Confiabilidade das fontes

A maior parte vem da wiki oficial (wiki.uooutlands.com) — alta confiança. Números de gold/hora, timeline de progressão e alguns detalhes de PvP vêm de um guia de fã (`hardlygospel.github.io/uo-outlands-2026-guide`) que às vezes mistura conhecimento genérico de UO clássico com Outlands específico (já achamos 1 erro: menciona "Britain Bank", que não existe em Avadon). Todo doc deste Compendium tem seção final "não confirmado" marcando o que ainda precisa validar em jogo — reporta de volta conforme for testando que eu atualizo.
