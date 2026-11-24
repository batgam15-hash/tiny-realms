# Tiny Realms — Web Sitesi ve GitHub Pages Yayınlama Rehberi

Bu klasör, **Tiny Realms** (`com.tinyrealms.roguelite`) oyunu için Google Play Console ve Google AdMob gereksinimlerini karşılayan, hiçbir harici bağımlılığı olmayan statik web sitesini içerir.

## Klasör İçeriği
- `index.html` — Oyunun tanıtım ana sayfası
- `privacy.html` — Google Play ve AdMob/UMP uyumlu **Gizlilik Politikası** (İngilizce varsayılan + `EN/TR` dil seçici)
- `terms.html` — Kullanım Koşulları
- `support.html` — Oyuncu Desteği, SSS ve Veri Silme yönergeleri
- `app-ads.txt` — Google AdMob yayıncı doğrulama dosyası (`pub-4266555286052187`)
- `.nojekyll` — GitHub Pages'in dosyaları olduğu gibi sunmasını sağlayan boş işaret dosyası
- `assets/icon.png` ve `assets/icon-round.png` — Oyun simgeleri

---

## Adım 0: Geliştirici E-postası Hazır
Tüm HTML sayfalarındaki iletişim ve destek adresi **`tinyrealms@hotmail.com`** olarak ayarlanmıştır (`index.html`, `privacy.html`, `terms.html`, `support.html`). Doğrudan yüklemeye geçebilirsin.

---

## Adım 1: GitHub'da Doğru Depo (Repository) Adını Seç — ÇOK ÖNEMLİ

Google AdMob, `app-ads.txt` dosyasını yalnızca **kök alan adında** (`https://<alan-adi>/app-ads.txt`) arar; alt klasörde (`.../tiny-realms/app-ads.txt`) bulunan dosyayı okumaz. Bu yüzden iki seçeneğin vardır:

1. **Önerilen (AdMob `app-ads.txt` dahil tam çözüm):**
   GitHub'da depo adını tam olarak **`<github-kullanici-adin>.github.io`** yap (ör. GitHub kullanıcı adın `ahmetyilmaz` ise depo adı `ahmetyilmaz.github.io` olmalı) ve görünürlüğü **Public** seç.
   - Bu durumda siten `https://<github-kullanici-adin>.github.io/` adresinde açılır ve `app-ads.txt` doğrudan `https://<github-kullanici-adin>.github.io/app-ads.txt` adresinde çalışır.
2. **Sadece Gizlilik Politikası için alt depo:**
   Eğer `<kullanici-adin>.github.io` depon zaten başka bir proje için doluysa, `tiny-realms` adında Public bir depo açabilirsin. Bu durumda `privacy.html` yine sorunsuz çalışır (`https://<kullanici-adin>.github.io/tiny-realms/privacy.html`), ancak AdMob `app-ads.txt` doğrulaması yalnızca kök depodan (`<kullanici-adin>.github.io`) veya özel alan adından yapılabilir.

---

## Adım 2: Dosyaları GitHub'a Yükle ve GitHub Pages'i Aç

### Yöntem A — Tarayıcı Üzerinden (En Kolayı)
1. GitHub'da oluşturduğun **Public** deponun içine gir.
2. **Add file → Upload files** seçeneğine tıkla *(veya "uploading an existing file" linkine bas)*.
3. `C:\Users\asust\Desktop\kod tarlası\tiny realms web` klasörünün **içindeki** her şeyi (`.nojekyll`, `app-ads.txt`, `index.html`, `privacy.html`, `terms.html`, `support.html`, `README.md` ve `assets` klasörü) seçip sürükle-bırak yap.
   - *Not: Klasörün kendisini değil, içindeki dosya ve `assets` klasörünü yükle ki `index.html` en üst dizinde yer alsın. `.nojekyll` gizli dosya göründüğü için seçerken unutma.*
4. Altta **Commit changes** butonuna bas.

### Yöntem B — Git Komut Satırı ile
```bash
cd "C:\Users\asust\Desktop\kod tarlası\tiny realms web"
git init -b main
git add .
git commit -m "Tiny Realms web site and privacy policy"
git remote add origin https://github.com/<github-kullanici-adin>/<depo-adi>.git
git push -u origin main
```

### GitHub Pages'i Aktifleştirme
1. Deponun üst menüsünden **Settings → Pages** sekmesine gir.
2. **Build and deployment → Source** altında **Deploy from a branch** seç.
3. **Branch** olarak `main` (veya `master`) ve klasör olarak **`/ (root)`** seçip **Save**'e bas.
4. 1–2 dakika bekleyip sayfayı yenilediğinde üstte sitenin canlı adresi (`https://...`) görünecektir.

---

## Adım 3: Google Play Console ve AdMob'a Yapıştırılacak Adresler

Kök depo (`https://<kullanici-adin>.github.io/`) kullandıysan adreslerin şunlardır *(alt depo kullandıysan aralarına `/<depo-adi>` eklenir)*:

1. **Google Play Console → Uygulama içeriği → Gizlilik politikası:**
   - `https://<kullanici-adin>.github.io/privacy.html`
2. **Google Play Console → Mağaza ayarları → Web sitesi (Mağaza girişi iletişim detayları):**
   - `https://<kullanici-adin>.github.io/`
3. **Google AdMob (`app-ads.txt`) doğrulaması:**
   - AdMob tarafında uygulama Play Store'da yayına alınıp eşleştirildikten sonra, Play Store mağaza ayarlarındaki geliştirici web sitenden `https://<kullanici-adin>.github.io/app-ads.txt` dosyasını otomatik tarar. Tarayıcıdan açtığında tek satır olarak şunu gördüğünden emin ol:
     ```text
     google.com, pub-4266555286052187, DIRECT, f08c47fec0942fa0
     ```
