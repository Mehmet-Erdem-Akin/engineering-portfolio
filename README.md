# Engineering Portfolio

Astro.js + Tailwind CSS ile oluşturulmuş modern, hızlı ve SEO uyumlu portfolio sitesi.

## 🚀 Kurulum

```bash
npm install
```

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

## 📄 Sayfalar

- `/` - Ana sayfa
- `/about` - Hakkımızda
- `/products` - Ürünler
- `/contact` - İletişim

## 🔧 Teknolojiler

- [Astro](https://astro.build/)
- [Tailwind CSS](https://tailwindcss.com/)
- TypeScript
