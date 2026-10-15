# OSI ve TCP/IP Modelleri, Kapsülleme ve Veri Birimleri

Bir bilgisayar başka bir bilgisayara veri gönderdiğinde, bu verinin yalnızca gönderilmesi yeterli değildir. Verinin nasıl taşınacağı, hangi hedefe ulaşacağı ve yerel ağ üzerinden nasıl iletileceği de belirlenmelidir.

Ağ iletişiminde bu görevler farklı katmanlar tarafından gerçekleştirilir. **OSI ve TCP/IP modelleri**, bu görevleri anlamamızı sağlayan katmanlı modellerdir.

## 1. OSI ve TCP/IP Modelleri

### OSI Modeli

OSI modeli, ağ iletişimini yedi katmana ayırır. Her katman, iletişimin farklı bir yönünü açıklar.

| Katman | Temel görevi |
|---|---|
| Application | Uygulamaların ağ hizmetlerini kullanmasını sağlar. HTTP ve DNS bu katmanla ilişkilidir. |
| Presentation | Verinin biçimlendirilmesi, kodlanması ve şifrelenmesi gibi işlevleri açıklar. |
| Session | İletişim oturumlarının yönetilmesini açıklar. |
| Transport | Verinin iki uç arasında taşınmasını yönetir. TCP ve UDP burada bulunur. |
| Network | IP adresleme ve farklı ağlar arasında yönlendirmeyle ilgilenir. |
| Data Link | Yerel ağdaki iletişimi, MAC adreslerini ve frame yapılarını ele alır. |
| Physical | Bitlerin kablo, fiber veya radyo sinyalleri üzerinden iletilmesini açıklar. |

Presentation ve Session katmanları, iletişimin belirli işlevlerini anlamamızı sağlayan kavramsal katmanlardır. Gerçek sistemlerde bu işlevler ayrı katmanlar hâlinde bulunmak zorunda değildir.

### TCP/IP Modeli

TCP/IP modeli, internet iletişimini daha pratik şekilde açıklayan dört katmanlı bir modeldir.

| Katman | Temel görevi |
|---|---|
| Application | HTTP, DNS ve SSH gibi uygulama protokollerini kapsar. |
| Transport | TCP ve UDP üzerinden veri aktarımını yönetir. |
| Internet | IP adresleme ve paketlerin ağlar arasında yönlendirilmesiyle ilgilenir. |
| Network Access | Yerel ağ iletişimini ve fiziksel iletimi kapsar. |

OSI ve TCP/IP modellerinin temel amacı aynıdır: Ağ iletişiminin farklı görevlerini birbirinden ayırmak.

OSI bu görevleri yedi katmanda açıklar. TCP/IP ise bazı görevleri birleştirerek dört katman kullanır.

## 2. Katmanlar Birlikte Nasıl Çalışır?

Bir web sitesine bağlandığımızı düşünelim.

Önce tarayıcı, sunucuya göndermek istediği isteği oluşturur. Bu veri taşınmak üzere Transport katmanına iletilir. Ardından IP katmanı, verinin kaynak ve hedef IP adresleriyle ilişkilendirilmesini sağlar. Data Link katmanı ise verinin mevcut yerel ağ üzerinden iletilmesine yardımcı olur.

Son olarak veri fiziksel ortamdan gönderilir.

Bu süreçte her katmanın farklı bir sorumluluğu vardır:

- **Application:** Hangi uygulama protokolüyle iletişim kuruluyor?
- **Transport:** Veri iki uç arasında nasıl taşınacak?
- **Internet / Network:** Paket hangi IP hedefine gönderilecek?
- **Network Access / Data Link:** Veri mevcut yerel ağ üzerinden nasıl iletilecek?
- **Physical:** Bitler fiziksel ortamdan nasıl taşınacak?

Buradaki önemli nokta, her katmanın tüm iletişimi tek başına yönetmemesidir. Her biri kendi görevini yerine getirir ve veriyi sonraki aşamaya aktarır.

## 3. Kapsülleme Nedir?

Bir uygulamanın oluşturduğu veri, ağ üzerinden gönderilmeden önce farklı katmanlardan geçer. Her katman, kendi görevini yerine getirebilmek için veriye gerekli kontrol bilgilerini ekler.

Bu işleme **Encapsulation**, yani kapsülleme denir.

Örneğin TCP kullanılarak bir HTTP isteği gönderildiğini düşünelim.

Önce uygulama verisi vardır. TCP bu veriye taşıma bilgilerini ekler. IP katmanı, kaynak ve hedef IP adreslerini içeren bilgileri ekler. Ethernet gibi yerel ağ teknolojisi de frame oluşturmak için gerekli bilgileri ekler.

Böylece veri gönderilmeye hazır hâle gelir.

```text
Uygulama verisi
      ↓
TCP bilgileri eklenir
      ↓
IP bilgileri eklenir
      ↓
Ethernet bilgileri eklenir
      ↓
Ağ üzerinden gönderilir
```

Bu bilgilerin eklenme amacı, her katmanın kendi işini yapabilmesidir. Örneğin IP bilgileri paketin ağlar arasında doğru hedefe yönlendirilmesine yardımcı olurken, Ethernet bilgileri frame'in mevcut yerel ağda iletilmesine yardımcı olur.

