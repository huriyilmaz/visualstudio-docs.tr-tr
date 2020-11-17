---
title: Değişiklik günlüğü (Unity için Visual Studio Araçları, Mac) | Microsoft Docs
description: Unity için Visual Studio Araçları, Mac için değişiklik günlüğünü görüntüleyin. 2.7.0.0 ve dışında 1.0.0.0 sürümündeki değişikliklere bakın.
ms.custom: ''
ms.date: 11/13/2020
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: conceptual
ms.assetid: 33a6ac54-d997-4308-b5a0-af7387460849
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 2f026c9d33f5aa49ebb7e974a507c85b87073897
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672853"
---
# <a name="change-log-visual-studio-tools-for-unity-mac"></a>Değişiklik Günlüğü (Unity için Visual Studio Araçları, Mac)

Unity için Visual Studio Araçları değişiklik günlüğü.

## <a name="2830"></a>2.8.3.0
Yayın tarihi 10 Kasım 2020

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Sý**

  - Çözümde bir VSTU projesi olmasa bile Unity 'ye ekleme düzeltildi.

## <a name="2820"></a>2.8.2.0
Yayın tarihi, 27 Ekim 2020

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - [`UNT0010`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0010.md)Yalnızca ' den devralan her şeye uygulanacak tanılama geliştirildi `Component` `MonoBehaviour` .

## <a name="2810"></a>2.8.1.0
Yayın tarihi, 13 Ekim 2020

### <a name="new-features"></a>Yeni Özellikler

- **Değerlendirmesinin**

  - Etkinleştirmeleri ile örtük dönüştürme desteği eklendi. Daha önce değerlendirici, kesin tür denetlemesini zorladı ve `Failed to find a match for method([parameters...])` uyarı iletileri elde ediyor.

- **Tümleştirme**

  - [`UNT0018`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0018.md)Tanılama eklendi. ,, `System.Reflection` Veya gibi performans açısından kritik iletilerde özellikleri kullanmamalısınız `Update` `FixedUpdate` `LateUpdate` `OnGUI` .

  - [`USP0003`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0003.md) [`USP0005`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0005.md) Tüm statik yöntemler desteğiyle geliştirilmiş ve gizliyoruz `AssetPostprocessor` .

  - [`USP0016`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0016.md)İçin Suppressor eklendi `CS8618` . `C# 8.0` Nullable başvuru türlerini ve null değer atanamaz başvuru türlerini tanıtır. ' Den devralan türlerin başlatılma algılaması `UnityEngine.Object` desteklenmez ve hatalara neden olur.

  - Artık hem Unity 2019. x hem de 2020. x + için aynı oynatıcı ve asmdef proje oluşturma mekanizmasını kullanıyor.
  
  - Bir sihirbazla Unity iletileri oluştururken Geliştirilmiş kullanıcı deneyimi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Açıklamalarda iletiler için beklenmeyen tamamlama düzeltildi.

## <a name="2800"></a>2.8.0.0 
Yayın tarihi 14 Eylül 2020

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Unity 2019. x ile sabit oynatıcı proje üretimi.

## <a name="2710"></a>2.7.1.0
5 Ağustos 2020 tarihinde yayınlandı

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - Unity iletileri API 'SI 2019,4 olarak güncelleştirildi.

  - [`USP0013`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0013.md)İçin Suppressor eklendi `CA1823` . Veya özniteliklerine sahip özel `SerializeField` alanlar `SerializeReference` kullanılmamış (FxCop) olarak işaretlenmemelidir.
  
  - [`USP0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0014.md)İçin Suppressor eklendi `CA1822` . Unity iletileri `static` değiştirici (FxCop) için aday olarak işaretlenmemelidir.

  - [`USP0015`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0015.md)İçin Suppressor eklendi `CA1801` . Kullanılmayan parametreler Unity iletilerinden (FxCop) kaldırılmamalıdır.
  
  - `MenuItem`Suppressor 'a destek eklendi [`USP0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0009.md) .  

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Sabit [`USP0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0001.md) ve [`USP0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0002.md) suppresler, ek parantezler veya yöntem bağımsız değişkenleriyle çalışmıyor.
  
  - Unity ayarlarında otomatik yenileme devre dışı bırakılsa bile, düzeltilen zorunlu varlık veritabanı yenilemesi.

