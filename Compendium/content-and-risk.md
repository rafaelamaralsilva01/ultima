# Conteúdo e risco — onde ir, o que evitar, como não perder tudo

Fontes: [UO Outlands Guide 2026 — cap. 3 e 4](https://hardlygospel.github.io/uo-outlands-2026-guide/), [New Player Guide](https://wiki.uooutlands.com/New_Player_Guide). Alguns detalhes deste guia fã parecem misturar conhecimento genérico de UO clássico com Outlands específico (ex: menciona "Britain Bank", que é nome de Britannia clássica, não existe em Avadon) — tratar como pista, não fato confirmado, até checar in-game.

## Regra de morte (a mais importante)

Morte tem **consequência real**: fora de zona segura, quem te mata pode pegar **tudo da sua backpack**. Isso muda como você joga desde o dia 1 — nunca carregue mais do que aceita perder.

## Status de notoriedade (quem pode te atacar / você pode atacar)

| Status | Cor | Significado |
|---|---|---|
| Innocent | Azul | Protegido por guarda em cidade |
| Criminal | Cinza | Atacável sem penalidade |
| Murderer | Vermelho | 5+ murder counts — guarda ataca na hora em qualquer cidade, caçado geral |

Matar um "azul" gera **murder count** (acumula, decai com dias de jogo). 5+ counts = vira vermelho.

## Zonas seguras vs perigosas

- **Shelter Island**: 100% seguro (Young Player status), mas skill capada em 80 e sem bônus pra crafting/gathering.
- **Cidades** (Prevalia, Andaria, etc): guarda protege innocent, mas criminal/red ainda pode ser atacado ali.
- **Wilderness/dungeon**: PvP e monstro livre, full loot na morte.
- **Dentro de dungeon especificamente**: sem recall (ver `world-map.md`) — se aparecer PK ali dentro, sua única fuga é andar até a saída ou achar moongate vermelho. **Isso é crítico pro nosso miner**: minerar em área de dungeon é mais arriscado que minerar em mina de superfície, porque o script de escape (`magery-escape/`) depende de recall, que não funciona lá dentro.

## Progressão de conteúdo por fase (estimativa, não confirmado 100%)

| Fase | Skills | O que fazer |
|---|---|---|
| Dias 1-3 | Skill primária 30+ | Farm gold básico, equipar armadura simples, dummy/Shelter Island |
| Semana 1 | 50-60 | Dungeons intermediárias, guardar 50k+ gold |
| Mês 1 | 70-80 | Dungeons mid-tier, 100-300k gold |
| Meses 2-3 | 90-100 (GM) | Dungeons de tier alto, considerar Power Scroll, comprar casa |
| 3+ meses | 100+ (com scroll) | Doom-tier / endgame, reputação, milhões guardados |

Isso é **estimativa de guia genérico** — nossa timeline real vai bater mais com `Builds/dexxer-swords.md` e `Builds/blacksmith-miner.md`, que são específicos de Outlands. Usar esta tabela só como sensação de ritmo, não meta fixa.

## Champion Spawns e Power Scrolls

Eventos PvE de múltiplas waves — o boss final dropa **Power Scrolls** (item que permite subir skill acima de 100, até 120). Isso é o que separa build "básica" (700 pts, cap 100) da build "avançada" (720 pts, algumas skills em 120) que já documentamos em `Builds/`. Scrolls valem de 50k a 2.000.000+ gold dependendo do tier — atrai disputa de PvP/guilda, não é atividade solo tranquila.

## Kit essencial antes de sair pra qualquer conteúdo de risco

- Bandagens em quantidade (Healing/Anatomy)
- Recall scroll ou runebook marcado (fuga de emergência — funciona fora de dungeon)
- Cure potion, Refresh potion
- Nunca carregar item que não aceita perder — deposita no banco antes de sair

## Ligação direta com o que já temos no repo

- Fuga de PK (`magery-escape/ultimate-escape-recall-runetome-chivalry.razor`) **só funciona fora de dungeon** — dentro, não tem recall.
- Miner script (`mining-crafting/lord-glacier-miner-autopilot-v1.0-lite.razor`) foi pensado pra mina de superfície, não dungeon — bate com essa regra.
- Dexxer autopilot já tem PK-detect embutido, mas mesma limitação de recall dentro de dungeon se aplica.

## Não confirmado / preciso checar in-game
- Se "Britain Bank" citado no guia genérico tem equivalente real em Avadon (provavelmente é a praça de Prevalia, não confirmado)
- Tempo exato de decay de murder count
- Lista completa de dungeons com PvP "quente" vs mais tranquilo
