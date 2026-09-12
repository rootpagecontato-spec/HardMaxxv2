# Método Hardmaxx v2 — página de vendas

Site estático de um arquivo só. Sem build, sem dependências, sem npm.

## Arquivos

| Arquivo | O que é |
|---|---|
| `index.html` | A página inteira (HTML, CSS e JS embutidos) |
| `404.html` | Página de erro com a mesma identidade |
| `favicon.svg` | Ícone da aba |
| `og.png` | Imagem de preview no WhatsApp, Instagram, X e Facebook (1200×630) |
| `robots.txt` | Libera indexação e aponta o sitemap |
| `sitemap.xml` | Uma URL só |
| `.nojekyll` | Impede o GitHub Pages de processar o site com Jekyll |

## Publicar no GitHub Pages

1. Crie um repositório novo (pode ser público ou privado com Pages habilitado).
2. Suba **o conteúdo desta pasta na raiz do repositório**, não a pasta em si.
   Pelo site: `Add file` → `Upload files` → arraste todos os arquivos → `Commit changes`.
   O `.nojekyll` começa com ponto e o navegador às vezes esconde: confira se ele subiu.
3. `Settings` → `Pages` → em **Source** escolha `Deploy from a branch`,
   branch `main`, pasta `/ (root)` → `Save`.
4. Em um ou dois minutos o endereço aparece no topo da mesma tela, no formato
   `https://SEU-USUARIO.github.io/NOME-DO-REPO/`.

### Se usar domínio próprio
Crie um arquivo chamado `CNAME` (sem extensão) contendo só o domínio, por exemplo `hardmaxx.com.br`,
e configure o DNS conforme a tela de Pages.

## O que você precisa editar antes de divulgar

Abra o `index.html` em qualquer editor de texto e faça três trocas.

**1. Link do checkout.** Procure por `data-checkout` e troque o `href="#"` pela URL da sua
plataforma (Hotmart, Kiwify, Kirvano, Stripe, Pepper). A linha fica assim:

```html
<a class="btn btn-lg" style="width:100%" href="https://pay.suaplataforma.com/xxxx">Comprar o guia agora</a>
```

Pode apagar o `data-checkout` depois de colocar o link real.

**2. Links legais.** Procure por `data-legal` (três ocorrências no rodapé: Termos, Privacidade,
Reembolso) e aponte cada um para a sua página correspondente.

**3. Endereço do site.** Procure por `SEU-USUARIO.github.io/hardmaxx` e substitua pelo seu
endereço real. Ele aparece em 6 lugares: `canonical`, `og:url`, `og:image`, `twitter:image`,
no bloco de dados estruturados do produto, no `robots.txt` e no `sitemap.xml`.
Enquanto isso não for feito, o preview de link no WhatsApp não carrega a imagem.

### Trocar o preço
O valor aparece em quatro lugares: `R$ 35` três vezes no `index.html` e `"price": "35.00"`
no bloco de dados estruturados. O `og.png` também traz o preço impresso, então precisa ser
refeito ou substituído se o valor mudar.

## Detalhes já resolvidos

- Tema claro e escuro, seguindo a preferência do sistema de quem abre
- Responsivo, testado de 375px para cima
- Sem bibliotecas externas: só as fontes do Google Fonts
- Animações de entrada com `IntersectionObserver`, desligadas para quem usa `prefers-reduced-motion`
- Link de pular para o conteúdo, foco visível no teclado, HTML semântico
- Dados estruturados de Produto e de FAQ para busca
- Aviso médico completo no rodapé, incluindo a orientação sobre transtorno dismórfico corporal
