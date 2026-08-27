# Mapa de rastreamento — LP Playbook Treinamento Corporativo

## Identificação

- Contêiner GTM: `GTM-K5VFXFKL`
- Checkout: `https://pay.hotmart.com/R107300924E?checkoutMode=2`
- CTA principal: `#checkout-playbook`
- CTAs internos: `a[href="#oferta-playbook"]`
- Produto: `Playbook Treinamento Corporativo 4.0`
- Valor: `R$ 39,90`
- GA4 da LP: `G-Z5501V90ND`

## Fluxo dos CTAs

Os CTAs da barra superior, hero, módulos, card do diagnóstico e seção final rolam até o botão principal da oferta. Somente o botão `#checkout-playbook` abre o checkout da Hotmart.

## Eventos no dataLayer

| Evento | Quando dispara | Uso recomendado |
| --- | --- | --- |
| `cta_offer_click` | Ao clicar em um CTA que leva ao botão principal | Medir quais áreas da LP conduzem o visitante à oferta |
| `checkout_cta_click` | Ao clicar no botão principal, capturado antes do widget | Medir a intenção de abrir o checkout |
| `hotmart_checkout_open` | Quando o iframe `pay.hotmart.com` aparece na página | Confirmar que o pop-up abriu de fato |
| `begin_checkout` | Enviado diretamente ao GA4 quando o iframe aparece | Início de checkout confirmado no GA4 |
| `faq_toggle` | Ao abrir ou fechar uma pergunta frequente | Medir interesse nas objeções e dúvidas |

`cta_offer_click` inclui:

- `cta_location`: `topbar`, `hero`, `modules`, `diagnostic-card` ou `final`
- `cta_target`: `checkout_playbook`
- `page_slug`: `playbook-treinamento-corporativo`

`hotmart_checkout_open` e `begin_checkout` incluem:

- `cta_location`: `offer_primary`
- `checkout_provider`: `hotmart`
- `page_slug`: `playbook-treinamento-corporativo`
- `ecommerce.currency`: `BRL`
- `ecommerce.value`: `39.90`
- `ecommerce.items[0].item_id`: `R107300924E`

O evento `faq_toggle` inclui `faq_id` e `faq_state` (`open` ou `closed`). Nenhum dado pessoal é enviado ao `dataLayer`.

## Configuração recomendada no GTM

1. Criar acionadores do tipo **Evento personalizado** para `cta_offer_click`, `checkout_cta_click`, `hotmart_checkout_open` e `faq_toggle`.
2. Enviar `cta_offer_click` ao GA4 como microconversão de navegação até a oferta.
3. A LP já envia `checkout_cta_click` e `begin_checkout` diretamente ao GA4 `G-Z5501V90ND`; não crie outra tag GA4 para esses mesmos eventos no GTM, pois isso causaria duplicidade.
4. Usar `hotmart_checkout_open` no Google Ads e na Meta apenas como início de checkout, nunca como compra confirmada.
5. Para Google Ads, configurar uma ação de conversão e usar o ID completo `AW-.../label`; somente o ID `AW-...` não identifica a ação.

## Eventos dentro do checkout Hotmart

O formulário do checkout está em um iframe de `pay.hotmart.com`. Por segurança do navegador, a LP não consegue ler campos, cliques ou o envio do formulário dentro desse iframe.

Para registrar eventos posteriores à abertura do pop-up na mesma propriedade da LP:

1. Na Hotmart, acessar **Ferramentas → Ver todas → Pixel de Rastreamento**.
2. Selecionar o produto `R107300924E`.
3. Em **Google Analytics 4**, cadastrar `G-Z5501V90ND`.
4. Habilitar os eventos de início de checkout e compra concluída.
5. Em **Google Ads**, cadastrar a ação de conversão com o ID e o label fornecidos pelo Google Ads.
6. No GTM da LP, habilitar o **Vinculador de conversões** para `hotmart.com` e configurar a vinculação entre domínios.

O GA4 encontrado atualmente dentro do checkout (`G-GQH2V1F11Q`) é diferente do GA4 da LP. Enquanto a Hotmart não receber `G-Z5501V90ND` na ferramenta Pixel de Rastreamento, os eventos internos do checkout não aparecerão na propriedade usada pela LP.

## Atribuição

O botão principal mantém o parâmetro `bid` do checkout e encaminha os parâmetros recebidos pela URL da LP, incluindo UTMs, `gclid` e `fbclid`, desde que não substituam um parâmetro já existente no link da Hotmart.
