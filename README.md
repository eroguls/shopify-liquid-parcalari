# shopify-liquid-parcalari

Shopify temaları için küçük, açıklamalı Liquid bölüm ve parçaları. Her dosyanın başında ne işe
yaradığı, hangi parametreleri aldığı ve nasıl çağrıldığı yazılı (LiquidDoc). Hepsi her değişiklikte
Shopify’ın [Theme Check](https://shopify.dev/docs/storefronts/themes/tools/theme-check) aracıyla
denetlenir.

Bu parçaların bir kısmı [saliherogul.com](https://saliherogul.com) blogundaki yazılarda örnek
olarak geçiyor; yazı, parçanın neden böyle yazıldığını anlatıyor.

## Parçalar

| Dosya | Ne yapar | Yazı |
| --- | --- | --- |
| [`sections/bilgi-bandi.liquid`](sections/bilgi-bandi.liquid) | Başlık, metin blokları ve uygulama blokları (@app) alan en küçük Online Store 2.0 bölümü | [Online Store 2.0 nedir?](https://saliherogul.com/blog/online-store-2-0-nedir) |
| [`snippets/urun-bilgileri.liquid`](snippets/urun-bilgileri.liquid) | Meta alan ve metaobject’ten malzeme ile beden tablosu; boş alan hiç yazılmaz | [Metafields ile yönetilebilir içerik](https://saliherogul.com/blog/shopify-metafields-ile-yonetilebilir-icerik) |
| [`snippets/urun-gorselleri.liquid`](snippets/urun-gorselleri.liquid) | İlk görsel öncelikli, diğerleri tembel yüklenen duyarlı ürün görselleri | [Görsel optimizasyonu](https://saliherogul.com/blog/shopify-gorsel-optimizasyonu) |
| [`snippets/urun-yapisal-veri.liquid`](snippets/urun-yapisal-veri.liquid) | Her varyantı ayrı Offer olarak işaretleyen Product JSON-LD | [Yapısal veri](https://saliherogul.com/blog/shopify-yapisal-veri) |
| [`snippets/breadcrumb-yapisal-veri.liquid`](snippets/breadcrumb-yapisal-veri.liquid) | Ana sayfa › koleksiyon › ürün BreadcrumbList JSON-LD | |
| [`snippets/indirim-orani.liquid`](snippets/indirim-orani.liquid) | Üstü çizili fiyattan “%20 indirim” rozeti | |
| [`snippets/stok-durumu.liquid`](snippets/stok-durumu.liquid) | “Son 3 ürün”, “Ön sipariş”, “Tükendi” metinleri | |
| [`snippets/ucretsiz-kargo-cubugu.liquid`](snippets/ucretsiz-kargo-cubugu.liquid) | Ücretsiz kargo eşiğine kalan tutar ve ilerleme çubuğu | |

## Kullanım

1. Dosyayı temanızda aynı klasöre kopyalayın (`snippets/` ya da `sections/`).
2. Parçayı ilgili bölümden çağırın; dosyanın başındaki `@example` satırı hazır çağrıyı gösterir:

```liquid
{% render 'indirim-orani', variant: product.selected_or_first_available_variant %}
```

3. Bölümler (`sections/`) tema düzenleyicide **Bölüm ekle** listesinde görünür.

Önce temanın bir kopyasında deneyin. Yapısal veri parçalarını eklemeden önce sayfa kaynağında
`application/ld+json` arayın: tema ya da bir uygulama aynı işaretlemeyi zaten üretiyorsa ikinci
bir tanım eklemeyin.

Parçalar bilerek stilsiz bırakıldı; sınıf adları (`.indirim-orani`, `.stok-durumu--az` …) temanızın
CSS’iyle biçimlendirilir. Metinler Türkçe ve doğrudan yazılı; çok dilli bir mağazada temanın
`locales` dosyalarına taşıyın.

## Denetim

```bash
npm install
npm run check
```

`.theme-check.yml`, Shopify’ın önerilen kurallarını kullanır. Tek fark: bu depo bir kütüphane
olduğu için “hiçbir yerden çağrılmayan parça” uyarısı kapalı. `locales/` klasörü yalnızca Theme
Check’in tema yapısını tanıması için var.

## Lisans

MIT · [Salih Eroğul](https://saliherogul.com), bağımsız Shopify geliştiricisi.
