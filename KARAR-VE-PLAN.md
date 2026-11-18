# AI Prompt Studio — Karar ve Plan (17 Kasım 2026)

Bu belge DEVIR-NOTU-v2.md'nin devamıdır. Yeni sohbet önce devir notunu, sonra bunu okusun.

## Karar

**Daraltılmış A** onaylandı (Görev 1 tamamlandı).

- Ticari beklenti bırakıldı; ürün tecrübe ve vitrin ürünü.
- Ürün tamamen ücretsiz (canlıda `enabled: false`, 17 Kasım 2026).
- Gumroad ürünü silinmiyor ve yayından kaldırılmıyor: **fiyat $0+ ("istediğin kadar öde")** yapılıyor. Gerekçe: eski linkler (LinkedIn yorumları, videolar) ölü sayfaya gitmiyor, destek olmak isteyen için kapı açık kalıyor, ücretsiz "satın alma"lar ilgi sinyali veriyor. Koşul: Gumroad sayfa metni ve teslim içeriği "uygulama ücretsiz, anahtar gerekmiyor" diye güncellenir; uygulamanın içine Gumroad linki geri konmaz.
- Hesap, ürün, `productId` ve koddaki lisans bloğu yerinde kalır. Talep oluşursa kilit `enabled: true` ile geri açılabilir.
- "Daraltılmış" = saat tavanı (ürüne ~18 saat, tasarım kimliği ayrı bütçe), yeni özellik yok, Show HN'den 14 gün sonra karar noktası.
- B (API ile dönüştürme) önerilmedi: ücretsiz ChatGPT/Claude ile aynı işte yarışır.

## Karara temel olan veri (16 Kasım 2026)

- Cloudflare, botlar hariç, son 30 gün: 50 ziyaret (günde ~1,7). INP örneği 20, yani en fazla 20 etkileşimli oturum.
- Netlify 24 saat: 57 görüntüleme, 37'si ABD, 2'si Türkiye; 404 listesi bot taraması. İnsan trafiği sunucu isteklerinin kabaca 30'da 1'i.
- Ücretli satış: sıfır.
- CLS kırmızı değil: %75 iyi, %25 "iyileştirilmeli". Kaynak `html>body>main.shell>div.composer`, 0,125.
- LCP iyi (P75 1.520 ms); sürenin çoğu ilk sunucu yanıtı (984 ms). Küçük örneklem.

## Plan

