# Ödev #1

## 1. Neden Nesne Yönelimli Programlama (OOP) kullanmalıyız? Bazı önemli OOP dilleri nelerdir?

### Neden OOP kullanılır?
- **Modülerlik**: Kod, sınıflar ve nesneler halinde düzenlenir, böylece bakım ve değiştirme daha kolay hale gelir.
- **Yeniden Kullanılabilirlik**: Kalıtım ve bileşim yoluyla mevcut kodu yeniden kullanabilirsiniz.
- **Kapsülleme**: İç durumu ve işlevselliği gizler, yalnızca gerekli olanı açığa çıkarır.
- **Polimorfizm**: Tek bir arayüzün farklı temel formları (metodlar veya sınıflar) kontrol etmesine izin verir.
- **Soyutlama**: Probleme uygun sınıfları modelleyerek karmaşık gerçeklikleri basitleştirir.

### Önemli OOP Dilleri
- **Java**
- **C++**
- **C#**
- **Python** (birden fazla paradigmayı destekler, OOP dahil)
- **Ruby**
- **JavaScript** (prototip tabanlı kalıtım)

---

## 2. Arayüz (Interface) vs Soyut Sınıf (Abstract Class)

### Arayüz (Interface)
- Yalnızca soyut metodlar (eski Java sürümlerinde) ve static/final alanlar içerir.
- Bir sınıf birden fazla arayüzü implemente edebilir.
- Bir sözleşme tanımlar (hangi metodların implemente edilmesi gerektiği), ancak bu metodların nasıl implemente edileceğini belirtmez (Java 8+ ile default metodlara izin verilir).

### Soyut Sınıf (Abstract Class)
- Hem soyut hem de somut metodlar içerebilir.
- Örnek değişkenler (instance variable) ve yapıcı metotlara (constructor) sahip olabilir.
- Bir sınıf yalnızca bir soyut sınıfı extend edebilir (tek kalıtım).
- Alt sınıflar arasında ortak durum ve davranışı paylaşmak istediğinizde kullanışlıdır.

---

## 3. `equals` ve `hashCode`'a neden ihtiyacımız var? Ne zaman override (üstüne yazma) etmeliyiz?

- **`equals`**: Nesneler arasındaki mantıksal eşitliği belirler. Varsayılan olarak, `Object` sınıfındaki `equals`, referans eşitliğini kontrol eder (yani, aynı bellek adresi). Nesne alanlarına dayalı eşitlik tanımlamak için override edilir.
- **`hashCode`**: `HashMap`, `HashSet` gibi hash tabanlı koleksiyonlarda kullanılır. Eğer iki nesne `equals`'a göre eşitse, aynı `hashCode` değerine sahip olmaları gerekir.
- **Ne zaman override etmeli?**:
  - Nesneleri mantıksal olarak (örneğin, aynı "değer" veya aynı alanlar) karşılaştırmanız gerektiğinde, referans yerine.
  - `equals` metodunu override ediyorsanız, aralarındaki sözleşmeyi korumak için her zaman `hashCode` metodunu da override edin.

---

## 4. Java'da Diamond Problemi nedir? Nasıl çözülür?

- **Nedir?**  
  Çoklu kalıtım durumlarında (örneğin, C++), bir sınıf ortak bir temel sınıfı paylaşan iki sınıftan kalıtım alabilir ve bu durum metodlar/alanlar için belirsizlik yaratır. Java, çoklu sınıf kalıtımından kaçındığı için bu problem tipik olarak default metodlara sahip arayüzlerde ortaya çıkar.
- **Nasıl çözülür?**:  
  Java, çakışan default metodları kendi sınıfınızda açıkça override etmenizi gerektirir, kendi implementasyonunuzu sağlayarak (veya ebeveyn arayüzlerden birinin default metodunu seçerek).

---

## 5. Neden Garbage Collector'a (Çöp Toplayıcı) ihtiyacımız var? Nasıl çalışır?

- **Neden Gerekir?**:  
  - Bellek yönetimini otomatikleştirir.  
  - Geliştiricileri manuel bellek ayırma/silme işinden kurtarır.  
  - Bellek sızıntılarını ve işaretçi (pointer) sarkan nesneleri (dangling pointers) önler.
- **Nasıl Çalışır?**:
  - JVM'nin çöp toplayıcısı, canlı referanslardan erişilemeyen nesneleri periyodik olarak tarar ve belleklerini geri kazanır.
  - Farklı GC algoritmaları (örneğin, Mark-Sweep, G1 vb.) performans ve strateji bakımından farklılık gösterir.

---

## 6. Java `static` Anahtar Kelimesinin Kullanımı

- **`static` alan (field)**: Bir sınıfın tüm örnekleri arasında paylaşılır.
- **`static` metod**: Sınıfa ait olup herhangi bir örneğe bağlı değildir, nesne oluşturmadan çağrılabilir.
- **`static` blok**: Bir sınıfın statik başlatılması (initialization) için kullanılır.
- **`static` iç sınıf (inner class)**: Dış sınıfın bir örneğine ihtiyaç duymayan iç içe geçmiş sınıf.

---

## 7. Değişmezlik (Immutability): Ne Demektir? Nerede, Nasıl ve Neden Kullanılır?

- **Anlamı**: Bir nesnenin durumu (state), oluşturulduktan sonra değiştirilemez.
- **Nerede**:
  - Veri aktarım nesnelerinde (DTO), değer nesnelerinde (value objects) ve çok iş parçacıklı (thread-safe) tasarımlarda yaygın olarak kullanılır.