## <a name="2700"></a>2.7.0.0
Yayın tarihi, 23 Haziran 2020

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - Unity çözüm ve projeleri yeniden oluştururken çözüm klasörlerinin kalıcı hale getirilmesi için destek eklendi.

  - [`UNT0015`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0015.md)Tanılama eklendi. Ya da özniteliğiyle yanlış metot imzasını Algıla `InitializeOnLoadMethod` `RuntimeInitializeOnLoadMethod` .

  - [`UNT0016`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0016.md)Tanılama eklendi. `Invoke` `InvokeRepeating` `StartCoroutine` `StopCoroutine` Dize sabit değeri olan ilk bağımsız değişken,, veya kullanarak tür kullanımı güvenli değildir.

  - [`UNT0017`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0017.md)Tanılama eklendi. `SetPixels` çağırma yavaş.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Sý**

  - Oyun eski mono çalışma zamanı üzerinde çalışırken (kesme noktası oluşturulduktan hemen sonra bağlantı noktasını bağlamaya çalışırken), kesme noktaları oluşturma düzeltildi. 
  
- **Tümleştirme**

  - Unity ileti Sihirbazı 'nda iletileri filtrelerken seçimi sıfırlamayın.
  
  - [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0004.md), [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) `IDE0044` `IDE0051` `CS0649` Serializefield özniteliğiyle donatılmış tüm alanlar için gösterme (salt okunur), (kullanılmamış), (atanmamış), ve bu kurallara göre düzeltildi. `Unity.Object` öğesini genişleten her türdeki genel alanlar için `CS0649` (hiçbir zaman atanmamış) öğesini gizleyin.

  - İçin sabit genel tür parametresi denetimi [`UNT0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0014.md) .

- **Değerlendirmesinin**

  - Numaralandırmalar ile sabit eşitlik karşılaştırması.

## <a name="2610"></a>2.6.1.0
Yayımlanma tarihi 19 Mayıs 2020

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Unity tarafında mesajlaşma sunucusunu oluşturdığımızda uyarın.

  - Hafif derleme sırasında Çözümleyicileri düzgün şekilde çalıştırın.

  - Unity hub yüklemeleri ile düzeltilen API belgeleri.
  
  - Sabit hata ayıklayıcı görselleştiricisi kilitleniyor.

## <a name="2600"></a>2.6.0.0
Yayın tarihi 14 Nisan 2020

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - [`UNT0012`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0012.md)Tanılama eklendi. İçindeki bağıntıları tespit edin ve bu çağrıları sarın `StartCoroutine()` .

  - [`UNT0013`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0013.md)Tanılama eklendi. Geçersiz veya gereksiz özniteliği tespit edin ve kaldırın `SerializeField` .

  - [`UNT0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0014.md)Tanılama eklendi. Algılama `GetComponent()` , bileşen olmayan veya arabirim olmayan türle çağrıldı.

  - [`USP0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0009.md)İçin Suppressor eklendi `IDE0051` . Özniteliği özniteliğiyle bayrak eklemeyin `ContextMenu` veya özniteliği kullanılmamış olarak bir alan tarafından başvurulmayın `ContextMenuItem` .

  - [`USP0010`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0010.md)İçin Suppressor eklendi `IDE0051` . `ContextMenuItem`Özniteliği, kullanılmayan olarak özniteliğe bayrak eklemeyin.

  - [`USP0011`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0011.md)İçin Suppressor eklendi `IDE0044` . `ContextMenuItem`Özniteliği ile salt okuma alanları yapmayın.

  - [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0004.md)[`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md)ve [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) artık ve öznitelikleri için de çalışır `SerializeReference` `SerializeField` .

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Yalnızca Düzenleyici iletişim kurabiliyorsa Unity 'ye Başlat/Durdur komutlarını gönderin.

  - Devralınan iletilerle düzeltilen QuickInfo belgeleri.

  - İleti için sabit ileti kapsamı `CreateInspectorGUI` .

  - [`UNT0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0001.md)Polimorfik değiştiricilere sahip yöntemler hakkında rapor vermeyin.

- **Değerlendirmesinin**

  - Diğer ad kullanımları düzeltildi.
  
  - Null değerlerin sabit işlenmesi.  

## <a name="2520"></a>2.5.2.0

Yayın tarihi, 23 Mart 2020

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Sý**

  - İliştirme sonrasında iş parçacıklarının sabit kaydı.

## <a name="2510"></a>2.5.1.0

Yayımlanma tarihi, 3 Mart 2020

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - [`USP0008`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0008.md)İçin Suppressor eklendi `IDE0051` . Invoke, InvokeRepeating, StartCoroutine veya StopCoroutine ile kullanılan özel yöntemler kullanılmamış olarak işaretlenmemelidir.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Fixed Ondrawgizmos öğesini uygulayın/Ondrawgizmosselected öğesini uygulayın belgeleri.

- **Değerlendirmesinin**

  - Sabit lambda bağımsız değişken incelemesi.

## <a name="2501"></a>2.5.0.1

Yayın tarihi, 19 Şubat 2020

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0006.md)Hatalı ileti imzası için tanılama denetimi düzeltildi. Birden çok devralma düzeyi olan türler incelenirken, bu tanı şu iletiyle başarısız olabilir: `warning AD0001: Analyzer 'Microsoft.Unity.Analyzers.MessageSignatureAnalyzer' threw an exception of type 'System.ArgumentException' with message 'An item with the same key has already been added` .

## <a name="2500"></a>2.5.0.0

22 Ocak 2020 tarihinde yayınlandı

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - HLSL dosyaları için destek eklendi.
  
  - Yeni bir klasör iletişim kutusu kullanıcı arabirimine geçti.
  
  - Ayarlar için yeni bir erişilebilir özellik kılavuzuna geçti.

  - [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md)İçin Suppressor eklendi `IDE0051` . Özniteliği olan özel alanlar `SerializeField` kullanılmamış olarak işaretlenmemelidir.

  - [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md)İçin Suppressor eklendi `CS0649` . Özniteliği olan alanlar `SerializeField` atanmamış olarak işaretlenmemelidir.  

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Sabit proje üretimi ( `GenerateTargetFrameworkMonikerAttribute` hedef her zaman doğru şekilde bulunamadı).

- **Değerlendirmesinin**

  - Sabit dize değerlendirmesi (ToString () çağrılarını kullanmıyor)

## <a name="2420"></a>2.4.2.0

Yayın 3 Aralık 2019

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Kullanıcı tanımlı arabirimler ile sabit Tanılamalar.

  - Hatalı biçimlendirilmiş ifadelerle hızlı araç ipuçları düzeltildi.
  
## <a name="2410"></a>2.4.1.0

Yayın tarihi, 6 Kasım 2019

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - Unity arka plan işlemlerine yönelik destek eklendi. (Hata ayıklayıcı alt işlem yerine ana işleme otomatik olarak bağlanabilir).

  - Unity iletileri için ilgili belgeleri görüntüleyen bir hızlı araç ipucu eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - `UNT0002`Gelişmiş ikili ve çağırma ifadeleriyle etiket karşılaştırma Çözümleyicisi düzeltildi.

### <a name="deprecated-features"></a>Kullanım dışı Özellikler

- **Tümleştirme**

  - Unity için Visual Studio Araçları, yalnızca Visual Studio 2017 + desteğine sahip olur.

## <a name="2400"></a>2.4.0.0

Yayımlanma tarihi, 15 Ekim 2019

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - [`USP0005`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0005.md) `IDE0060` Tüm Unity iletileri için Suppressor (kullanılmamış parametre) eklendi.

  - İle etiketlenmiş alanlar için hızlı araç ipucu eklendi `TooltipAttribute` . (Bu, bu alanı kullanarak basit bir get erişimcisi için de çalışır).

## <a name="2330"></a>2.3.3.0

Yayın tarihi, 23 Eylül 2019

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - IDE 'nin kullanılmayan parametreleri kaldırmak üzere hızlı bir çözüm göstermesini engellemek için, IDE0060 için yeni bir supprescursor eklendi.
    - `USP0005` için `IDE0060` : Unity Iletileri Unity çalışma zamanı tarafından çağrılır.

## <a name="2320"></a>2.3.2.0

Yayın tarihi, 16 Eylül 2019

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - Unity 'ye özgü yeni Tanılamalar ekleyerek, Visual Studio 'nun Unity projelerine yönelik olduğunu anlama konusunu sunuyoruz. Unity projeleri için geçerli olmayan genel C# tanılamalarını gizleyerek IDE’yi daha akıllı hale getirdik. Örneğin, IDE, Unity düzenleyicisinde değişkeni değiştirmenize engel olacak bir Inspector değişkenini değiştirmek için hızlı bir çözüm göstermez `readonly` .
    - `UNT0001`: Unity iletileri, boş olsalar bile çalışma zamanı tarafından çağrılır, Unity çalışma zamanına göre uncesseray işlemesini önlemek için bunları bildiremezsiniz.
    - `UNT0002`: Dize eşitlik kullanılarak etiket karşılaştırması yerleşik CompareTag yönteminden daha yavaştır.
    - `UNT0003`: Tür güvenliği için GetComponent 'un genel biçiminin kullanımı tercih edilir.
    - `UNT0004`: Güncelleştirme iletisi çerçeve hızına bağımlıdır ve Time. deltaTime yerine Time. fixedDeltaTime kullanın.
    - `UNT0005`: FixedUpdate iletisi çerçeve hızına bağımsızdır ve Time. fixedDeltaTime yerine Time. deltaTime kullanın.
    - `UNT0006`: Bu Unity iletisi için yanlış bir yöntem imzası algılandı.
    - `UNT0007`: Unity, null birleştirme ile uyumsuz olan Unity nesneleri için null karşılaştırma işlecini geçersiz kılar.
    - `UNT0008`: Unity, null yayılmayla uyumsuz olan Unity nesneleri için null karşılaştırma işlecini geçersiz kılar.
    - `UNT0009`: Initializeonload özniteliği bir sınıfa uygulanırken, bir statik Oluşturucu sağlamanız gerekir. InitializeOnLoad özniteliği, düzenleyici başlatıldığında bunun çağrılmasını sağlar.
    - `UNT0010`: MonoBehaviours yalnızca AddComponent () kullanılarak oluşturulmalıdır. MonoBehaviour bir bileşendir ve bunun GameObject’e eklenmesi gerekir.
    - `UNT0011`: ScriptableObject yalnızca CreateInstance () kullanılarak oluşturulmalıdır. Unity ileti yöntemlerinin işlenmesi için ScriptableObject’in Unity altyapısı tarafından oluşturulması gerekir.
    - `USP0001` için `IDE0029` : Unity nesneleri null birleştirme kullanmamalıdır.
    - `USP0002` için `IDE0031` : Unity nesneleri null yayma kullanmamalıdır.
    - `USP0003` için `IDE0051` : Unity Iletileri Unity çalışma zamanı tarafından çağrılır.
    - `USP0004` için `IDE0044` : SerializeField özniteliğine sahip alanlar ReadOnly yapılmamalıdır.

## <a name="2310"></a>2.3.1.0

Yayımlanma tarihi 4 Eylül 2019

### <a name="new-features"></a>Yeni Özellikler

- **Değerlendirmesinin**

  - Daha iyi tür görüntüleme desteği eklendi, yani `List<object>` yerine `List'1[[System.Object, <corlib...>]]` .

  - İşaretçi üye erişimi için destek eklendi, `p->data->member` ör.

  - Dizi başlatıcılarda örtük dönüştürmeler için destek eklendi, örn. `new byte [] {1,2,3,4}` .

  - Bayt dizileri ve dizeleri incelenirken Onaltılı düzenleyici desteği eklendi.

## <a name="2300"></a>2.3.0.0

Yayın tarihi 13 Ağustos 2019

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Değerlendirmesinin**

  - Özel durumlarla düzeltilen Adımlama sorunları.

  - Sözde tanımlayıcıların ($exception gibi) sabit değerlendirmesi.

  - Geçersiz adreslerin başvurusu kaldırılırken kilitlenmeyi önleyin.  

  - Kaldırılmış AppDomain 'ler ile ilgili sorun düzeltildi.

## <a name="2200"></a>2.2.0.0

Yayın tarihi, 25 Temmuz 2019

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Değerlendirmesinin**

  - IntPtr türleriyle düzeltilen İnceleme.

- **Sý**

  - Catch noktaları ve işlev kesme noktalarının sabit işlenmesi.

## <a name="2130"></a>2.1.3.0

Yayın tarihi, 9 Temmuz 2019

### <a name="new-features"></a>Yeni Özellikler

- **Sý**

  - Özel durumların yakalamak için destek eklendi.

  - MDS Protokolü 2,51 için destek eklendi.

- **Tümleştirme**

  - Asmdef dosyaları için destek eklendi.

  - Şablondan bir dosya eklendiğinde yeniden adlandırma moduna geçin (Unity Düzenleyicisi davranışını taklit etmek için).

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Unity oynatıcılarla iletişim kurulurken hatalı biçimlendirilmiş iletilerin işlenmesi düzeltildi.

- **Değerlendirmesinin**

  - İfadelerde ad alanlarını sabit olarak işleme.

## <a name="2120"></a>2.1.2.0

Yayın 2 Temmuz 2019

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Değerlendirmesinin**

  - Ayrıştırılamayan ifadelerle düzeltilen hata raporlaması.

## <a name="2110"></a>2.1.1.0

Yayın tarihi, 27 Haziran 2019

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - Monodavranış API 'SI 2019,1 olarak güncelleştirildi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Sabit Unity Proje Gezgini performansı.

  - Hafif derleme etkinleştirildiğinde, çıktının düzeltilme uyarıları ve hataları düzeltildi.

  - Sabit basit derleme performansı.

## <a name="2100"></a>2.1.0.0

Yayın tarihi 20 Haziran 2019

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - IntelliSense hatalarının ve uyarılarının kullanımı açısından Unity projelerinin tam derlemesini devre dışı bıraktı. Aslında Unity, dahili olarak hangi Unity 'nin yaptığını temsil eden sınıf kitaplığı projeleri içeren bir Visual Studio çözümü oluşturur. Bu şekilde, Visual Studio 'daki derlemenin sonucu, derleme işlem hattı kapalıyken Unity tarafından hiçbir şekilde kullanılmaz veya alınmaz. Visual Studio 'da oluşturma işlemi yalnızca hiçbir şey için kaynakları tüketiyor. Kendisine bağlı araçlara veya kuruluma sahip olduğunuz için tam bir yapıya ihtiyacınız varsa, bu iyileştirmeyi devre dışı bırakabilirsiniz (Unity için ayarlar/araçlar/projelerin tam derlemesini devre dışı bırak).
  
  - UPE içinde Unity paketleri için destek eklendi. Yalnızca başvurulan paketler (klasöründe manifest.jskullanılarak `Packages` ) ve yerel paketler ( `Packages` klasöre katıştırılmış) görünür.

## <a name="2021"></a>2.0.2.1

Yayımlanma tarihi 30 Mayıs 2019

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - Unity yürütme hedefleri için özel simge eklendi.

## <a name="2020"></a>2.0.2.0

Yayın 2 Nisan 2019

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - Kayıt sırasında Unity 'nin varlık veritabanının otomatik olarak yenilenmesi için destek eklendi. Bu, varsayılan olarak etkindir ve Visual Studio 'da bir betiği kaydederken Unity tarafında yeniden derleme tetikleyecektir. Kayıt sırasında Unity 'nin Assetveritabanını yenilemek için Tools\Options\Tools içinde bu özelliği devre dışı bırakabilirsiniz.

  - Çevrimdışı belgeler için tercih edilen Unity yüklemesinin ayarlanmasına yönelik destek eklendi.

  - Yeni düzenleyici için bağlam menüsü eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Sý**

  - Boş çerçevelerle sabit derleme filtrelemesi ve çerçeve incelemesi.

## <a name="2011"></a>2.0.1.1
 
 Yayın tarihi 26 Mart 2019

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Yalnızca bu çok özel yayın için mono varsayılan ve yalnızca kullanılabilir hata ayıklayıcı 'yı geçici olarak yapın.

## <a name="2006"></a>2.0.0.6

Yayın tarihi 26 Mart 2019

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - "Unity 'ye Ekle ve Yürüt" desteği eklendi.

## <a name="2005"></a>2.0.0.5

Yayımlanma tarihi, 20 Mart 2019

### <a name="new-features"></a>Yeni Özellikler

- **Proje oluşturma:**

  - Çözüm dosyasını işlerken dış özellikleri koruyun.
  
- **Değerlendirmesinin**

  - Diğer ad nitelenmiş adlar için destek eklendi (şimdilik yalnızca genel ad alanı). Bu nedenle, ifade değerlendirici artık genel:: Namespace. Type biçimini kullanarak türleri kabul ediyor.

  - `pointer[index]`İşaretçi başvuru formuyla anlam ile aynı olan form için destek eklendi `*(pointer+index)` .

## <a name="2004"></a>2.0.0.4

Yayımlanma tarihi, 5 Mart 2019

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - API güncelleştirildi `ScriptableObject` .

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Ad alanları şablonlardan kaldırıldı.

## <a name="2003"></a>2.0.0.3
 
 Yayımlanma tarihi, 5 Mart 2019

### <a name="new-features"></a>Yeni Özellikler

- **Proje oluşturma:**

  - Ortak ve serileştirilmiş alanlar artık uyarılara neden olmaz. `CS0649` `IDE0051` Bu Iletileri oluşturan Unity projelerinde ve derleyici uyarılarını otomatik olarak gizliyoruz.

- **Tümleştirme**

  - Bir Unity işlemi çalışıyorsa, belirli bir örneğe İliştirilmek için uyar.

- **Değerlendirmesinin**

  - Yerel işlevler için destek eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Sý**

  - Eski protokol sürümleri kullanılırken adlandırılmış bağımsız değişkenlerde özel öznitelik okuma düzeltildi.

## <a name="2002"></a>2.0.0.2

Yayımlanma tarihi 4 Şubat 2019

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - Monodavranış API 'SI güncelleştirildi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Sý**

  - Hata ayıklayıcıda temel değerler ayarı düzeltildi.

## <a name="2001"></a>2.0.0.1

Yayın tarihi 4 Aralık 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Sabit yükleme paketi kendi kendine kapsama.

## <a name="2000"></a>2.0.0.0
 Yayın tarihi 4 Aralık 2018

### <a name="new-features"></a>Yeni Özellikler

- **Sý**

  - Mac üzerindeki Unity hata ayıklayıcı, Windows 'daki aynı Core Unity hata ayıklayıcısıyla değiştirildi.

  - İfade değerlendirmesi için NRefactory 'ın Roslyn tarafından değiştirildiği yer.

  - İşaretçiler için destek eklendi: başvuru, atama ve işaretçi aritmetiği (Bu, hem Unity 2018.2 + hem de yeni çalışma zamanı için gereklidir).

  - Dizi işaretçisi görünümü için (C++ ' da olduğu gibi) destek eklendi. Bir işaretçi ifadesi alın, sonra da bir virgül ve görmek istediğiniz öğe sayısını ekleyin.

  - Zaman uyumsuz yapılar için destek eklendi.

  - Sözde değişkenler (özel durum ve nesne tanımlayıcıları) için destek eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Sý**

  - Hatalı biçimlendirilmiş veya desteklenmeyen ifadelerle ifade değerlendirmesi düzeltildi.

## <a name="1700"></a>1.7.0.0

Yayın tarihi, 13 Kasım 2018

### <a name="new-features"></a>Yeni Özellikler

- **Sý**

  - Ekleme iletişim kutusuna daha fazla istemci bilgisi (IP, makine adı) eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Sý**

  - Unity 'nin hata ayıklayıcı altyapısı ile iletişim kurmak için kullanılan kitaplıkta bir kilitlenme düzeltildi, özellikle ' Unity 'ye Ekle ' veya oyunu yeniden başlatma sırasında, Visual Studio veya Unity dondurma

- **Tümleştirme**

  - Başka bir varsayılan düzenleyici seçildiğinde, sabit Unity eklentisi etkinleştirmesi.

  - Sabit Unity dosya şablonu oluşturma.

## <a name="1602"></a>1.6.0.2

Yayın tarihi, 24 Temmuz 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Unity tarafından düzeltilen bir Unity performans hatası için geçici çözümü geri alındı.

## <a name="1601"></a>1.6.0.1

Yayın tarihi 10 Temmuz 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Sabit gölgelendirici kodu coloration desteği.

## <a name="1600"></a>1.6.0.0

Yayın tarihi 26 Haziran 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **'Nı**

  - OnApplicationFocus iletisi ile sabit yazım hatası.

- **Proje oluşturma:**

  - Unity performans hatası için geçici geçici çözüm: proje oluştururken Cache Monoadaları.

  - Yeni Unity çalışma zamanı kullanılırken taşınabilir pdb 'yi artık mdb 'ye dönüştürmeyin.

## <a name="1502"></a>1.5.0.2

Yayın tarihi 18 Nisan 2018

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - Temel gölgelendirici kodu tamamlama desteği eklendi.

  - Gölgelendirici dosyalarında yorumların geçiş için destek eklendi.

## <a name="1501"></a>1.5.0.1

Yayın tarihi, 28 Mart 2018

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - Unity proje Gezgininde ek şablonlar için destek eklendi.

## <a name="1500"></a>1.5.0.0

Yayımlanma tarihi 21 Mart 2018

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - USB üzerinden bağlı Android oyuncularını algılama ve ekleme desteği eklendi.

## <a name="1403"></a>1.4.0.3

Yayımlanma tarihi, 5 Mart 2018

### <a name="new-features"></a>Yeni Özellikler

- **Proje oluşturma:**

  - Unity 2018,1 ' de yeni proje Oluşturucu desteği eklendi.

- **Tümleştirme**

  - Adanmış ayarlar için seçenek paneli eklendi.

## <a name="1402"></a>1.4.0.2

24 Ocak 2018 ' de yayınlandı

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Proje oluşturma:**

  - Sabit mono sürümü algılama.

- **Tümleştirme**

  - 2018,1 ve eklenti etkinleştirme ile ilgili sabit zamanlama sorunları.

  - Yeni bir oynatıcı algılanırken uyarı düzeltildi.

## <a name="1401"></a>1.4.0.1

Yayın tarihi, 23 Ocak 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Çift tıklama üzerinde klasörleri sabit Genişlet/Daralt

## <a name="1400"></a>1.4.0.0

Yayın tarihi, 13 Aralık 2017

### <a name="new-features"></a>Yeni Özellikler

- **Proje oluşturma:**

  - .NET Standard için destek eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Otomatik pdb 'den mdb hata ayıklama sembol dönüştürme.

## <a name="1301"></a>1.3.0.1

Yayın tarihi, 12 Aralık 2017

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - EditorPrefs. GetBool öğesine yapılan dolaylı çağrı, dizi boyutunu değiştirmeye çalışırken Inspector 'ı etkiliyor.

- **'Nı**

  - Yöntemi eklemeden önce Roslyn bağlamını yenileyin.

## <a name="1300"></a>1.3.0.0

Yayımlanma tarihi, 20 Kasım 2017

### <a name="new-features"></a>Yeni Özellikler

- **'Nı**

  - "Unity iletisi uygulama" Sihirbazı eklendi.

  - Mac 7,4 ' de yeni tamamlanma API 'SI için destek eklendi.

## <a name="1200"></a>1.2.0.0

Yayın tarihi, 23 Ekim 2017

### <a name="new-features"></a>Yeni Özellikler

- **Sý**

  - Taşınabilir hata ayıklama sembol dosyaları için destek eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Proje oluşturma:**

  - Derleme dosya adına yanlışlıkla eklenmiş ek. dll uzantısı düzeltildi.

  - Varsayılan olarak ' true ' olduğundan AllowAttachedDebuggingOfEditor Unity bayrağını zorlamayın.

## <a name="1103"></a>1.1.0.3

Yayın tarihi, 23 Ekim 2017

### <a name="new-features"></a>Yeni Özellikler

- **Proje oluşturma:**

  - .NET 4,6 profili için destek eklendi.

## <a name="1102"></a>1.1.0.2

Yayın tarihi, 8 Ağustos 2017

### <a name="new-features"></a>Yeni Özellikler

- **Sý**

  - Hangi Unity 'nin iliştirilemiyor olduğundan emin olmak için işleme İliştir iletişim kutusunu başlatın.

- **Proje oluşturma:**

  - Unity 5,6 kullanıldığında her zaman güvenli olmayan derleme anahtarını etkinleştirin.

## <a name="1101"></a>1.1.0.1

Yayın tarihi 20 Temmuz 2017

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - Yerelleştirilmiş kaynaklar için destek eklendi.

## <a name="1100"></a>1.1.0.0

Yayımlanma tarihi, 12 Temmuz 2017

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - İşleme Ekle penceresi aracılığıyla oyunculara ve düzenleyicilere ekleme desteği eklendi.

- **Proje oluşturma:**

  - MCS. rsp dosyalarıyla düzeltilen derleme adı başvuruları.

  - Derleme birimlerinde assembly.jsiçin destek eklendi.

  - API düzeyleriyle düzeltilen tanımlar.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Derlerken düzeltilen gölgelendirici hata iletisi.

## <a name="1001"></a>1.0.0.1

Yayımlanma tarihi 4 Mayıs 2017

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Karma ve normal projelerle sabit etkin belge izleme.

## <a name="1000"></a>1.0.0.0

Yayımlanma tarihi 3 Mayıs 2017
