# Unicast, Broadcast ve Multicast

Bir ağda veri gönderirken, verinin **kime veya kimlere gönderileceği** önemlidir.

Bir bilgisayar başka bir bilgisayara veri gönderebilir, ağdaki herkese gönderebilir veya belirli bir gruba gönderebilir.

Bu iletişim şekilleri üç temel yöntemle ifade edilir:

- **Unicast**
- **Broadcast**
- **Multicast**

Temel fark, verinin **kaç alıcıya gönderildiğidir.**

---

## Unicast

**Unicast**, bir cihazın başka **tek bir cihaza** veri göndermesidir.

Örneğin bilgisayarımız bir web sunucusuna bağlandığında, gönderdiğimiz istek belirli bir hedefe gider.

```text
PC A
  │
  └────────→ PC B
```

Burada:

```text
1 gönderici → 1 alıcı
```

vardır.

Günlük ağ iletişiminin büyük bir bölümü Unicast şeklindedir.

Örneğin:

- Web sitesine bağlanmak
- SSH ile bir sunucuya bağlanmak
- Bir sunucudan dosya indirmek

gibi iletişimlerde belirli bir hedefle iletişim kurarız.

### Mantığı

Unicast'i bir kişiye doğrudan mesaj göndermek gibi düşünebiliriz.

```text
Sen → Ahmet
```

Mesajı yalnızca Ahmet'e gönderirsin.

---

## Broadcast

**Broadcast**, bir cihazın aynı yerel ağdaki **tüm uygun cihazlara** veri göndermesidir.

```text
             → PC B
            ↗
PC A ───────→ PC C
            ↘
             → PC D
```

Burada:

```text
1 gönderici → Ağdaki tüm uygun cihazlar
```

mantığı vardır.

Broadcast'in önemli özelliği, genellikle **yerel ağ ile sınırlı olmasıdır**. Router'lar normal koşullarda broadcast trafiğini başka ağlara iletmez.

### Neden kullanılır?

Bir cihaz ağdaki belirli bir cihazın adresini henüz bilmiyorsa, yerel ağdaki cihazlara soru sorabilir.

Örneğin **ARP** sürecinde bir cihaz, belirli bir IP adresinin hangi MAC adresine ait olduğunu öğrenmek için yerel ağa broadcast gönderir.

Basitleştirirsek:

```text
"192.168.1.20 kimde?"
        ↓
Ağdaki cihazlara gönderilir
        ↓
192.168.1.20 adresine sahip cihaz cevap verir
```

### Mantığı

Broadcast'i sınıfta herkese soru sormak gibi düşünebiliriz:

> "Kalemi kim aldı?"

Soruyu sınıftaki herkes duyar ancak yalnızca ilgili kişi cevap verir.

---

## Multicast

**Multicast**, verinin ağdaki **belirli bir gruba** gönderilmesidir.

```text
             → PC B
            ↗
PC A ───────→ PC C
            ↘
             PC D
```

Burada PC A'nın seçtiği belirli bir grup vardır.

Örneğin:

```text
1 gönderici → Belirli bir alıcı grubu
```

Mesaj grupta olmayan cihazlara gönderilmez.

### Mantığı

Multicast'i belirli kişilerin bulunduğu bir mesaj grubuna mesaj göndermek gibi düşünebiliriz.

```text
Gönderici
   ↓
[Grup üyeleri]
   ↓
Ali
Ayşe
Mehmet
```

Grupta olmayan kişiler bu iletişimin hedefi değildir.

Multicast özellikle **aynı veriyi birden fazla alıcıya verimli şekilde ulaştırmak** gereken durumlarda kullanılabilir.

---

# Üçünü Karşılaştırma

En kolay şekilde şöyle düşünebiliriz:

```text
Unicast
→ Bir kişiye gönder

Broadcast
→ Herkese gönder

Multicast
→ Belirli bir gruba gönder
```

| İletişim | Gönderim |
|---|---|
| Unicast | 1 → 1 |
| Broadcast | 1 → Herkes |
| Multicast | 1 → Belirli bir grup |

---

# Neden Önemli?

Bu ayrım ağ trafiğini anlamak açısından önemlidir.

Örneğin ağ üzerinde çok fazla Broadcast trafiği oluşması, yerel ağdaki cihazların gereksiz trafikle meşgul olmasına neden olabilir.

Multicast ise aynı verinin birçok alıcıya gönderilmesi gerektiğinde her alıcı için ayrı ayrı veri göndermek yerine grup iletişimi sağlayabilir.

Unicast ise iki belirli cihaz arasındaki normal iletişimin temel şeklidir.

Bu nedenle bir ağ trafiğini incelerken şu soruyu sormak önemlidir:

> **Bu veri tek bir cihaza mı, ağdaki herkese mi, yoksa belirli bir gruba mı gönderiliyor?**

Bu sorunun cevabı bize iletişimin **Unicast, Broadcast veya Multicast** olduğunu gösterir.