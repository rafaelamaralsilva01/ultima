# Checklist de teste — antes de rodar script novo/editado no personagem

Não existe simulador offline pro Razor Outlands (confirmado por pesquisa — ver conversa original deste repo). "Teste" aqui significa: análise estática automatizada + protocolo manual em ambiente seguro. Sempre os dois, nessa ordem.

## 1. Checagem estática (rodar sempre, é rápido)

Balanço de blocos — todo `if` precisa de `endif`, todo `while` de `endwhile`, todo `for`/`foreach` de `endfor`:

```bash
python3 -c "
import re
DEST = 'caminho/do/script.razor'
for pair in [('if','endif'), ('while','endwhile'), ('for','endfor'), ('foreach','endfor')]:
    c = 0
    with open(DEST) as f:
        for line in f:
            s = line.strip()
            if re.match(rf'^{pair[0]}\b', s): c += 1
            if re.match(rf'^{pair[1]}\b', s): c -= 1
    print(pair, 'saldo:', c)
"
```
Saldo devia ser 0 pra cada par (exceto for/foreach que compartilham `endfor` — somar os dois antes de comparar com o total de `endfor`).

Outras checagens rápidas:
- **Aspas balanceadas por linha** (fora de comentário) — string quebrada é bug silencioso.
- **`()` de agrupamento** — não existe no Razor Outlands, ver PATTERNS.md. `grep -c '('` só deve aparecer dentro de comentário.
- **Variável usada mas nunca declarada** — comparar toda variável checada em `if X = `/`if X != ` contra toda declaração `@setvar!`/`setvar`. Sinal de flag "fantasma" tipo o `EnableRedAlertOverhead` do miner.
- **ID numérico isolado onde o resto do script usa nome** — ver regra em PATTERNS.md.
- **`or`/`and` misturado sem separar em `if` aninhado** — risco de precedência ambígua.

## 2. Protocolo manual (sempre antes de liberar versão nova)

1. Rodar **parado**, dentro de casa/pousada/banco — nunca a primeira execução em campo.
2. Adicionar `overhead` extra temporário em cada branch nova/alterada, pra confirmar visualmente qual caminho o script tomou.
3. Rodar 1 ciclo completo observando os overheads — não deixar correndo sozinho na primeira vez.
4. Se envolve auto-recall/escape: confirmar que o método de fuga configurado (rune/runebook/magery/chivalry) realmente existe no inventário **antes** de ir pra área de risco. Ver aviso no README sobre `ultimate-escape` exigir runa própria.
5. Se envolve variável de sessão (`@setvar!`) que já existia de testes anteriores: rodar `SCRIPTRESET` (se o script tiver) ou verificar manualmente na aba Variables do Razor se algo ficou "travado" de um bug antigo já corrigido no código mas não no estado salvo.
6. Só depois de 1 ciclo limpo, remover overheads de debug extra e liberar pra uso normal.

## 3. Depois de identificar bug em produção

1. Reproduzir a causa raiz no código (não só sintoma) — ver histórico de commits deste repo pra exemplos (`git log --oneline -- <arquivo>`).
2. Corrigir com commit próprio, mensagem explicando causa raiz + sintoma observado.
3. Se a causa for um padrão novo de erro (tipo "parênteses não funciona"), documentar em `PATTERNS.md` pra não repetir.
4. Se envolveu variável de sessão que pode ter ficado com estado ruim salvo, adicionar ao mecanismo de reset do script (ver caso `idonthaveapacky` no miner — `SCRIPTRESET` não limpava e ficou stuck).
