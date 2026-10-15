# OSI ve TCP/IP Modelleri

Ağ iletişimi tek bir işlemden oluşmaz. Bir cihazdan başka bir cihaza veri gönderilirken uygulamadan fiziksel iletişime kadar birçok farklı işlem gerçekleşir.

Bu işlemleri daha anlaşılır hâle getirmek için ağ iletişimi **katmanlara** ayrılır.

En temel mantık:

```text
Uygulama
   ↓
Verinin taşınması
   ↓
Adresleme ve yönlendirme
   ↓
Yerel ağ iletişimi
   ↓
Fiziksel iletim
```

Bu yapıyı açıklamak için **OSI** ve **TCP/IP** modelleri kullanılır.

---

# OSI Modeli

OSI modeli ağ iletişimini **7 katmana** ayırır:

```text
7 - Application
6 - Presentation
5 - Session
4 - Transport
3 - Network
2 - Data Link
1 - Physical
```

Katmanları ezberlemekten çok her katmanın temel görevini anlamak önemlidir.

---

## 7. Application Layer

Kullanıcıya ağ hizmetlerini sunan uygulama protokollerinin bulunduğu katmandır.

Örneğin:

- HTTP / HTTPS
- DNS
- SSH
- FTP
- SMTP

Bir web sitesine girdiğimizde tarayıcının kullandığı HTTP/HTTPS iletişimi bu katmanla ilişkilidir.

**Pentest açısından:** Web uygulamaları, API'ler, DNS ve diğer ağ servisleri bu seviyede karşımıza çıkar.

---

## 6. Presentation Layer

Verinin karşı tarafın anlayabileceği biçime dönüştürülmesiyle ilgilidir.

Örneğin:

- Veri formatlama
- Encoding / Decoding
- Compression
- Encryption / Decryption

Ancak gerçek sistemlerde bu işlemler her zaman ayrı bir katmanda gerçekleşmez. OSI'deki Presentation Layer daha çok bu görevleri açıklamak için kullanılan kavramsal bir katmandır.

---

## 5. Session Layer

İki sistem arasındaki iletişim oturumlarının yönetilmesiyle ilgilidir.

Basitçe:

```text
Oturumu başlat
      ↓
İletişimi sürdür
      ↓
Oturumu sonlandır
```

Modern TCP/IP ağlarında bu işlevler genellikle uygulamalar ve diğer protokoller tarafından gerçekleştirilir.

---

## 4. Transport Layer

Verinin **iki uç sistem arasında taşınmasını** sağlar.

En önemli protokoller:

- **TCP**
- **UDP**

TCP güvenilir ve bağlantı odaklı iletişim sağlar.

UDP ise bağlantı kurmadan veri gönderir ve TCP gibi teslim garantisi sağlamaz.

Bu katmanda **port numaraları** da kullanılır.

Örneğin:

```text
192.168.1.10:443
```

Burada:

```text
192.168.1.10 → IP adresi
443           → Port
```

IP adresi cihazı, port ise cihaz üzerindeki ilgili iletişim noktasını belirtir.

**Pentest açısından:** Port scanning ve açık servislerin tespit edilmesi bu katmanla yakından ilişkilidir.

---

## 3. Network Layer

Verinin **hangi ağdan geçerek hedefe ulaşacağını** belirlemekle ilgilidir.

Temel protokol **IP**'dir.

Bu katmanda:

- IP adresleme
- Routing
- Packet forwarding

gibi işlemler gerçekleştirilir.

Örneğin iki bilgisayar farklı ağlardaysa veri doğrudan gönderilmeyebilir. Paketler router'lar üzerinden geçirilir.

Router, hedef IP adresine bakarak paketin nereye gönderileceğine karar verir.

---

## 2. Data Link Layer

Aynı yerel ağ içerisindeki cihazların iletişimiyle ilgilenir.

Bu katmanda:

- MAC address
- Ethernet
- Wi-Fi
- Frame
- Switch

gibi kavramlar bulunur.

Switch, yerel ağdaki cihazlar arasında veri aktarırken **MAC adreslerini** kullanır.

Basit olarak:

```text
IP  → Hangi cihaz / ağ?
MAC → Yerel ağdaki hangi arayüz?
```

şeklinde düşünebiliriz.

---

## 1. Physical Layer

Verinin fiziksel ortam üzerinden iletilmesini ifade eder.

Örneğin:

- Ethernet kablosu
- Fiber
- Wi-Fi radyo sinyalleri

üzerinden verinin **bitler** şeklinde taşınması bu katmanla ilişkilidir.

---

# Verinin Katmanlardan Geçmesi

Örneğin tarayıcıdan bir web sitesine istek gönderdiğimizi düşünelim.

Önce uygulama verisi oluşturulur:

```text
HTTP Request
```

Daha sonra veri katmanlar boyunca aşağı doğru ilerler.

```text
Application
     ↓
Transport
     ↓
Network
     ↓
Data Link
     ↓
Physical
```

Her katman kendi bilgilerini veriye ekleyerek onu bir sonraki katmana gönderir.

Basitleştirirsek:

```text
Data
  ↓
TCP Segment
  ↓
IP Packet
  ↓
Ethernet Frame
  ↓
Bits
```

Bu işleme **Encapsulation** denir.

Hedef bilgisayarda ise süreç tersine gerçekleşir:

```text
Bits
  ↓
Frame
  ↓
Packet
  ↓
Segment
  ↓
Data
```

Buna **Decapsulation** denir.

Bu yüzden OSI modelini anlamanın en önemli noktalarından biri, **verinin gönderici tarafta katmanlar boyunca aşağı indiğini, alıcı tarafta ise yukarı çıktığını** anlamaktır.

---

# TCP/IP Modeli

TCP/IP modeli, gerçek ağ iletişimini açıklamak için daha pratik bir modeldir.

Genellikle 4 katmandan oluşur:

```text
Application
Transport
Internet
Network Access
```

OSI ile ilişkisi:

```text
OSI                         TCP/IP

Application       ┐
Presentation      ├──────→  Application
Session           ┘

Transport         ───────→  Transport

Network           ───────→  Internet

Data Link         ┐
Physical          ┴──────→  Network Access
```               ┘

TCP/IP modelinde OSI'nin Presentation ve Session katmanları ayrı katmanlar olarak bulunmaz. Bu işlevler çoğunlukla Application katmanı içinde ele alınır.

---

# OSI ve TCP/IP'yi Nasıl Düşünmeliyiz?

Bir web sitesine bağlandığımızı düşünelim:

```text
HTTP
 ↓
TCP
 ↓
IP
 ↓
Ethernet / Wi-Fi
 ↓
Fiziksel ortam
```

Burada her teknoloji farklı bir soruya cevap verir:

```text
HTTP
→ Hangi uygulama iletişimi?

TCP
→ Veri nasıl taşınacak?

IP
→ Veri hangi cihaza / ağa gidecek?

Ethernet / Wi-Fi
→ Yerel ağda nasıl iletilecek?

Physical
→ Fiziksel olarak nasıl taşınacak?
```

Asıl önemli olan katman isimlerini ezberlemek değil, **bu görevlerin birbirinden nasıl ayrıldığını anlamaktır.**

Bu mantık daha sonra TCP/UDP, IP adresleme, routing, switching, packet analysis ve network reconnaissance konularını anlamayı kolaylaştırır.

