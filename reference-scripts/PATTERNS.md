# Padrões de sintaxe observados (base: corpus real desta pasta)

Extraído de 4 scripts reais (~938k linhas combinadas de código, dominado pelo Dexxer autopilot de 16.5k linhas). Isto é o "manual" — grounded em código real, não em teoria da wiki.

## Estrutura de controle de fluxo

- **Sem `gosub`/`goto`/labels** nos 4 scripts. Fluxo é 100% `if/endif`, `while/endwhile`, e reinício do topo via `replay` (147 ocorrências) — não `loop` (só 1 ocorrência, script pequeno). `replay` é o padrão dominante pra script "infinito" (miner, dexxer autopilot).
- Nesting profundo é normal: scripts grandes chegam a 4-5 níveis de `if` aninhado. Indentação com espaços, não tabs.

## Variáveis

- Sempre `@setvar!` (598 ocorrências, prefixo `@` = silencioso, `!` = sessão-only, não persiste). Praticamente nunca usam `setvar` persistente puro nesses scripts de automação — faz sentido pra não vazar estado entre sessões/personagens.
- Nome de variável em **PascalCase** ou **camelCase** descritivo: `EnableOverheadMessages`, `EnableAutoParalyzePouch`, `MiningActive`. Bloco de config fica todo no topo do arquivo, com comentário explicando cada flag (`# Disable or Enable ...`).
- Operador `as` pra capturar resultado de busca é o padrão universal pra manipular item encontrado: `if findtype 'dagger' as MyDagger` → aparece dezenas de vezes (`as BagofPot`, `as HealPot`, `as MyCodex`, etc). Nome da variável capturada sempre PascalCase, referenciando o item.

## Comentários

- `#` é majoritário (718 vs 371 de `//`) pra explicação/documentação de bloco.
- `//` usado mais pra separadores visuais e headers decorativos (`/////////`, banners ASCII com nome do script/autor/versão no topo).
- Todo script sério abre com bloco de banner: nome, versão, autor, data, contato, requisitos de inventário, lista do que o script faz — isso deve ser o padrão nos scripts que escrevermos.

## Timers e cooldowns

- `settimer` (235+ ocorrências) é o mecanismo dominante pra qualquer "espera X e faz Y", mais usado que `cooldown` (feature nova da Outlands). Convém checar `timerexists` antes de reusar nome de timer.

## Loot / target seguro

- `overhead` usado pra feedback visual (347+ ocorrências) com hue numérico fixo por tipo de mensagem (ex: `88` = sucesso, `69` = aviso) — convenção de cor por severidade, não aleatório.
- `wait` curto (100-300ms) intercalado entre ações de UI (clique de gump, target) — nunca ação instantânea sem wait após abrir gump/menu.

## Escape / recall (do `ultimate-escape` e `miner`)

- Prioridade de fuga: **moongate próximo → recall via runa (Magery) → Sacred Journey (Chivalry) → runetome/runebook carregado**. Testar cada método em cascata com `if/elseif`, nunca assumir só um disponível.
- Placeholder de nome de runa (`DoS` no script de exemplo) precisa ser trocado manualmente por find-and-replace antes de usar — nunca script hardcoded com nome genérico sem aviso.
- `gumpexists <id>` + `gumpresponse` é o padrão pra fechar prompts de moongate/menu que aparecem no meio da fuga.

## Operadores lógicos — SEM parênteses

- **Razor (fork Outlands) não suporta `()` de agrupamento em expressões.** Confirmado em teste real: `if (A or B) and C` deu `Script error: unknwon operator in exression` no client. Erro descoberto ao "corrigir" precedência de `or`/`and` no miner script — o fix inicial (adicionar parênteses) quebrou o script; teve que ser revertido.
- Pra forçar agrupamento lógico, usar **`if` aninhado**, nunca parênteses:
  ```
  # errado (não compila):
  if (findtype A or findtype B) and findtype C
  
  # certo:
  if findtype A or findtype B
      if findtype C
          ...
      endif
  endif
  ```
- Qualquer condição `X or Y and Z` sem parênteses é ambígua sobre precedência real do interpretador — se a lógica importa (ex: "ore só conta se tiver forge E ore", não só forge OU ore-com-forge), sempre quebrar em `if` aninhado em vez de confiar em precedência implícita ou tentar agrupar com `()`.

## Regra prática pra escrever scripts novos aqui

1. Banner de header (nome, versão, requisitos) sempre.
2. Bloco de config no topo com `@setvar!` + comentário por flag.
3. `as` pra qualquer resultado de `findtype`/`find` que será usado depois.
4. `replay` como padrão de loop principal, não `goto`.
5. `overhead` com hue consistente por severidade (padronizar: erro/vermelho, sucesso/verde, info/branco).
6. Qualquer valor específico da conta (nome de runa, serial, nome de personagem) marcado com comentário `# CONFIGURAR` — nunca deixar hardcoded sem aviso.
7. Nunca usar `()` pra agrupar condições — usar `if` aninhado (ver seção acima).
