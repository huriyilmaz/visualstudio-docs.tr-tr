---
title: Log'u Değiştir (Unity için Visual Studio Tools, Mac) | Microsoft Dokümanlar
ms.custom: ''
ms.date: 12/02/2019
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 33a6ac54-d997-4308-b5a0-af7387460849
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 5599153f79b273249e93c48aaa197214d92f5fe7
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80232913"
---
# <a name="change-log-visual-studio-tools-for-unity-mac"></a>Değişiklik Günlüğü (Unity için Visual Studio Araçları, Mac)

Unity için Visual Studio Tools değişiklik günlüğü.

## <a name="2520"></a>2.5.2.0

Yayınlanma Mart 23, 2020

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Hata ayıklayıcı:**

  - Ekteki iş parçacıklarının sabit kaydı.

## <a name="2510"></a>2.5.1.0

Yayınlanma Mart 3, 2020

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Için [`IDE0051`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/USP0008.md)bir bastırıcı eklendi. Invoke, InvokeRepeating, StartCoroutine veya StopCoroutine ile kullanılan özel yöntemler kullanılmamış olarak işaretlenmemeli.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Sabit OnDrawGizmos/OnDrawGizmosSeçme belgeler

- **Değerlendirme:**

  - Lambda argüman denetimi düzeltildi.

## <a name="2501"></a>2.5.0.1

Yayınlanma Şubat 19, 2020

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Yanlış [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/UNT0006.md) ileti imzası için tanılama denetimi düzeltildi. Birden çok devralma düzeyine sahip türleri denetlerken, bu `warning AD0001: Analyzer 'Microsoft.Unity.Analyzers.MessageSignatureAnalyzer' threw an exception of type 'System.ArgumentException' with message 'An item with the same key has already been added`tanılama aşağıdaki iletiyle başarısız olabilir: .

## <a name="2500"></a>2.5.0.0

Yayınlanma Ocak 22, 2020

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - HLSL dosyaları için destek eklendi.
  
  - Yeni bir klasör iletişim arabirimi ara birimine geçti.
  
  - Ayarlar için yeni erişilebilir özellik ızgarasına geçti.

  - Için [`IDE0051`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/USP0006.md)bir bastırıcı eklendi. Öznitelik içeren `SerializeField` özel alanlar kullanılmamış olarak işaretlenmemeli.

  - Için [`CS0649`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/USP0007.md)bir bastırıcı eklendi. Öznitelik `SerializeField` içeren alanlar atanmamış olarak işaretlenmemeli.  

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Sabit proje`GenerateTargetFrameworkMonikerAttribute` oluşturma (hedef her zaman doğru bulunamadı)

- **Değerlendirme:**

  - Sabit dize değerlendirmesi (ToString() çağrıları kullanılmaz)

## <a name="2420"></a>2.4.2.0

Yayınlanma Aralık 3, 2019

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Kullanıcı tanımlı arabirimlerle sabit tanılama.

  - Hatalı biçimlendirilmiş ifadeleriçeren hızlı araç uçları düzeltildi.
  
## <a name="2410"></a>2.4.1.0

Yayınlanma Kasım 6, 2019

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Unity arka plan işlemleri için destek eklendi. (Hata ayıklama, alt işlem yerine ana işleme otomatik olarak bağlanabilir).

  - İlişkili belgeleri görüntüleyen Birlik iletileri için hızlı bir araç ipucu eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Gelişmiş ikili ve `UNT0002` çağırma ifadeleri ile etiket karşılaştırma çözümleyicisi düzeltildi.

### <a name="deprecated-features"></a>Amortismana Küçümsülen Özellikler

- **Entegrasyon:**

  - İleriye dönük olarak, Visual Studio Tools for Unity sadece Visual Studio 2017+'yı destekleyecektir.

## <a name="2400"></a>2.4.0.0

Yayınlanma Tarihi: 15 Ekim 2019

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Tüm Unity iletileri için (kullanılmayan parametre) için `IDE0060` bir bastırıcı eklendi.

  - `TooltipAttribute`' ile etiketlenen alanlar için hızlı bir araç ipucu eklendi (Bu da bu alanı kullanarak basit bir erişimci almak için çalışacaktır).

## <a name="2330"></a>2.3.3.0

Yayınlanma Eylül 23, 2019

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Kullanılmayan parametreleri kaldırmak için IDE'nin hızlı düzeltme göstermesini önlemek için IDE0060 için yeni bir bastırıcı eklendi.
    - `USP0005`for `IDE0060`: Birlik iletileri Birlik çalışma zamanı tarafından çağrılır.

