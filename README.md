# LP — Playbook Treinamento Corporativo 4.0

Landing page de vendas do Instituto Axon, criada para Joe Weider.

## URL de produção

`https://produto.joeweider.com.br/playbook-treinamento-corporativo/`

## LP /playbook-set26

Nova versão da página com a copy de setembro/2026, em `playbook-set26/index.html`. Usa os mesmos `assets/` da raiz, o mesmo checkout Hotmart, GTM, GA4 e Clarity da LP principal. Os eventos no `dataLayer` são os mesmos de `RASTREAMENTO-GTM.md`, com `page_slug: playbook-set26`.

- GitHub Pages: `https://atende3ads-ux.github.io/lp-joeweider/playbook-set26/`
- O `.cpanel.yml` ainda publica somente a LP principal.

Pendências:

- Preencher `WHATSAPP_NUMERO` no script do final da página. Sem número, o botão "Falar sobre o Playbook" leva ao FAQ.
- Garantia: o bloco da oferta e a pergunta "E se eu comprar e não gostar?" estão comentados no HTML até a validação com cliente/Hotmart.
- Rodapé: CNPJ, e-mail de suporte, telefone, WhatsApp e link de "Termos de Compra".

## LP /acelerador (protótipo)

Página do Axon Acelerador de Negócios, em `acelerador/index.html`. Mesma diagramação da `/playbook-set26`, tema escuro com o rosa do Instituto (#E92063). Captação por formulário, sem checkout.

- GitHub Pages: `https://atende3ads-ux.github.io/lp-joeweider/acelerador/`
- Rastreamento: GTM e Clarity da LP principal; eventos `cta_form_click`, `lead_form_submit`, `whatsapp_click` e `faq_toggle` com `page_slug: acelerador`.
- WhatsApp (62) 99200-5555 com a mensagem da copy já preenchida.

Pendências:

- Formulário: preencher `FORM_ENDPOINT` no script do final da página com a URL que vai receber o POST (Formspree, Make, n8n…). Sem endpoint, o protótipo só mostra a mensagem "Recebemos sua solicitação".
- Logos autorizados (seção Experiência), exemplos reais de painéis/processos/planos e casos com depoimento (seção "Como o trabalho ganha forma", hoje com espaços marcados "Exemplo ilustrativo").
- FAQ: "Os encontros são online ou presenciais?" e "Qual é a frequência dos encontros?" estão comentadas até confirmação comercial.
- Rodapé: link da Política de Privacidade, razão social, CNPJ e e-mail institucional.

## LP /acelerador-consultores

Axon Acelerador de Negócios para consultores, instrutores e mentores, em `acelerador-consultores/index.html`, com a página de obrigado em `acelerador-consultores/obrigado/`. Copy do Google Doc "LP | Axon acelerador de negócios" (tarefa [JOE WEIDER] AXON ACELERADOR, 3ADS Flow). Mesmo design system da `/acelerador`; formulário multi-step em 3 passos que termina na página de obrigado com botão para o WhatsApp.

- GitHub Pages: `https://atende3ads-ux.github.io/lp-joeweider/acelerador-consultores/`
- Rastreamento: GTM e Clarity da LP principal; eventos `cta_form_click`, `form_step_view`, `lead_form_submit`, `vsl_play`, `whatsapp_click` e `faq_toggle` com `page_slug: acelerador-consultores` (`obrigado_view` na página de obrigado).

Pendências:

- VSL: incorporada pelo player do Drive ("Joe Weider - Vídeo 1 LP.mp4", 569 MB). Para trocar por YouTube/Vimeo (com autoplay e sem a marca do Drive), altere `VSL_URL` no script do final da página. Falta inserir a duração final, se for exibida.
- Formulário: preencher `FORM_ENDPOINT` com a URL que recebe o POST. Sem endpoint, o envio só leva à página de obrigado.
- Logos autorizados na faixa "Experiência em organizações" (hoje são os nomes em texto) e bloco de cases e depoimentos (oculto até haver material aprovado).
- WhatsApp: a copy pede "[Inserir WhatsApp validado]"; está usando (62) 99200-5555, o mesmo da `/acelerador`.
- Rodapé: razão social, CNPJ, e-mail, telefone, Política de Privacidade e Termos marcados como [CONFIRMAR] na copy.

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