| # | Adım | Bitti sayılır | Süre | Nerede | Model |
|---|---|---|---|---|---|
| 1 | Ücretsize çevir, Gumroad'u $0+ yap | Canlıda 6 araç kilitsiz; `productId` satırı yerinde; Gumroad fiyatı $0+, sayfa metni güncel | 1 sa | claude.ai projesi | Sonnet 5.5 |
| 2 | Kişisel tasarım kimliği (Görev 2) | 2-3 yönden biri seçildi; Design System kaydedildi | 4-5 sa (ayrı bütçe) | claude.ai projesi | Fable 5.2 |
| 3 | Kullanılabilirlik değerlendirmesi ve maket | Maket onaylandı; `/` ve `/app` ayrımı kararı verildi | 3 sa | claude.ai projesi | Opus 5.5 (Fable Pro'da yok) |
| 4 | GitHub reposu, Netlify bağlantısı, yönlendirme | Otomatik yayın çalışıyor; netlify.app adresi .com'a 301 veriyor; canonical etiketi var | 2 sa | Claude Code | Sonnet 5.5 |
| 5 | Yeni tasarımı uygula, CLS'i düzelt, indekslenebilir metni ekle | Canlı site makete uyuyor; `div.composer` kayması giderildi | 7 sa | Claude Code | Opus 5.5 |
| 6 | Canlı kontrol | 9 dil, 2 tema, mobil, 10 AI düğmesi elle denendi; Cloudflare ölçüyor | 1 sa | Claude Code | Sonnet 5.5 |
| 7 | LinkedIn gönderisi | Metin onaylandı, mesai dışında paylaşıldı | 1,5 sa | claude.ai projesi | Opus 5.5 |
| 8 | Show HN | Başlık ve ilk yorum hazır, gönderildi, yorumlar yanıtlandı | 2 sa | claude.ai projesi | Opus 5.5 |
| 9 | Karar noktası (Show HN + 14 gün) | Cloudflare verisine bakıldı; dondur ya da yeniden değerlendir kararı yazıldı | 0,5 sa | claude.ai projesi | Opus 5.5 (Fable Pro'da yok) |

Sıra notları: Adım 4, 5'ten önce. Adım 7 ile 8 arasında birkaç gün bırakılır (trafik kaynakları ayrışsın).

## Adım 9 eşiği (öneri, kıyas verisine dayanmıyor)

14 günde ikisi birlikte olursa "yeniden değerlendir", aksi halde dondur:

- Türkiye dışından en az 300 insan ziyareti ve bunların en az üçte birinde etkileşim.
- Tanımadık kişilerden en az 5 kendiliğinden geri bildirim ya da özellik isteği.

Ek sinyal: Gumroad'daki $0+ ürününü alanların sayısı ve ödeme yapanlar.

## Açık notlar

- LinkedIn gönderisi için önerilen açı: "güncelledim, artık ücretsiz" yerine "ilk ticari denemeden ne öğrendim" (aynı ürünün üçüncü paylaşımı olacağı için). Karar Adım 7'de.
- Tarayıcı konsolu hâlâ "LIVE selling mode" yazıyor; Adım 5'te düzeltilecek.
- Koddaki iki değişiklik (Adım 1): `LICENSE.enabled: false` ve `buildChrome()` içinde `$("footCta").style.display = gatingOn() ? "" : "none";`.

## Adım 2 sonucu: tasarım kimliği "Bant" (17 Kasım 2026)

- Dört yön gösterildi. A (Defter), B (Teknik resim), C (Editoryal) beğenilmedi: "AI izi olmasın ama ilkel de görünmesin, şık olsun". Seçilen: **D — Bant**.
- Bant, Mubea web şablonunun iskeletinden esinlenir (koyu üst bant + ince vurgu çizgisi, tek satır bölüm çubuğu, hap düğmeler, yumuşak köşeli kart, açık/koyu düğmesi) ama Mubea'ya özgü hiçbir şeyi taşımaz: arka plan deseni, ürün görseli, logo, lacivert + amber yok.
- Palet: varsayılan **petrol** (yeşile çalan), ikinci palet **mavi** (Mubea şablonundaki açık mavi ve koyu tonlara yakın, projeye göre seçilir). Her birinin açık ve koyu görünümü var: `petrol-acik`, `petrol-koyu`, `mavi-acik`, `mavi-koyu`. Vurgu: mercan `#e8704a`.
- Yazı: Bricolage Grotesque (başlık), Instrument Sans (metin), JetBrains Mono (rakam).
- Kayıtlar (claude.ai artifact):
  - Design System "Bant — Kemal Beydilli kişisel tasarım sistemi": https://claude.ai/artifact/PKdhyzERATqCnd8jT2tjW1 (27 renk, 4 tema, 11 yazı stili, 5 bileşen örneği: UstBant, Dugme, Cip, Kart, Tablo)
  - Yön maketleri tuvali "Kişisel tasarım kimliği — 3 yön": https://claude.ai/artifact/4sYpSSEUEjVuc9KwE1eH2N (D — Bant · Uygulama ve D — Bant · Rapor çerçeveleri Adım 3 için başlangıç)
- Adım 3'e taşınan istek: not yazma alanı geniş olmalı (ilk maketlerde dar bulundu; D maketinde ekranın yarısı).

## Adım 3: kullanılabilirlik değerlendirmesi ve maket (18 Kasım 2026)

### Bulgular (canlı dosya + ekran görüntüleri)

Yüksek öncelik:
1. Adım 2'deki elle düzenleme, soldaki her tuş/seçim değişikliğinde sessizce siliniyor (`renderPrompt()` `promptOut.value`'yu eziyor). Geçmişten geri yüklenen komut da ilk tuşta gidiyor.
2. Şablonlar ve "Örnek yükle" yazılmış metni onaysız eziyor; şablon başka araca sessizce geçiyor.
3. 10 AI düğmesi üç katmanda ~550 px; son kullanılan AI hatırlanmıyor.
4. Mobilde gönder düğmeleri iki 350 px alanın altında kalıyor.

Orta: seçim kutuları yerine hap düğme; "Hiçbiri" → "Fark etmez"; çıktı dili en üste; karşılama paneli ~280 px; Genel komutta "İçerik/Veri" tek satır; etiketler seçim kutularına bağlı değil, sekmelerde ok tuşu yok, ikincil metin kontrastı ~3,1:1 (AA 4,5:1).

Görsel kimlik: Space Grotesk + Inter, radyal parıltı, parlayan noktalı mono başlıklar, gradyanlı "AI", "9 ✦ LANG" rozeti. Satış kalıntıları (SETUP BEFORE SELLING yorumu, PRO modalı, konsol mesajı) Adım 5'te temizlenecek.

CLS kök nedeni (güven: yüksek): karşılama paneli HTML'de `hidden` gelip JS ile açılıyor ve `div.composer`'ı ~280 px itiyor; sekmeler ve şablon satırı da JS ile doluyor. Çözüm: statik HTML ya da önceden ayrılmış yer.

### Kararlar

- **`/` ve `/app` ayrılmıyor.** Tek sayfa: uygulama üstte, altında statik İngilizce bilgi bölümü (About, How it works, Privacy, 5 SSS, footer) ve sayfada `h1`. Güven: orta-yüksek.
- **Logo değişmiyor**, mevcut logo kalıyor (Kemal, 18 Kasım).

### Maket

Tuval "AI Prompt Studio — yeni arayüz maketi (Bant)": https://claude.ai/artifact/Xh9Xmd2gC8uMWXu6rFiVcu — 4 çerçeve:
- Masaüstü · Açık (etkileşimli: sekmeler, hap düğmeler, şablonlar, düzenleme işareti, AI seçimi, geçmiş sekmesi çalışıyor; komut gerçek kurallarla oluşuyor)
- Masaüstü · Koyu ("Düzenlendi" durumu açık)
- Mobil · 390 px (altta sabit Gönder/Kopyala, ayarlar tek satırda katlanır)
- Bilgi bölümü (EN, indekslenecek metin)

Maketteki tasarım kararları:
- Karşılama paneli yok; 3 adım + 60 sn tanıtım bağlantısı bölüm çubuğunda.
- Not alanı ~%55; çıktı dili ilk satır; ayarlar hap düğme.
- Şablonlar yalnızca not alanı boşken görünür.
- Komut elle düzenlenince "Düzenlendi" + "Yeniden oluştur"; soldaki değişiklik komutu ezmez.
- Tek ana eylem: son kullanılan AI'ya gönder (açılır liste) + Kopyala; diğer AI'lar "Otomatik doldurur" / "Aç ve yapıştır" hap satırlarında; tıklanan AI ana düğmeye geçer.
- Geçmiş komut kartında sekme. 9 ✦ LANG, Gumroad düğmesi, PRO modalı yok.

## Adım 4: GitHub + Netlify (18 Kasım 2026)

- Repo: **https://github.com/beydillik/aiprompt-studio** (herkese açık, dal `main`). Claude GitHub App bu repoya yetkili; Claude Code oturumundan push çalışıyor.
- İlk commit `a726906`: canlı dosya (Netlify'dan indirilen, Adım 1 değişiklikleri dahil) + `<head>` içinde `<link rel="canonical" href="https://aiprompt-studio.com/">`, `_redirects` (netlify.app → .com, `301!`, http ve https), `netlify.toml` (derleme yok, yayın kökü `.`), `README.md`.
- Netlify sitesi `aiprompt-studio` (site id `65725662-081a-4201-9906-70f947780197`) repoya bağlandı. İlk otomatik yayın `6afdeada…` 18 Kasım 21:13'te yayında: `manual_deploy: false`, commit `a726906`, "2 redirect rules processed, without errors".
- **Sürükle-bırak dönemi bitti.** Bundan sonra canlı dosyanın tek kaynağı repodaki `index.html`; projedeki `index (1).html` eski (Adım 1 öncesi), temel alınmamalı.
- Doğrulama sınırı: Claude oturumunun ağ izni aiprompt-studio.com ve netlify.app'e erişmiyor; 301 ve canonical kontrolü tarayıcıdan elle yapılır.

## Durum

- Adım 1: kod canlıda ve gizli sekmede kontrol edildi (17 Kasım 2026). Kalan: Gumroad fiyatını $0+ yapmak ve sayfa metnini güncellemek (Kemal'de).
- Adım 2: tamamlandı.
- Adım 3: değerlendirme ve `/`–`/app` kararı tamam; maket tuvalde (18 Kasım 2026).
- Adım 4: tamamlandı (18 Kasım 2026). Tarayıcıdan doğrulandı: netlify.app adresi .com'a dönüyor (301), canonical etiketi sayfa kaynağında var.
- Adım 5: tamamlandı. `main`'e birleştirildi (`a57356d`), canlıda (18 Kasım 2026). Yerel ölçüm (sayfa 8 KB'lık parçalarla yavaş yüklenerek): CLS masaüstü 0,156 → 0,014, mobil 0,466 → 0,000.
- Adım 6: tamamlandı (18 Kasım 2026, Kemal elle). aiprompt-studio.com yeni tasarımla açılıyor; netlify.app → .com yönlendirmesi ve canonical çalışıyor; 9 dil, 2 tema, mobil, 10 AI düğmesi denendi; Cloudflare ölçüyor.
- Adım 6 sonrası düzeltme (18 Kasım 2026): alttaki bilgi bölümü (About, How it works, Privacy, SSS) seçilen arayüz diline çevriliyor (`T4`, 27 metin × 9 dil). Kaynak HTML İngilizce kalır, indeksleme için. Türkçe dışındaki çeviriler ana dili konuşan biri tarafından kontrol edilmedi.
- Sonraki: Adım 7 (claude.ai projesi, Opus 5.5) — LinkedIn gönderisi. Açı kararı "Açık notlar"daki öneriyle başlar.