## <a name="2320"></a>2.3.2.0

Yayınlanma Eylül 16, 2019

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Visual Studio'nun Birlik projelerine özel yeni tanılamalar ekleyerek Birlik projeleri için sahip olduğu anlayışı derinleştirdik. Unity projeleri için geçerli olmayan genel C# tanılamalarını gizleyerek IDE’yi daha akıllı hale getirdik. Örneğin, IDE, Unity Editor'daki değişkeni değiştirmenizi engelleyecek `readonly` bir denetçi değişkenini değiştirmek için hızlı düzeltme göstermez.
    - `UNT0001`: Birlik iletileri boş olsalar bile çalışma zamanına göre çağrılır, Unity çalışma süresine göre kesintisiz işlemeden kaçınmak için bunları bildirmeyin.
    - `UNT0002`: Dize eşitliği ni kullanarak etiket karşılaştırması yerleşik CompareTag yönteminden daha yavaştır.
    - `UNT0003`: GetComponent'in genel formunun kullanımı tip güvenliği için tercih edilir.
    - `UNT0004`: İletiyi güncelleştirme klitime bağlıdır ve Time.fixedDeltaTime yerine Time.deltaTime'ı kullanmalıdır.
    - `UNT0005`: FixedUpdate iletisi çerçeve hızından bağımsızdır ve Time.deltaTime yerine Time.fixedDeltaTime kullanmalıdır.
    - `UNT0006`: Bu Birlik iletisi için yanlış yöntem imzası algılandı.
    - `UNT0007`: Unity, null coalescing ile uyumsuz olan Unity nesneleri için null karşılaştırma işlecigeçersiz.
    - `UNT0008`: Unity, null yayma ile uyumsuz olan Unity nesneleri için null karşılaştırma işlecigeçersiz kılar.
    - `UNT0009`: InitializeOnLoad özniteliğini bir sınıfa uygularken statik bir oluşturucu sağlamanız gerekir. InitializeOnLoad özniteliği, düzenleyici başlatıldığında bunun çağrılmasını sağlar.
    - `UNT0010`: MonoBehaviours yalnızca AddComponent() kullanılarak oluşturulmalıdır. MonoBehaviour bir bileşendir ve bunun GameObject’e eklenmesi gerekir.
    - `UNT0011`: ScriptableObject yalnızca CreateInstance() kullanılarak oluşturulmalıdır. Unity ileti yöntemlerinin işlenmesi için ScriptableObject’in Unity altyapısı tarafından oluşturulması gerekir.
    - `USP0001`için `IDE0029`: Birlik nesneleri null coalescing kullanmamalıdır.
    - `USP0002`for `IDE0031`: Unity nesneleri null yayılımı kullanmamalıdır.
    - `USP0003`for `IDE0051`: Birlik iletileri Birlik çalışma zamanı tarafından çağrılır.
    - `USP0004`for `IDE0044`: SerializeField özniteliği olan alanlar yalnızca okunmamalıdır.

## <a name="2310"></a>2.3.1.0

Yayınlanma Eylül 4, 2019

### <a name="new-features"></a>Yeni Özellikler

- **Değerlendirme:**

  - Daha iyi tür ekranı için destek `List<object>` eklendi, yani `List'1[[System.Object, <corlib...>]]`.

  - İşaretçi üye erişimi için destek `p->data->member`eklendi, yani.

  - Dizi başharflerinde örtük dönüşümler için destek `new byte [] {1,2,3,4}`eklendi, yani .

  - Bayt dizilerini ve dizeleri incelerken hex düzenleyicisi için destek eklendi.

## <a name="2300"></a>2.3.0.0

Yayınlanma 13 Ağustos 2019

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Değerlendirme:**

  - Özel durumlar dışında basamak sorunları düzeltildi.

  - Sözde tanımlayıcıların ($exception gibi) sabit değerlendirilmesi.

  - Geçersiz adresleri derefered ederken kilitlenmeyi önleyin.  

  - Boşaltılan etki alanlarıyla ilgili sorun giderildi.

## <a name="2200"></a>2.2.0.0

Yayınlanma 25 Temmuz 2019

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Değerlendirme:**

  - IntPtr tipleri ile sabit denetim.

- **Hata ayıklayıcı:**

  - Catchpoints ve işlev kesme noktalarının sabit kullanımı.

