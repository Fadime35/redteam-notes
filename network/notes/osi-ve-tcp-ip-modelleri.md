# OSI ve TCP/IP Modelleri

## 1. Ağ Modelleri Nedir?

Ağ modelleri, cihazlar arasındaki iletişimin nasıl gerçekleştiğini anlamak için kullanılan katmanlı yapılardır.

Ağ iletişimi birçok farklı işlem içerir. Bu işlemleri katmanlara ayırmak, ağın nasıl çalıştığını anlamayı ve sorunları tespit etmeyi kolaylaştırır.

İki temel ağ modeli vardır:

- **OSI Model:** Ağ iletişimini yedi katmanda açıklar.
- **TCP/IP Model:** İnternet ve modern ağlarda kullanılan protokol ailesini dört katmanda ele alır.

## 2. OSI Modeli

OSI modeli, ağ iletişimini yedi katmana ayırır. Her katman belirli görevleri yerine getirir ve diğer katmanlarla birlikte çalışır.

### 7. Application — Uygulama Katmanı

Ağ hizmetlerinin uygulamalara sunulduğu katmandır.

**Örnek protokoller:** HTTP, HTTPS, DNS, SMTP.

**Örnek:** Tarayıcının bir web sunucusundan sayfa istemesi.

### 6. Presentation — Sunum Katmanı

Verilerin uygulamalar tarafından anlaşılabilecek biçime dönüştürülmesiyle ilgilenir. Veri biçimi dönüşümü, kodlama ve şifreleme gibi işlevler bu katmanla ilişkilendirilir.

**Örnek:** Verinin farklı sistemler tarafından aynı biçimde yorumlanabilmesi.

**Not:** OSI modelinde şifreleme ve veri biçimlendirme görevleri Presentation Layer ile ilişkilendirilir. Ancak gerçek ağ uygulamalarında bu işlemler farklı protokoller ve uygulamalar tarafından gerçekleştirilebilir; her zaman ayrı bir 6. katman bulunmaz.

### 5. Session — Oturum Katmanı

Uygulamalar arasındaki iletişim oturumlarının kurulması, yönetilmesi ve sonlandırılması kavramlarını ele alır.

**Örnek:** İki uygulama arasındaki iletişim oturumunun yönetilmesi.

### 4. Transport — Taşıma Katmanı

Uygulamalar arasında uçtan uca veri aktarımını sağlar. Portlar ve veri aktarımının özellikleri bu katmanla ilişkilidir.

**Örnek protokoller:** TCP ve UDP.

- TCP, güvenilir ve sıralı veri aktarımı sağlar.
- UDP, bağlantısız veri aktarımı sağlar.

### 3. Network — Ağ Katmanı

Paketlerin farklı ağlar arasında hedeflerine ulaştırılmasıyla ilgilenir.

**Örnek:** IP adresleri ve yönlendirme.

**Örnek protokol:** IP.

### 2. Data Link — Veri Bağı Katmanı

Aynı yerel ağ bağlantısı üzerindeki cihazlar arasında çerçevelerin iletilmesini sağlar.

**Örnek:** Ethernet, MAC adresleri ve switch'lerin çerçeve iletimi.

### 1. Physical — Fiziksel Katman

Bitlerin fiziksel ortam üzerinden nasıl taşındığıyla ilgilenir.

**Örnek:** Ethernet kablosu, fiber optik kablo, elektriksel sinyaller ve radyo sinyalleri.

## 3. OSI Katmanlarının Özeti

| Katman | İngilizce adı | Temel görevi |
|---|---|---|
| 7 | Application | Uygulamalara ağ hizmetleri sunmak |
| 6 | Presentation | Veri biçimi ve gösterimi |
| 5 | Session | Oturum yönetimi |
| 4 | Transport | Uçtan uca aktarım ve portlar |
| 3 | Network | IP adresleme ve yönlendirme |
| 2 | Data Link | Yerel bağlantıda çerçeve iletimi |
| 1 | Physical | Bitlerin fiziksel ortamda iletimi |


## 4. TCP/IP Modeli

TCP/IP modeli, internet iletişiminin temelini oluşturan protokolleri dört katmanda ele alır.

### 4.1. Application — Uygulama Katmanı

Uygulamaların ağ üzerinden iletişim kurmasını sağlayan protokolleri kapsar.

**Örnekler:** HTTP, HTTPS, DNS, SMTP, SSH.

