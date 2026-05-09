# Exploratory-Data-Analysis-EDA-and-visualization-pipeline-for-stellar-classification.
Gelişmiş Yıldız Sınıflandırması ve Astroinformatik EDA Boru Hattı


Advanced Stellar Classification & Astroinformatics EDA Pipeline
Bu depo, tablosal astronomik veri setlerinin (Stellar Data) istatistiksel analizini ve görselleştirilmesini sağlayan kapsamlı bir veri mühendisliği çalışmasını içerir. Proje, ham veriyi işleyip anlamlı astrofiziksel çıktılara dönüştüren, Python ve JavaScript entegrasyonlu bir mimariye sahiptir.


## Sistem Mimarisi ve Veri Hattı (Data Pipeline)

* Proje sadece bir analiz dosyası değil, aşağıdaki aşamalardan oluşan bir veri işleme hattıdır:
* Data Ingestion: Google Drive tabanlı dış kaynaklardan (CSV) dinamik veri çekimi.
* Preprocessing & Schema Validation: Pandas kullanılarak verinin tip kontrolü, eksik veri analizi ve tanımlayıcı istatistiklerin (std, mean, quartiles) çıkarılması.
* Scientific Visualization Layer: Matplotlib ve Seaborn kütüphaneleriyle katmanlı (layered) görselleştirme.
* Automated Export Engine: Üretilen çıktıların JavaScript Blob API kullanılarak birleştirilmesi ve kernel üzerinden asenkron olarak yerel diske aktarılması.



## Bilimsel Analiz ve Teknik Detaylar

### 1. Astrofiziksel Parametre Korelasyonu
Veri seti üzerindeki analizler, yıldızların evrimsel süreçlerini temsil eden Hertzsprung-Russell (HR) Diyagramı mantığına dayanır.

* Luminosity (L/Lo) vs. Temperature (K): Yıldızların ana kol üzerindeki konumlarını belirlemek için logaritmik ölçeklendirme ve saçılım analizi uygulanmıştır.

* Absolute Magnitude (Mv) Analizi: Yıldızın gerçek parlaklığı ile sıcaklığı arasındaki ters orantı, veri kümeleme (clustering) görselleştirmeleriyle doğrulanmıştır.
<img width="2048" height="2048" alt="licensed-image" src="https://github.com/user-attachments/assets/25f8f303-6422-42a2-ab8b-292fd1ec9370" />


### 2. Görselleştirme Stratejisi (Visualization Matrix)

| Analiz Türü | Kullanılan Yöntem | Teknik Tercih Nedeni |
| :--- | :--- | :--- |
| **Univariate (Tek Değişkenli)** | KDE (Kernel Density Estimate) | Sıcaklık ve parlaklık dağılımındaki olasılık yoğunluğunu pürüzsüzleştirmek için. |
| **Bivariate (İki Değişkenli)** | JointPlot / Scatter Plot | İki fiziksel parametre arasındaki korelasyon katsayısını görsel olarak doğrulamak için. |
| **Categorical (Kategorik)** | Box & Violin Plots | Yıldız tiplerine göre fiziksel eşik değerlerini (outliers) ve varyansı saptamak için. |


### 3. Teknik İnovasyon: JavaScript-Python Bridge
Notebook içerisinde, standart files.download() yönteminden daha gelişmiş bir dışa aktarım tekniği kullanılmıştır:

* Python tarafında oluşturulan tüm .png dosyaları ZipFile kütüphanesiyle bellek üzerinde (buffer) paketlenir.

* JavaScript Entegrasyonu: google.colab.kernel.comms kullanılarak Python kernel'ı ile tarayıcı arasında bir kanal açılır.

* Veriler Uint8Array formatında parçalara (chunks) bölünerek JavaScript tarafındaki bir Blob nesnesine aktarılır ve otomatik download tetiklenir. Bu, büyük veri setlerinde ve toplu görsel çıktılarda bellek yönetimini optimize eder.

## 4. Teknoloji Yığını (Stack)
* Language: Python 3.7.12
* Data Analysis: NumPy, Pandas
* Scientific Plotting: Seaborn (v0.11+), Matplotlib (Pyplot)
* Frontend Integration: JavaScript (ES6+), Google Colab Comm API
* Data Source: Stellar Type Dataset (Astroquery uyumlu yapı)

## Akademik ve Profesyonel Arka Plan
İskenderun Teknik Üniversitesi (İSTE) Bilgisayar Mühendisliği son sınıf öğrencisiyim. Gömülü sistemler (Embedded Systems) ve GNC (Guidance, Navigation, and Control) sistemleri üzerine olan uzmanlığımı, astroenformatik disipliniyle birleştirerek veri odaklı astronomi projeleri geliştiriyorum.

*  Hedef: Gözlemevlerinin (TUG/DAG) veri işleme birimlerinde, gerçek zamanlı veri analizi ve gömülü yazılım mimarileri üzerinde katkı sağlamak.

Bu çalışma, astronomi verilerinin mühendislik prensipleriyle nasıl işlenebileceğini gösteren profesyonel bir portfolyo ürünüdür.


#Reprodüksiyon (Nasıl Çalıştırılır?)
**1. Ortam Hazırlığı:** 
```bash
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
pip install pandas numpy matplotlib seaborn


