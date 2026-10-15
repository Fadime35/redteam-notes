# Ağ Topolojileri

## 1. Ağ Topolojisi Nedir?

Ağ topolojisi (Network Topology), bir ağdaki cihazların ve bağlantıların nasıl düzenlendiğini ifade eder.

Topoloji, cihazların birbirine nasıl bağlandığını ve verilerin ağ içerisinde hangi yollar üzerinden iletilebildiğini anlamamıza yardımcı olur.

İki temel topoloji yaklaşımı vardır:

- **Fiziksel topoloji (Physical Topology):** Cihazların ve kabloların fiziksel olarak nasıl bağlandığını gösterir.
- **Mantıksal topoloji (Logical Topology):** Verilerin ağ içerisinde nasıl iletildiğini gösterir.

Fiziksel ve mantıksal topolojiler aynı olmak zorunda değildir.

## 2. Temel Ağ Topolojileri

### 2.1. Bus Topology — Veri Yolu Topolojisi

Tüm cihazların ortak bir ana kabloya bağlandığı topolojidir.

**Nasıl çalışır?**

Bir cihaz veri gönderdiğinde veri ortak kablo üzerinden ilerler. Ağdaki cihazlar verinin kendilerine ait olup olmadığını kontrol eder.

**Avantajları:**
- Az kablo gerektirir.
- Küçük ağlarda kurulumu basittir.

**Dezavantajları:**
- Ana kablodaki arıza tüm ağı etkileyebilir.
- Cihaz sayısı ve trafik arttıkça performans sorunları yaşanabilir.
- Arızanın kaynağını bulmak zor olabilir.

**Örnek:** Eski Ethernet ağlarında kullanılan ortak kablo yapısı.

### 2.2. Star Topology — Yıldız Topolojisi

Tüm cihazların merkezi bir ağ cihazına bağlandığı topolojidir. Günümüzde Ethernet tabanlı yerel ağlarda yaygın olarak kullanılır.

**Nasıl çalışır?**

Bir bilgisayar başka bir cihaza veri gönderdiğinde trafik genellikle merkezi switch üzerinden iletilir.

**Avantajları:**
- Yeni cihaz eklemek kolaydır.
- Bir bağlantı kablosunun arızalanması genellikle diğer cihazları etkilemez.
- Sorunları tespit etmek görece kolaydır.

**Dezavantajları:**
- Merkezi switch arızalanırsa ona bağlı cihazlar iletişim kuramayabilir.
- Diğer topolojilere göre daha fazla kablo gerekebilir.

**Örnek:** Bir ofisteki bilgisayarların aynı switch'e bağlanması.

### 2.3. Ring Topology — Halka Topolojisi

Cihazların halka oluşturacak şekilde birbirine bağlandığı topolojidir.

**Nasıl çalışır?**

Veri, halka üzerindeki bağlantılardan ilerleyerek hedef cihaza ulaşır. Verinin tek yönde veya çift yönde ilerlemesi kullanılan teknolojiye bağlıdır.

**Avantajları:**
- Bazı tasarımlarda veri iletimi düzenli ve öngörülebilir olabilir.
- Belirli halka teknolojileri yoğun trafik altında kontrollü erişim sağlayabilir.

**Dezavantajları:**
- Yedeklilik yoksa tek bir bağlantı veya cihaz arızası iletişimi kesebilir.
- Sorun giderme ve yeni cihaz ekleme, tasarıma bağlı olarak zor olabilir.

**Örnek:** Halka biçiminde çalışan bazı endüstriyel ağlar.

### 2.4. Mesh Topology — Örgü Topolojisi

Cihazların veya ağ düğümlerinin birden fazla bağlantı üzerinden birbirine bağlandığı topolojidir.

İki temel çeşidi vardır:

- **Full Mesh:** Her düğüm diğer tüm düğümlere doğrudan bağlıdır.
- **Partial Mesh:** Yalnızca belirli düğümler arasında birden fazla bağlantı bulunur.

**Nasıl çalışır?**

Bir bağlantı kullanılamaz hâle gelirse, uygun alternatif yollar üzerinden iletişim devam edebilir.

**Avantajları:**
- Yedeklilik sağlar.
- Bazı bağlantı arızalarına karşı dayanıklıdır.