## <a name="2130"></a>2.1.3.0

Yayınlanma Tarihi: 9 Temmuz 2019

### <a name="new-features"></a>Yeni Özellikler

- **Hata ayıklayıcı:**

  - Özel durumların alt sınıflarını yakalamak için destek eklendi.

  - MDS protokolü 2.51 için destek eklendi.

- **Entegrasyon:**

  - Asmdef dosyaları için destek eklendi.

  - Bir dosya şablondan eklendiğinde (Unity Editor davranışını taklit etmek için) yeniden adlandırma moduna geçin.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Unity Players ile iletişim kurarken hatalı biçimlendirilmiş iletilerin sabit kullanımı.

- **Değerlendirme:**

  - İfadelerde ad alanlarının işlenmesi düzeltildi.

## <a name="2120"></a>2.1.2.0

Yayınlanma Tarihi: 2 Temmuz 2019

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Değerlendirme:**

  - Ayrıştırılamaz ifadelerle hata raporlaması düzeltildi.

## <a name="2110"></a>2.1.1.0

Yayınlanma Haziran 27, 2019

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - 2019.1 için Güncelleştirilmiş MonoBehaviour API.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Unity Project Explorer performansı düzeltildi.

  - Hafif yapı etkinleştirildiğinde çıktıya raporlama uyarıları ve hataları düzeltildi.

  - Hafif yapı performansı düzeltildi.

## <a name="2100"></a>2.1.0.0

Yayınlanma Haziran 20, 2019

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - IntelliSense hatalarını ve uyarılarını kullanmak lehine, Unity projeleri için tam yapıyı devre dışı bıraktı. Nitekim Birlik, Birlik'in dahili olarak ne yaptığını temsil eden sınıf kitaplığı projeleri ile Visual Studio çözümü oluşturur. Bununla birlikte, Visual Studio'daki yapının sonucu, derleme boru hattı kapalı olduğu için Unity tarafından asla kullanılmaz veya alınmaz. Visual Studio'da bina oluşturmak boşuna kaynak tüketmektir. Araçlarınız veya buna bağlı bir kurulumunuz olduğu için tam bir yapıya ihtiyacınız varsa, bu optimizasyonu devre dışı kullanabilirsiniz (Ayarlar/Unity araçları/projelerin tam oluşturmasını devre dışı kullanabilirsiniz).
  
  - UPE'de Birlik paketleri için destek eklendi. Yalnızca Başvurulan paketler `Packages` (klasörde manifest.json kullanılarak) ve `Packages` Yerel paketler (klasöre katıştırılmış) görünür.

## <a name="2021"></a>2.0.2.1

Yayınlanma Mayıs 30, 2019

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Unity yürütme hedefleri için özel simge eklendi.

## <a name="2020"></a>2.0.2.0

Yayınlanma Nisan 2, 2019

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Unity'nin varlık veritabanını otomatik olarak yenilemek için destek eklendi. Bu varsayılan olarak etkinleştirilir ve Visual Studio'da bir komut dosyası kaydederken Unity tarafında bir yeniden derlemetetikletir. Bu özelliği Araçlar\Seçenekler\Birlik Için Araçlar\Unity\Refresh Unity'nin Varlık Veritabanında kaydedebilirsiniz.

  - Çevrimdışı belgeler için tercih edilen birlik yüklemesi ayarlamak için destek eklendi.

  - Yeni Düzenleyici için bağlam menüsü eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Hata ayıklayıcı:**

  - Boş çerçevelerle montaj filtresi ve çerçeve denetimi düzeltildi.

## <a name="2011"></a>2.0.1.1
 
 Yayınlanma Mart 26, 2019

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Bu çok özel sürüm için Mono'yu geçici olarak varsayılan ve yalnızca kullanılabilir hata ayıklama haline getirin.

## <a name="2006"></a>2.0.0.6

Yayınlanma Mart 26, 2019

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - "Birlik ve Oyun ataşmak" için destek eklendi.

## <a name="2005"></a>2.0.0.5

Yayınlanma Mart 20, 2019

### <a name="new-features"></a>Yeni Özellikler

- **Proje Oluşturma:**

  - Çözüm dosyasını işlerken dış özellikleri koruyun.
  
- **Değerlendirme:**

  - Takma ad nitelikli adlar için destek eklendi (şimdilik yalnızca genel ad alanı). Yani ifade değerlendiricisi şimdi genel form kullanarak türleri kabul ediyor::namespace.type.

  - İşaretçi `pointer[index]` dereference `*(pointer+index)` formuyla anlamsal olarak aynı olan form için destek eklendi.

