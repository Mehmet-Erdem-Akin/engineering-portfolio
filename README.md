# Engineering Portfolio

Astro.js + Tailwind CSS ile oluşturulmuş modern, hızlı ve SEO uyumlu portfolio sitesi.

## 🚀 Kurulum

```bash
npm install
```

### Environment Variables

Projeyi çalıştırmadan önce `.env` dosyası oluşturun:

```bash
cp .env.example .env
```

`.env` dosyasını düzenleyin ve gerekli değişkenleri ekleyin:

```env
PUBLIC_GOOGLE_SHEETS_WEB_APP_URL=https://script.google.com/macros/s/YOUR_SCRIPT_ID/exec
```

**Google Sheets Web App URL Nasıl Alınır?**

Detaylı kurulum için `GOOGLE_APPS_SCRIPT.md` dosyasına bakın. Kısaca:

1. Google Sheets oluşturun
2. Extensions → Apps Script'e gidin
3. `GOOGLE_APPS_SCRIPT.md` dosyasındaki kodu yapıştırın
4. Deploy → New deployment → Web app
5. Oluşan URL'yi `.env` dosyasına ekleyin

## 📝 Geliştirme

Geliştirme sunucusunu başlatmak için:

```bash
npm run dev
```

Tarayıcıda `http://localhost:4321` adresini açın.

## 🏗️ Build

Production build için:

```bash
npm run build
```

Build çıktısı `dist/` klasöründe oluşur. Bu klasörü Nginx sunucusuna yükleyebilirsiniz.

## 📁 Proje Yapısı

```
/
├── public/          # Statik dosyalar (görseller, favicon, vb.)
├── src/
│   ├── components/  # Astro bileşenleri
│   ├── layouts/     # Layout şablonları
│   └── pages/       # Sayfalar (routing otomatik)
├── astro.config.mjs # Astro konfigürasyonu
└── tailwind.config.mjs # Tailwind CSS konfigürasyonu
```

## 🎨 Özellikler

- ⚡ Astro.js ile sıfır JavaScript runtime overhead
- 🎨 Tailwind CSS ile modern ve responsive tasarım
- 📱 Mobile-first yaklaşım
- 🔍 SEO optimizasyonu
- 🚀 Statik site generation (SSG)
- 💰 Düşük hosting maliyeti (Nginx ile)
- 📊 Google Sheets ile form verilerini otomatik kaydetme

## 📄 Sayfalar

- `/` - Ana sayfa
- `/about` - Hakkımızda
- `/products` - Ürünler
- `/contact` - İletişim

## 📸 Ekran Görüntüleri

### Ana Sayfa
![Ana Sayfa](public/FireShot%20Capture%20003%20-%20Ana%20Sayfa%20-%20Kompres%C3%B6r%20Bayi%20-%20%5Blocalhost%5D.png)

### Ürünler Sayfası
![Ürünler Sayfası](public/FireShot%20Capture%20002%20-%20%C3%9Cr%C3%BCnler%20-%20Kompres%C3%B6r%20Bayi%20-%20%5Blocalhost%5D.png)

### İletişim Sayfası
![İletişim Sayfası](public/FireShot%20Capture%20005%20-%20%C4%B0leti%C5%9Fim%20-%20%5Blocalhost%5D%20%281%29.png)

### Hakkımızda Sayfası
![Hakkımızda Sayfası](public/FireShot%20Capture%20006%20-%20Hakk%C4%B1m%C4%B1zda%20-%20%5Blocalhost%5D.png)

## 📊 Google Sheets Entegrasyonu

İletişim formu, Google Apps Script kullanarak form verilerini Google Sheets'e otomatik olarak kaydeder.

### Hızlı Kurulum

1. Google Sheets oluşturun ve başlık satırını ekleyin (Tarih, Ad Soyad, E-posta, Telefon, Konu, Mesaj)
2. `GOOGLE_APPS_SCRIPT.md` dosyasındaki adımları takip edin
3. Google Apps Script'i Web App olarak deploy edin
4. Web App URL'sini `.env` dosyasına ekleyin

Detaylı kurulum için: [GOOGLE_APPS_SCRIPT.md](./GOOGLE_APPS_SCRIPT.md)

## 🔧 Teknolojiler

- [Astro](https://astro.build/)
- [Tailwind CSS](https://tailwindcss.com/)
- TypeScript
- Google Apps Script (Form entegrasyonu)
