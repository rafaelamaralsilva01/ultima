---
name: uorazorscripts-fetch
description: Use whenever fetching, downloading, or extracting a Razor script from outlands.uorazorscripts.com (or scraping any script content from that site). Trigger on requests like "pega esse script do site", "baixa o script de...", "adiciona esse script de referência", or any URL under outlands.uorazorscripts.com/script/. Do NOT use plain WebFetch on these pages — it only paraphrases/summarizes and never returns the real script text.
---

# Extrair scripts de outlands.uorazorscripts.com

Antes de tentar `WebFetch` numa URL `outlands.uorazorscripts.com/script/...`, leia o guia completo em [reference-scripts/HOW_TO_FETCH_SCRIPTS.md](../../reference-scripts/HOW_TO_FETCH_SCRIPTS.md) neste repo. Resumo do porquê e do como:

## Por que WebFetch não funciona aqui

A página é uma SPA Remix. O texto do script não existe em HTML simples (nem `<textarea>`, nem `<pre>`) — está embutido, **duas vezes serializado como JSON**, dentro do payload de hidratação `loaderData`. Pedir pra uma ferramenta de fetch "resumir" isso faz ela parafrasear a descrição do autor, nunca devolve o script real.

## Método correto (resumo — detalhes completos no HOW_TO_FETCH_SCRIPTS.md)

1. `curl -sL "<url-do-script>" -o pagina.html -A "Mozilla/5.0"`
2. Localizar o marcador `\"content\",\"` no HTML bruto — é onde o campo do script começa.
3. Desescapar o valor **duas vezes** com `json.loads('"' + valor + '"')` (nunca `str.encode().decode('unicode_escape')` — corrompe caracteres UTF-8 multi-byte tipo `▼`).
4. `html.unescape()` no resultado pra resolver entidades tipo `&#x27;`.
5. Validar: início deve ser o banner ASCII do script, nunca `[{"_1":2...` (sinal de que pegou o blob errado).

O script Python pronto pra isso está documentado inteiro no HOW_TO_FETCH_SCRIPTS.md — copiar de lá em vez de reescrever do zero.

## Aviso de segurança — sempre relembrar

O mesmo payload carrega `username` e `passwordHash` (bcrypt) do autor do script, em texto plano, sem autenticação. **Nunca** salvar, logar ou repetir esses campos em arquivo do repo ou em output que persista — extrair só o campo `content` e descartar o resto.

## Onde salvar o resultado

`reference-scripts/<categoria>/<nome-descritivo>-v<versao>.razor` + entrada na tabela de `reference-scripts/README.md` (autor, versão, link original, categoria).