**Dezavantajları:**
- Kurulum ve yönetim maliyeti yüksek olabilir.
- Bağlantı sayısı ve yapılandırma karmaşıklığı artabilir.

**Örnek:** Birden fazla alternatif bağlantıya sahip kurumsal ağlar.

### 2.5. Tree Topology — Ağaç Topolojisi

Cihazların ve ağ segmentlerinin hiyerarşik bir yapı içerisinde bağlandığı topolojidir.

**Nasıl çalışır?**

Ağ, ana bağlantı noktalarından alt ağlara doğru dallanır. Büyük ağlarda farklı switch grupları bu yapıda düzenlenebilir.

**Avantajları:**
- Büyük ağları düzenlemeyi kolaylaştırır.
- Ağın bölümlere ayrılmasını sağlar.
- Yeni bölümler eklenebilir.

**Dezavantajları:**
- Üst seviyedeki kritik bir cihazın arızası alt bölümleri etkileyebilir.
- Yapı büyüdükçe yönetim karmaşıklaşabilir.

**Örnek:** Bir üniversitenin ana switch üzerinden fakülte ve laboratuvar ağlarına ayrılması.

### 2.6. Hybrid Topology — Hibrit Topoloji

Birden fazla topoloji türünün aynı ağ içerisinde birlikte kullanılmasıdır.

**Nasıl çalışır?**

Örneğin her ofis kendi içinde yıldız topolojisi kullanırken, farklı ofisler birbirine örgü veya hiyerarşik bağlantılarla bağlanabilir.

**Avantajları:**
- İhtiyaca göre esnek tasarım yapılabilir.
- Farklı topolojilerin avantajları birleştirilebilir.

**Dezavantajları:**
- Tasarım ve yönetim daha karmaşık olabilir.
- Maliyet artabilir.

**Örnek:** Yıldız topolojili yerel ağların birden fazla bağlantıyla birbirine bağlandığı kurumsal ağ.

## 3. Topolojilerin Karşılaştırılması

| Topoloji | Temel özellik | Başlıca dezavantaj |
|---|---|---|
| Bus | Ortak ana kablo | Ana kablo arızası ağı etkileyebilir |
| Star | Merkezi switch veya başka bir bağlantı noktası | Merkezi cihaz arızası |
| Ring | Halka şeklinde bağlantı | Yedeklilik yoksa bağlantı arızası |
| Mesh | Birden fazla bağlantı yolu | Maliyet ve karmaşıklık |
| Tree | Hiyerarşik yapı | Üst seviye arızalarının geniş etkisi |
| Hybrid | Birden fazla topolojinin birleşimi | Yönetim karmaşıklığı |

## 4. Ağ Topolojilerinin Siber Güvenlik Açısından Önemi

Ağ topolojisini bilmek, ağdaki kritik cihazları, olası arıza noktalarını ve sistemler arasındaki bağlantıları anlamayı sağlar.

- **Ağ segmentasyonu:** Farklı sistemlerin ayrı ağ bölümlerinde tutulması, erişimin sınırlandırılmasına yardımcı olur.
- **Yedeklilik:** Alternatif bağlantılar, belirli arızaların iletişimi tamamen kesmesini önleyebilir.
- **Ağ keşfi:** Cihazlar ve bağlantılar belirlendiğinde ağın yapısı daha iyi anlaşılır.
- **Kritik noktalar:** Merkezi switch veya ana yönlendirici gibi cihazların arızası ya da ele geçirilmesi geniş çaplı etkilere yol açabilir.

**Örnek:** Bir kurumda çalışan bilgisayarları ve sunucuları ayrı ağ segmentlerine ayırmak, bir çalışanın bilgisayarı ele geçirildiğinde sunuculara doğrudan erişimi sınırlandırmaya yardımcı olur.

## 5. Önemli Noktalar

- Fiziksel topoloji, cihazların ve bağlantıların fiziksel düzenini; mantıksal topoloji ise veri iletiminin düzenini ifade eder.
- Star topolojisinde cihazlar merkezi bir noktaya bağlanır.
- Mesh topolojisi birden fazla bağlantı yolu sağlayabilir.
- Tree topolojisi hiyerarşik ağ yapısı oluşturur.
- Hybrid topoloji, farklı topolojileri bir araya getirir.
- Bir topolojinin uygunluğu maliyet, ölçek, yedeklilik ve yönetim ihtiyaçlarına bağlıdır.
