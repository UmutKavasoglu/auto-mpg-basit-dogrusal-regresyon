# Auto MPG Veri Seti ile Yakıt Verimliliği Tahmini

Bu proje, bir aracın **ağırlık (`weight`)** bilgisini kullanarak yakıt verimliliğini (**`mpg`**) tahmin eden bir basit doğrusal regresyon modeli geliştirmeyi amaçlamaktadır. Projenin temel hedefi, istatistiksel olarak geçerli, güvenilir ve pratik bir tahmin aracı oluşturmaktır.

## Proje Özeti

Otomotiv sektöründe yakıt verimliliği, hem tüketici kararlarını hem de çevresel düzenlemeleri etkileyen kritik bir faktördür. Bu bağlamda, araçların temel özelliklerinden yola çıkarak hızlı ve güvenilir tahminler yapabilmek büyük önem taşır.

Bu çalışma, standart bir basit doğrusal regresyon modelinin, başlangıçta veri setinin yapısı nedeniyle temel istatistiksel varsayımları sağlayamadığını ortaya koymuştur. Modelin tahmin gücünü ve istatistiksel geçerliliğini artırmak için aşağıdaki adımlar izlenmiştir:

1.  **Başlangıç Modeli ve Varsayım İhlalleri:** `mpg` ve `weight` değişkenleri arasında standart bir doğrusal regresyon modeli kuruldu. Ancak, artıkların normal dağılmadığı ve varyanslarının sabit olmadığı tespit edildi.
2.  **Veri Dönüşümü Arayışı:** Model varsayımlarını sağlamak ve doğrusal ilişkiyi güçlendirmek amacıyla bağımlı ve bağımsız değişkenler için farklı matematiksel dönüşüm kombinasyonları test edildi.
3.  **Final Modelinin Geliştirilmesi:** Varsayımları en iyi sağlayan ve en yüksek R² değerini sunan **`log(mpg) ~ sqrt(weight)`** dönüşümü seçilerek nihai model oluşturuldu.
4.  **Model Validasyonu:** Geliştirilen nihai model, daha önce ayrılan test verisi üzerinde değerlendirilerek performansı doğrulandı.

## Temel Bulgular ve Sonuçlar

Yapılan analizler sonucunda başlangıç modeli ile veri dönüşümü uygulanmış nihai model arasındaki performans farkı aşağıdaki tabloda özetlenmiştir. Tablodaki metrikler **eğitim seti** üzerinde hesaplanmıştır.

| Metrik | Başlangıç Modeli | Final Modeli | Yorum |
| :--- | :--- | :--- | :--- |
| **Eğitim R²** | 0.699 | **0.772** | Modelin veriyi açıklama gücü yaklaşık **%10.4** oranında arttı. |
| **Eğitim MAE** | 3.230 | **3.016** | Modelin tahmin hatası yaklaşık **%6.6** oranında azaldı. |
| **Normallik Varsayımı** | Sağlanmadı (p < 0.05) | **Sağlandı** (p > 0.05) | Normal dağılım varsayımı sağlandı. |
| **Sabit Varyanslılık Varsayımı** | Sağlanmadı (p < 0.05) | **Sağlandı** (p > 0.05) | Sabit varyanslılık varsayımı sağlandı. |

**Test Verisi Performansı:**

Nihai modelin test verisi üzerindeki performansı, modelin genellenebilirliğini doğrulamaktadır:
-   **R² Değeri:** **0.698**
-   **Ortalama Mutlak Hata (MAE):** **3.088 MPG**

## Model Denklemleri

-   **Başlangıç Modeli:**
    `mpg = 46.2212 - 0.0076 * weight`

-   **Dönüştürülmüş Final Modeli:**
    `log(mpg) = 5.1896 - 0.0387 * sqrt(weight)`

## Veri Seti

Bu çalışmada kullanılan **Auto MPG** veri seti, UCI Machine Learning Repository'den temin edilmiştir.

-   **Kaynak:** [UCI Machine Learning Repository: Auto MPG Data Set](https://archive.ics.uci.edu/dataset/9/auto+mpg)
