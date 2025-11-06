Тайшыбай Медициналық Орталығы (TMO) — TMO SITE v3 (Бағалар, Галерея, Аналитика, Онлайн жазылу)
================================================================

НЕ ІСТЕУ КЕРЕК:
1) Файлды ашу: index.html — екі рет шертіп браузерде.
2) Бағалар/мәтіндер: index.html ішінен тікелей түзетіңіз.
3) Галерея: assets/gallery/photo1.png … photo8.png файлын өз фотоларыңызға ауыстырыңыз.

ANALYTICS (GA4):
- index.html ішінде GA4_ID айнымалысын өзіңіздің өлшем бірлік ID-мен ауыстырыңыз: G-XXXXXXXXXX → G-XXXXXXX

META PIXEL:
- index.html ішінде META_PIXEL_ID мәнін ауыстырыңыз: 000000000000000 → нақты Pixel ID.

ОНЛАЙН БРОНЬ (Google Sheets арқылы):
A) Google Sheets жасаңыз (бағандар: timestamp, name, phone, service, date, message, source).
B) Apps Script жасаңыз (Extensions → Apps Script), төмендегі кодты қойыңыз:
----------------------------------------------------------------------------
function doPost(e) {
  const sheetId = "PASTE_SHEET_ID";
  const ss = SpreadsheetApp.openById(sheetId);
  const sh = ss.getSheets()[0];
  const data = JSON.parse(e.postData.contents);
  sh.appendRow([new Date(), data.name, data.phone, data.service, data.date, data.message, data.source]);
  return ContentService.createTextOutput("OK").setMimeType(ContentService.MimeType.TEXT);
}
----------------------------------------------------------------------------
C) Deploy: Deploy → New deployment → type: Web app → "Anyone" немесе "Anyone with the link" → URL шығады.
D) index.html ішіндегі GAS_ENDPOINT мәнін сол URL-ге ауыстырыңыз.

ТЕЛЕГРАМ АЛЬТЕРНАТИВАСЫ (кеңес):
- Браузерден тікелей бот токенін қолдану қауіпсіз емес (токен ашылып қалады). Сондықтан Google Apps Script арқылы Telegram-ға прокси жасаңыз (secure). Қажет болса, дайын код үлгісін жіберемін.

ҚОЛДАНЫЛАТЫН ФАЙЛДАР:
- index.html — сайт
- assets/logo.svg — логотип
- assets/doctor1.png, assets/doctor2.png — дәрігер фотосы (плейсхолдер)
- assets/gallery/photo1..8.png — галерея фотолары (плейсхолдер)
