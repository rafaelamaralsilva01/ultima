# Setup do personagem (Dexxer Swords + Chivalry) — baseline

Você começou recentemente, sem setup organizado ainda. Isto é um ponto de partida simples — dá pra crescer conforme for jogando. Nomes de macro abaixo são sugestão minha; crie no Razor com esse nome exato (Options → Macros → Add) que os scripts deste repo já vão reconhecer sem precisar editar nada.

## Equipamento confirmado
- **Weapon Codex**: Sword Codex (special moves de espada)
- **Chivalry Codex**: acesso a spells/buffs de Chivalry

## Display sempre visível (config de UI, não é macro)
- Razor → aba **Agents** → **Health Tracker** → adiciona `self` → fixa barra de vida na tela
- Client → arrasta a skill **Chivalry** pra um hotbar/quickbar fixo (vê % sem abrir janela)

## Macros sugeridos (crie no Razor com este nome exato)

| Nome do macro | O que faz | Ação no Razor |
|---|---|---|
| `Open Sword Codex` | Abre o codex de espada (special moves) | dclick no seu Sword Codex |
| `Open Chivalry Codex` | Abre o codex de Chivalry (spells/buffs) | dclick no seu Chivalry Codex |
| `Bandage Self` | Curar com bandagem | *(já existe por padrão no Razor, não precisa criar)* |
| `Target Self` | Target em si mesmo | *(já existe por padrão)* |
| `Attack Closest` | Ataca o inimigo mais próximo | hotkey nativo "Target Closest Enemy" + "Attack Last Target" |

## O que ainda não sei (preencher depois de testar in-game)
- Nome exato dos **finishers**/**stances** dentro do Sword Codex (varia por gump, preciso ver o layout real)
- Se spells de Chivalry (ex: Divine Fury, Close Wounds) são castáveis direto por `cast 'Divine Fury'` ou só via gump do codex — isso muda como o script chama

## Como isso vira código depois
Quando formos escrever/adaptar script pra você, ele vai referenciar esses nomes de macro exatamente como estão na tabela (`hotkey 'Open Sword Codex'`, etc). Se você renomear no Razor, avisa que eu atualizo o script.
