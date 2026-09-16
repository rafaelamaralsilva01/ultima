# Como baixar scripts de outlands.uorazorscripts.com (pra IA em sessões futuras)

Guia técnico de como extrair o texto puro de um script daquele site. Não é intuitivo — a página não expõe o script em HTML simples, e ferramentas de fetch genéricas (tipo WebFetch) só devolvem um resumo em prosa gerado por um modelo pequeno, não o código real. Segue o método que funciona.

## Por que não dá pra usar WebFetch direto

O site é uma SPA em Remix. O texto do script fica embutido dentro de um blob JSON de hidratação (`loaderData`) que o servidor manda junto com o HTML — não existe em nenhuma tag `<textarea>`/`<pre>` visível. Pedir pra uma ferramenta de fetch "resumir a página" faz ela alucinar/parafrasear o conteúdo, ou na melhor das hipóteses devolver só a descrição do autor, nunca o script inteiro.

## Passo 1: baixar o HTML bruto

```bash
curl -sL "https://outlands.uorazorscripts.com/script/<uuid-do-script>" -o pagina.html -A "Mozilla/5.0"
```
O UUID vem da URL da página do script (ex: busca no site, ou resultado de WebSearch por categoria em `/skills/<categoria>`).

## Passo 2: entender o encoding

O campo do script aparece no HTML assim (bytes literais, contando barras invertidas):

```
\"content\",\"/////////\\n////////   Nome do Script...
```

Ou seja: o JSON de hidratação foi serializado **duas vezes** (stringify de stringify). Cada aspas virou `\"`, cada quebra de linha virou `\\n` (duas barras). Precisa desescapar 2 vezes, não 1 — desescapar só uma vez deixa lixo tipo `Ã¢ÂÂ¼` no lugar de caracteres especiais (acontece porque `str.encode().decode('unicode_escape')` corrompe UTF-8 multi-byte; usar `json.loads` evita isso).

## Passo 3: extrair

Script Python que faz a extração certa (localizar o campo pelo marcador, desescapar 2x com `json.loads`, depois `html.unescape` pras entidades tipo `&#x27;`):

```python
import re, html, json, sys

def unescape_json_str(s):
    # json.loads entende \n \t \" \\ \uXXXX sem tocar em caracteres
    # unicode literais já corretos (diferente de encode().decode('unicode_escape'),
    # que corrompe UTF-8 multi-byte tipo "▼").
    return json.loads('"' + s + '"')

def extract(path, out):
    data = open(path, encoding='utf-8', errors='ignore').read()
    start_marker = '\\"content\\",\\"'
    si = data.find(start_marker)
    if si == -1:
        print("NO content field found (double-escaped)", path)
        return
    vstart = si + len(start_marker)
    end_marker = '\\",\\"'
    ei = data.find(end_marker, vstart)
    if ei == -1:
        print("NO end marker found", path)
        return
    val = data[vstart:ei]
    v = unescape_json_str(val)
    v = unescape_json_str(v)   # desescapar 2x (double-encoded)
    v = html.unescape(v)
    open(out, 'w', encoding='utf-8').write(v)
    print(out, len(v))

if __name__ == '__main__':
    extract(sys.argv[1], sys.argv[2])
```

Uso:
```bash
python3 extract_script.py pagina.html script_extraido.razor
```

## Passo 4: validar antes de salvar no repo

- Confere início e fim do arquivo (`head -c 300` / `tail -c 300`) — deve começar com o banner ASCII do script (`/////////` ou `#`), nunca com lixo tipo `[{"_1":2...` (sinal de que pegou o blob errado, não o campo `content`).
- Se aparecer `Ã¢ÂÂ` em qualquer lugar, o desescape duplo falhou — não usar `str.encode().decode('unicode_escape')`, usar `json.loads` como acima.
- Confere balanço de `if`/`endif` e `while`/`endwhile` (útil pra scripts grandes, ver checagem em `PATTERNS.md`).

## ⚠️ Aviso de segurança — NÃO ignorar

O mesmo blob de hidratação da página carrega, além do `content`, um objeto `scriptCreator` com **username e password hash bcrypt do autor do script**, em texto plano, sem autenticação nenhuma pra acessar. Isso é falha de segurança do site, não nossa.

**Nunca** salvar, logar ou repetir esses campos (`username`, `passwordHash`) em nenhum arquivo do repo ou em output de terminal que possa persistir. Extrair só o campo `content` (o script em si) e descartar o resto do HTML/JSON baixado depois de extrair.

## Onde salvar o resultado

```
reference-scripts/
  <categoria>/<nome-descritivo>-v<versao>.razor
```
E adicionar entrada na tabela de `reference-scripts/README.md` (autor, versão, link original, categoria, o que faz). Ver commits anteriores no histórico do repo (`git log --oneline -- reference-scripts/`) pra exemplos de mensagens de commit ao importar um script novo (baseline sem modificação primeiro, depois fixes em commits separados).
