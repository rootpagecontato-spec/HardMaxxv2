# Método Hardmaxx v2 · página de vendas

Site estático de um arquivo só. Sem build, sem dependências, sem npm.

## Arquivos

| Arquivo | O que é |
|---|---|
| `index.html` | A página inteira (HTML, CSS, JS e os diagramas SVG embutidos) |
| `404.html` | Página de erro com a mesma identidade |
| `assets/` | Logo (crânio), ícones e as fotos de antes e depois |
| `favicon.ico` | Ícone da aba |
| `og.png` | Imagem de preview no WhatsApp, Instagram, X e Facebook (1200×630) |
| `robots.txt` | Libera indexação e aponta o sitemap |
| `sitemap.xml` | Uma URL só |
| `.nojekyll` | Impede o GitHub Pages de processar o site com Jekyll |

## Identidade

Extraída do PDF do ebook, para o site e o livro falarem a mesma língua.

| Token | Valor | Onde aparece |
|---|---|---|
| Preto | `#0A0A0B` | fundo da página |
| Off-white | `#F2F0ED` | texto |
| Vermelho | `#C8102E` | filetes, botões, marcadores |
| Vermelho claro | `#FF4256` | texto pequeno em destaque (contraste 5.8:1 no preto) |
| Papel | `#F4F2EF` | blocos claros: tabela de prazos e card da oferta |

Tipografia: **Archivo** nos títulos, **Source Serif 4** no corpo (mesma lógica do livro:
sans nos títulos, serifada no corpo), **Geist Mono** nos rótulos.

A marca usada no site é só o crânio, recortado da arte original do ebook, mais o nome
em tipografia. O lockup completo do PDF não é usado aqui porque traz um erro de digitação
no texto (`MEDOTO` em vez de `MÉTODO`).

## Seções de estrutura óssea e hard chewing

Acompanham as Partes II e III do ebook. Traz dois diagramas em SVG inline (perfil e frontal) com as
referências estruturais marcadas, os três estados de uma característica (dado, coberto,
modificável), mais o bloco de hard chewing com o diagrama da cadeia da mecanotransdução
(mordida, osteócito, esclerostina, via Wnt, osteoblasto).

Os diagramas usam variáveis CSS (`--fig-form`, `--fig-line`, `--fig-accent`, `--fig-text`,
`--fig-hair`), definidas em `.fig svg`. Os mesmos arquivos servem o PDF, onde os valores
padrão do próprio SVG entram no lugar (fundo claro).

## Seção de antes e depois

Cada caso tem duas fotos e quatro marcadores numerados sobre a foto do depois, ligados a
uma legenda que explica o que mudou em cada região (arco supraciliar, ângulo gonial,
projeção do queixo, ângulo cervicomental, terço médio).

Para trocar as fotos: substitua os arquivos em `assets/` mantendo os nomes e a proporção
4:5, e ajuste as coordenadas dos marcadores no `index.html` (`style="--x:30%;--y:31%"`,
em porcentagem da própria imagem).

As fotos atuais receberam recorte e escala para a cabeça ficar do mesmo tamanho nos dois
lados do par, e o mesmo ajuste de cor nas duas. Nenhum retoque de traço.

## Publicar no GitHub Pages

1. Suba **o conteúdo desta pasta na raiz do repositório**, não a pasta em si.
   O `.nojekyll` começa com ponto e o navegador às vezes esconde: confira se ele subiu.
2. `Settings` → `Pages` → em **Source** escolha `Deploy from a branch`,
   branch `main`, pasta `/ (root)` → `Save`.
3. Em um ou dois minutos o endereço aparece no topo da mesma tela:
   `https://rootpagecontato-spec.github.io/HardMaxxv2/`.

### Se usar domínio próprio
Crie um arquivo chamado `CNAME` (sem extensão) contendo só o domínio, por exemplo
`hardmaxx.com.br`, e configure o DNS conforme a tela de Pages. Depois troque a URL em
`robots.txt`, `sitemap.xml` e nas tags `canonical` e `og:*` do `index.html`.

## Rodar local

```bash
python -m http.server 8000
```

Abra `http://localhost:8000`.

## Checklist antes de anunciar

- [ ] Link do checkout da Kiwify conferido no `index.html` e no schema de produto
- [ ] Preço igual em três lugares: hero, card da oferta e `application/ld+json`
- [ ] Número de páginas igual em cinco lugares: meta description, og, schema, hero e oferta
- [ ] Páginas de termos, privacidade e reembolso publicadas e linkadas no rodapé
      (hoje os três links mostram um aviso de placeholder)
- [ ] Autorização de uso de imagem de quem aparece nas fotos
