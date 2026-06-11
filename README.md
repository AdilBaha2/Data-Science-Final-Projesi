# 📊 E-Ticaret Dinamik Fiyatlandırma ve Yapay Zeka Odaklı Kâr Optimizasyonu

**YBS 4. Sınıf Python ile Veri Bilimi Dönem Sonu Projesi**

Bu proje, bir e-ticaret platformundaki ürünlerin talep tahmin süreçlerini makine öğrenmesi algoritmalarıyla modellemenin ötesine geçerek; şirket içi maliyet yapıları ve rakip fiyat verilerini harmanlayarak kuruma en yüksek net kârı sağlayacak **"Optimum Dinamik Fiyatlama Kararını"** simüle etmek amacıyla kurgulanmıştır.

---

## 🛠️ Zorunlu Proje Kriterleri ve Gerçekleştirimler

Proje, ders dökümantasyonunda belirtilen tüm kritik gereksinimleri harfiyen karşılamaktadır:

1. **Veri Harmanlama (Data Fusion - %20):** Tek bir hazır veri seti kullanılmamıştır. Şirket içi operasyonel satış verileri (*Amazon Sale Report*) ile pazar bazlı rakip fiyat verileri (*Flipkart Fiyatları*), benzersiz ürün kodları (SKU) ve kategoriler üzerinden `pandas.merge()` yöntemiyle akıllıca harmanlanmıştır.
2. **İş Mantığına Dayalı Özellik Mühendisliği (%20):** Modelin tahmin gücünü artırmak amacıyla tamamen işletme mantığına dayalı 3 yeni stratejik değişken türetilmiştir:
   * `Indirim_Oranı`: Sepette uygulanan fiili indirim yüzdesi.
   * `Fiyat_Oranı`: Şirket fiyatının rakip fiyatına olan rasyosu.
   * `Hafta_Sonu_Mu`: Tüketici davranışlarındaki dönemselliği yakalayan zaman serisi metriği.
3. **Keşifçi Analiz (EDA) ve Açıklanabilirlik (XAI - %20):** Eğitilen **Random Forest Regressor** modelinin kararları SHAP (SHapley Additive exPlanations) kütüphanesiyle görselleştirilerek "kara kutu" olmaktan çıkarılmıştır. `Indirim_Oranı` ve `Fiyat_Oranı` değişkenlerinin model üzerindeki baskın etkileri SHAP grafikleriyle ispatlanmıştır.
4. **Maliyet/Fayda Simülasyonu ve ROI (%40):** Modelin ürettiği talep tahminleri doğrultusunda %0 ile %30 arasında indirim senaryoları çalıştırılmıştır. Fiyat esnekliği analiz edilerek, agresif indirimlerin hacmi artırsa da kâr marjını eriterek şirketi fırsat zararına uğrattığı, maksimum kârlılık için liste fiyatının korunması (%0 İndirim) gerektiği simülasyon motoruyla kanıtlanmıştır.

---

## 📈 Model Performansı ve Başarım Oranı

Tahminleme problemi için geliştirilen Random Forest modelimiz, test setinde **%80'in üzerinde bir R-Kare ($R^2$) başarım oranına** ulaşmıştır. Bu sayede, ödev dökümanında belirtilen **minimum %70 başarım oranı kriterini** başarıyla geride bırakmıştır.

---

## 📁 Depo (Repository) İçeriği

* `FinalÖdevi.ipynb`: Veri ön işleme, harmanlama, özellik mühendisliği, modelleme, SHAP analizi ve kâr optimizasyonu simülasyon kodlarının tamamını içeren Jupyter Notebook dosyası.
* `YÖNETİCİ ÖZETİ RAPORU.pdf`: Projenin iş problemini, veri kaynaklarını, teknik bulgularını ve şirkete sağladığı finansal katma değeri içeren, üst yönetime hitap eden profesyonel rapor dökümanı.
* `Veri Kaynakları`: Model eğitiminde ve harmanlamada kullanılan ham veri dökümanları.

---

## 🚀 Projeyi Yerelde Çalıştırma

Gerekli kütüphaneleri kurmak için:
```bash
pip install pandas numpy scikit-learn xgboost shap matplotlib seaborn
