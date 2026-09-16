# Gear e itemização por fase

Fontes: [Armor & Weapons (wiki)](https://wiki.uooutlands.com/index.php/Armor_%26_Weapons), [Aspect Mastery (wiki)](https://wiki.uooutlands.com/Aspect_Mastery), [Aspect Crystals (wiki)](https://wiki.uooutlands.com/Aspect_Crystals), [UO Outlands Guide 2026 — cap. 2](https://hardlygospel.github.io/uo-outlands-2026-guide/chapter-2-your-character/).

Complementa `Builds/dexxer-swords.md` e `Builds/blacksmith-miner.md` — aqueles docs dizem **qual skill treinar**, este diz **o que vestir/craftar** em cada fase.

## Tiers de material — armadura

Ordem de leve pra pesado, com penalidade de Meditação (não é "proteção" isolada, é o custo em mana-regen de usar aquele material):

| Material | Penalidade de Meditação |
|---|---|
| Sem armadura / Leather / Buckler / Wooden Shield | 0% |
| Studded | 10% |
| Bone | 25% |
| Ringmail | 50% |
| Chainmail | 75% |
| Platemail / Heater Shield / Chaos/Order Shield | 100% |

**Regra importante**: penalidade é **cumulativa por peça equipada**, não pega só a pior peça. Se você mistura leather + platemail, soma a penalidade de cada peça.

Pra Dexxer (nosso build, Swords + Chivalry): Chivalry usa **tithing point**, não mana direto pra maioria dos spells, então a penalidade de Meditação importa menos que pra um mago puro — pode ir de Chainmail/Platemail sem culpa assim que tiver Blacksmith rodando pra fazer as peças (ver `Builds/blacksmith-miner.md`).

## Tiers de material — ore/weapon

Ore sobe em cor: **Iron → Dull Copper → Shadow Iron → Copper → Bronze → Golden → Agapite → Verite → Valorite**, cada cor mais rara/melhor. Board (madeira) e leather também têm equivalentes coloridos com o mesmo tipo de bônus.

| Fase | Ore/Board alvo |
|---|---|
| Early (Blacksmith 0-50) | Iron — treino puro, não importa qualidade |
| Mid (50-85) | Dull Copper/Shadow Iron/Copper — já dá bônus, ainda barato |
| Late (85-120) | Bronze/Golden/Agapite | 
| Endgame | Verite/Valorite — mais raro, mais caro, maior bônus |

## Exceptional quality

Item craftado com sucesso "exceptional" (chance ligada a skill + Arms Lore) ganha bônus de stat e carrega o nome do craftador. Isso é o motivo de subir **Arms Lore** no build de Blacksmith (já está na build final).

## Aspect System (mid/endgame — não é dia 1)

Sistema separado de imbuing/enchant:
1. Desbloquear aspect gastando **aspect distillation + aspect cores + aspect mastery kit**
2. Abastecer com **arcane essence**
3. Ativar o aspect na arma/spellbook e na armadura (custo pequeno de arcane essence)

Pontos importantes:
- Tier/experiência de Aspect é **compartilhado entre todo equipamento** — não é por peça.
- Ativar um Aspect na armadura faz **toda armadura na bolsa que não é desse aspect perder o aspect dela** — só pode ter armadura de 1 aspect ativo por vez na bolsa.
- Isso é conteúdo de progressão **depois** que a build básica de skill já estiver rodando — não é prioridade nas primeiras semanas.
- É provavelmente o que o Dexxer autopilot script checa quando vê `"aspect" in WeaponLabel` (achado durante a revisão de código) — confirma esse ponto quando já tiver um aspect ativo pra testar o script de verdade.

## Checklist de bolsa por fase (baseado no que já documentamos)

| Fase | Levar sempre |
|---|---|
| Early | Bandagem (50-150), arma básica, sem item de valor que não aceite perder |
| Mid | + potion de cura/cure, runa/runebook marcado (recall) |
| Late/risco | + potion de refresh, recall scroll reserva, nunca carregar aspect gear raro em área de risco sem necessidade |

## Não confirmado / preciso checar in-game
- Onde comprar/craftar Aspect Distillation, Aspect Cores, Aspect Mastery Kit
- Custo exato de Arcane Essence por ativação
- Se existe versão "beginner" de aspect mais barata ou é tudo endgame mesmo
