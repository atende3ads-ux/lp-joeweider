# Mapa de rastreamento — LP Playbook Treinamento Corporativo

## Identificação

- Contêiner GTM: `GTM-K5VFXFKL`
- Checkout: `https://pay.hotmart.com/R107300924E?bid=1787597709306`
- CTA principal: `#checkout-playbook`
- CTAs internos: `a[href="#checkout-playbook"]`
- Produto: `Playbook Treinamento Corporativo 4.0`
- Valor: `R$ 39,90`

## Fluxo dos CTAs

Os CTAs da barra superior, hero, módulos, card do diagnóstico e seção final rolam até o botão principal da oferta. Somente o botão `#checkout-playbook` abre o checkout da Hotmart.

## Eventos no dataLayer

| Evento | Quando dispara | Uso recomendado |
| --- | --- | --- |
| `cta_offer_click` | Ao clicar em um CTA que leva ao botão principal | Medir quais áreas da LP conduzem o visitante à oferta |
| `begin_checkout` | Ao clicar no botão principal que abre a Hotmart | GA4, Google Ads e Meta como início de checkout |
| `faq_toggle` | Ao abrir ou fechar uma pergunta frequente | Medir interesse nas objeções e dúvidas |

`cta_offer_click` inclui:

- `cta_location`: `topbar`, `hero`, `modules`, `diagnostic-card` ou `final`
- `cta_target`: `checkout_playbook`
- `page_slug`: `playbook-treinamento-corporativo`

`begin_checkout` inclui:

- `cta_location`: `offer_primary`
- `checkout_provider`: `hotmart`
- `page_slug`: `playbook-treinamento-corporativo`
- `ecommerce.currency`: `BRL`
- `ecommerce.value`: `39.90`
- `ecommerce.items[0].item_id`: `R107300924E`

O evento `faq_toggle` inclui `faq_id` e `faq_state` (`open` ou `closed`). Nenhum dado pessoal é enviado ao `dataLayer`.

## Configuração recomendada no GTM

1. Criar acionadores do tipo **Evento personalizado** para `cta_offer_click`, `begin_checkout` e `faq_toggle`.
2. Enviar `cta_offer_click` ao GA4 como microconversão de navegação até a oferta.
3. Enviar `begin_checkout` ao GA4 mantendo o mesmo nome recomendado de comércio eletrônico.
4. Usar `begin_checkout` no Google Ads e na Meta apenas como início de checkout, nunca como compra confirmada.
5. Configurar a compra definitiva pelo Pixel/API da Hotmart ou pela página pós-compra apropriada.

## Atribuição

O botão principal mantém o parâmetro `bid` do checkout e encaminha os parâmetros recebidos pela URL da LP, incluindo UTMs, `gclid` e `fbclid`, desde que não substituam um parâmetro já existente no link da Hotmart.
