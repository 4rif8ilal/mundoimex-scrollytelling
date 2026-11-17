# Mundoimex · Scrollytelling

**Canlı demo → [4rif8ilal.github.io/mundoimex-scrollytelling](https://4rif8ilal.github.io/mundoimex-scrollytelling/)**

Mundoimex Gümrük Müşavirliği A.Ş. için kaydırmayla ilerleyen, tek sayfalık interaktif kurumsal web deneyimi. Bir yükün denizden gümrüğe yolculuğunu, şirketin hizmetlerini ve tarihçesini tek bir kesintisiz sahne akışıyla anlatır. Logo, renkler ve içerik [mundoimex-web](https://4rif8ilal.github.io/mundoimex-web/) sitesinden alınmıştır.

## Sahneler

| # | Sahne | Ne oluyor |
|---|---|---|
| 0 | **Açılış & Hero** | Su yukarıdan ekranı doldurup ufka çekilir; navbar yerine oturur. Solda konteyner gemisi, sağda kargo uçağı. |
| 1 | **Deniz & Hava** | Gemi limana yanaşır, uçak paraşütle bir hava konteyneri bırakır; konteyner gemideki Mundoimex konteynerinin üstüne kilitlenir. |
| 2 | **Liman & Kara** | Liman vinci birleşik bloğu tırın dorsesine indirir; tır otoyolda gümrüğe ilerler. |
| 3 | **Gümrük** | Saha görevlisi konteynerden mühürlü kutuyu alır, tarayıcı kemerden geçer, gişe ekranında "E-GÜMRÜK ONAYLANDI" yanar. |
| 4 | **Tarihçe** | Kamera kutuya dalar, kutu 3D olarak 90° döner ve kraft yüzeyi tarihçe tuvaline dönüşür (masaüstünde yatay, mobilde dikey akış). |
| 5 | **İletişim** | Kutu yüzeyi dev tipografili footer'a genişler: teklif formu, kariyer başvurusu, adres ve iletişim. |

## Özellikler

- **Tek dosya, sıfır kurulum:** Her şey `index.html` içinde; tüm görseller elle çizilmiş inline SVG, logo gömülü.
- **Akıllı teklif formu** (3 adım: hizmet → rota & yük → firma) ve **kariyer başvurusu** paneli; gönderimde e-posta uygulaması hazır mesajla açılır.
- **TR / EN** dil geçişi, sayfa yenilenmeden; sahne içi yazılar dahil.
- **Liquid Glass** WhatsApp butonu (SVG kırılma filtresi + çok katmanlı cam).
- Sol kenarda **rota göstergesi (HUD)**; navbar'dan uzak sahnelere tüm animasyonu oynatmadan **doğrudan geçiş**.
- **Responsive:** telefon, dikey tablet, yatay telefon ve masaüstü için ayrı kamera kurgusu.
- **Erişilebilirlik:** `prefers-reduced-motion` desteği, klavye ile modal gezinme (odak tuzağı, Esc).

## Teknoloji

- [GSAP 3.12](https://gsap.com/) + ScrollTrigger: tek pin, tek master timeline (sahneler arası çakışma yok)
- [Lenis](https://lenis.darkroom.engineering/): yumuşak kaydırma
- Vanilla JS, CSS 3D transforms, inline SVG
- Yazı tipleri: Archivo, JetBrains Mono (Google Fonts)

Kütüphaneler CDN üzerinden yüklenir; derleme adımı yoktur.

## Yerelde çalıştırma

`index.html` dosyasını tarayıcıda açmanız yeterli. İsterseniz basit bir sunucuyla da açabilirsiniz:

```bash
npx serve .
```

## Mimari notlar

- **Kamera:** Tüm dünya tek bir 5200×900 SVG'dir; kamera bir nesne (`f`, `s`, `fy`, `vc`, `lz`) olarak tween edilir ve tek bir `transform` ile uygulanır. Kutuya zoom, sahne ölçeğinden ayrı bir log çarpanıyla (`lz`) yönetilir.
- **Performans:** Kamera her zaman GPU katmanında (`translate3d`) çalışır; gümrük ve zoom bölümünde görünmeyen gruplar gizlenir ve döngü animasyonları durdurulur.
- **Deterministik timeline:** Tüm tween'ler `fromTo` + `immediateRender: false` ile yazılmıştır; böylece `invalidateOnRefresh` sonrası başlangıç değerleri bozulmaz.

---

© Mundoimex Gümrük Müşavirliği A.Ş. · Tam Zamanında
