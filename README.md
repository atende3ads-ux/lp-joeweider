# LP — Playbook Treinamento Corporativo 4.0

Landing page de vendas do Instituto Axon, criada para Joe Weider.

## URL de produção

`https://produto.joeweider.com.br/playbook-treinamento-corporativo/`

## Publicação no cPanel

1. Abra o Gerenciador de Arquivos do cPanel.
2. Entre em `public_html` do subdomínio `produto.joeweider.com.br`.
3. Envie o arquivo `joe-weider-cpanel.zip`.
4. Extraia o ZIP diretamente dentro de `public_html`.
5. Confirme que `.htaccess`, `robots.txt`, `sitemap.xml`, `llms.txt`, `llm.txt` e a pasta `playbook-treinamento-corporativo` ficaram diretamente em `public_html`.
6. Apague somente o arquivo ZIP do servidor depois de confirmar a publicação.

A raiz do subdomínio redireciona para o slug final. O `.htaccess` também configura HTTPS, cache, compressão e cabeçalhos de segurança compatíveis com Apache/cPanel.

## Otimizações aplicadas

- Layout mobile-first com breakpoints para mobile, tablet, desktop, widescreen e telas 4K.
- Imagens AVIF com fallback JPEG e dimensões declaradas para evitar deslocamento de layout.
- Fade-in acionado por `IntersectionObserver`, com suporte a `prefers-reduced-motion`.
- SEO técnico, Open Graph, Twitter Card, canonical e dados estruturados Schema.org.
- Conteúdo orientado a respostas, FAQ e arquivos `llms.txt`/`llm.txt` para agentes de IA.
- Regras de cache, compressão, HTTPS e segurança no `.htaccess`.

## Pendência comercial

- Substituir o `href="#"` de "Termos de Compra" pelo documento jurídico definitivo.

## Rastreamento

Todos os CTAs de compra direcionam ao botão principal da oferta. Esse botão abre o checkout oficial da Hotmart e preserva os parâmetros de campanha recebidos pela LP. Consulte `RASTREAMENTO-GTM.md` para os seletores, eventos e parâmetros disponíveis aos gestores de tráfego.

## Auditoria local

Lighthouse: Performance 100, Acessibilidade 100, Boas Práticas 100 e SEO 100.
