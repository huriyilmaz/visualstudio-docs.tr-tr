---
title: Değişiklik günlüğü (Unity için Visual Studio Araçları, Windows) | Microsoft Docs
ms.custom: ''
ms.date: 5/19/2020
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: ea490b7e-fc0d-44b1-858a-a725ce20e396
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: cc1cbc98d4612c8f480cca0a9469d4a56da10bb3
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84184789"
---
# <a name="change-log-visual-studio-tools-for-unity-windows"></a>Değişiklik günlüğü (Unity için Visual Studio Araçları, Windows)

Unity için Visual Studio Araçları değişiklik günlüğü.

## <a name="4610"></a>4.6.1.0
Yayımlanma tarihi 19 Mayıs 2020

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Unity tarafında mesajlaşma sunucusunu oluşturdığımızda uyarın.
  
  - Hafif derleme sırasında Çözümleyicileri düzgün şekilde çalıştırın.
  
  - UPE 'dan oluşturulan Monodavranış sınıfının dosya adı ile eşleşmediği bir sorun düzeltildi.

## <a name="4600"></a>4.6.0.0
Yayın tarihi 14 Nisan 2020

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - CodeLens (Unity betikleri ve iletileri) için destek eklendi.
  
  - [`UNT0012`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/UNT0012.md)Tanılama eklendi. İçindeki bağıntıları tespit edin ve bu çağrıları sarın `StartCoroutine()` .

  - [`UNT0013`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/UNT0013.md)Tanılama eklendi. Geçersiz veya gereksiz özniteliği tespit edin ve kaldırın `SerializeField` .

  - [`UNT0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/UNT0014.md)Tanılama eklendi. Algılama `GetComponent()` , bileşen olmayan veya arabirim olmayan türle çağrıldı.
  
  - [`USP0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/USP0009.md)İçin Suppressor eklendi `IDE0051` . Özniteliği özniteliğiyle bayrak eklemeyin `ContextMenu` veya özniteliği kullanılmamış olarak bir alan tarafından başvurulmayın `ContextMenuItem` .

  - [`USP0010`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/USP0010.md)İçin Suppressor eklendi `IDE0051` . `ContextMenuItem`Özniteliği, kullanılmayan olarak özniteliğe bayrak eklemeyin.
  
  - [`USP0011`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/USP0011.md)İçin Suppressor eklendi `IDE0044` . `ContextMenuItem`Özniteliği ile salt okuma alanları yapmayın.
  
  - [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/USP0004.md)[`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/USP0006.md)ve [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/USP0007.md) artık ve öznitelikleri için de çalışır `SerializeReference` `SerializeField` .
  
### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Yalnızca Düzenleyici iletişim kurabiliyorsa Unity 'ye Başlat/Durdur komutlarını gönderin.
  
  - Devralınan iletilerle düzeltilen QuickInfo belgeleri.
  
  - İleti için sabit ileti kapsamı `CreateInspectorGUI` .

  - [`UNT0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/UNT0001.md)Polimorfik değiştiricilere sahip yöntemler hakkında rapor vermeyin.

- **Değerlendirmesinin**

  - Diğer ad kullanımları düzeltildi.

## <a name="4510"></a>4.5.1.0

Yayın tarihi 16 Mart 2020

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - [`USP0008`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/USP0008.md)İçin Suppressor eklendi `IDE0051` . Invoke, InvokeRepeating, StartCoroutine veya StopCoroutine ile kullanılan özel yöntemler kullanılmamış olarak işaretlenmemelidir.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Fixed Ondrawgizmos öğesini uygulayın/Ondrawgizmosselected öğesini uygulayın belgeleri.

- **Değerlendirmesinin**

  - Sabit lambda bağımsız değişken incelemesi.

## <a name="4501"></a>4.5.0.1

Yayın tarihi, 19 Şubat 2020

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/UNT0006.md)Hatalı ileti imzası için tanılama denetimi düzeltildi. Birden çok devralma düzeyi olan türler incelenirken, bu tanı şu iletiyle başarısız olabilir: `warning AD0001: Analyzer 'Microsoft.Unity.Analyzers.MessageSignatureAnalyzer' threw an exception of type 'System.ArgumentException' with message 'An item with the same key has already been added` .

## <a name="4500"></a>4.5.0.0

22 Ocak 2020 tarihinde yayınlandı

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - HLSL dosyaları için destek eklendi.
  
  - [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/USP0006.md)İçin Suppressor eklendi `IDE0051` . Özniteliği olan özel alanlar `SerializeField` kullanılmamış olarak işaretlenmemelidir.
  
  - [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/USP0007.md)İçin Suppressor eklendi `CS0649` . Özniteliği olan alanlar `SerializeField` atanmamış olarak işaretlenmemelidir.  

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Sabit proje üretimi ( `GenerateTargetFrameworkMonikerAttribute` hedef her zaman doğru şekilde bulunamadı).

## <a name="4420"></a>4.4.2.0

Yayın 3 Aralık 2019

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Kullanıcı tanımlı arabirimler ile sabit Tanılamalar.

  - Hatalı biçimlendirilmiş ifadelerle hızlı araç ipuçları düzeltildi.

## <a name="4410"></a>4.4.1.0

Yayın tarihi, 6 Kasım 2019

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - Unity arka plan işlemlerine yönelik destek eklendi. (Hata ayıklayıcı alt işlem yerine ana işleme otomatik olarak bağlanabilir).
  
  - Unity iletileri için ilgili belgeleri görüntüleyen bir hızlı araç ipucu eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - [`UNT0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/UNT0002.md)Gelişmiş ikili ve çağırma ifadeleriyle etiket karşılaştırma Çözümleyicisi düzeltildi.

### <a name="deprecated-features"></a>Kullanım dışı Özellikler

- **Tümleştirme**

  - Unity için Visual Studio Araçları, yalnızca Visual Studio 2017 + desteğine sahip olur.

## <a name="4400"></a>4.4.0.0

Yayımlanma tarihi, 15 Ekim 2019

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - [`USP0005`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/USP0005.md) `IDE0060` Tüm Unity iletileri için Suppressor (kullanılmamış parametre) eklendi.
  
  - İle etiketlenmiş alanlar için hızlı araç ipucu eklendi `TooltipAttribute` . (Bu, bu alanı kullanarak basit bir get erişimcisi için de çalışır).

## <a name="4330"></a>4.3.3.0

Yayın tarihi, 23 Eylül 2019

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Basit derlemeler için düzeltilen hata ve uyarı raporlaması.

## <a name="4320"></a>4.3.2.0

Yayın tarihi, 16 Eylül 2019

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - Unity 'ye özgü yeni Tanılamalar ekleyerek, Visual Studio 'nun Unity projelerine yönelik olduğunu anlama konusunu sunuyoruz. Unity projeleri için geçerli olmayan genel C# tanılamalarını gizleyerek IDE’yi daha akıllı hale getirdik. Örneğin, IDE, Unity düzenleyicisinde değişkeni değiştirmenize engel olacak bir Inspector değişkenini değiştirmek için hızlı bir çözüm göstermez `readonly` .
    - [`UNT0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/UNT0001.md): Unity iletileri, boş olsalar bile çalışma zamanı tarafından çağrılır, Unity çalışma zamanına göre uncesseray işlemesini önlemek için bunları bildiremezsiniz.
    - [`UNT0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/UNT0002.md): Dize eşitlik kullanılarak etiket karşılaştırması yerleşik CompareTag yönteminden daha yavaştır.
    - [`UNT0003`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/UNT0003.md): Tür güvenliği için GetComponent 'un genel biçiminin kullanımı tercih edilir.
    - [`UNT0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/UNT0004.md): Güncelleştirme iletisi çerçeve hızına bağımlıdır ve Time. deltaTime yerine Time. fixedDeltaTime kullanın.
    - [`UNT0005`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/UNT0005.md): FixedUpdate iletisi çerçeve hızına bağımsızdır ve Time. fixedDeltaTime yerine Time. deltaTime kullanın.
    - [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/UNT0006.md): Bu Unity iletisi için yanlış bir yöntem imzası algılandı.
    - [`UNT0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/UNT0007.md): Unity, null birleştirme ile uyumsuz olan Unity nesneleri için null karşılaştırma işlecini geçersiz kılar.
    - [`UNT0008`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/UNT0008.md): Unity, null yayılmayla uyumsuz olan Unity nesneleri için null karşılaştırma işlecini geçersiz kılar.
    - [`UNT0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/UNT0009.md): Initializeonload özniteliği bir sınıfa uygulanırken, bir statik Oluşturucu sağlamanız gerekir. InitializeOnLoad özniteliği, düzenleyici başlatıldığında bunun çağrılmasını sağlar.
    - [`UNT0010`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/UNT0010.md): MonoBehaviours yalnızca AddComponent () kullanılarak oluşturulmalıdır. MonoBehaviour bir bileşendir ve bunun GameObject’e eklenmesi gerekir.
    - [`UNT0011`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/UNT0011.md): ScriptableObject yalnızca CreateInstance () kullanılarak oluşturulmalıdır. Unity ileti yöntemlerinin işlenmesi için ScriptableObject’in Unity altyapısı tarafından oluşturulması gerekir.
    - [`USP0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/USP0001.md)için `IDE0029` : Unity nesneleri null birleştirme kullanmamalıdır.
    - [`USP0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/USP0002.md)için `IDE0031` : Unity nesneleri null yayma kullanmamalıdır.
    - [`USP0003`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/USP0003.md)için `IDE0051` : Unity Iletileri Unity çalışma zamanı tarafından çağrılır.
    - [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/USP0004.md)için `IDE0044` : SerializeField özniteliğine sahip alanlar ReadOnly yapılmamalıdır.

