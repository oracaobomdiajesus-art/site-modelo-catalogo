# Site Modelo Catálogo

Template de site institucional + catálogo simples de produtos, feito em [Hugo](https://gohugo.io/), pronto para publicar grátis no Cloudflare Pages e editar pelo [Pages CMS](https://pagescms.org/).

É a versão "institucional" com uma página de catálogo a mais: produtos organizados por categoria, busca, carrinho de compras (salvo no navegador do cliente) e finalização de pedido pelo WhatsApp ou Pix. Sem painel administrativo próprio, sem integração com planilha e sem pagamento online — o pedido final sempre é combinado direto com o cliente pelo WhatsApp.

## O que dá para editar pelo CMS

- Nome do negócio, foto de perfil e biografia
- Links de Instagram, WhatsApp e avaliação no Google
- Chave Pix (opcional — se preenchida, aparece um botão de "já paguei via Pix" no carrinho)
- Lista de links personalizados
- Vídeo do YouTube em destaque
- Galeria de fotos
- Categorias do catálogo (pode ligar/desligar cada uma)
- Produtos: nome, preço, foto, descrição, categoria, promoção, estoque exibido no site
- Tema de cor e imagem de fundo do site (com opção de ligar/desligar e ajustar opacidade)

## Como funciona o pedido

O cliente monta o carrinho navegando pelo catálogo. Na hora de fechar, ele escolhe:
- **Enviar pedido pelo WhatsApp** — abre uma conversa já com a lista de itens e o total.
- **Já paguei via Pix — enviar pedido** — só aparece se a chave Pix estiver preenchida no perfil.

Não há cobrança automática nem painel de gestão de pedidos: cada pedido chega como mensagem no WhatsApp do negócio.

## Como usar este template para um novo cliente

1. Crie um novo repositório no GitHub a partir deste (use o botão "Use this template" ou clone e troque o remote).
2. No Cloudflare Pages, crie um novo projeto apontando para o repositório novo. Build command: `hugo --minify`. Diretório de saída: `public`.
3. Configure o [Pages CMS](https://pagescms.org/) apontando para o novo repositório — o arquivo `.pages.yml` já define todos os campos editáveis.
4. Edite `content/_index.md`, `content/links/`, `content/categorias/` e `content/produtos/` com as informações reais do cliente.
5. Troque `static/img/perfil.svg` pela foto real do negócio (pode ser feito direto pelo CMS, no campo "Foto de perfil").

## Estrutura

```
content/
  _index.md        → dados do perfil (nome, bio, redes sociais, tema, fundo, chave Pix)
  links/           → cada arquivo é um link exibido na página
  categorias/      → categorias do catálogo
  produtos/        → produtos do catálogo
  galeria/         → cada arquivo é uma foto da galeria
layouts/
  index.html            → página inicial (perfil, links, promoções, galeria)
  produtos/list.html    → página do catálogo completo
  partials/
    theme-style.html    → aplica tema de cor e imagem de fundo
    analytics.html      → espaço opcional para script de estatísticas
    product-card.html   → cartão de produto reutilizado no catálogo e nas promoções
    cart-panel.html      → painel do carrinho
static/
  css/style.css    → estilos do site
  js/cart.js       → lógica do carrinho (localStorage) e checkout
  js/catalogo.js   → busca e filtro de categorias no catálogo
  img/             → imagens (perfil, fundo, produtos, galeria)
```

## Desenvolvimento local

Requer [Hugo](https://gohugo.io/installation/) instalado.

```
hugo server -D
```
