GarantiVp
=========

Garanti Bankası Sanal Pos İstemcisi .Net Framework üzerinde C# kullanılarak geliştirilmştir. Garanti Bankasının yeni 
sanal pos sistemine göre düzenlenmiştir. OOS_PAY ödeme tipi için düzenlenmiştir.

Oğuzhan<br/>
oguzhan.info<br/>
aspsrc@gmail.com

Kullanım
=========

Satış:
```C#
            var _pay = new Client()
                         .Test().Company(terminalId, merchandId, "PROVAUT", Password)
                                            .Customer("apsrc@gmail.com", "192.168.0.1")
                                            .CreditCard("1145213658974525", "555", 5, 2015)
                                            .Order(Guid.NewGuid().ToString("N"))
                                            .Amount(100, CurrencyCode.TRL)
                                            .Sales();

            Assert.AreEqual("00", _pay.Transaction.Response.Code);
            Assert.AreEqual("Approved", _pay.Transaction.Response.Message);
        }
```

Taksitli Satış:
```C#
            var _pay = new Client().Test()
                            .Company(terminalId, merchandId, "PROVAUT", Password)
                                .Customer("apsrc@gmail.com", "192.168.0.1")
                                .CreditCard(credit_card_number, credit_card_cvv2, credit_card_month, credit_card_year)
                                .Order(Guid.NewGuid().ToString("N"))
                                .Amount(95)
                                .Installment(2)
                                .Sales();
                                
```

İptal:
```C#
            var _pay = new Client()
                                    .Test()
                                    .Company(terminalId, merchandId, "PROVRFN", Password)
                                    .Customer("apsrc@gmail.com", "192.168.0.1")
                                    .Order(orderId)
                                    .Amount(95)
                                    .Cancel("405014619754");
```

İade:
```C#
            var _pay = new Client()
                                    .Test()
                                    .Company(terminalId, merchandId, "PROVAUT", Password)
                                    .Customer("apsrc@gmail.com", "192.168.0.1")
                                    .Order("405014619754")
                                    .Amount(95)
                                    .Refund();
```

Fonksiyonlar
=========

<h6>
Desteklenmesi planlanan fonksiyonların listesi aşağıdaki gibidir. Üstü çizli olanlar implementasyonu ve test'i tamamlanmış fonksiyonlardır.

Tamamlanmamış herhangi bir fonksiyonu siz geliştirebilir ve bu projeye katkı sağlayabilirsiniz.
</h6>

Adres Gönderimi<br/>
Bekleyen Tekrarlayan Satış Tutar Değişikliği<br/>
Bekleyen Tekrarlı Satışların İptali<br/>
Bin sorgulama<br/>
Bonus kullanımı ve sorgulama<br/>
BonusPay<br/>
BonusPay Bonus Sorgu<br/>
BonusPay İşlem Sorgu<br/>
Bonus Kullanımlı Satış<br/>
Bonus sorgulama<br/>
Firma Bonus<br/>
Kampanya Kodu Sorgulama<br/>
Peşinatlı Taksitli Satış<br/>
~~Satış (sales)~~<br/>
~~Taksitli İşlem~~<br/>
Tarih Aralığı İşlem Sorgu<br/>
Tekrarlı Satış<br/>
Ticari Kart İşlemi<br/>
Tüketici Kredisi<br/>
Tüketici Kredisi Sorgulama<br/>
Türkcell Cüzdan<br/>
~~Ön.Oto Kapamanın İptali~~<br/>
~~Önotorizasyon~~<br/>
~~Ötelemeli Satış~~<br/>
Özel Alan Gönderimi<br/>
Ürün Bilgisi Gönderimi<br/>
~~İade~~<br/>
~~İadenin İptali~~<br/>
~~İptal~~<br/>
İşlem Detay Sorgu<br/>
İşlem Sorgu<br/>
DCC<br/>
Ekstre Doğrulama<br/>
Günsonu sorgulama<br/>
Kampanya Kodu Sorgulama<br/>
Peşinatlı Taksitli Satış<br/>
QR Pay<br/>
Tarih Aralığı İşlem Sorgu<br/>
~~TCKN_Doğrulama~~<br/>


Test Ortamı
=========

Raporlama için:<br/>
https://sanalposwebtest.garanti.com.tr
<br/>
Provizyon için:<br/>
https://sanalposprovtest.garanti.com.tr/VPServlet<br/>
https://sanalposprovtest.garanti.com.tr/servlet/gt3dengine<br/>

<br/>
Mağazalar dışarıdan erişirken gelecekleri ip ler:

*194.29.209.225* (raporlama sayfaları)<br/>
*194.29.209.226* (provizyon)<br/>

hosts dosyasına Provizyon denemeleri sırasında *194.29.209.226 sanalposprovtest.garanti.com.tr*
 
Raporlar ekranı testleri sırasında *194.29.209.225  sanalposwebtest.garanti.com.tr* yazılması gerekiyor.