TCP/IP modelinin uygulama katmanı, OSI modelindeki Application, Presentation ve Session katmanlarının işlevlerini büyük ölçüde kapsar.

### 4.2. Transport — Taşıma Katmanı

Uygulamalar arasındaki veri aktarımını yönetir.

**Örnekler:** TCP ve UDP.

Port numaraları, verinin doğru uygulamaya ulaştırılmasına yardımcı olur.

### 4.3. Internet — İnternet Katmanı

IP adresleme ve paketlerin farklı ağlar arasında iletilmesiyle ilgilenir.

**Örnekler:** IPv4, IPv6 ve ICMP.

Router'lar, IP paketlerini hedef ağa doğru yönlendirir.

### 4.4. Network Access — Ağ Erişim Katmanı

Verinin yerel ağ bağlantısı ve fiziksel iletim ortamı üzerinden taşınmasıyla ilgilenir.

**Örnekler:** Ethernet ve Wi-Fi.

Bu katman, OSI modelindeki Data Link ve Physical katmanlarının işlevlerini bir araya getirir.

## 5. OSI ve TCP/IP Modellerinin Karşılaştırılması

| OSI modeli | TCP/IP modeli |
|---|---|
| Application | Application |
| Presentation | Application |
| Session | Application |
| Transport | Transport |
| Network | Internet |
| Data Link | Network Access |
| Physical | Network Access |

OSI modeli yedi, TCP/IP modeli ise yaygın kullanılan dört katmanlı gösterimde dört katmandan oluşur.

**Temel fark:** OSI, iletişimi anlamak ve açıklamak için kullanılan referans modeldir. TCP/IP ise internet iletişiminde kullanılan protokol ailesini temel alan modeldir.

## 6. Veriler Katmanlar Arasında Nasıl İlerler?

Bir bilgisayardan web sunucusuna istek gönderildiğini düşünelim.

1. **Uygulama:** Tarayıcı bir HTTP isteği oluşturur.
2. **Taşıma:** TCP kullanılıyorsa veri, TCP segmenti içerisinde taşınır.
3. **Ağ:** TCP segmenti IP paketinin içine yerleştirilir.
4. **Veri bağı:** IP paketi, yerel bağlantıda iletilmek üzere Ethernet çerçevesine yerleştirilir.
5. **Fiziksel:** Çerçeve, bitler ve sinyaller aracılığıyla iletilir.

Hedef cihazda veriler ters yönde işlenerek ilgili uygulamaya ulaştırılır.

Bu süreçte her katman kendi görevini yerine getirir. Gerçek iletişimde kullanılan protokoller ve ayrıntılar ağ türüne göre değişebilir.

## 7. Siber Güvenlik ve Pentest Açısından Önemi

OSI ve TCP/IP modelleri, ağ trafiğini analiz ederken bir problemin hangi katmanla ilişkili olduğunu anlamaya yardımcı olur.

- **Application:** HTTP istekleri, DNS sorguları ve uygulama katmanı zafiyetleri.
- **Transport:** TCP bağlantıları, UDP trafiği ve port taramaları.
- **Network:** IP adresleri, yönlendirme ve ağ erişilebilirliği.
- **Data Link:** MAC adresleri, Ethernet çerçeveleri ve yerel ağ iletişimi.
- **Physical:** Kablolama, fiziksel bağlantılar ve donanımsal erişim.

**Örnek:** Bir web sunucusuna erişilemiyorsa sorun DNS çözümlemesinde, IP yönlendirmesinde, TCP bağlantısında, güvenlik duvarında veya uygulamanın kendisinde olabilir. Katmanlı düşünmek, sorunun kaynağını sistematik biçimde bulmayı kolaylaştırır.

## 8. Önemli Noktalar

- OSI modeli yedi katmandan oluşur.
- TCP/IP modeli yaygın gösterimde dört katmandan oluşur.
- TCP ve UDP, taşıma katmanında değerlendirilir.
- IP, internet/ağ katmanında görev yapar.
- Ethernet çerçeveleri veri bağı katmanıyla ilişkilidir.
- Veriler gönderilirken kapsüllenebilir, alıcı tarafta ise katmanlar boyunca açılır.
- Katmanlı modeller, ağ sorunlarını analiz etmeyi ve protokollerin görevlerini ayırt etmeyi kolaylaştırır.




