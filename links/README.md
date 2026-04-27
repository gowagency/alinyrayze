# Página `/links` — Link in Bio da Aliny Rayze

Página minimalista no estilo "link in bio" para `https://alinyrayze.com.br/links`, seguindo o guia de marca da Aliny.

## Estrutura visual

- **Avatar circular com anel estilo Instagram** — gradiente cônico nas cores da marca (sage → bege → dourado), com gap interno cremoso, igual ao ring do feed/stories.
- **Nome** "Aliny Rayze" em **Raleway Light (300)** com letterspacing — fonte fina e minimalista.
- **Subtítulo** "PSICANÁLISE & FEMINILIDADE" em caixa alta sage com letterspacing largo.
- **Tagline** curta no tom da marca.
- **4 botões em pílula** stack vertical:
  1. **Agendar minha consulta** — CTA primário sage com animação `breathe`.
  2. **Conheça meu site** — alinyrayze.com.br
  3. **Ouça _Ordem no Caos_ no Spotify** — com tag _em breve_, não-clicável.
  4. **Fale comigo no WhatsApp**.
- Divisor ornamental + frase de fechamento.

## Antes de publicar — substituir 2 coisas

### 1. Foto de perfil
Salve a foto da Aliny em:
```
links/avatar.jpg
```
(pode ser `.jpg`, `.jpeg`, `.png` ou `.webp` — se não for `.jpg`, edite `<img src="./avatar.jpg">` no HTML).

Se o arquivo não existir, o `onerror` do `<img>` faz fallback automático para a foto que já está no servidor (`alinyrayze-2.webp`), então a página não quebra durante testes.

### 2. Número do WhatsApp
Trocar `wa.me/55SEUNUMERO` em **dois botões** (1º e 4º) pelo DDI+DDD+número da Aliny. Ex: `wa.me/5511999999999`.

### 3. (Quando o podcast estrear)
No 3º botão (Spotify), trocar:
```html
<a class="link coming" aria-disabled="true" tabindex="-1">
```
por:
```html
<a class="link" href="https://open.spotify.com/show/SEU-ID-DO-SHOW" target="_blank" rel="noopener">
```
E remover o `<span class="tag">em breve</span>` do label.

## Como publicar no WordPress

A rota `alinyrayze.com.br/links` já está criada. Três opções:

### Opção 1 — Página com Elementor "HTML"
1. Editar a página `/links` no WordPress.
2. Trocar o template para **Elementor Canvas** (sem header/footer do tema).
3. Adicionar widget **HTML** e colar o conteúdo de `<body>...</body>`. CSS pode ir no widget HTML mesmo (junto) ou no _Custom CSS_.
4. Subir `avatar.jpg` na biblioteca de mídia e trocar `./avatar.jpg` pela URL completa.

### Opção 2 — Pasta estática (mais simples e mais rápido)
Subir a pasta `links/` inteira via FTP para a raiz do servidor:
```
public_html/links/
├── index.html
└── avatar.jpg
```
WordPress não interfere — a pasta é servida diretamente. Performance máxima, zero plugin, zero config. Resultado em `alinyrayze.com.br/links/`.

### Opção 3 — Page template no tema
Criar `page-links.php` no child theme com o conteúdo de `index.html`. WordPress detecta pela slug `links`.

## Observações técnicas

- **Fontes:** Raleway 200/300/400/500/700 carregadas do Google Fonts (precisamos do peso 300 que não está nos `.ttf` locais da marca, daí a exceção). Carregamento com `display=swap`.
- **Performance:** zero JS, CSS embutido, ~9KB HTML.
- **Acessibilidade:** `aria-label`, `aria-disabled` no botão "em breve", `prefers-reduced-motion` desliga animação.
- **Mobile-first:** layout central até 440px, ajustes finos em <380px.
- **Open Graph** configurado pra compartilhamento bonito no WhatsApp/Instagram DM.

## Personalização rápida

| Mudar | Onde |
|---|---|
| Cor primária (sage) | `--sage` no `:root` |
| Foto do avatar | trocar `./avatar.jpg` |
| Adicionar/remover botão | duplicar bloco `<a class="link">` em `<nav class="links">` |
| Promover botão para CTA | adicionar classe `primary` no `<a>` |
| Tirar animação breathe | remover `animation: breathe...` em `.link.primary` |
| Ativar botão "em breve" | trocar `class="link coming"` por `class="link"` e adicionar `href` |
