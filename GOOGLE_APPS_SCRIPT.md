# Google Sheets Entegrasyonu - Google Apps Script Kodu

İletişim formu verilerini Google Sheets'e kaydetmek için Google Apps Script kullanılır.

## 📋 Kurulum Adımları

### 1. Google Sheets Oluşturma

1. [Google Sheets](https://sheets.google.com) adresine gidin
2. Yeni bir spreadsheet oluşturun
3. İlk satıra başlıkları ekleyin:
   - A1: `Tarih`
   - B1: `Ad Soyad`
   - C1: `E-posta`
   - D1: `Telefon`
   - E1: `Konu`
   - F1: `Mesaj`

### 2. Google Apps Script Oluşturma

1. Google Sheets'te **Extensions** → **Apps Script** seçin
2. Açılan editöre aşağıdaki kodu yapıştırın:

```javascript
function doPost(e) {
  try {
    // Veriyi parse et
    const data = JSON.parse(e.postData.contents);
    
    // Google Sheets'i aç
    const sheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();
    
    // Yeni satıra verileri ekle
    const row = [
      new Date(data.timestamp), // Tarih
      data.name,                // Ad Soyad
      data.email,               // E-posta
      data.phone || '',         // Telefon
      data.subject || '',       // Konu
      data.message              // Mesaj
    ];
    
    sheet.appendRow(row);
    
    // Başarılı yanıt döndür
    return ContentService.createTextOutput(
      JSON.stringify({success: true})
    ).setMimeType(ContentService.MimeType.JSON);
    
  } catch (error) {
    // Hata durumunda log tut
    Logger.log('Hata: ' + error.toString());
    
    return ContentService.createTextOutput(
      JSON.stringify({success: false, error: error.toString()})
    ).setMimeType(ContentService.MimeType.JSON);
  }
}
```

### 3. Web App Olarak Dağıtma

1. Apps Script editöründe **Deploy** → **New deployment** seçin
2. **Select type** bölümünden **Web app** seçin
3. Ayarları yapılandırın:
   - **Description**: İletişim Formu Entegrasyonu
   - **Execute as**: Me (your-email@gmail.com)
   - **Who has access**: Anyone (herkes erişebilir, güvenlik için form validation eklenebilir)
4. **Deploy** butonuna tıklayın
5. Açılan pencerede **Web app URL**'yi kopyalayın
6. Bu URL'yi `.env` dosyasındaki `PUBLIC_GOOGLE_SHEETS_WEB_APP_URL` değişkenine yapıştırın

### 4. İlk Test

1. Apps Script editöründe **Run** → **doPost** çalıştırın (hata alabilirsiniz, normal)
2. İzinleri onaylayın
3. `.env` dosyasını güncelleyin
4. Formu test edin

## 🔒 Güvenlik Notları

- Google Apps Script URL'si herkese açık olacak
- İsteğe bağlı olarak basit bir API key kontrolü eklenebilir
- Gelişmiş güvenlik için Google Cloud Functions veya başka bir backend çözümü kullanılabilir

## 📝 Örnek Kod (API Key ile Güvenlik)

Daha güvenli bir çözüm için:

```javascript
function doPost(e) {
  try {
    // API Key kontrolü (isteğe bağlı)
    const API_KEY = 'YOUR_SECRET_API_KEY'; // .env'den alabilirsiniz
    const data = JSON.parse(e.postData.contents);
    
    // API key kontrolü
    if (data.apiKey !== API_KEY) {
      return ContentService.createTextOutput(
        JSON.stringify({success: false, error: 'Unauthorized'})
      ).setMimeType(ContentService.MimeType.JSON);
    }
    
    // Google Sheets'i aç
    const sheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();
    
    // Yeni satıra verileri ekle
    const row = [
      new Date(data.timestamp),
      data.name,
      data.email,
      data.phone || '',
      data.subject || '',
      data.message
    ];
    
    sheet.appendRow(row);
    
    return ContentService.createTextOutput(
      JSON.stringify({success: true})
    ).setMimeType(ContentService.MimeType.JSON);
    
  } catch (error) {
    Logger.log('Hata: ' + error.toString());
    return ContentService.createTextOutput(
      JSON.stringify({success: false, error: error.toString()})
    ).setMimeType(ContentService.MimeType.JSON);
  }
}
```
