# Cafe Sales Dashboard

Kafe satış məlumatları əsasında hazırlanmış interaktiv dashboard. Məlumatlar əvvəlcə Excel-də təmizlənib, PivotTable ilə analiz edilib, sonra dashboard-a çevrilib.

## Dashboard

📄 [Dashboard-a bax (PDF)](dashboard%20screen.pdf)

## Dataset

- **Mənbə:** Kaggle, Dirty Cafe Sales
- **Həcm:** 10 000 əməliyyat, 8 sütun (Transaction ID, Item, Quantity, Price Per Unit, Total Spent, Payment Method, Location, Transaction Date)
- **Dövr:** 2023
- Dataset qəsdən "çirkli" hazırlanıb: ERROR, UNKNOWN, boş xanalar və səhv formatlar var.

## Məlumatın təmizlənməsi (Excel)

| Sütun | Problem | Həll |
|---|---|---|
| Item | ERROR, UNKNOWN, boş (969 xana) | Hamısı `Unknown` edildi |
| Quantity | Mətn dəyərləri və boşlar | Mümkün olanlar `Total Spent ÷ Price` ilə hesablandı |
| Price Per Unit | Mətn kimi qalmış rəqəmlər, `1,5` qiyməti tarixə çevrilmişdi | Format düzəldildi, boşlar `Total ÷ Quantity` ilə bərpa edildi |
| Total Spent | `1,5 / 4,5 / 7,5` tarix nömrəsinə çevrilmişdi (205 xana) | Düzgün rəqəm yazıldı, boşlar `Quantity × Price` ilə hesablandı |
| Payment Method | ERROR, UNKNOWN, boş (3 178 xana) | `Unknown` edildi |
| Location | ERROR, UNKNOWN, boş (3 961 xana) | `Unknown` edildi |
| Transaction Date | ERROR, UNKNOWN | Boş edildi |

Dublikat yoxlanıldı: Transaction ID unikaldır, dublikat tapılmadı. Hər addım Excel faylındakı `Cleaning_Log` sheet-ində qeyd olunub.

## Dashboard-da nələr var

- **KPI-lar:** Ümumi gəlir (88,95K), Əməliyyat sayı (10K), Orta çek (8,90)
- Məhsul üzrə gəlir
- Ödəniş üsulu üzrə bölgü
- Məkan üzrə gəlir (In-store / Takeaway)
- Aylar üzrə gəlir dəyişimi
- Sifariş ölçüsünə (Quantity) görə gəlir
- Məhsul filtri (slicer)

## Əsas nəticələr

- **Ən çox gəlir gətirən məhsul:** Salad (17 320)
- **Ən çox satılan məhsul:** Coffee (3 536 ədəd), amma gəliri aşağıdır, çünki qiyməti ucuzdur
- **Ən yüksək / ən aşağı gəlirli ay:** Yanvar-Iyun arasında ən yüksək gəlir İyun ayındadır (7 350), ən aşağı Fevraldır (6 633,5)
- **Ən çox seçilən ödəniş üsulu:** Digital Wallet (2 291 əməliyyat)
- **In-store və Takeaway:** Əhəmiyyətli fərq yoxdur (27 127 və 26 487,5, fərq təxminən 2,4%)
- **Orta əməliyyat məbləği:** 8,90. Ən yüksək Salad (15), ən aşağı Cookie (3)
- **Məhsul və ödəniş üsulu arasında** əlaqə tapılmadı, fərqlər təsadüfidir
- Sifariş ölçüsü artdıqca gəlir artır

> **Qeyd:** Ödəniş üsulunun 31,8%-i, məkanın 39,6%-i naməlumdur, ona görə bu hissələr üzrə nəticələr qismən etibarlıdır.

## İstifadə olunan alətlər

- Excel (məlumat təmizləmə, formullar, PivotTable, PivotChart)
- Dashboard vizuallaşdırma