Kapsülleme sırasında verinin etrafına yalnızca rastgele bilgiler eklenmez. Her katmanın eklediği bilgiler, o katmanın iletişim görevleri için kullanılır.

## 4. Segment, Packet ve Frame Nedir?

Veri farklı katmanlardan geçerken farklı isimlerle anılır. Bu isimler, verinin hangi katmanda ele alındığını anlamamızı sağlar.

### Data

Uygulamanın göndermek istediği asıl içeriktir. Örneğin bir HTTP isteği veya mesaj içeriği olabilir.

### Segment

Veri TCP katmanında işlendiğinde TCP segmenti olarak adlandırılır. TCP header içerisinde port numaraları, sıra numaraları ve diğer taşıma bilgileri bulunabilir.

UDP kullanıldığında ise **UDP datagramı** terimi kullanılır.

### Packet

IP katmanı, IP header bilgilerini ekleyerek verinin IP paketleri üzerinden taşınmasını sağlar. Kaynak ve hedef IP adresleri bu katmandaki önemli bilgilerdendir.

### Frame

Data Link katmanı, IP paketini yerel ağda iletilebilecek bir frame içinde taşır. Ethernet frame'i kaynak ve hedef MAC adresleri gibi bilgiler içerebilir.

Bu nedenle TCP üzerinden gönderilen bir verinin yolculuğu basitçe şöyle gösterilebilir:

```text
Data
  ↓
TCP Segment
  ↓
IP Packet
  ↓
Ethernet Frame
```

**Segment, Packet ve Frame birbirinden bağımsız üç ayrı mesaj değildir.** Aynı iletişimin farklı katmanlarda ele alınan yapılarıdır. Her katman kendi başlığıyla birlikte bu veriyi işler.

Bu gösterim TCP ve Ethernet örneğidir. UDP kullanıldığında Segment yerine Datagram terimi kullanılır; farklı yerel ağ teknolojilerinde frame yapısı da değişebilir.

## 5. Kapsül Açma Nedir?

Veri hedef bilgisayara ulaştığında göndericinin yaptığı işlemlerin tersi gerçekleşir.

Alıcı, gelen frame'i işler. İçindeki IP paketini değerlendirir ve paketin ilgili üst katmana aktarılmasını sağlar. TCP kullanılıyorsa TCP katmanı da kendi bilgilerini değerlendirerek veriyi uygun uygulamaya iletir.

Bu işleme **Decapsulation**, yani kapsül açma denir.

```text
Gönderici

Data
  ↓
Segment
  ↓
Packet
  ↓
Frame
  ↓
Ağ üzerinden iletim


Alıcı

Frame
  ↓
Packet
  ↓
Segment
  ↓
Data
```

Bu şema, sürecin temel mantığını gösterir. Gerçek iletişimde her katman kendi bilgilerini işler; örneğin Ethernet frame'i alıcıdaki her durumda hedef uygulamaya kadar taşınmaz.

Kısacası gönderici veriyi taşınmaya hazırlar, alıcı ise katmanların eklediği bilgileri işleyerek veriyi doğru uygulamaya ulaştırır.

## 6. Hepsini Bir Örnekle Birleştirelim

Tarayıcıdan bir web sunucusuna istek gönderdiğimizi düşünelim.

**1. Uygulama veriyi oluşturur.**

Tarayıcı, HTTP isteğini hazırlar.

**2. TCP taşıma bilgilerini ekler.**

TCP, kaynak ve hedef portları gibi bilgileri kullanır. TCP bağlantısı kullanılıyorsa verinin güvenilir biçimde aktarılmasına yönelik mekanizmalar da devrededir.

**3. IP katmanı hedefi belirler.**

Kaynak ve hedef IP adreslerini içeren bir IP paketi oluşturulur. Router'lar, hedef IP adresine ve yönlendirme tablolarına göre paketin hangi yöne gönderileceğine karar verir.

**4. Data Link katmanı frame oluşturur.**

Paket, mevcut bağlantıda kullanılacak yerel ağ bilgileriyle bir frame içinde taşınır. Ethernet kullanılan bir ağda bu bilgiler MAC adreslerini içerir.

**5. Veri fiziksel ortamdan gönderilir.**

Frame, fiziksel katmanda bitlerin iletimiyle temsil edilen sinyaller üzerinden taşınır.

Sunucuya ulaştığında katmanlar kendi bilgilerini işler ve uygulama verisi ilgili yazılıma teslim edilir.

## 7. Bu Konuların Birbirleriyle İlişkisi

Bu üç konu aslında aynı sürecin farklı yönlerini açıklar:

- **OSI ve TCP/IP modelleri**, iletişimin hangi görevlerden oluştuğunu gösterir.
- **Encapsulation**, verinin gönderilirken her katmanda nasıl hazırlandığını açıklar.
- **Segment, Packet ve Frame**, verinin farklı katmanlardaki yapılarını adlandırır.
- **Decapsulation**, alıcı tarafında bu yapıların nasıl işlendiğini açıklar.

Bu mantığı anlamak, daha sonra TCP/UDP, IP adresleme, routing ve Wireshark ile paket analizi konularını öğrenmeyi kolaylaştırır.
