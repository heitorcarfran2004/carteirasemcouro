# Moldes de Carteiras em Couro — página de vendas

Página estática, mobile-first, sem dependência de build. Basta servir a raiz.

## Rodar local

```bash
node dev/server.cjs   # http://localhost:3100
```

## Estrutura

```
index.html          página inteira (HTML + CSS + JS inline)
assets/
  mockups/          mockup do produto
  modelos/          moldes exibidos no carrossel
  carrossel/        fotos de produção
  bonus/            capas dos 4 bônus
  depoimentos/      prints de comentário
dev/server.cjs      servidor estático para preview local (ignorado no deploy)
vercel.json         forca deploy estatico, sem build
```

## Pendências antes de subir tráfego

- [ ] Trocar `SEU_PIXEL_ID` pelo ID do Meta Pixel
- [ ] Trocar `SEU_UTMIFY_ID` pelo ID da Utmify
- [ ] Trocar os 3 placeholders de checkout pelos links da Wiapy:
  - `#checkout-basico` → R$ 10,00
  - `#checkout-premium` → R$ 24,90
  - `#checkout-upsell` → R$ 16,90 (oferta do popup, precisa ser um produto separado na Wiapy)
- [ ] Substituir as imagens de `assets/` pelas próprias
- [ ] Substituir os depoimentos (prints e os 3 textos) por depoimentos próprios

## Ofertas

| Plano | Preço | Onde |
|---|---|---|
| Básico | R$ 10,00 | seção de planos e recusa do popup |
| Completo | R$ 24,90 | seção de planos |
| Completo (oferta do popup) | R$ 16,90 | popup ao clicar no básico |

## Eventos do pixel

`PageView` na carga · `ViewContent` quando a seção de planos entra na tela · `InitiateCheckout` no clique, com o valor lido do `data-valor` de cada botão.
