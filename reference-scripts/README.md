# Reference Scripts — UO Outlands Razor

Corpus de scripts reais da comunidade, usado como **base de referência de sintaxe** (não pra rodar direto sem revisão). Fonte: [outlands.uorazorscripts.com](https://outlands.uorazorscripts.com/).

Build alvo: **Dexxer (Swords)** + **Blacksmith/Miner (Mining + Blacksmithy + Magery escape)**.

## Índice

| Arquivo | Categoria | Autor | Versão | Fonte |
|---|---|---|---|---|
| `dexxer-combat/lord-glacier-dexxer-autopilot-v3.1.1.razor` | Combate Dexxer (multi-arma, config p/ Swords) | Lord Glacier (danstock.\_98439) | 3.1.1 (2026-09-08) | [link](https://outlands.uorazorscripts.com/script/7aba7670-e30e-489d-86ec-c95e79ad57c6) |
| `mining-crafting/lord-glacier-miner-autopilot-v1.0-lite.razor` | Mineração + auto-forge + auto-recall | Lord Glacier (danstock.\_98439) | 1.0 LITE (2025-07-08) | [link](https://outlands.uorazorscripts.com/script/6535aac0-adc2-4135-94ef-ded481fe71aa) |
| `mining-crafting/blacksmithy-crafting-queue-50-120.razor` | Progressão de skill Blacksmithy 50→120 via fila de crafting | TheGmaster1 | — (2023, base) | [link](https://outlands.uorazorscripts.com/script/791a9815-cde8-407d-8001-a06160685dd7) |
| `magery-escape/ultimate-escape-recall-runetome-chivalry.razor` | Fuga de PK: moongate → recall (magery) → sacred journey (chivalry) → runetome/runebook | special_sy (mod: Chumber) | — (2025-06-06) | [link](https://outlands.uorazorscripts.com/script/df86f94a-832a-496d-b65c-34bc2f7f97ab) |

## Como usar cada um (linha racional)

1. **Mineração (XP + material)** → `lord-glacier-miner-autopilot-v1.0-lite.razor`. Cobre mining + auto-forge (funde ore em ingot) + auto-recall em ninho/PK. É a opção mais prática: junta minerar e virar ingot (pré-requisito de XP de blacksmith) num script só, sem precisar de dois separados.
2. **Craftar itens (XP de Blacksmithy)** → `blacksmithy-crafting-queue-50-120.razor`. Roda parado no forge/anvil consumindo os ingots gerados pelo miner, avançando a skill 50→120 automaticamente por faixa de item.
3. **Fuga (PK durante mineração)** → `ultimate-escape-recall-runetome-chivalry.razor`. Standalone, focado em Magery (recall) como prioridade — dispara à parte do miner, não substitui o auto-recall QOL que já vem embutido nele. Use quando o auto-recall do miner falhar ou quiser controle manual de hotkey.
4. **Combate (Dexxer, Swords)** → `dexxer-combat/lord-glacier-dexxer-autopilot-v3.1.1.razor`. Suporta várias armas — ao configurar, focar bloco de `Swords` e desativar os outros weapon-types no setup inicial do script.

Tudo que não é gathering/crafting/combate base fica manual, por decisão do usuário.

## Aviso de segurança

Ao raspar o HTML de `outlands.uorazorscripts.com` pra extrair o texto puro dos scripts, o payload de hidratação (Remix `loaderData`) da página **vazou username + password hash bcrypt dos autores dos scripts** (ex.: `danstock._98439`, `TheGmaster1`, `special_sy`) em texto plano na resposta HTTP pública, sem autenticação. Isso é uma falha de segurança do site (exposição de dados de sessão/admin no SSR payload), não algo relacionado ao seu personagem. Nada disso foi salvo nos arquivos deste repositório — só o corpo do script em si. Se quiser, posso te ajudar a reportar isso ao mantenedor do site.
