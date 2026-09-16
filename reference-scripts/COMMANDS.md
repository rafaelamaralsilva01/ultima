# Índice de comandos — onde procurar o quê

Referência oficial completa, dividida em 2 arquivos por camada:

- [`docs/razor-base-reference.md`](docs/razor-base-reference.md) — Razor Community Edition (engine base). Commands, Expressions, Keywords, Layers, Variables. Fonte: razorce.com/guide.
- [`docs/outlands-extensions.md`](docs/outlands-extensions.md) — só o que a Outlands **adicionou/modificou** sobre o CE base (findtype expandido, listas, timers, cooldowns, interpolação `{{var}}`, restrições PvP). Fonte: wiki.uooutlands.com.

## Categorias rápidas (base CE)

| Categoria | Comandos principais |
|---|---|
| Ação | attack, cast, dclick, dclicktype, drop, lift, lifttype, walk, wait, hotkey, potion, virtue, setability, skill, script |
| Agente | organizer, restock, scavenger, sell, useonce |
| Gump/Menu | gumpresponse, gumpclose, menu, menuresponse, promptresponse, waitforgump, waitformenu, waitforprompt |
| Ignore | ignore, unignore, clearignore |
| Lista | createlist, clearlist, removelist, pushlist, poplist |
| Mensagem | say, sysmsg, overhead, whisper, yell, emote, guild, alliance, waitforsysmsg, clearsysmsg |
| Target | target, targettype, targetloc, targetrelloc, lasttarget, setlasttarget, clearall, waitfortarget |
| Timer | createtimer, removetimer, settimer, timer, timerexists |
| Controle de fluxo | if/elseif/else/endif, for/endfor, foreach/endfor, while/endwhile, break, continue, stop, loop/replay |
| Operadores lógicos | and, or, not, as, in, `=` `==` `!=` `<` `<=` `>` `>=` |

## Extensões Outlands (não existem no CE puro)

`findtype`/`dclicktype`/`targettype`/`lifttype` expandidos (hue/qty/range), `findtypelist`, `find`, `findlayer`, `targetexists`, `followers`, `hue`, `name`, `paralyzed`, `invul`, `warmode` (cmd+expr), `noto`, `dead`, `maxweight`, `diffweight/diffhits/diffmana/diffstam`, `counttype`, `gumpexists`, `ingump`, `varexist`, `bandaging`, `cooldown` (cmd+expr), `getlabel`, `rename`, `setskill`, listas completas (`createlist/clearlist/removelist/pushlist/poplist/listexists/list/inlist/atlist`), timers (`createtimer/removetimer/settimer/timer/timerexists`), interpolação `{{var}}`, variável `index` em loops, restrições de PvP.

## O que já vimos funcionar de verdade (grounded nos 5 scripts do repo)

Ver [`PATTERNS.md`](PATTERNS.md) — padrões confirmados por uso real, incluindo a descoberta de que **`()` de agrupamento não é suportado** mesmo estando documentado como sintaxe padrão de "parâmetros obrigatórios" (isso é notação da doc, não sintaxe de agrupamento lógico executável).

## Antes de escrever comando que nunca vimos em uso real

1. Procurar em `docs/razor-base-reference.md` ou `docs/outlands-extensions.md` — se documentado, a sintaxe exata está lá.
2. Se não achar, é porque não existe nessas duas fontes — não inventar sintaxe por analogia sem avisar que é especulativo.
3. Depois de usar em um script e confirmar que funciona no client, atualizar `PATTERNS.md` com o padrão confirmado.
