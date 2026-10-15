# Ağ Kavramları ve Ağ Türleri

## 1. Ağ Nedir?

Bilgisayar ağı, cihazların birbirine bağlanarak veri paylaşmasını ve iletişim kurmasını sağlayan sistemdir.

Örneğin bir evde bilgisayar, telefon ve yazıcı aynı ağa bağlanabilir. Böylece cihazlar iletişim kurabilir ve ortak kaynakları kullanabilir.

### Ağlar Neden Kullanılır?

- **Veri paylaşımı:** Dosyaların cihazlar arasında aktarılması.
- **Kaynak paylaşımı:** Yazıcı ve depolama alanı gibi kaynakların ortak kullanılması.
- **İletişim:** Cihazların ve uygulamaların birbirleriyle veri alışverişi yapması.
- **Merkezi yönetim:** Kurumlarda kullanıcıların, cihazların ve erişim izinlerinin yönetilmesi.

## 2. Ağın Temel Bileşenleri

Bir ağda cihazların iletişim kurabilmesi için farklı bileşenler birlikte çalışır.

- **Uç cihazlar (End Devices):** Bilgisayar, sunucu, telefon gibi veriyi gönderen veya alan cihazlardır.
- **Ağ arayüzü (Network Interface):** Cihazın ağa bağlanmasını sağlar.
- **İletim ortamı (Transmission Medium):** Verinin taşındığı Ethernet kablosu, fiber optik kablo veya kablosuz ortamdır.
- **Ağ cihazları (Network Devices):** Switch ve router gibi cihazlar, verinin doğru hedefe iletilmesine yardımcı olur.
- **Protokoller (Protocols):** Cihazların nasıl iletişim kuracağını belirleyen kurallardır.

**Örnek:** Bilgisayarından aynı ağdaki bir sunucuya veri gönderdiğinde ağ arayüzün, iletim ortamı ve ilgili protokoller birlikte çalışır.

## 3. Ağ Türleri

Ağlar, kapsadıkları alan ve kullanım amaçlarına göre farklı türlere ayrılır.

### PAN — Personal Area Network

Kişisel cihazları kısa mesafede birbirine bağlar.

**Örnek:** Telefon ile Bluetooth kulaklık arasındaki bağlantı.

### LAN — Local Area Network

Ev, ofis veya okul gibi sınırlı bir alandaki cihazları birbirine bağlar.

**Örnek:** Bir ofisteki bilgisayarların, yazıcıların ve sunucuların bağlı olduğu ağ.

### WLAN — Wireless Local Area Network

Cihazların Wi-Fi gibi kablosuz teknolojilerle yerel ağa bağlanmasını sağlar.

**Örnek:** Evdeki Wi-Fi ağı.

WLAN, kablosuz bağlantı kullanan bir LAN türüdür. Temel fark, bağlantının kablosuz teknoloji üzerinden kurulmasıdır.

### MAN — Metropolitan Area Network

Bir şehir veya metropol içerisindeki farklı ağları birbirine bağlar.

**Örnek:** Aynı şehirdeki farklı kampüslerin ağlarının birbirine bağlanması.

### WAN — Wide Area Network

Geniş coğrafi alanlarda bulunan ağları birbirine bağlar. Şehirler, ülkeler veya kıtalar arasındaki iletişimi sağlar.

**Örnek:** Bir şirketin Ankara ve İstanbul ofislerini birbirine bağlayan ağ.

### SAN — Storage Area Network

Sunucuların merkezi depolama sistemlerine erişmesini sağlayan özel amaçlı ağ mimarisidir.

**Örnek:** Bir veri merkezindeki birden fazla sunucunun merkezi depolama sistemini kullanması.

### Ağ Türlerinin Karşılaştırılması

| Ağ türü | Temel özellik | Örnek |
|---|---|---|
| PAN | Kişisel cihazlar arasında kısa mesafeli iletişim | Bluetooth |
| LAN | Sınırlı bir alandaki cihazları bağlar | Ofis ağı |
| WLAN | Kablosuz yerel ağ bağlantısı sağlar | Wi-Fi |
| MAN | Şehir içerisindeki ağları bağlar | Kampüsler arası bağlantı |
| WAN | Geniş coğrafi alanlardaki ağları bağlar | Uzak ofis ağları |
| SAN | Sunucu ve depolama sistemlerini bağlar | Veri merkezi depolama ağı |

**Önemli:** PAN, LAN, MAN ve WAN temel olarak ağın kapsadığı alanla ilişkilidir. WLAN bağlantı teknolojisini, SAN ise depolama amacına yönelik özel bir ağ mimarisini ifade eder.

## 4. Internet, Intranet ve Extranet

Bu üç kavram, ağların kimlere açık olduğu ve hangi amaçla kullanıldığıyla ilgilidir.

- **Internet:** Dünya genelindeki bağımsız ağların birbirine bağlanmasıyla oluşan küresel ağ sistemidir.
- **Intranet:** Bir kurumun kendi kullanıcılarına sunduğu özel ağ ve hizmetlerdir.
- **Extranet:** Bir kurumun belirli kaynaklarını yetkilendirilmiş dış kullanıcılarla paylaşmasını sağlayan yapıdır.

**Örnek:** Bir şirketin herkese açık web sitesi Internet üzerinden erişilebilir. Yalnızca çalışanların kullandığı iç portal Intranet kapsamında olabilir. Tedarikçilerin sınırlı erişim sağladığı portal ise Extranet örneğidir.

## 5. Ağların Siber Güvenlik Açısından Önemi

Bir ağın yapısını bilmek, cihazların nasıl iletişim kurduğunu ve hangi kaynaklara erişebildiğini anlamayı sağlar.

Pentest çalışmalarında bu bilgi şu alanlarda kullanılır:

- **Network Reconnaissance:** Ağdaki cihazların ve hizmetlerin belirlenmesi.
- **Network Segmentation:** Ağın farklı bölümlere ayrılarak erişimin sınırlandırılması.
- **Access Control:** Kullanıcıların ve cihazların hangi kaynaklara erişebileceğinin belirlenmesi.
- **Attack Surface:** Bir sistemin saldırıya açık olabilecek noktalarının anlaşılması.

**Örnek:** Bir kurumun çalışan ağı ile misafir Wi-Fi ağının birbirinden ayrılması, misafir cihazlarının kurum içindeki hassas sistemlere doğrudan erişmesini engellemeye yardımcı olur.