## <a name="4310"></a>4.3.1.0

Yayımlanma tarihi 4 Eylül 2019

### <a name="new-features"></a>Yeni Özellikler

- **Değerlendirmesinin**

  - Daha iyi tür görüntüleme desteği eklendi, yani `List<object>` yerine `List'1[[System.Object, <corlib...>]]` .

  - İşaretçi üye erişimi için destek eklendi, `p->data->member` ör.

  - Dizi başlatıcılarda örtük dönüştürmeler için destek eklendi, örn. `new byte [] {1,2,3,4}` .

## <a name="4300"></a>4.3.0.0

Yayın tarihi 13 Ağustos 2019

### <a name="new-features"></a>Yeni Özellikler

- **Sý**

  - MDS Protokolü 2,51 için destek eklendi.

- **Tümleştirme**

  - Sıralama, arama ve yenileme özellikleriyle "Unity örneğine Ekle" penceresi geliştirildi. PID artık yerel oyuncular için de görüntülenir (sahip olan işlemi almak için sistemdeki dinleme yuvaları sorgulanarak).

  - Asmdef dosyaları için destek eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Unity oynatıcılarla iletişim kurulurken hatalı biçimlendirilmiş iletilerin işlenmesi düzeltildi.

- **Değerlendirmesinin**

  - İfadelerde ad alanlarını sabit olarak işleme.

  - IntPtr türleriyle düzeltilen İnceleme.
  
  - Özel durumlarla düzeltilen Adımlama sorunları.

  - Sözde tanımlayıcıların ($exception gibi) sabit değerlendirmesi.

  - Geçersiz adreslerin başvurusu kaldırılırken kilitlenmeyi önleyin.  

  - Kaldırılmış AppDomain 'ler ile ilgili sorun düzeltildi.

## <a name="4201"></a>4.2.0.1

Yayın tarihi, 24 Temmuz 2019

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - Unity Proje Gezgini 'nden herhangi bir tür dosya oluşturmak için yeni bir seçenek eklendi.
  
  - Unity projeleri için hızlı derlemeler kullanırken tanılama önbelleğe almayı geliştirme.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Dosya Uzantısı iyi bilinen herhangi bir düzenleyici tarafından işlenmediğinde bir sorun düzeltildi.

  - Unity proje Gezgininde özel uzantılar için sabit destek.

  - Ana iletişim kutusunun dışında sabit kaydetme ayarları.

  - Eski Microsoft. VisualStudio. MPF bağımlılığı kaldırıldı.

## <a name="4110"></a>4.1.1.0

Yayımlanma tarihi 24 Mayıs 2019

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - Monodavranış API 'SI 2019,1 olarak güncelleştirildi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Hafif derleme etkinleştirildiğinde, çıktının düzeltilme uyarıları ve hataları düzeltildi.

  - Sabit basit derleme performansı.

## <a name="4100"></a>4.1.0.0

Yayımlanma tarihi 21 Mayıs 2019

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - Projeleri daha hızlı yeniden yüklemek için yeni Batch API 'SI için destek eklendi.

  - IntelliSense hatalarının ve uyarılarının kullanımı açısından Unity projelerinin tam derlemesini devre dışı bıraktı. Aslında Unity, dahili olarak hangi Unity 'nin yaptığını temsil eden sınıf kitaplığı projeleri içeren bir Visual Studio çözümü oluşturur. Bu şekilde, Visual Studio 'daki derlemenin sonucu, derleme işlem hattı kapalıyken Unity tarafından hiçbir şekilde kullanılmaz veya alınmaz. Visual Studio 'da oluşturma işlemi yalnızca hiçbir şey için kaynakları tüketiyor. Kendisine bağlı araçlara veya kuruluma sahip olduğunuz için tam bir yapıya ihtiyacınız varsa, bu iyileştirmeyi devre dışı bırakabilirsiniz (Unity için Araçlar/Seçenekler/araçlar/projelerin tam derlemesini devre dışı bırak).

  - Unity projesi yüklendiğinde Unity Proje Gezgini 'ni (UPE) otomatik olarak gösterin. UPE Çözüm Gezgini yanına yerleştirilir.

  - Unity 2019. x ile güncelleştirilmiş proje adı ayıklama mekanizması.

  - UPE içinde Unity paketleri için destek eklendi. Yalnızca başvurulan paketler (klasöründe manifest. JSON kullanılarak `Packages` ) ve yerel paketler ( `Packages` klasöre katıştırılmış) görünür.

- **Proje oluşturma:**

  - Çözüm dosyasını işlerken dış özellikleri koruyun.

- **Değerlendirmesinin**

  - Diğer ad nitelenmiş adlar için destek eklendi (şimdilik yalnızca genel ad alanı). Bu nedenle, ifade değerlendirici artık genel:: Namespace. Type biçimini kullanarak türleri kabul ediyor.

  - `pointer[index]`İşaretçi başvuru formuyla anlam ile aynı olan form için destek eklendi `*(pointer+index)` .

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Microsoft. VisualStudio. MPF ile ilgili sabitlenmiş bağımlılık sorunları.

  - Yüklü bir proje olmadan sabit UWP oynatıcı iliştirme.

  - Visual Studio henüz iliştirilmediğinde düzeltilen otomatik varlık veritabanı yenilemesi.

  - Etiketler ve onay kutuları ile ilgili sabit Tema sorunları.

- **Sý**

  - Statik oluşturucularla düzeltilen Adımlama.

## <a name="4005"></a>4.0.0.5

Yayın tarihi, 27 Şubat 2019

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Kurulum paketiyle Visual Studio sürüm algılaması düzeltildi.

  - Kullanılmayan derlemeler kurulum paketinden kaldırıldı.

## <a name="4004"></a>4.0.0.4

Yayın tarihi, 13 Şubat 2019

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - Yükleme sırasında Unity süreçlerini düzgün bir şekilde algılamak ve kurulum altyapısının dosya kilitlerini daha iyi işlemesini sağlamak için destek eklendi.

  - API güncelleştirildi `ScriptableObject` .

## <a name="4003"></a>4.0.0.3

Yayın tarihi 31 Ocak 2019

### <a name="new-features"></a>Yeni Özellikler

- **Proje oluşturma:**

  - Ortak ve serileştirilmiş alanlar artık uyarılara neden olmaz. `CS0649` `IDE0051` Bu Iletileri oluşturan Unity projelerinde ve derleyici uyarılarını otomatik olarak gizliyoruz.

- **Tümleştirme**

  - Unity Düzenleyicisi ve oynatıcı örneklerini görüntülemek için Kullanıcı deneyimi geliştirildi (Windows artık yeniden boyutlandırılabilir, tek biçimli kenar boşlukları kullanıyor ve bir yeniden boyutlandırma tutamacı görüntülüyor). Unity düzenleyicileri için Işlem kimliği bilgileri eklendi.

  - API güncelleştirildi `MonoBehaviour` .

- **Değerlendirmesinin**

  - Yerel işlevler için destek eklendi.

  - Sözde değişkenler (özel durum ve nesne tanımlayıcıları) için destek eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Bilinen ad görüntüleri ve temalarıyla ilgili bir sorun düzeltildi.

  - Varlık veritabanının otomatik olarak yenilenmesi sırasında hata ayıklama sırasında yalnızca Çıkış Penceresi yazın.

  - Monodavranış Sihirbazı filtrelemesinde sabit UI gecikmeleri.

- **Sý**

  - Eski protokol sürümleri kullanılırken adlandırılmış bağımsız değişkenlerde özel öznitelik okuma düzeltildi.

## <a name="4002"></a>4.0.0.2

Yayın tarihi, 23 Ocak 2019

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Deneysel derleme üretimi düzeltildi.

  - UI-iş parçacığı basıncını en aza indirmek için sabit proje dosyası olay işleme.

  - Toplu metin değişiklikleri ile sabit tamamlama sağlayıcısı.

- **Sý**

  - Kullanıcı hata ayıklama iletilerinin ekli hata ayıklayıcısına gösterilmesi düzeltildi.

## <a name="4001"></a>4.0.0.1

Yayın tarihi 10 Aralık 2018

### <a name="new-features"></a>Yeni Özellikler