## <a name="2004"></a>2.0.0.4

Yayınlanma Mart 5, 2019

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - API'yi `ScriptableObject` güncelleştirildi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Ad alanları şablonlardan kaldırıldı.

## <a name="2003"></a>2.0.0.3
 
 Yayınlanma Mart 5, 2019

### <a name="new-features"></a>Yeni Özellikler

- **Proje Oluşturma:**

  - Genel ve serihale alan artık uyarılara neden olmaz. Bu iletileri oluşturan Unity `CS0649` `IDE0051` projelerindeki ve derleyici uyarılarını otomatik olarak bastırdık.

- **Entegrasyon:**

  - Bir Birlik işlemi çalışıyorsa, belirli bir örne eklemek için komut istemi.

- **Değerlendirme:**

  - Yerel işlevler için destek eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Hata ayıklayıcı:**

  - Eski protokol sürümlerini kullanırken adlandırılmış bağımsız değişkenlerde okuma özel özniteliği düzeltildi.

## <a name="2002"></a>2.0.0.2

Yayınlanma Şubat 4, 2019

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - MonoBehaviour API'si güncelleştirildi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Hata ayıklayıcı:**

  - Hata ayıklamada ilkel değerler ayarlı sabit.

## <a name="2001"></a>2.0.0.1

Yayınlanma Tarihi: 4 Aralık 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Sabit kurulum paketi kendi kendini kapsama.

## <a name="2000"></a>2.0.0.0
 Yayınlanma Tarihi: 4 Aralık 2018

### <a name="new-features"></a>Yeni Özellikler