- **Nasıl**:
  - Alanları `private final` olarak tanımlayın.
  - Setter metodları (veya alanları değiştiren metodlar) sağlamayın.
  - Alanları yapıcı metod (constructor) içerisinde başlatın.
- **Neden**:
  - Kodun anlaşılmasını kolaylaştırır, özellikle çok iş parçacıklı ortamlarda.
  - Durum değişikliğine bağlı hataları azaltır.

---

## 8. Bileşim (Composition) ve Toplulaştırma (Aggregation): Anlamları ve Farkları

- **Bileşim (Composition)**:
  - İlişkinin güçlü formu: Sahiplik ile "sahip-olma" ilişkisi.
  - Eğer konteyner nesnesi yok edilirse, bileşen nesneler de yok edilir.
  - Örnek: Bir `Araba`'nın bir `Motor`u vardır (motor, araba olmadan var olamaz).

- **Toplulaştırma (Aggregation)**:
  - İlişkinin zayıf formu: Sahiplik olmaksızın "sahip-olma" ilişkisi.
  - Eğer konteyner nesnesi yok edilirse, içerilen nesne başka yerlerde var olmaya devam edebilir.
  - Örnek: Bir `Takım`ın `Oyuncuları` vardır, ancak bir oyuncu farklı takımlarda da yer alabilir.

---

## 9. Uyum (Cohesion) ve Bağlılık (Coupling): Anlamları ve Farkları

- **Uyum (Cohesion)**:
  - Bir modül/sınıf içindeki öğelerin ne kadar bir araya ait olduğunu ifade eder.
  - Yüksek uyum, sınıfın tek bir göreve veya birbirine yakın görevlerde odaklandığı anlamına gelir.

- **Bağlılık (Coupling)**:
  - Modüller/sınıflar arasındaki bağımlılık derecesidir.
  - Düşük bağlılık, bir sınıftaki değişikliklerin diğer sınıfları minimum derecede etkilemesi anlamına gelir.

### İdeal Senaryo
- **Yüksek uyum** ve **düşük bağlılık**.

---

## 10. Heap ve Stack: Anlamları ve Farkları

- **Stack (Yığın)**:
  - Metod yürütme ve yerel değişkenler için bellek alanıdır.
  - Metod çağrıları/geri dönüşleriyle büyür veya küçülür.
  - Yığında saklanan değişkenlerin ömrü kısa (metod kapsamındadır).

- **Heap (Yığın Bellek)**:
  - Nesnelerin dinamik olarak atanması (allocation) için bellek alanıdır.
  - Nesneler, referans verilmediğinde (sonrasında çöp toplanır) heap'te yaşarlar.
  - Daha esnektir, ancak yönetilmesi daha maliyetlidir.

---

## 11. İstisna (Exception): Nedir? İstisna Türleri Nelerdir?

- **Nedir?**: İstisna, bir programın normal yürütme akışını bozan bir olaydır.
- **Türler**:
  1. **Checked Exceptions (Kontrol Edilen İstisnalar)**: `Exception` sınıfından türetilmiştir (ancak `RuntimeException` hariç). Ya yakalanmalı ya da metod imzasında `throws` ile bildirilmelidir.
     - Örnek: `IOException`, `SQLException`.
  2. **Unchecked Exceptions (Kontrol Edilmeyen İstisnalar)**: `RuntimeException` sınıfından türetilmiştir. Yakalanması veya bildirilmesi gerekmez.
     - Örnek: `NullPointerException`, `ArrayIndexOutOfBoundsException`.
  3. **Error**: Genellikle tipik uygulamalar tarafından ele alınmayan ciddi sorunlardır.
     - Örnek: `OutOfMemoryError`.

---

## 12. “Clean Code” (Temiz Kod) Nasıl En Kısa Şekilde Özetlenir?

- **Temiz Kod**: Okunabilir, sürdürülebilir ve verimli olan, tutarlı kurallara, basit tasarıma ve anlamlı isimlendirmeye sahip, gereksiz tekrarların olmadığı koddur.

---

## 13. Java'da Metod Gizleme (Method Hiding) Nedir?

- **Metod Gizleme**, alt sınıfta bulunan bir **static metodun**, üst sınıfta bulunan static metodla aynı imzaya (signature) sahip olması durumunda meydana gelir.  
- Bu, instance metodlarda geçerli olan override ile aynı şey değildir. Bunun yerine, alt sınıfın static metodu, üst sınıfın static metodunu **gizler**.

---

## 14. Java'da Soyutlama (Abstraction) ile Polimorfizm (Polymorphism) Arasındaki Fark Nedir?

- **Soyutlama (Abstraction)**:
  - Bir sınıfın veya metodun **ne yaptığına** odaklanır, **nasıl yaptığına** değil.
  - Soyut sınıflar ve arayüzler aracılığıyla gerçekleştirilir.
  - Uygulama detaylarını gizleyerek karmaşıklığı azaltır.

- **Polimorfizm (Polymorphism)**:
  - Nesnelerin, üst tipleri (veya arayüzleri) şeklinde temsil edilmesine ve gerçek (çalışma zamanındaki) tiplere bağlı olarak farklı davranmasına olanak tanır.
  - Başlıca **metod override (üstüne yazma)** (dinamik bağlama) yoluyla gerçekleştirilir.
  - Farklı implementasyonların yer değiştirmesine izin vererek kodda esneklik sağlar.