- **Değerlendirmesinin**

  - İfade değerlendirmesi için NRefactory 'ın Roslyn tarafından değiştirildiği yer.

  - İşaretçiler için destek eklendi: başvuru, atama ve işaretçi aritmetiği (Bu, hem Unity 2018.2 + hem de yeni çalışma zamanı için gereklidir).

  - Dizi işaretçisi görünümü için (C++ ' da olduğu gibi) destek eklendi. Bir işaretçi ifadesi alın, sonra da bir virgül ve görmek istediğiniz öğe sayısını ekleyin.

  - Zaman uyumsuz yapılar için destek eklendi.

- **Tümleştirme**

  - Kayıt sırasında Unity 'nin varlık veritabanının otomatik olarak yenilenmesi için destek eklendi. Bu, varsayılan olarak etkindir ve Visual Studio 'da bir betiği kaydederken Unity tarafında yeniden derleme tetikleyecektir. Kayıt sırasında Unity 'nin Assetveritabanını yenilemek için Tools\Options\Tools içinde bu özelliği devre dışı bırakabilirsiniz.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Tercih edilen harici düzenleyici olarak Visual Studio seçilmediğinde, sabitlenmiş köprü etkinleştirme.

  - Hatalı biçimlendirilmiş veya desteklenmeyen ifadelerle ifade değerlendirmesi düzeltildi.

## <a name="4000"></a>4.0.0.0

Yayın tarihi 4 Aralık 2018

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - Visual Studio 2019 için destek eklendi (Visual Studio 2019 ' i dış betik düzenleyicisi olarak kullanabilmeniz için en az Unity 2018,3 gerekir).

  - HDPı ölçeklendirme, piksel kusursuz görüntüler ve tema için tam destek sayesinde Visual Studio görüntü hizmeti ve kataloğunu benimseyen.

### <a name="deprecated-features"></a>Kullanım dışı bırakılan özellikler

- **Tümleştirme**

  - Unity için Visual Studio Araçları, yalnızca Unity 5.2 + ' ı destekler (Unity 'nin yerleşik Visual Studio tümleştirmesiyle).

  - Unity için Visual Studio Araçları, yalnızca Visual Studio 2015 + ' u destekleyecektir.

  - Eski dil hizmeti, hata listesi ve durum çubuğu kaldırıldı.

  - Hızlı Monodavranış Sihirbazı kaldırıldı (adanmış IntelliSense desteğinin yararına).

## <a name="3903"></a>3.9.0.3

Yayın tarihi, 28 Kasım 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Çok birinci projede bulunan betikleri eklerken veya kaldırırken düzeltilen proje yeniden yükleme ve IntelliSense sorunları.

## <a name="3902"></a>3.9.0.2

Yayın tarihi 19 Kasım 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Sý**

  - Unity 'nin hata ayıklayıcı altyapısı ile iletişim kurmak için kullanılan kitaplıkta bir kilitlenme düzeltildi, özellikle ' Unity 'ye Ekle ' veya oyunu yeniden başlatma sırasında, Visual Studio veya Unity dondurma

## <a name="3901"></a>3.9.0.1

Yayımlanma tarihi, 15 Kasım 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Başka bir varsayılan düzenleyici seçildiğinde, sabit Unity eklentisi etkinleştirmesi.

## <a name="3900"></a>3.9.0.0

Yayın tarihi, 13 Kasım 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Proje oluşturma:**

  - Unity tarafından düzeltilen bir Unity performans hatası için geçici çözümü geri alındı.

## <a name="3807"></a>3.8.0.7

Yayımlanma tarihi, 20 Eylül 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Sý**

  - (3.9.0.2 'ten geri alma) Unity 'nin hata ayıklayıcı altyapısı ile iletişim kurmak için kullanılan kitaplıkta bir kilitlenme düzeltildi, özellikle ' Unity 'ye Ekle ' veya oyunu yeniden başlatma sırasında, Visual Studio veya Unity dondurma

## <a name="3806"></a>3.8.0.6

Yayın tarihi 27 Ağustos 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Proje ve çözümün yeniden yüklenmesi düzeltildi.

## <a name="3805"></a>3.8.0.5

Yayın 20 Ağustos 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Sabit proje izleme aboneliği elden çıkarma.

## <a name="3804"></a>3.8.0.4

14 Ağustos 2018 tarihinde yayınlandı

### <a name="new-features"></a>Yeni Özellikler

- **Değerlendirmesinin**

  - İşaretçi değerleri için destek eklendi.

  - Genel yöntemler için destek eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Birden çok projeyle birlikte akıllı yeniden yükleme değiştirildi.

## <a name="3803"></a>3.8.0.3

Yayın tarihi, 24 Temmuz 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Proje oluşturma:**

  - (3.9.0.0 'ten geri alma) Unity tarafından düzeltilen bir Unity performans hatası için geçici çözümü geri alındı.

## <a name="3802"></a>3.8.0.2

Yayın tarihi 7 Temmuz 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Proje oluşturma:**

  - Unity performans hatası için geçici geçici çözüm: proje oluştururken Cache Monoadaları.

## <a name="3801"></a>3.8.0.1

Yayın tarihi 26 Haziran 2018

### <a name="new-features"></a>Yeni Özellikler

- **Masının**

  - UserLog ve UserBreak komutları için destek eklendi.

  - Geç tür yükleme desteği eklendi (ağ yükü ve hata ayıklayıcı yanıt gecikmesini en iyi duruma getirme).

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Değerlendirmesinin**

  - Geliştirilmiş ikili işleç ifade değerlendirmesi ve yöntem arama.

## <a name="3800"></a>3.8.0.0

Yayımlanma tarihi 30 Mayıs 2018

### <a name="new-features"></a>Yeni Özellikler

- **Masının**

  - Zaman uyumsuz yapıların değişkenlerini görüntülemek için destek eklendi.

  - Derleyici yapıları ile uyarıları engellemek için kesme noktaları ayarlanırken iç içe türlerin işlenmesine yönelik destek eklendi.

- **Tümleştirme**

  - Gölgelendiriciler için TextMate dilbilgisi desteği eklendi (gölgelendirici kodu renklendirme için C++ iş yükü artık gerekli değildir).

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Proje oluşturma:**

  - Yeni Unity çalışma zamanı kullanılırken taşınabilir pdb 'yi artık mdb 'ye dönüştürmeyin.

## <a name="3701"></a>3.7.0.1

Yayımlanma tarihi 7 Mayıs 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Yükleyicinin**

  - Deneysel derlemeler kullanılırken sabitlenmiş bağımlılık sorunu.

## <a name="3700"></a>3.7.0.0

Yayımlanma tarihi 7 Mayıs 2018

### <a name="new-features"></a>Yeni Özellikler

- **Masının**

  - Düzenlenmiş hata ayıklama için destek eklendi (aynı Visual Studio oturumunda birden çok oynatıcı/düzenleyicide hata ayıklama).

  - Android USB oynatıcı hata ayıklama desteği eklendi.

  - UWP/IL2CPP Player hata ayıklama desteği eklendi.

- **Değerlendirmesinin**

  - Onaltılık tanımlayıcılar için destek eklendi.

  - Geliştirilmiş Gözcü penceresi değerlendirme deneyimi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Özel durum ayarlarının sabit kullanımı.

- **Proje oluşturma:**

  - Paket Yöneticisi derleme birimlerini oluşturma işleminden dışlayın.

## <a name="3605"></a>3.6.0.5

Yayın tarihi 13 Mart 2018

### <a name="new-features"></a>Yeni Özellikler

- **Proje oluşturma:**

  - Unity 2018,1 ' de yeni proje Oluşturucu desteği eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Özel projelerle bozulmuş durumları işleme düzeltildi.

- **Sý**

  - Next ifadesinin ayarlanması düzeltildi.

## <a name="3604"></a>3.6.0.4

Yayımlanma tarihi, 5 Mart 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Proje oluşturma:**

  - Sabit mono sürümü algılama.

- **Tümleştirme**

  - 2018,1 ve eklenti etkinleştirme ile ilgili sabit zamanlama sorunları.

## <a name="3603"></a>3.6.0.3

Yayın tarihi, 23 Şubat 2018

### <a name="new-features"></a>Yeni Özellikler

- **Proje oluşturma:**

  - .NET Standard için destek eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Proje oluşturma:**

  - Sabit Unity hedef Framework algılaması.

- **Sý**

  - UserCode dışında oluşturulan özel durumlarla ilgili sabit bir bölme.

## <a name="3602"></a>3.6.0.2

Yayın tarihi 7 Şubat 2018

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - 2017,3 için UnityMessage API yüzeyini güncelleştirin.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Yalnızca dış değişiklik üzerinde projeleri yeniden yükle (daraltma ile).

## <a name="3601"></a>3.6.0.1

24 Ocak 2018 ' de yayınlandı

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Otomatik pdb 'den mdb hata ayıklama sembol dönüştürme.

  - EditorPrefs. GetBool öğesine yapılan dolaylı çağrı, dizi boyutunu değiştirmeye çalışırken Inspector 'ı etkiliyor.

## <a name="3600"></a>3.6.0.0

Yayımlanma tarihi 10 Ocak 2018

### <a name="new-features"></a>Yeni Özellikler

- **Proje oluşturma:**

  - 2018,1 Monoadası başvuru modeli için destek eklendi.

- **Değerlendirmesinin**

  - $Exception tanımlayıcı için destek eklendi.

- **Sý**

  - Yeni Unity çalışma zamanına sahip öznitelikler aracılığıyla DebuggerHidden/Debuggerstepdesteği eklendi.

- **'Nı**

  - Sihirbazlar için ' en son ' sürümünü tanıtın.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Proje oluşturma:**

  - Oynatıcı projeleri için sabit proje GUID hesaplaması.

- **Sý**

  - Parçalama olaylarını işlerken bir yarış düzeltildi.

- **'Nı**

  - Yöntemi eklemeden önce Roslyn bağlamını yenileyin.

## <a name="3503"></a>3.5.0.3

Yayımlanma tarihi 9 Ocak 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Otomatik pdb 'den mdb hata ayıklama sembol dönüştürme.

## <a name="3502"></a>3.5.0.2

Yayın tarihi 4 Aralık 2017

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - Artık Unity'de bir betik eklediğinizde veya kaldırdığınızda Unity projeleri Visual Studio'da otomatik olarak yeniden yükleniyor.

- **Sý**

  - Unity düzenleyicisinde hata ayıklamak için Xamarin ve Mac için Visual Studio tarafından paylaşılan mono hata ayıklayıcısını kullanma seçeneği eklendi.

  - Taşınabilir hata ayıklama sembol dosyaları için destek eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Düzeltilen kurulum bağımlılıkları sorunları.

  - Sabit Unity API Yardım menüsü gösterilmiyor.

- **Proje oluşturma:**

  - IL2CPP/. NET 4,6 arka ucu ile UWP oyunu üzerinde çalışırken düzeltilen oynatıcı proje üretimi.

  - Derleme dosya adına yanlışlıkla eklenmiş ek. dll uzantısı düzeltildi.

  - Genel bir tane yerine belirli bir Project API Uyumluluk düzeyinin sabit kullanımı.

  - Varsayılan olarak ' true ' olduğundan AllowAttachedDebuggingOfEditor Unity bayrağını zorlamayın.

## <a name="3402"></a>3.4.0.2

Yayın tarihi 19 Eylül 2017

### <a name="new-features"></a>Yeni Özellikler

- **Proje oluşturma:**

  - Assembly. JSON derleme birimleri için destek eklendi.

  - Unity derlemelerinin proje klasörüne kopyalanması durduruldu.

- **Sý**

  - Yeni Unity çalışma zamanı ile sonraki ifadeyi ayarlamaya yönelik destek eklendi.

  - Yeni Unity çalışma zamanına sahip onlu tür için destek eklendi.

  - Örtük/açık dönüştürmeler için destek eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Değerlendirmesinin**

  - Örtük boyut ile sabit dizi oluşturma.

  - Sabit derleyici, Yerellerle oluşturulmuş öğeler.

- **Proje oluşturma:**

  - 4,6 API düzeyi için Microsoft. CSharp 'e yönelik sabit başvuru.

## <a name="3302"></a>3.3.0.2

15 Ağustos 2017 ' de yayınlandı

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Proje oluşturma:**

  - Unity 5,5 ve önceki sürümlerde Visual Studio çözüm üretimi düzeltildi.

## <a name="3300"></a>3.3.0.0

14 Ağustos 2017 tarihinde yayınlandı

### <a name="new-features"></a>Yeni Özellikler

- **Değerlendirmesinin**

  - Yeni Unity çalışma zamanı ile yapı oluşturma desteği eklendi.

  - İşaretçiler için minimum aList desteği eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Değerlendirmesinin**

  - Temel elemanlar üzerinde sabit Yöntem çağırma.

  - BeforeFieldInit ile işaretlenmiş türlerle sabit alan değerlendirmesi.

  - İkili işleçlerle (substract) desteklenmeyen ve olmayan çağrılar düzeltildi.

  - Visual Studio Watch 'a öğe eklenirken oluşan sorunlar düzeltildi.

- **Proje oluşturma:**

  - MCS. rsp dosyalarıyla düzeltilen derleme adı başvuruları.

  - API düzeyleriyle düzeltilen tanımlar.

## <a name="3200"></a>3.2.0.0

Yayımlanma tarihi 10 Mayıs 2017

### <a name="new-features"></a>Yeni Özellikler

- **Yükleyicinin**

  - MEF önbelleğini temizleme desteği eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Kod Düzenleyicisi:**

  - Özel özniteliklerle sabit sınıflandırma/tamamlama.

  - Unity iletileriyle düzeltilen titreşme.

## <a name="3100"></a>3.1.0.0

Yayın tarihi, 7 Nisan 2017

### <a name="new-features"></a>Yeni Özellikler

- **Sý**

  - Yeni Unity çalışma zamanı (.NET 4,6/C# 6 uyumluluğuyla) için destek eklendi.

- **Proje oluşturma:**

  - .NET 4,6 profili için destek eklendi.

  - MCS. rsp dosyaları için destek eklendi.

  - Unity 5,6 kullanıldığında her zaman güvenli olmayan derleme anahtarını etkinleştirin.

  - Windows Mağazası platformu ve il2cpp arka ucu kullanılırken "oynatıcı" proje üretimi için destek eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Kod Düzenleyicisi:**

  - Otomatik tamamlama ile Yöntem eklendikten sonra düzeltilen giriş işareti konumu.

- **Proje oluşturma:**

  - Derleme sürümü işleme sonrası kaldırıldı.

## <a name="3001"></a>3.0.0.1

Yayın tarihi 7 Mart 2017

### <a name="this-version-includes-all-new-features-and-bug-fixes-introduced-with-28x-series"></a>Bu sürüm, 2.8. x serisi ile tanıtılan tüm yeni özellikleri ve hata düzeltmelerini içerir.

## <a name="2820---30-preview-3"></a>2.8.2.0-3,0 Preview 3
25 Ocak 2017 tarihinde yayınlandı

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Proje oluşturma:**

  - İkinci kez bir ikili DLL olarak, önce bir proje başvurusu olarak başvurulan eklenti projelerinin bulunduğu bir sabit gerileme.

## <a name="2810---30-preview-2"></a>2.8.1.0-3,0 Preview 2
Yayın tarihi, 23 Ocak 2017

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Kod Düzenleyicisi:**

  - Küme ayracı tamamlanana gerek olmadan bir öznitelik bildirimi başlatıldığında kilitlenme düzeltildi.

- **Sý**

  - Yeni Unity derleyicisi/çalışma zamanı altındaki eş değerleri içeren sabit işlev kesme noktaları.

  - Bağlanabilir kesme noktası (karşılık gelen kaynak-konum bulunamadı) durumunda uyarı eklendi.

- **Proje oluşturma:**

  - Özel/yerelleştirilmiş karakterlerle sabit csproj oluşturma.

  - Kitaplık (Facebook SDK gibi) dışındaki varlık başvuruları.

- **Muht**

  - Yükleme veya kaldırma sırasında Unity 'nin çalışmasını engellemek için denetim eklendi.

  - Uzak Unity belgelerini hedeflemek için https 'ye geçildi.

## <a name="2800---30-preview"></a>2.8.0.0-3,0 Preview
Yayınlanan 17 Kasım 2016

### <a name="new-features"></a>Yeni Özellikler

- **Genel**

  - Visual Studio 2017 yükleyici desteği eklendi.

  - Visual Studio 2017 uzantı desteği eklendi.

  - Yerelleştirme desteği eklendi.

- **Kod Düzenleyicisi:**

  - Unity iletileri için C# IntelliSense eklendi.

  - Unity iletileri için C# kod renklendirme eklendi.

- **Sý**

  - ,, Doğrudan atama,, ifadeleri için destek eklendi `is` `as` `default` `new` .

  - Dize Concat ifadeleri için destek eklendi.

  - Tamsayı değerlerinin onaltılı görünümü için destek eklendi.

  - Yeni geçici değişkenler (deyimler) oluşturma desteği eklendi.

  - Örtük ilkel dönüştürmeler için destek eklendi.

  - Bir tür beklendiğinde veya bulunamadığında daha iyi hata iletileri eklendi.

- **Proje oluşturma:**

  - Proje adlarından CSharp son eki kaldırıldı.

  - Bir sistem genelinde MSBuild hedef dosyasına başvuru kaldırıldı.

- **'Nı**

  - Düzenleyici veya EditorWindow gibi davranış türlerinde Unity iletileri için destek eklendi.

  - Unity iletilerini eklemek ve biçimlendirmek için Roslyn 'e geçildi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Sý**

  - Genel türler değerlendirilirken Unity 'yi kilitlenen bir hata düzeltildi.

  - Null yapılabilir türlerin sabit işlenmesi.

  - Numaralandırmaların sabit işlenmesi.

  - İç içe üye türlerin sabit işlenmesi.

  - Koleksiyon dizin oluşturucu erişimi düzeltildi.

  - Yeni C# derleyicisi ile Yineleyici çerçeveleri hata ayıklama için sabit destek.

- **Proje oluşturma:**

  - Unity Web oynatıcı hedeflenirken derlemeyi önleyen hata düzeltildi.

  - Web kodlamalı dosya adı ile bir betiği derlerken derlemeyi önleyen hata düzeltildi.

## <a name="2300"></a>2.3.0.0

Yayın tarihi 14 Temmuz 2016

### <a name="new-features"></a>Yeni Özellikler

- **Genel**

  - Visual Studio 'nun hata listesindeki Unity konsol günlüklerini devre dışı bırakma seçeneği eklendi.

  - Oluşturulan proje özelliklerinin değiştirilmesine izin veren bir seçenek eklendi.

- **Sý**

  - Metin, XML, HTML ve JSON dize Görselleştiriciler eklendi.

- **'Nı**

  - Eksik Monodavranışlar eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Genel**

  - Visual Studio ayarlarının içindeki denetimlerin görüntülenmesini önleyen ReSharper ile bir çakışma düzeltildi.

  - Bazı durumlarda hata ayıklamayı önleyen Xamarin ile bir çakışma düzeltildi.

- **Sý**

  - Hata ayıklarken Visual Studio 'Nun dondurmasına neden olan bir sorun düzeltildi.

  - Visual Studio 2015 ' de işlev kesme noktaları ile ilgili bir sorun düzeltildi.

  - Birkaç ifade değerlendirme sorunu düzeltildi.

## <a name="2200"></a>2.2.0.0

Yayımlanma tarihi 4 Şubat 2016

### <a name="new-features"></a>Yeni Özellikler

- **'Nı**

  - **Tek davranış uygulama** sihirbazına akıllı arama eklendi.

  - Sihirbazlar bağlamı uyumlu hale getirilir; Örneğin, NetworkBehavior iletileri yalnızca bir NetworkBehavior ile çalışırken kullanılabilir.

  - Sihirbazlardaki NetworkBehavior iletileri için destek eklendi.

- **'SıNı**

  - Tek davranış iletilerinin görünürlüğünü yapılandırmak için bir seçenek eklenmiştir.

  - Unity projeleriyle ilgili olmayan Visual Studio özellik sayfaları kaldırıldı.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Proje oluşturma:**

  - Unity 4,6 ' de UnityEngine ve UnityEditor 'a yönelik sabit başvurular.

  - Unity, OSX üzerinde çalışırken proje dosyalarının sabit üretimi düzeltildi.

  - Diyez işareti (#) karakteri içeren proje adlarının sabit işlenmesi.

  - Kısıtlanmış oluşturulan projeler C# 4 ' e.

- **Sý**

  - Unity eş içinde hata ayıklanırken ifade değerlendirmesiyle ilgili bir sorun düzeltildi.

  - Hata ayıklarken Visual Studio 'Nun dondurmasına neden olan bir sorun düzeltildi.

- **'SıNı**

  - [Sekmeler Studio](https://tabsstudio.com/) Visual Studio uzantısıyla uyumsuzluk düzeltildi.

- **Yükleyicinin**

  - HKLM Kayıt defteri girişleri oluşturarak, bir VSTU (tüm kullanıcılar için yükleme) makine genelinde yüklemesini destekler.

  - Aynı VSTU sürümü Visual Studio 'nun birden çok farklı sürümüne yüklendiğinde, VSTU 'nin kaldırılmasıyla ilgili sorunlar düzeltildi. Örneğin, VSTU **2015** 2.1.0.0 ve vstu **2013** 2.1.0.0 her ikisi de yüklüyse.

## <a name="2100"></a>2.1.0.0

Yayın tarihi, 8 Eylül 2015

### <a name="new-features"></a>Yeni Özellikler

- Unity 5,2 için destek

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Unity < 4,2 ' de menü öğelerini görüntüle

- Visual Studio XML IntelliSense dosyalarını kilitlediğinde bir hata iletisi artık görüntülenmez.

- \<When Changed>Koşullu bağımsız değişken bir Boole değeri olmadığında, koşullu kesme noktaları> <tanıtıcısı.

- Windows Mağazası uygulamaları için UnityEngine ve UnityEditor Derlemeleriyle ilgili sabit başvurular.

- Hata ayıklayıcıda adımla düzeltilen hata: adım, genel özel durum.

- Visual Studio 2015 ' de sabit isabet sayısı kesme noktaları.

## <a name="2000"></a>2.0.0.0

Yayın tarihi 20 Temmuz 2015

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Unity tümleştirmesi:**

  - DLL ve hata ayıklama sembolleri (PDB) içeri aktarılırken Visual Studio 2015 ile oluşturulan hata ayıklama simgelerinin dönüştürülmesi düzeltildi.

  - Bir MDB dosyası da sağlanmasının dışında, bir DLL ve hata ayıklama sembolleri (PDB) içeri aktarırken her zaman MDB dosyaları oluştur.

  - Bir obj diziniyle Unity proje dizininin sabit bir şekilde kirmi düzeltildi.

  - System. xml. Link ve System. Runtime. Serialization başvuruları düzeltildi.

  - Proje dosyası oluşturma API kancalarına birden çok abone desteği eklendi.

  - Oluşturulacak dosyalardan biri kilitlendiğinde bile proje dosya oluşturmayı her zaman doldurun.

  - C# projesine dahil edilecek dosyaları belirtirken uzantı filtresinde * joker karakterleri için destek eklendi.

- **Visual Studio tümleştirmesi:**

  - Üretkenlik güç araçlarıyla bir uyumluluk sorunu düzeltildi.

  - Olaylar ve temsilciler bildirimlerinin etrafında Monodavranışlar üretme düzeltildi.

- **Sý**

  - Hata ayıklanırken olası dondurma düzeltildi.

  - Belirli yığın çerçevelerinde Yerellerden görüntülenmeyen bir sorun düzeltildi.

  - Boş dizileri inceliyor düzeltildi.

## <a name="1990---20-preview-2"></a>1.9.9.0-2,0 Preview 2
Yayın 2 Nisan 2015

### <a name="new-features"></a>Yeni özellikler

- **Unity Proje Gezgini:**

  - Unity proje Gezgininde bir dosyayı yeniden adlandırırken otomatik olarak sınıfı yeniden adlandır (bkz. **Seçenekler** iletişim kutusu).

  - Unity proje Gezgininde yeni oluşturulan betikleri otomatik olarak seçin.

  - Unity proje Gezgininde etkin betiği izleyin (bkz. **Seçenekler** iletişim kutusu).

  - Visual Studio Çözüm Gezgini ikili olarak eşitler (bkz. **Seçenekler** iletişim kutusu).

  - Unity proje Gezgininde Visual Studio simgelerini benimseyin.

- **Sý**

  - Kaydedilmiş veya son kullanılan hata ayıklama hedefleri listesinden etkin hata ayıklama hedefini seçin (bkz. **Seçenekler** iletişim kutusu).

  - Tek davranış yöntemlerinde işlev kesme noktaları oluşturun ve bunları birden çok MonoBehavior sınıfına uygulayın.

  - Hata ayıklayıcıda nesne KIMLIĞI oluşturma desteği.

  - Hata ayıklayıcıda destek kesme noktası isabet sayısı.

  - Hata ayıklayıcıda kesme özel durumunu destekle (deneysel. Bkz. **Seçenekler** iletişim kutusu).

  - Hata ayıklayıcıda ifadeler değerlendirilirken nesne ve dizi oluşturulmasını destekler.

  - Hata ayıklayıcıda değerlendirme ifadeleri olduğunda null karşılaştırmayı destekler.

  - Hata ayıklayıcı 'da eski üyeleri filtrele Windows izleme.

- **Yükleyicinin**

  - En iyi duruma getirilmiş Unity için Visual Studio Araçları uzantısı kaydı.

  - Unity 5 için Unity için Visual Studio Araçları paketini yükler.

- **Belgeler:** Belge oluşturma performansını geliştirir.

- **Sihirbazlar:** Unity 4,6 ve Unity 5 için yeni MonoBehavior yöntemlerini destekler.

- **Unity:** Proje dosyası oluşturma sırasında. rsp dosyalarında güvenli olmayan bayraklar ve özel tanımlar arama yapın.

- **Kullanıcı arabirimi:** Visual Studio 'da Unity için Visual Studio Araçları **seçenekleri** iletişim kutusu eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Unity Proje Gezgini:**

  - Dosyalar taşındıktan veya Visual Studio Çözüm Gezgini yeniden adlandırıldıktan sonra Unity proje Gezginini yenileyin.

  - Unity proje Gezgininde dosyaları yeniden adlandırırken seçimleri koru.

  - Unity proje Gezgininde dosyalar çift tıklandığında otomatik genişletmeyi önleyin ve daraltın.

  - Yeni seçilen dosyaların Unity proje Gezgininde göründüğünden emin olun.

- **Sý**

  - Hata ayıklayıcıda ifadeler değerlendirilirken olası bir Visual Studio donmasını önleyin.

  - Yöntem etkinleştirmeleri hata ayıklayıcıda doğru etki alanında gerçekleşdiğinden emin olun.

- **'Yi**

  - UnityVS. OpenFile konumunu Unity 5 ile düzeltin.

  - Pdb2mdb konumunu Unity 5 ile düzeltin.

  - Proje dosyası oluşturma sırasında olası bir özel durumu önleyin.

  - OSX üzerinde Unity çalıştırırken olası dondurma önleme.

  - İç özel durumları işleyin.

  - Unity konsol günlüklerini VS hata listesine gönderin.

- **Belgeler:** Yeni Unity belgeleri için doğru belge oluşturma.

- **Proje:** Gerektiğinde de Unity. meta dosyalarını taşıyın ve yeniden adlandırın.

- **Sihirbazlar:** Kod oluştururken MonoBehavior yöntem parametrelerinin sırasını düzeltin.

- **Kullanıcı arabirimi:** Bağlam menüsü ve simgeler için Visual Studio temalarını destekleme.

## <a name="1980---20-preview"></a>1.9.8.0-2,0 Preview
Yayımlanma tarihi, 12 Kasım 2014

### <a name="new-features"></a>Yeni özellikler

- Visual Studio 2015 için destek.

- Visual Studio 2015 ' de Unity gölgelendiriciler için kod renklendirme.

- Hata ayıklama sırasında değerlerin görselleştirilmesi geliştirildi:

  - ArrayLists, listeler, hashtables ve sözlükler için daha iyi görselleştirme.

  - Genel olmayan üyeleri ve statik üyeleri, izleme ve yerel görünümlerde kategori olarak gösterin.

  - Unity 'nin SerializedProperty özelliğinin yalnızca özellik için geçerli olan değer alanını değerlendirmek için iyileştirilmiş görünümü.

  - Sınıflar ve yapılar için DebuggerDisplayAttribute desteği.

  - DebuggerTypeProxyAttribute desteği.

- Kullanıcı kodlama kurallarına göre sihirbazları kullanarak Monodavranış yöntemlerinin eklenmesini sağlayın.

- UnityVS tarafından oluşturulan projelerde derleme zamanı metin şablonları için destek uygulayın.

- UnityVS tarafından oluşturulan projelerde ResX kaynakları için destek uygulayın.

- Unity 'den Visual Studio 'da gölgelendiriciler açmayı destekler.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Visual Studio 'da Iliştirme ve yürütme tetiklendikten sonra Unity 'de oyunu başlatmadan önce Yuvaları Temizleme. Bu, Attach ve Play kullanılırken Unity ile VS arasındaki bağlantının kararlılığı ile ilgili bazı sorunları düzeltir.

- Unity 'nin betik altyapısı hata ayıklayıcısı arabirimindeki, Unity 'nin donmasına engel olan yöntemlerin çağrılmasını önleyin. Bu, hata ayıklayıcı eklenirken Unity dondurma 'yı düzeltir.

- Kullanılabilir sembol olmadığında çağrı yığınlarının görüntülenmesini düzeltir.

- Gerekmiyorsa, günlük geri aramayı kaydedin.

## <a name="1920"></a>1.9.2.0

Yayın tarihi 9 Ekim 2014

### <a name="new-features"></a>Yeni özellikler

- Unity oynatıcıların algılanmasını geliştirme.

- Dosya openmizi kullanırken, Unity 'yi dosya adının yanı sıra satır numarası olarak geçirin.

- Yerel belge yoksa, çevrimiçi Unity belgeleri için varsayılan değer.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Bir etki alanı yeniden yüklendikten sonra bir kesme noktasına gelindiğinde olası Unity kilitlenmeyi düzeltir.

- Bir etki alanı yeniden yüklendikten sonra, konfigürasyonumuzu veya Windows 'u kapatırken Unity konsolunda gösterilen özel durumları düzeltir.

- Yerel olarak çalışan 64bit Unity algılama işlemini düzeltir.

- Sihirbazlardaki Unity sürümü başına MonoBehaviours filtrelemesini onarın.

- Uzantı filtresi boşsa tüm varlıkların proje dosyalarına dahil edildiği hatayı düzeltir.

## <a name="1910"></a>1.9.1.0

Yayımlanma tarihi, 22 Eylül 2014

### <a name="new-features"></a>Yeni özellikler

- Bağlama kesme noktasını kaynak konumlarına iyileştirin.

- Hata ayıklayıcının Ifade değerlendirmesinde aşırı yüklenmiş yöntemler için destek.

- Hata ayıklayıcının Ifade değerlendirmesinde paketleme temelleri ve değer türleri için destek.

- Anonim yöntemlerde hata ayıklarken C# yerel değişkenleri ortamını yeniden oluşturmayı destekler.

- Visual Studio 'dan dosyaları silerken veya yeniden adlandırırken. meta dosyalarını silin ve yeniden adlandırın.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Visual Studio temalarını işlemeyi çözme. Daha önce, siyah temalardaki iletişim kutuları boş görünebilir.

- Unity yeniden derlenirken hata ayıklayıcıyı bağlarken Unity donması 'nı düzeltemedi.

- Başka bir sistemde derlenen uzak düzenleyicilerde veya yürütücülerde hata ayıklarken kesme noktalarını düzeltme.

- Kesme noktası isabet edildiğinde olası bir Visual Studio kilitlenmesine çözüm.

- Kesme noktaları bağlantısını, bellekten kaldırılmamasına engel olmak için düzeltir.

- Kapsam dışında görünen canlı değişkenlerin önüne geçmek için hata ayıklayıcıda değişken kapsamının işlenmesini düzeltir.

- Hata ayıklayıcının Ifade değerlendirmesi içindeki statik üyelerin aramasını düzeltir.

- Statik alanları ve özellikleri göstermek için hata ayıklayıcının Ifade değerlendirmesinde türlerin görüntülenmesini düzeltir.

- Unity proje adları, Visual Studio yasaklıyor (Connect sorun #948666) özel karakterler içerdiğinde çözüm üretimini düzeltir.

- Seçenek işaretlendikten sonra konsol olaylarının gönderilmesini hemen durdurmak için Visual Studio Araçları Unity paketini onarın (bağlantı verme #933357).

- UnityEngine. UI gibi yeni API 'Lerin başvurularını doğru şekilde yeniden oluşturmak için başvuruları algılamayı, UnityVS tarafından oluşturulan projelerde düzeltir.

- Yükleyici, bozulan yüklemeleri önlemek için yüklemeden önce Visual Studio 'Nun kapatılmasını gerektirecek şekilde düzeltilir.

- Unity başvuru derlemelerini, tüm VSTU sürümleri arasında paylaşılan, uygun bir bağımsız bileşen olarak yüklemek için yükleyiciyi onarın.

- Unity 'nin 64 bit sürümlerinde VSTU ile betikleri açmayı onarma.

## <a name="1900"></a>1.9.0.0

Piyasaya çıkarılan 29 Temmuz 2014

### <a name="new-features"></a>Yeni özellikler

- Unity hata ayıklayıcısı Ekle penceresinde, hata ayıklama için özel bir IP ve bağlantı noktası girme özelliğini ekleyin.

- Unity 'yi arka planda çalışacak şekilde ayarlamak için yapılandırma seçeneği ekleyin.

- Yalnızca çözüm ve proje dosyaları ya da proje dosyaları oluşturmak için yapılandırma seçeneği ekleyin.

- Başlangıç hedefi: Unity 'ye eklemek veya Unity 'ye eklemek ve oynatmak için seçin.

- Hata ayıklayıcıda çok boyutlu dizileri görüntüleme.

- Yeni Unity oynatıcı hata ayıklama bağlantı noktalarını işleyin.

- Unity 'nin 4,6 GUI derlemeleri gibi yeni Unity derlemelerine başvuruları işleyin.

- Hata ayıklarken yerel değişkenleri düzgün şekilde göstermek için kapanışları kaldırır.

- Hata ayıklarken oluşturulan yineleyiciler değişkenlerini bağımsız değişkenlerle kaldırır.

- Proje yeniden yüklendikten sonra Unity Proje Gezgini 'nin durumunu koru.

- Unity proje Gezginini geçerli belgeyle eşitleyecek bir komut ekleyin.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Koşulu hata ayıklayıcıya başlamadan önce ayarlanan koşullu kesme noktalarını düzeltir.

- Uyarıları önlemek için UnityEngine başvurularını onarın.

- Unity betas için ayrıştırma sürümlerini onarma.

- Bir kesme noktasına veya adımlamayı vurarak değişkenlerin yerel değişkenler penceresinde gözükmesine neden olan sorunu giderme.

- Visual Studio 2013 değişkenleri araç ipuçlarını düzeltir.

- Unity 4,5 için IntelliSense belgelerinin oluşturulmasını düzeltir.

- Bir etki alanı yeniden yüklendikten sonra Unity/Visual Studio iletişimini onarın (Unity 'de Oynat/Durdur).

- Visual Studio temalarının parçalarını işlemeyi çözme.

> [!IMPORTANT]
> C#, Unity ekosisteminde önceden baskın bir dil olmasını sağlar. yeni örnek varlıklar C# ' ta, Unity belgelerinin varsayılan değeri C# ' dir; C# deneyimine daha iyi odaklanmak için, Unityscrıpt ve Boo 'nun temel desteğini kaldırdık. Sonuç olarak, VSTU çözümleri artık C# ' dir ve yükleme için çok daha hızlıdır.

## <a name="1820"></a>1.8.2.0

Yayın tarihi 7 Ocak 2014

### <a name="new-features"></a>Yeni özellikler

- , Düzenleyicilerin uzaktan keşfi için Mavericks adresindeki Ağ katmanında bir sorunu geçici olarak çözmek.

- Uzak Unity oynatıcılarını keşfetmeye yönelik yeni bağlantı noktalarını işleyin.

- Geçerli derleme hedefine özel UnityEngine derlemesine başvur.

- Oluşturulan projelere dahil edilecek dosyaları filtrelemek için ayar ekleyin.

- Konsol günlüklerinin Visual Studio hata listesine gönderilmesini devre dışı bırakmak için ayar ekleyin. Konsol günlüklerini almak için Unity 'de kayıtlı yalnızca bir geri çağırma işlemi olduğu için, PlayMaker veya Console Pro kullanıyorsanız bu faydalıdır.

- MDB hata ayıklama sembolleri oluşturmayı devre dışı bırakmak için ayar ekleyin. Bu, mdb 'yi kendiniz oluşturuyorsanız yararlı olur.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Unity 'den VS >= 4,2 ' de açılan dosyalar IntelliSense 'i kaybedecektir.

- Özel temaları işlemek için VS iletişim kutusumuzu düzeltir.

- UPE öğesinin bağlam menüsünü kapatmayı düzeltir.

- Sürüme özgü oluşturulan derleme eşitleme dışı olduğunda Unity 'de kilitlenmeyi önleyin.

## <a name="1810"></a>1.8.1.0

Yayın tarihi 21 Kasım 2013

### <a name="new-features"></a>Yeni özellikler

- Unity 4,3 API 'Leri ile Monodavranış sihirbazları ayarlandı.

- Tek davranış sihirbazları, kullandığınız sürüme bağlı olarak Unity API 'Larını filtrelemedir.

- Unity > 4,1 için projelere System. xml. Linq başvurusu ekleyin.

- İletiye StackTrace 'in başlangıcını dahil etmek için hata ayıklama. log çağrılarımızın önmizi yapın.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Visual Studio 'da JavaScript dosyalarının varsayılan işlemesini etkileyebilecek bir hata düzeltildi.

- Bu kez, gerçek zamanlı olarak VS. olarak görünen beyaz bir piksel düzeltildi.

- Bir SCM tarafından ReadOnly olarak işaretlenmişse UnityVS. VersionSpecific derlemesini silme işlemi düzeltildi.

- UnityVS paketinde yuva oluşturulurken oluşan özel durumlar düzeltildi.

- Visual Studio derlemelerinden hisse senedi görüntüleri yüklenirken Visual Studio 'da kilitlenme düzeltildi.

- Unity 'nin kaynak yapıları için UnityVS. VersionSpecific 'ın oluşturulmasında hata düzeltildi.

- Unity paketinde bir yuva açılırken olası bir dondurma düzeltildi.

- Unity projesinin adında bir tire (-) ile işlenmesi düzeltildi.

- Unity 'de betikler 4,2 ve üzeri için ALT + sekme sırasını karıştırmayın.

## <a name="1800"></a>1.8.0.0

Yayın tarihi, 24 Eylül 2013

### <a name="new-features"></a>Yeni özellikler

- Büyük ölçüde geliştirilmiş hata ayıklayıcı bağlantı hızı.

- Unity 4,2 ve üzeri üzerine dosya ve satıra gezintiyi otomatik olarak işler.

- Koşullu kesme noktaları.

- Proje dosya üreticisi artık T4 şablonlarını işler.

- Yeni API 'lerle MonBehavior sihirbazları ' nı güncelleştirin.

- Unity türleri Için C# ' de IntelliSense belgeleri.

- Aritmetik ve mantıksal ifadeler değerlendirmesi.

- Uzaktan hata ayıklama önizlemesi için uzak düzenleyicilerin daha iyi bulunması.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Hata ayıklayıcının bağlantısını kestikten sonra VS 'deki bir iş parçacığını sızdığımız bir hata düzeltildi.

- VS 'de görünen beyaz piksel düzeltildi.

- Durum çubuğu simgesinde tıklamaların işlenmesi düzeltildi.

- Eklentiler klasörlerinde Derlemelerle başvuruların üretimi düzeltildi.

- Özel durumlar söz konusu olduğunda UnityVS paketinden yuvaların oluşturulması düzeltildi.

- Yeni bir UnityVS sürümünün algılanması düzeltildi.

- Lisansın süre dolduğunda Lisans Yöneticisi istemi düzeltildi.

- VS 'nin işlem hata ayıklayıcısına karşılık gelen işlem listesini içeren bir hata düzeltildi.

- Yerel görünümde Boole değerleri değiştirme değeri düzeltildi.

## <a name="1220"></a>1.2.2.0

Yayın tarihi, 9 Temmuz 2013

### <a name="bug-fixes"></a>Hata düzeltmeleri

- İfade değerlendirici içinde tam nitelikli adları işleyin.

- Unity betik altyapısının yanlış StackFrame verileri gönderdiği özel durum işlemeyle ilgili bir dondurma düzeltildi.

- Web hedefleri için düzeltilen derleme işlemi.

- Visual Studio başlatıldığında ve silinen bir dosyanın başlangıçta açılacak dosya listesinde olması durumunda oluşabilecek bir hata düzeltildi.

- Derlenmiş gölgelendiriciler gibi betik olmayan dosyaları işlemek için fixed UnityVS. OpenFile.

- Şimdi tüm C# projelerinden Boo. lang ve UnityScript. lang başvurduk.

- Projede özel karakterler varsa, projelerdeki başvuruların sabit üretimi.

- Geçici çözüm, yöntemin atılmış projelere çağrı yaptığı bir VS sorunu, birden çok NullReferenceException MessageBox tetikleyecektir.

- Unity 4,2 Beta derlemelerinin sabit işlenmesi.

## <a name="1210"></a>1.2.1.0

Yayımlanma tarihi, 9 Nisan 2013

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Bir GÇ hatası (salt okuma dosyaları veya Visual Studio tarafından kilitlenen dosyalar gibi) durumunda kod tamamlama için Unity derlemelerinin sabit yerel dağıtımı.

- Unity 'den bir betik açmak, Visual Studio 'da zaten açılırsa dosyayı odaklanmaz.

- Yeni özel durum işlemenin sabit performans sorunu.

- Bazı dış dll 'lerde kesme noktalarının sabit bağlaması.

## <a name="1200"></a>1.2.0.0

Yayımlanma tarihi, 25 Mart 2013

### <a name="new-features"></a>Yeni özellikler

- Büyük ölçüde geliştirilmiş hata ayıklayıcı bağlantı hızı.

- Daha büyük projeler için iyileştirilmiş Unity Proje Gezgini.

- İşlenmiş ve işlenmemiş özel durumların üzerine kesmek (veya not etmek) için Visual Studio ayarlarını dikkate alır.

- Yerel değişkenlerde ToString çağrısı yapmak için Visual Studio ayarını dikkate alır.

- Yeni menü hata ayıklama-> Unity oynatıcısında hata ayıklamak için kullanabileceğiniz Unity hata ayıklayıcısı ekleyin.

- Çözüm dosyası oluşturma sırasında UnityVS çözümüne eklenen özel projeleri koruma.

- Yeni klavye kısayolu Ekle CTRL + ALT + M->, CTRL + H tuşlarına basarak Unity işlevine veya üyesine yönelik Unity belgelerini giriş işareti konumunda görüntüleyin.

- Visual Studio 'dan derlerken derleyici yanıt dosyalarını (rsp) hesaba alın.

- Oluşturucu metotlarında hata ayıklama sırasında değişkenleri göstermek için derleyicinin ürettiği türler kaldırılıyor.

- Paylaşılan bir klasörü Unity 'ye yapılandırma gereksinimini kaldırarak uzaktan hata ayıklamayı kolaylaştırın. Artık yalnızca Windows 'da Unity projenize erişiminizin olması gerekir.

- Özel bir Unity profilini standart .net hedef profili olarak yükler. Bu, ReSharper tarafından gösterebilecek tüm hatalı pozitif durumları düzeltir.

- Bir Unity betik altyapısı hatasına geçici olarak çalışın, bu nedenle hata ayıklayıcı düzgün şekilde kaydedilmemiş iş parçacıklarında kesintiye uğramaz.

- Dosya açma isteği üzerinde kilitlenme sırasında dosyaları açmak için gereken yerde bir yarış durumu oluşmasını önlemek için dosyayı Opener 'da yeniden çalışın.

- UnityVS, artık projeyi oluştururken ve artık dosya Kaydet 'de değil derlemeyi yenilemeyi istiyor.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Özel .net profiliniz düzeltildi

- Tema tümleştirmesi düzeltildi, bu, VS 2012 koyu temasıyla ilgili sorunlarımızı düzeltir.

- VS 2012 ' de sabit hızlı davranış kısayolu.

- Hata ayıklama ve ana olmayan iş parçacığı bir kesme noktasına isabet edildiğinde oluşabilecek bir Adımlama sorunu düzeltildi.

- İnt gibi tür diğer adların sabit Unityscrıpt ve Boo 'un tamamlanması.

- Yeni bir UnityScript veya Boo dizesi yazılırken düzeltilen özel durum.

- Bir çözüm yüklenmediği zaman Unity menülerindeki özel durumlar düzeltildi.

- Düzeltilen hata UVS-48: çift tırnak yazıldığında bazen hata oluşur ve tüm işlev kesilir (kod tamamlama, sözdizimi vurgusu vb.).

- Düzeltilen hata UVS-46: Visual Studio 'nun Hata Listesi tıklandığında yinelenen açık betik dosyası (UnityScript).

- Düzeltilen hata UVS-42: durum çubuğundaki Unity bağlantı logosu, VS 2012 ' de fare olaylarını işlemez.

- Sabit hata UVS-44: CTRL + SHIFT + Q, VS 2012 ' de hızlı MonoBehaviours için kullanılamaz.

- Düzeltilen hata UVS-40: Unity proje Gezgininde seçili öğeler, VS2012 "koyu" teması içinde pencere etkin olmadığında okunamaz.

- Düzeltilen hata UVS-39: atlanan dizeleri simgeleştirirken sorun.

- Düzeltilen hata UVS-35: değişkenleri incelerken nesnelerde ToString çağrısı yapın.

- Düzeltilen hata UVS-27: VS2012 içinde "koyu" temayla sembol penceresine git.

- Sabit hata UVS-11: eş öğelerdeki Yereller.

## <a name="1100---beta-release"></a>1.1.0.0-Beta sürümü
Çıkarılan, 9, 2013

## <a name="10130"></a>1.0.13.0
Yayımlanma tarihi 21 Ocak 2013

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Hedef hata ayıklananın geçersiz iş parçacığı olayları göndermesi durumunda oluşabilecek bir Visual Studio kilitleniyor düzeltildi. Bu, genellikle OSX üzerinde Uzak Unity hata ayıklaması yapılırken meydana gelir.

- Bir özel durum hata ayıklayıcıyı kapdığı takdirde oluşabilecek bir Visual Studio kilitleniyor düzeltildi.

- C# MonoBehavior bir ad alanında olduğunda MonoBehavior yardımcılarımız düzeltildi.

- Visual Studio 2012 ' de Unityscrıpt için düzeltilen hata ayıklayıcı araç ipuçları.

- Unity 'den yalnızca hata ayıklama sabitleri değiştirildiğinde düzeltilen proje oluşturma.

- Unity proje Gezgininde sabit klavye gezintisi.

- Atlanan dizeler için kod renklendirme düzeltildi.

- Unity dışında kullanıldığında proje adını daha iyi tahmin etmek için dosya Openme düzeltildi. Bu, Kullanıcı Unity 'de UnityVS 'ye temsilci olarak üçüncü bir bölüm dosyası kullandığında gereklidir.

- Unity 'den UnityVS 'e gönderilen uzun mesajların sabit işlenmesi. Bundan önce, uzun iletiler ileti alımızın bir parçası olan mesajlaşma bölümünü çökebilir. Sonuç olarak, bazen Unity 'den bir dosya açılmaz.

## <a name="10120"></a>1.0.12.0
Yayımlanma tarihi 3 Ocak 2013

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Visual Studio bir kesme noktasını sildiğinde oluşabilecek sabit Visual Studio kilitleniyor.

- Unity 'nin oyun betiklerini yeniden derlendikten sonra bazı kesme noktaları isabet ettirilmeyen bir hata düzeltildi.

- Kesme noktaları ilişkisiz olduğunda Visual Studio 'Yu düzgün şekilde bilgilendirmek için hata ayıklayıcı düzeltildi.

- Visual Studio hata ayıklayıcının yerel programlarda hata ayıklamasına engel olabilecek bir kayıt sorunu düzeltildi.

- UnityScript ve Boo ifadeleri değerlendirilirken oluşabilecek bir özel durum düzeltildi.

- Unity 'de .NET API düzeyinin değiştirilmesinin proje dosyalarının güncelleştirilmesini tetikleyemediğinde bir gerileme düzeltildi.

- Kullanıcı kodunun günlük geri çağırma işleyicisine katılabileceği bir API hatası düzeltildi.

## <a name="10110"></a>1.0.11.0
Yayın tarihi, 28 Kasım 2012

### <a name="new-features"></a>Yeni özellikler

- Unity 4 için resmi destek.

- Unity Proje Gezgini 'nden betikleri düzenleme.

- Visual Studio 'da tümleştirme, pencereye git.

- Bilgi konsolu iletisini ayrıştırma, Hata Listesi tıklamak, simgeleri olan ilk StackFrame 'e götürür.

- Kullanıcının proje üretimine katılmasını sağlamak için bir [API](../cross-platform/customize-project-files-created-by-vstu.md) ekleyin.

- Kullanıcının LogCallback 'a katılmasını sağlamak için bir [API](../cross-platform/share-the-unity-log-callback-with-vstu.md) ekleyin.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Visual Studio 2012 ' de Unity Proje Gezgini 'nin arka planında düzeltilen gerileme.

- Tam .net profilinin kullanıcıları için sabit proje üretimi.

- Web hedefinin kullanıcıları için sabit proje üretimi.

- Unity olarak hata ayıklama ve Izleme derleme sembolleri dahil olmak üzere sabit proje üretimi.

- Goto symbol penceremizdeki özel karakterler kullanılırken oluşan kilitlenme düzeltildi.

- Visual Studio 'nun durum çubuğunda simgemizi ekleyeemiz için çökme düzeltildi.

## <a name="10100"></a>1.0.10.0
Yayın tarihi 9 Ekim 2012

### <a name="bug-fixes"></a>Hata Düzeltmeleri

- Visual Studio 2010 ' de Unity Proje Gezgini 'nin arka planı düzeltildi.

- Hata ayıklayıcı arabirimi daha önce kilitlenen bir Unity 'ye hata ayıklayıcı eklemesi denenirse bir Visual Studio donması düzeltildi.

- Bir kesme noktası ayarlandığında ve bir AppDomain yeniden yüklemesi gerçekleştiğinde ortaya çıkabilecek bir Visual Studio donması düzeltildi.

- Dosyaları kilitlemenin ve Unity oluşturma işleminin karışmasını önlemek için derlemelerin Unity 'den nasıl alındığı düzeltildi.

## <a name="1090"></a>1.0.9.0

Yayımlanma tarihi, 3 Ekim 2012

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Unity projesi gerçek JavaScript varlıklarını içerdiğinde, sabit proje üretimi.

- İfade değerlendirmesinde düzeltilen hata işleme.

- Değer türlerinin alanlarına yeni değerleri ayarlama düzeltildi.

- Kod düzenleyicisinden ifadelerin üzerine gelindiğinde olası yan etkiler düzeltildi.

- İfade değerlendirmesi için yüklü derlemelerde türlerin nasıl arandığı düzeltildi.

- Düzeltilen hata UVS-21: Unity nesnelerinde atamanın değerlendirmesi etkisizdir.

- Düzeltilen hata UVS-21: Unity matematik API 'sine bir yöntem çağrısı değerlendirilirken geçersiz işaretçi.

## <a name="1080"></a>1.0.8.0

Yayımlanma tarihi, 26 Eylül 2012

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Betiğimizin, hem Visual Studio hem de betikleri açabildiğinden emin olmak için, projenin yolunu elde ettiği şekilde düzeltildi.

- Hata ayıklama oturumu çalıştırılırken oluşturulan kesme noktalarıyla bir hata düzeltildi ve bu, Visual Studio 'Nun kilitlenmesini istiyor olabilir.

- Visual Studio 2010 ' de UnityVS 'in nasıl kaydedildiği düzeltildi.

## <a name="1070"></a>1.0.7.0

Yayın tarihi 14 Eylül 2012

### <a name="new-features"></a>Yeni özellikler

- Visual Studio 2012 desteği.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Unity 'nin davranışını eşleştirmek için, düzenleyici ve eklenti proje dosyalarının sabit üretimi.

- Unity 4 ' te. pdb sembolleri çevirisi düzeltildi.

> [!IMPORTANT]
> Visual Studio 2012 desteği nedeniyle, birkaç dosyayı yeniden adlandırdık ve başka bir süre içinde taşınacak. Unity 'yi içeri aktarmaya yönelik UnityVS paketi, sırasıyla Visual Studio 2010 ve Visual Studio 2012 için UnityVS 2010 ya da UnityVS 2012 olarak adlandırılmaktadır. Bu sürüm ayrıca, UnityVS proje dosyalarının yeniden oluşturulmasını gerektirir.

## <a name="1060---internal-build"></a>1.0.6.0-iç derleme
12 Eylül 2012 ' de yayınlandı

## <a name="1050"></a>1.0.5.0

Yayın tarihi 10 Eylül 2012

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Betiklerin veya gölgelendiricilerin geçersiz bir XML karakteri olduğunda proje dosyalarının sabit üretimi düzeltildi.

- Unity varlık sunucusuna bağlıyken Unity örneklerinin sabit algılanması. Bu, Unity 'den dosyaları açmak ve Visual Studio hata ayıklayıcının otomatik bağlantısı için hata tetikledi.

## <a name="1040"></a>1.0.4.0

Yayımlanma tarihi, 5 Eylül 2012

### <a name="new-features"></a>Yeni özellikler

- Unity 'de hata ayıklama sembollerini otomatik dönüştürme.

    Varlık klasörünüzde ilişkili. pdb ile bir .NET. dll derlemesi varsa, derlemeyi yeniden içeri aktarmanız yeterlidir ve UnityVS,. pdb 'yi Unity 'nin betik altyapısının anladığı bir hata ayıklama sembolleri dosyasına dönüştürür.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Unity içindeki metotlar veya özellikler tarafından oluşturulan özel durumlar nedeniyle hata ayıklamada hata ayıklama sırasında sabit Unıvs kilitlenmesi

## <a name="1030"></a>1.0.3.0

Yayımlanma tarihi 4 Eylül 2012

### <a name="new-features"></a>Yeni özellikler

- Unity 'den dosya açmaya yönelik UnityVS kullanımını devre dışı bırakmak için yeni yapılandırma seçeneği.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Düzenleyici olmayan projeler için UnityEditor başvuruları düzeltildi.

- Düzenleyici olmayan projeler için UNITY_EDITOR sembolün sabit tanımı.

- Özel durum çubuğumuzdan kaynaklanan sabit rastgele VS kilitlenmesi.

## <a name="1020"></a>1.0.2.0

30 Ağustos 2012 tarihinde yayınlandı

### <a name="bug-fixes"></a>Hata düzeltmeleri

- PythonTools hata ayıklayıcı ile çakışma düzeltildi.

- Mono. CECIL 'e yönelik sabit başvurular.

- Unity 4 B7 ile Unity 'den komut dosyası derlemelerinin nasıl alındığı ile ilgili hata düzeltildi.

## <a name="1010"></a>1.0.1.0

28 Ağustos 2012 ' de yayınlandı

### <a name="new-features"></a>Yeni özellikler

- Unity 4,0 Beta için Önizleme desteği.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Özelliklerin özel durum atma denetimi düzeltildi.

- Nesneler incelenirken temel nesnelerde azalan şekilde düzeltildi.

- Tek davranış sihirbazında ekleme noktası için boş açılan liste.

- UnityScript ve Boo 'un varlık klasörü içindeki dll için sabit tamamlama.

## <a name="1000---initial-release"></a>1.0.0.0-ilk sürüm
Yayın tarihi 22 Ağustos 2012