- **Hata ayıklayıcı:**

  - Mac'teki Unity hata ayıklamasını Windows'tan aynı çekirdekli Unity hata ayıklamayla değiştirdi.

  - İfade değerlendirmesi için Roslyn lehine NRefactory değiştirildi.

  - İşaretçiler için ek destek: dereference, döküm ve işaretçi aritmetik (hem Unity 2018.2+ hem de yeni çalışma süresi gereklidir).

  - Dizi işaretçisi görünümü için destek eklendi (C++'daki gibi). İşaretçi ifadesini alın ve virgül ve görmek istediğiniz öğe sayısını tamamlayın.

  - Async yapıları için destek eklendi.

  - Sözde değişkenler (özel durum ve nesne tanımlayıcıları) için destek eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Hata ayıklayıcı:**

  - Yanlış biçimlendirilmiş veya desteklenmeyen ifadeler ile sabit ifade değerlendirmesi.

## <a name="1700"></a>1.7.0.0

Yayınlanma Kasım 13, 2018

### <a name="new-features"></a>Yeni Özellikler

- **Hata ayıklayıcı:**

  - Ekle iletişim kutusuna daha fazla istemci bilgisi (IP, makine adı) eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Hata ayıklayıcı:**

  - Unity'nin hata ayıklayıcı motoruyla iletişim kurmak için kullanılan kütüphanedeki bir kilitlenme giderildi ve özellikle 'Birliğe Ekle' tuşuna basarken veya oyunu yeniden başlatırken Visual Studio veya Unity dondurdu.

- **Entegrasyon:**

  - Başka bir varsayılan düzenleyici seçildiğinde Unity eklentisi etkinleştirme düzeltildi.

  - Unity dosya şablonu oluşturma düzeltildi.

## <a name="1602"></a>1.6.0.2

Yayınlanma Tarihi: 24 Temmuz 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Unity tarafından düzeltilmiş bir Unity performans hatası için geçici çözüm geri alındı.

## <a name="1601"></a>1.6.0.1

Yayınlanma 10 Temmuz 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Shader kodu renklendirme desteği düzeltildi.

## <a name="1600"></a>1.6.0.0

Yayınlanma Haziran 26, 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Sihirbaz:**

  - OnApplicationFocus iletisi ile yazım hatası düzeltildi.

- **Proje Oluşturma:**

  - Bir Unity performans hatası için geçici geçici çözüm: proje oluştururken Önbellek MonoIslands.

  - Yeni Unity çalışma süresini kullanırken taşınabilir pdb'yi artık mdb'ye dönüştürün.

## <a name="1502"></a>1.5.0.2

Yayınlanma Nisan 18, 2018

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Temel Shader kod tamamlama desteği eklendi.

  - Shader dosyalarında yorumları niçin değiştirin.

## <a name="1501"></a>1.5.0.1

Yayınlanma Mart 28, 2018

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Unity Project Explorer'da ek şablonlar için destek eklendi.

## <a name="1500"></a>1.5.0.0

Yayınlanma Tarihi: 21 Mart 2018

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - USB üzerinden bağlanan Android oynatıcıların algılanması ve bağlanması için destek eklendi.

## <a name="1403"></a>1.4.0.3

Yayınlanma Mart 5, 2018

### <a name="new-features"></a>Yeni Özellikler

- **Proje Oluşturma:**

  - Birlik 2018.1'de yeni proje jeneratörüne destek eklendi.

- **Entegrasyon:**

  - Özel ayarlar için seçenek paneli eklendi.

## <a name="1402"></a>1.4.0.2

Yayınlanma Ocak 24, 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Proje Oluşturma:**

  - Mono sürüm algılaması düzeltildi.

- **Entegrasyon:**

  - 2018.1 ve eklenti etkinleştirme ile zamanlama sorunları giderildi.

  - Yeni bir oyuncu algılarken bildirimler düzeltildi.

## <a name="1401"></a>1.4.0.1

Yayınlanma Ocak 23, 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Çift tıklatıldığında klasörleri Genişlet/Daralt düzeltildi

## <a name="1400"></a>1.4.0.0

Yayınlanma 13 Aralık 2017

### <a name="new-features"></a>Yeni Özellikler

- **Proje Oluşturma:**

  - .NET Standard için destek eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - mdb hata ayıklama sembolü dönüştürme için otomatik pdb düzeltildi.

## <a name="1301"></a>1.3.0.1

Yayınlanma 12 Aralık 2017

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Array Boyutunu değiştirmeye çalışırken denetçiyi etkileyen EditorPrefs.GetBool'a dolaylı arama düzeltildi.

- **Sihirbaz:**

  - Yöntem eklemeden önce roslyn bağlamı yenileyin.

## <a name="1300"></a>1.3.0.0

Yayınlanma Kasım 20, 2017

### <a name="new-features"></a>Yeni Özellikler

- **Sihirbaz:**

  - "Birlik iletisi uygula" sihirbazı eklendi.

  - Mac 7.4 için VS yeni tamamlama API için destek eklendi.

## <a name="1200"></a>1.2.0.0

Yayınlanma Tarihi: 23 Ekim 2017

### <a name="new-features"></a>Yeni Özellikler

- **Hata ayıklayıcı:**

  - Taşınabilir hata ayıklama simgesi dosyaları için destek eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Proje Oluşturma:**

  - Montaj dosya adına yanlış eklenen ekstra .dll uzantısı düzeltildi.

  - Varsayılan artık 'true' olduğu için AllowAttachedDebuggingOfEditor Unity bayrağını zorlamayın.

## <a name="1103"></a>1.1.0.3

Yayınlanma Tarihi: 23 Ekim 2017

### <a name="new-features"></a>Yeni Özellikler

- **Proje Oluşturma:**

  - .NET 4.6 profili için destek eklendi.

## <a name="1102"></a>1.1.0.2

Yayınlanma 8 Ağustos 2017

### <a name="new-features"></a>Yeni Özellikler

- **Hata ayıklayıcı:**

  - Hangi Birliğe ekleyeceğinden emin değilse, işlem iletişim kutusuna eklemeyi başlatın.

- **Proje Oluşturma:**

  - Unity 5.6 kullanıldığında her zaman güvenli olmayan derleme anahtarını etkinleştirin.

## <a name="1101"></a>1.1.0.1

Yayınlanma Tarihi: 20 Temmuz 2017

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Yerelleştirilmiş kaynaklar için destek eklendi.

## <a name="1100"></a>1.1.0.0

Yayınlanma 12 Temmuz 2017

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - İşleme Ekle penceresinden oyunculara ve editörlere iliştirme desteği eklendi.

- **Proje Oluşturma:**

  - Mcs.rsp dosyaları ile sabit montaj adı başvuruları.

  - assembly.json derleme birimleri için destek eklendi.

  - Sabit API düzeyleri ile tanımlar.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Derleme yaparken gölgeli hata iletisi düzeltildi.

## <a name="1001"></a>1.0.0.1

Yayınlanma Mayıs 4, 2017

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Karma ve düzenli projelerle etkin belge takibi düzeltildi.

## <a name="1000"></a>1.0.0.0

Yayınlanma Mayıs 3, 2017
