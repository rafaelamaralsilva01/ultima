# Build: Blacksmith/Miner (suporte) — plano fase a fase pra iniciante

Fontes: [wiki.uooutlands.com/Blacksmithy](https://wiki.uooutlands.com/Blacksmithy), [Tinkering](https://wiki.uooutlands.com/Tinkering), [New Player Guide](https://wiki.uooutlands.com/New_Player_Guide), [uo.jaseowns.com starter items](https://uo.jaseowns.com/outlands/starter-items).

## Meta final

| Skill | Alvo |
|---|---|
| Blacksmithy | 120 |
| Mining | 100 |
| Tinkering | 100 |
| Magery | 60-100 (utilidade: recall pra minerar/fugir) |

Diferente do Dexxer, esse personagem **não é de combate** — cada ponto em skill de luta é ponto tirado de crafting/utilidade. Template inicial "Blacksmith" já vem com **Blacksmith 50, Tinkering 50, Mining 50, Macing 50** (200 pontos) — o Macing 50 é sobra do template, não é foco da build (só autodefesa básica).

## Fase 0 — Criação de personagem

- Escolher template **Blacksmith** na criação — vem com Tongs x2, Pickaxe x4, TinkerTools x3, Maul, e os 50/50/50/50 acima já alocados.
- Se Magery não vier de template, vai ter que treinar do zero depois (fase 3).

## Fase 1 — Shelter Island (0 → 50, o que der de graça)

- Mining/Blacksmith/Tinkering são **skills de trade/gathering** — a bonificação de ganho acelerado da ilha **não vale pra elas** (confirmado no New Player Guide: "except for Crafting/Gathering skills"). Ou seja, não adianta ficar preso na ilha esperando bônus pra essas 3 — sobe igual em qualquer lugar, na prática.
- Ainda vale ficar na ilha pra treinar **Macing** de graça nos Battle Trainers se quiser um mínimo de autodefesa, mas não é prioridade.
- **Mining 0-50** e **Blacksmithy 0-50**: treináveis direto com **NPC trainer** (clique simples nele, escolhe a skill, paga gold ou usa Training Credits Deed).

## Fase 2 — Mineração ativa (Mining 50 → 100)

- Mining sobe por **uso prático** — minerar ore com a picareta, toda tentativa tem chance de falhar = chance de ganhar skill.
- Precisa ficar perto de veios de minério (mina). Ore vira ingot no forge (ver script `mining-crafting/lord-glacier-miner-autopilot-v1.0-lite.razor` — automatiza isso).
- Sem bônus de ilha aqui — é grind normal de uso.

## Fase 3 — Blacksmithy (50 → 120, o núcleo da build)

Tiers de custo em ingot (confirmado na wiki, valores aproximados):

| Faixa | O que craftar | Ingots aprox. |
|---|---|---|
| 0-50 | Treino direto no NPC | — |
| 40-65 | Chainmail (peças) | ~11.700-33.400 total até 85 |
| 60-85 | Platemail (peças) | (mesma faixa acima) |
| 85-120 | Platemail avançado + Repair Kits | ~16.700-33.300 por incremento de 5 |

- Estimativa total: **~130.000 ingots** pra ir de 50→100, mais **~110.000** de 100→120 (com reciclagem de peças pra recuperar material).
- Precisa estar perto de **forge + anvil**, com tongs ou smith's hammer na bolsa.
- Script de referência pronto: `mining-crafting/blacksmithy-crafting-queue-50-120.razor` (fila automática, mas checar `TESTING_CHECKLIST.md` antes de rodar).

## Fase 4 — Tinkering (50 → 120, ferramentas + suporte)

| Faixa | O que craftar |
|---|---|
| 0-50 | Treino direto no NPC |
| 50-75 | Lanternas |
| 75-80 | Iron Lockpicks |
| 80-100 | Keyrings ou Trap Detonators |
| 100-120 | Candelabras |

- ~70.000 ingots até GM (100), +80.000 até 120 — mesma lógica de reciclagem do Blacksmithy pra economizar material.
- Serve pra fazer suas próprias **Tinker Tools** (5 iron ingots, sem requisito de skill) — não depende de comprar ferramenta.
- **Craftsman's Toolbox** (vendedor em Prevalia) combina ferramentas parcialmente gastas — economiza recurso, vale comprar cedo.

## Fase 5 — Magery (utilidade: recall pra minerar e fugir de PK)

- Não é skill de combate aqui, é **utilidade**: Recall pra ir/voltar da mina rápido, e principal fuga de PK (junto com o script `magery-escape/ultimate-escape-recall-runetome-chivalry.razor`).
- 60 de Magery já libera Recall via cast. Acima disso (até 100) é ganho de margem/confiabilidade, não essencial no início.
- Precisa de **runa/runebook marcado** — sem isso, nem o cast de Recall nem o script de fuga funcionam (ver aviso em `reference-scripts/README.md`).

## Onde treinar — resumo rápido

| Skill | Onde | Custo |
|---|---|---|
| Mining/Blacksmithy (0-50) | NPC trainer, qualquer cidade | Gold ou Training Credits Deed |
| Mining (50-100) | Minerar de verdade em veio de minério | Grátis (uso) |
| Blacksmithy (50-120) | Craftar peças no forge/anvil (ver tabela) | Ingot (compra ou minerado) |
| Tinkering (0-50) | NPC trainer | Gold/Training Credits |
| Tinkering (50-120) | Craftar itens (ver tabela) | Ingot |
| Magery (0-60+) | NPC trainer + uso (cast) | Gold + reagente |

## Coisas que preciso confirmar in-game
- Local exato de veios de minério bons pra early game (perto de Avadon?)
- Se dá pra comprar ingot em quantidade de vendor ou só minerando mesmo
- Onde fica o Craftsman's Toolbox vendor em Prevalia exatamente
