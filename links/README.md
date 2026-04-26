# Página `/links` — Link in Bio da Aliny Rayze

Página minimalista no estilo "link in bio" para `https://alinyrayze.com.br/links`, seguindo 100% o guia de marca da Aliny.

## O que é

Um único arquivo HTML autocontido (`index.html`) com:
- Avatar circular com halo sage suave
- Nome em **Averes Title Roman** + função em **Raleway** (caixa alta com letterspacing)
- Tagline curta no tom da marca ("Existe um jeito *mais claro* de viver")
- 7 links em pílula (cards arredondados full-width)
- Botão CTA primário com a animação `breathe` (pulsa como respiração — assinatura do site)
- Divisor ornamental sage + frase de fechamento + copyright

Inspirado no formato do `juniorlopes.com.br`, mas inteiramente com a paleta sage/cream/taupe e a tipografia da Aliny.

## Botões incluídos (na ordem)

1. **Agendar sessão pelo WhatsApp** — CTA primário, fundo sage, com animação breathe
2. **Site oficial** — alinyrayze.com.br
3. **Instagram** — @alinyrayze
4. **Atendimento online** — âncora `#atendimentoonline` no site
5. **Quem sou eu** — âncora `#quemsou`
6. **Depoimentos** — âncora `#depoimentos`
7. **E-mail** — `mailto:contato@alinyrayze.com.br`

## Antes de publicar — substituir placeholders

Edite no `index.html`:

| Placeholder | Onde | O que colocar |
|---|---|---|
| `wa.me/55SEUNUMERO` | botão WhatsApp | DDI+DDD+número da Aliny (ex: `wa.me/5511999999999`) |
| `contato@alinyrayze.com.br` | botão E-mail (texto e `href`) | e-mail real, ou remover o botão se preferir só WhatsApp |
| Mensagem pré-preenchida do WhatsApp | parâmetro `text=` | personalizar se quiser |

## Como publicar no WordPress

A rota `alinyrayze.com.br/links` já está criada no WordPress. Três opções:

### Opção 1 — Página com Elementor "HTML"
1. Editar a página `/links` com Elementor.
2. Trocar o template para **Elementor Canvas** (sem header/footer do tema) — _Configurações da página → Layout → Elementor Canvas_.
3. Adicionar um widget **HTML** e colar o conteúdo de `<body>...</body>` (apenas o que está dentro do body), e mover o conteúdo dentro de `<style>` para a aba _Custom CSS_ (ou manter no widget HTML mesmo).
4. Salvar.

### Opção 2 — Page template customizado (mais limpo)
1. Criar `page-links.php` no tema (ou child theme) com o conteúdo deste arquivo.
2. WordPress detecta automaticamente se a slug da página for `links`.
3. Limpar cache.

### Opção 3 — Estática (mais simples)
1. Subir `index.html` direto via FTP em `/links/index.html` na raiz do servidor.
2. WordPress não interfere se a pasta existir antes de chegar no roteamento.
3. Resultado: `alinyrayze.com.br/links/` serve o HTML diretamente — performance máxima.

## Observações técnicas

- **Fontes** carregadas direto de `alinyrayze.com.br/wp-content/uploads/2026/04/` — não há request externo a Google Fonts.
- **Performance:** zero JS, CSS embutido, ~7KB HTML + 3 fontes (~450KB total).
- **Acessibilidade:** `aria-label` nos blocos, `prefers-reduced-motion` desliga a animação `breathe`, contraste validado.
- **Mobile-first:** layout até 440px de largura central, ajusta tipografia em telas <380px.
- **Open Graph** configurado para compartilhamento bonito no WhatsApp/Instagram DM.

## Personalização rápida

| Mudar | Onde no CSS |
|---|---|
| Cor primária (sage) | `--sage` no `:root` |
| Foto do avatar | `<img src="..."` dentro de `.avatar` |
| Adicionar/remover botão | duplicar bloco `<a class="link">` em `.links` |
| Promover botão para CTA primário | adicionar classe `primary` no `<a>` |
| Tirar animação breathe | remover `animation: breathe...` em `.link.primary` |
