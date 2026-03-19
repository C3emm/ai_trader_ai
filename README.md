# ai_trader_ai
# 🔮 Pro Trader AI - V15.0 (Oracle Mode)

Bu proje, finansal piyasalarda (Kripto ve Borsa) **LSTM (Long Short-Term Memory)** tabanlı derin öğrenme mimarisi kullanarak 30 günlük fiyat trendi tahmini yapan gelişmiş bir "Oracle" analiz aracıdır.

## 🚀 Öne Çıkan Özellikler

* **10 Yıllık Derin Veri Analizi:** `yfinance` API aracılığıyla son 10 yılın günlük (1D) verilerini analiz ederek uzun vadeli piyasa paternlerini öğrenir.
* **Hibrit Teknik İndikatör Seti:** Sadece fiyat verisiyle yetinmez; **RSI, MACD, ATR** ve **Golden Cross (SMA 50/200)** gibi kritik teknik indikatörleri girdi (feature) olarak işler.
* **LSTM Derin Öğrenme Modeli:** Zaman serisi verilerindeki "uzun vadeli bağımlılıkları" (long-term dependencies) yakalayan çift katmanlı LSTM mimarisi kullanır.
* **Zaman Serisi Çapraz Doğrulama:** Veriyi rastgele bölmek yerine, zaman akışına uygun 3-Fold Cross-Validation ile gerçekçi bir "Backtest" başarı oranı sunar.
* **İnteraktif Projeksiyon:** Plotly kütüphanesi ile 30 gün sonrasına dair görsel bir hedef yönü ve güven seviyesi grafiği oluşturur.

## 🛠️ Teknik Yığın (Tech Stack)

| Bileşen | Teknoloji | Kullanım Amacı |
| :--- | :--- | :--- |
| **Dil** | Python 3.10+ | Ana geliştirme dili |
| **AI/ML** | TensorFlow & Keras | LSTM Model tasarımı ve eğitimi |
| **Veri Analizi** | Pandas & NumPy | Veri temizleme ve özellik mühendisliği |
| **Görselleştirme** | Plotly | İnteraktif finansal grafikler |
| **Veri Kaynağı** | YFinance | Gerçek zamanlı borsa ve kripto verisi |

---

## 🧠 Model Mimarisi (Technical Deep Dive)

Model, finansal zaman serilerinin gürültülü yapısıyla başa çıkmak için şu katmanlarla optimize edilmiştir:

1.  **Lookback Window (60 Gün):** Model, her 30 günlük tahmin için geçmiş 60 günlük periyodu bir "bellek" (context) olarak kullanır.
2.  **LSTM Layers:** 128 ve 64 birimlik iki katmanlı yapı, piyasadaki karmaşık ve doğrusal olmayan hareketleri öğrenir.
3.  **Regularization:** `%40 Dropout` ve `BatchNormalization` katmanları ile modelin geçmiş verilere aşırı uyum sağlaması (overfitting) engellenir.
4.  **Binary Classification:** Model, fiyatın net değerini tahmin etmek yerine "30 gün sonraki fiyat bugünkünden yüksek mi olacak?" sorusuna (0 veya 1) odaklanarak sinyal kalitesini artırır.



---

## 💻 Kurulum ve Kullanım

1.  **Depoyu Klonlayın:**
    ```bash
    git clone [https://github.com/KULLANICI_ADIN/ai-trading-app.git](https://github.com/KULLANICI_ADIN/ai-trading-app.git)
    cd ai-trading-app
    ```

2.  **Bağımlılıkları Yükleyin:**
    (Kod, eksik kütüphaneleri çalışma anında otomatik yükleme özelliğine sahiptir ancak manuel yükleme önerilir:)
    ```bash
    pip install yfinance pandas numpy scikit-learn tensorflow plotly
    ```

3.  **Uygulamayı Başlatın:**
    ```bash
    python ai_trading_app.py
    ```

---

## 📊 Örnek Çıktı

Uygulama çalıştırıldığında iki ana sonuç üretir:
* **Terminal Özeti:** Seçilen varlığın 30 gün sonraki yükseliş/düşüş ihtimali ve modelin test verilerindeki başarı puanı (Accuracy).
* **İnteraktif Grafik:** Güncel fiyatın sonuna eklenen yıldız ikonu ve kesikli çizgilerle AI'nın 30 günlük "Hedef Yönü" görselleştirilir.

---

## ⚠️ Yasal Uyarı
Bu yazılım bir **eğitim ve mühendislik projesidir.** Üretilen sonuçlar tamamen yapay zeka tahminlerine dayalıdır ve **kesinlikle yatırım tavsiyesi niteliği taşımaz.** Finansal kararlarınızı kendi analizleriniz doğrultusunda veriniz.
