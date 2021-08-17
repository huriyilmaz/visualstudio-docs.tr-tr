---
title: değişiklik günlüğü (Unity için Visual Studio Araçları, Windows) | Microsoft Docs
description: Unity için Visual Studio Araçları, Windows için değişiklik günlüğünü görüntüleyin. 4.7.0.0 ve dışında 1.0.0.0 sürümündeki değişikliklere bakın.
ms.custom: ''
ms.date: 6/2/2021
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: conceptual
ms.assetid: ea490b7e-fc0d-44b1-858a-a725ce20e396
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 0f8fef8ff6d96f5184e3ae90de8d8df3354968facaea6e637d21c6df210551b4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121423583"
---
# <a name="change-log-visual-studio-tools-for-unity-windows"></a>değişiklik günlüğü (Unity için Visual Studio Araçları Windows)

Unity için Visual Studio Araçları değişiklik günlüğü.

## <a name="41020"></a>4.10.2.0
Yayımlanma tarihi 25 Mayıs 2021

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - [`UNT0024`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0024.md)Tanılama eklendi. Vektör hesaplamaları üzerinde skalar hesaplamalar için öncelik verin.

- **Değerlendirmesinin**

  - Görünür yerelleri düzgün filtrelemek için taşınabilir pdb sembolleri kullanma desteği eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Sabit varlık başvuru araması kararlılığı.

  - Son Unity sürümleriyle ayrıştırma ile sabit oynatıcı duyurusu.

## <a name="41010"></a>4.10.1.0
Piyasaya sürüldü 11 Mayıs 2021

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Hızlı düzeltme ile düzeltilen kararlılık sorunları [`UNT0008`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0008.md) .

  - İş parçacıklarında düzeltilen performans sorunları.

## <a name="41000"></a>4.10.0.0
Yayın tarihi, 13 Nisan 2021

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - [`UNT0019`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0019.md)Tanılama eklendi. İçin gereksiz yöneltme çağrısı `GameObject.gameObject` .

  - [`UNT0020`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0020.md)Tanılama eklendi. `MenuItem` statik olmayan yöntemde kullanılan öznitelik.

  - [`UNT0021`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0021.md)Tanılama eklendi. Unity iletisi korunmalıdır (OPT).

  - [`UNT0022`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0022.md)Tanılama eklendi. Konum ve döndürme ayarlamak için verimsiz yöntem.

  - [`UNT0023`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0023.md)Tanılama eklendi. Unity nesnelerinde birleştirme ataması.

  - [`USP0017`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0017.md)İçin Suppressor eklendi `IDE0074` . Unity nesneleri birleştirme atamasını kullanmamalıdır.

  - Unity 'yi hedefleyen flavored C# projelerinin algılanması eklendi.

  - CodeLens 'te Unity varlık başvuru araması eklendi.

## <a name="4910"></a>4.9.1.0
Yayımlanma tarihi 2 Mart 2021

### <a name="new-features"></a>Yeni Özellikler

- **Değerlendirmesinin**

  - `Active Scene`Kök oyun nesnelerini gösteren Yereller 'e eklenir.

  - `this.gameObject`Unity projelerinde yaygın olarak kullanıldığından, Yereller 'e eklenir.

  - Tüm `Children` `Components` `GameObject` nesne hiyerarşisini kolayca görüntüleyebilmeniz için tüm örneklere eklenen ve gruplar.

  - `Scene Path` `GameObject` Sahnenin konumunu göstermek için tüm örneklere eklenir.

  - `JobEntityBatch`Kaynak oluşturucuları Ile varlıklar kullanılırken/Lambdas desteği eklendi.

  - Büyük dizileri (Dizin demetlenmesidir kullanarak) görüntüleme desteği geliştirildi.
  
  - 2019,4 API için eksik Unity iletileri eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - TRK dil olmayan dillerde çeşitli kullanıcı arabirimi sorunları düzeltildi.

  - Tanılama ile ilgili sabit kararlılık sorunları [`UNT0018`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0018.md) .
  
- **Masının**

  - Yöntemler kullanılırken sabit VM bağlantısı kesme sorunları `Trace` .

- **Değerlendirmesinin**

  - Geçersiz özellikleri oluşturan özel durumlar düzeltildi.

## <a name="4900"></a>4.9.0.0
Yayın 20 Ocak 2021

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - `raytrace shaders`Ve dosyaları için destek `UXML` eklendi `USS` .

  - `.vsconfig`Oluşturma desteği eklendi. Visual Studio artık hangi bileşenlerin eksik olduğunu tespit etmelidir ve Unity projelerini kullanırken bunları yüklemenizi ister.

  - Unity iletileri API 'SI güncelleştirildi (eş yordam olarak kullanılan tüm yöntemler için).

  - Android SDK algılaması güncelleştirildi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Örnek seçimi iletişim kutusu kullanılırken sabit işlem yenileme.

  - Sabit [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0006.md) tanı, corlar ve için yanlış uyarılar veriliyor `AssetPostprocessor.OnAssignMaterialModel` .

## <a name="4820"></a>4.8.2.0
Yayın tarihi 10 Kasım 2020

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - [`UNT0010`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0010.md)Yalnızca ' den devralan her şeye uygulanacak tanılama geliştirildi `Component` `MonoBehaviour` .

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Sabit CodeLens iletisi ınvalidation.

## <a name="4810"></a>4.8.1.0
Yayın tarihi, 13 Ekim 2020

### <a name="new-features"></a>Yeni Özellikler

- **Değerlendirmesinin**

  - Etkinleştirmeleri ile örtük dönüştürme desteği eklendi. Daha önce değerlendirici, kesin tür denetlemesini zorladı ve `Failed to find a match for method([parameters...])` uyarı iletileri elde ediyor.

- **Tümleştirme**

  - [`UNT0018`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0018.md)Tanılama eklendi. ,, `System.Reflection` Veya gibi performans açısından kritik iletilerde özellikleri kullanmamalısınız `Update` `FixedUpdate` `LateUpdate` `OnGUI` .

  - [`USP0003`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0003.md) [`USP0005`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0005.md) Tüm statik yöntemler desteğiyle geliştirilmiş ve gizliyoruz `AssetPostprocessor` .

  - [`USP0016`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0016.md)İçin Suppressor eklendi `CS8618` . `C# 8.0` Nullable başvuru türlerini ve null değer atanamaz başvuru türlerini tanıtır. ' Den devralan türlerin başlatılma algılaması `UnityEngine.Object` desteklenmez ve hatalara neden olur.

  - Artık hem Unity 2019. x hem de 2020. x + için aynı oynatıcı ve asmdef proje oluşturma mekanizmasını kullanıyor.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Açıklamalarda iletiler için beklenmeyen tamamlama düzeltildi.

## <a name="4800"></a>4.8.0.0 
Yayın tarihi 14 Eylül 2020

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Unity 2019. x ile sabit oynatıcı proje üretimi.

## <a name="4710"></a>4.7.1.0
5 Ağustos 2020 tarihinde yayınlandı

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - Varsayılan şablonlara ad alanı desteği eklendi.
  
  - Unity iletileri API 'SI 2019,4 olarak güncelleştirildi.

  - [`USP0013`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0013.md)İçin Suppressor eklendi `CA1823` . Veya özniteliklerine sahip özel `SerializeField` alanlar `SerializeReference` kullanılmamış (FxCop) olarak işaretlenmemelidir.
  
  - [`USP0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0014.md)İçin Suppressor eklendi `CA1822` . Unity iletileri `static` değiştirici (FxCop) için aday olarak işaretlenmemelidir.

  - [`USP0015`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0015.md)İçin Suppressor eklendi `CA1801` . Kullanılmayan parametreler Unity iletilerinden (FxCop) kaldırılmamalıdır.
  
  - Suppressor 'a MenuItem desteği eklendi [`USP0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0009.md) .  

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Sabit [`USP0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0001.md) ve [`USP0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0002.md) suppresler, ek parantezler veya yöntem bağımsız değişkenleriyle çalışmıyor.
  
  - Unity ayarlarında otomatik yenileme devre dışı bırakılsa bile, düzeltilen zorunlu varlık veritabanı yenilemesi.

## <a name="4700"></a>4.7.0.0
Yayın tarihi, 23 Haziran 2020

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - Unity çözüm ve projeleri yeniden oluştururken çözüm klasörlerinin kalıcı hale getirilmesi için destek eklendi.

  - [`UNT0015`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0015.md)Tanılama eklendi. Ya da özniteliğiyle yanlış metot imzasını Algıla `InitializeOnLoadMethod` `RuntimeInitializeOnLoadMethod` .

  - [`UNT0016`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0016.md)Tanılama eklendi. `Invoke` `InvokeRepeating` `StartCoroutine` `StopCoroutine` Dize sabit değeri olan ilk bağımsız değişken,, veya kullanarak tür kullanımı güvenli değildir.

  - [`UNT0017`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0017.md)Tanılama eklendi. `SetPixels` çağırma yavaş.

  - Gölgelendirici dosyaları için blok açıklaması ve girintileme desteği eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Unity ileti Sihirbazı 'nda iletileri filtrelerken seçimi sıfırlamayın.
  
  - Unity API belgelerini açarken her zaman varsayılan tarayıcıyı kullanın.
  
  - [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0004.md), [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) `IDE0044` `IDE0051` `CS0649` Serializefield özniteliğiyle donatılmış tüm alanlar için gösterme (salt okunur), (kullanılmamış), (atanmamış), ve bu kurallara göre düzeltildi. `Unity.Object` öğesini genişleten her türdeki genel alanlar için `CS0649` (hiçbir zaman atanmamış) öğesini gizleyin.

  - Diagostik için sabit genel tür parametresi denetimi [`UNT0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0014.md) .

- **Değerlendirmesinin**

  - Numaralandırmalar ile sabit eşitlik karşılaştırması.

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

## <a name="4510"></a>4.5.1.0

Yayın tarihi 16 Mart 2020

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - [`USP0008`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0008.md)İçin Suppressor eklendi `IDE0051` . Invoke, InvokeRepeating, StartCoroutine veya StopCoroutine ile kullanılan özel yöntemler kullanılmamış olarak işaretlenmemelidir.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Fixed Ondrawgizmos öğesini uygulayın/Ondrawgizmosselected öğesini uygulayın belgeleri.

- **Değerlendirmesinin**

  - Sabit lambda bağımsız değişken incelemesi.

## <a name="4501"></a>4.5.0.1

Yayın tarihi, 19 Şubat 2020

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0006.md)Hatalı ileti imzası için tanılama denetimi düzeltildi. Birden çok devralma düzeyi olan türler incelenirken, bu tanı şu iletiyle başarısız olabilir: `warning AD0001: Analyzer 'Microsoft.Unity.Analyzers.MessageSignatureAnalyzer' threw an exception of type 'System.ArgumentException' with message 'An item with the same key has already been added` .

## <a name="4500"></a>4.5.0.0

22 Ocak 2020 tarihinde yayınlandı

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - HLSL dosyaları için destek eklendi.
  
  - [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md)İçin Suppressor eklendi `IDE0051` . Özniteliği olan özel alanlar `SerializeField` kullanılmamış olarak işaretlenmemelidir.
  
  - [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md)İçin Suppressor eklendi `CS0649` . Özniteliği olan alanlar `SerializeField` atanmamış olarak işaretlenmemelidir.  

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

  - [`UNT0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0002.md)Gelişmiş ikili ve çağırma ifadeleriyle etiket karşılaştırma Çözümleyicisi düzeltildi.

### <a name="deprecated-features"></a>Kullanım dışı Özellikler

- **Tümleştirme**

  - Unity için Visual Studio Araçları ileri giderek yalnızca Visual Studio 2017 + desteklenir.

## <a name="4400"></a>4.4.0.0

Yayımlanma tarihi, 15 Ekim 2019

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - [`USP0005`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0005.md) `IDE0060` Tüm Unity iletileri için Suppressor (kullanılmamış parametre) eklendi.
  
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

  - unity 'ye özgü yeni tanılamalar ekleyerek Visual Studio unity projelerine yönelik olduğunu anlamak daha fazla sunuyoruz. Unity projeleri için geçerli olmayan genel C# tanılamalarını gizleyerek IDE’yi daha akıllı hale getirdik. Örneğin, IDE, Unity düzenleyicisinde değişkeni değiştirmenize engel olacak bir Inspector değişkenini değiştirmek için hızlı bir çözüm göstermez `readonly` .
    - [`UNT0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0001.md): Unity iletileri, boş olsalar bile çalışma zamanı tarafından çağrılır, Unity çalışma zamanına göre uncesseray işlemesini önlemek için bunları bildiremezsiniz.
    - [`UNT0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0002.md): Dize eşitlik kullanılarak etiket karşılaştırması yerleşik CompareTag yönteminden daha yavaştır.
    - [`UNT0003`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0003.md): Tür güvenliği için GetComponent 'un genel biçiminin kullanımı tercih edilir.
    - [`UNT0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0004.md): Güncelleştirme iletisi çerçeve hızına bağımlıdır ve Time. deltaTime yerine Time. fixedDeltaTime kullanın.
    - [`UNT0005`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0005.md): FixedUpdate iletisi çerçeve hızına bağımsızdır ve Time. fixedDeltaTime yerine Time. deltaTime kullanın.
    - [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0006.md): Bu Unity iletisi için yanlış bir yöntem imzası algılandı.
    - [`UNT0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0007.md): Unity, null birleştirme ile uyumsuz olan Unity nesneleri için null karşılaştırma işlecini geçersiz kılar.
    - [`UNT0008`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0008.md): Unity, null yayılmayla uyumsuz olan Unity nesneleri için null karşılaştırma işlecini geçersiz kılar.
    - [`UNT0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0009.md): Initializeonload özniteliği bir sınıfa uygulanırken, bir statik Oluşturucu sağlamanız gerekir. InitializeOnLoad özniteliği, düzenleyici başlatıldığında bunun çağrılmasını sağlar.
    - [`UNT0010`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0010.md): MonoBehaviours yalnızca AddComponent () kullanılarak oluşturulmalıdır. MonoBehaviour bir bileşendir ve bunun GameObject’e eklenmesi gerekir.
    - [`UNT0011`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0011.md): ScriptableObject yalnızca CreateInstance () kullanılarak oluşturulmalıdır. Unity ileti yöntemlerinin işlenmesi için ScriptableObject’in Unity altyapısı tarafından oluşturulması gerekir.
    - [`USP0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0001.md) için `IDE0029` : Unity nesneleri null birleştirme kullanmamalıdır.
    - [`USP0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0002.md) için `IDE0031` : Unity nesneleri null yayma kullanmamalıdır.
    - [`USP0003`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0003.md) için `IDE0051` : Unity Iletileri Unity çalışma zamanı tarafından çağrılır.
    - [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0004.md) için `IDE0044` : SerializeField özniteliğine sahip alanlar ReadOnly yapılmamalıdır.

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

  - AVH Protocol 2,51 için destek eklendi.

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

  - Unity Project gezgini 'nden herhangi bir tür dosya oluşturmak için yeni bir seçenek eklendi.
  
  - Unity projeleri için hızlı derlemeler kullanırken tanılama önbelleğe almayı geliştirme.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Dosya Uzantısı iyi bilinen herhangi bir düzenleyici tarafından işlenmediğinde bir sorun düzeltildi.

  - Unity Project gezgininde özel uzantılar için sabit destek.

  - Ana iletişim kutusunun dışında sabit kaydetme ayarları.

  - Eski Microsoft. VisualStudio. MPF bağımlılığı kaldırıldı.

## <a name="4110"></a>4.1.1.0

Yayımlanma tarihi 24 Mayıs 2019

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - MonoBehaviour API'si 2019.1'e güncelleştirildi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Basit derleme etkinleştirildiğinde çıkışa raporlama uyarıları ve hataları düzeltildi.

  - Basit derleme performansı düzeltildi.

## <a name="4100"></a>4.1.0.0

Yayın tarihi: 21 Mayıs 2019

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Projeleri daha hızlı yeniden yüklemek için yeni batch API'si desteği eklendi.

  - IntelliSense hataları ve uyarılarını kullanmak yerine Unity projeleri için tam derleme devre dışı bırakıldı. Hatta Unity, Unity Visual Studio yaptığı işi temsil eden sınıf kitaplığı projeleriyle birlikte bir çözüm oluşturur. Bununla birlikte derleme işlem hattı kapatılan Visual Studio unity tarafından hiçbir zaman kullanılmaz veya toplanmayacak. Bu Visual Studio yalnızca kaynakları hiçbir şey için tüketmektir. Tam derlemeye ihtiyacınız varsa, buna bağlı araçlar veya bir kurulum varsa, bu iyileştirmeyi devre dışı abilirsiniz (Unity için Araçlar/Seçenekler/Araçlar/Projelerin tam derlemesini devre dışı bırak).

  - Unity projesi yüklendiğinde Unity Project Gezgini'ni (UPE) otomatik olarak göster. UPE, yüklemenin yanına Çözüm Gezgini.

  - Unity 2019.x ile proje adı ayıklama mekanizması güncelleştirildi.

  - UPE'de Unity paketleri için destek eklendi. Yalnızca Başvurulan paketler (manifest.jsklasördeki paketler kullanılarak) ve `Packages` Yerel paketler (klasöre `Packages` eklenmiş) görünür.

- **Project Nesil:**

  - Çözüm dosyasını işlerken dış özellikleri koruma.

- **Değerlendirme:**

  - Diğer adlar için destek eklendi (şimdilik yalnızca genel ad alanı). Bu nedenle ifade değerlendiricisi artık global::namespace.type formunu kullanarak türleri kabul ediyor.

  - İşaretçi `pointer[index]` başvuru formuyla benzer olan form desteği `*(pointer+index)` eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Microsoft.VisualStudio.MPF ile ilgili bağımlılık sorunları düzeltildi.

  - Hiçbir proje yüklenmeden UWP oynatıcı eklemesi düzeltildi.

  - Veritabanı henüz bağlı Visual Studio otomatik varlık veritabanı yenilemesi düzeltildi.

  - Etiketler ve onay kutularıyla ilgili tema sorunları düzeltildi.

- **Hata ayıklayıcı:**

  - Statik oluşturucularla adımlama düzeltildi.

## <a name="4005"></a>4.0.0.5

Yayın tarihi: 27 Şubat 2019

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Kurulum Visual Studio ile sürüm algılama düzeltildi.

  - Kullanılmayan derlemeler kurulum paketinden kaldırıldı.

## <a name="4004"></a>4.0.0.4

Yayın tarihi: 13 Şubat 2019

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Yükleme sırasında Unity işlemlerini düzgün algılamaya ve kurulum altyapısının dosya kilitlerini daha iyi işlemesine izin vermek için destek eklendi.

  - API `ScriptableObject` güncelleştirildi.

## <a name="4003"></a>4.0.0.3

Yayın tarihi: 31 Ocak 2019

### <a name="new-features"></a>Yeni Özellikler

- **Project Nesil:**

  - Genel ve serileştirilmiş alanlar artık uyarılara neden olmaz. Bu iletileri oluşturan Unity projelerinde `CS0649` `IDE0051` ve derleyici uyarılarını otomatik olarak bastırmıştık.

- **Entegrasyon:**

  - Unity düzenleyicisi ve oynatıcı örneklerini görüntülemeye ilişkin kullanıcı deneyimi iyileştirildi (windows artık yeniden boyutlandırılabilir, tekdüz kenar boşlukları kullanabilir ve yeniden boyutlandırılabilir bir kavrama görüntüleniyor). Unity Process-Id için daha fazla bilgi eklendi.

  - API `MonoBehaviour` güncelleştirildi.

- **Değerlendirme:**

  - Yerel işlevler için destek eklendi.

  - Sahte değişkenler (özel durum ve nesne tanımlayıcıları) için destek eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Bilinen görüntüler ve temalarla ilgili bir sorun düzeltildi.

  - Varlık veritabanını Çıkış Penceresi hata ayıklarken yalnızca hata ayıklarken bu veritabanına yazın.

  - MonoBehaviour sihirbazı filtrelemesi ile kullanıcı arabirimi gecikmeleri düzeltildi.

- **Hata ayıklayıcı:**

  - Eski protokol sürümleri kullanırken adlandırılmış bağımsız değişkenler üzerinde özel özniteliğin okunması düzeltildi.

## <a name="4002"></a>4.0.0.2

Yayın tarihi: 23 Ocak 2019

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Deneysel derleme oluşturma düzeltildi.

  - Kullanıcı arabirimi iş parçacığı baskılarını en aza indirmek için proje dosyası olay işleme düzeltildi.

  - Toplu metin değişiklikleriyle tamamlama sağlayıcısı düzeltildi.

- **Hata ayıklayıcı:**

  - Ekli hata ayıklayıcıda kullanıcı hata ayıklama iletilerinin görüntüsü düzeltildi.

## <a name="4001"></a>4.0.0.1

Yayın tarihi: 10 Aralık 2018

### <a name="new-features"></a>Yeni Özellikler

- **Değerlendirme:**

  - İfade değerlendirmesi için Roslyn yerine NRefactory değiştirildi.

  - İşaretçiler için destek eklendi: başvuru, atama ve işaretçi aritmetiği (bunun için hem Unity 2018.2+ hem de yeni çalışma zamanı gereklidir).

  - Dizi işaretçisi görünümü için destek eklendi (C++'da olduğu gibi). Bir işaretçi ifadesi alıp virgül ve görmek istediğiniz öğe sayısını girin.

  - Zaman uyumsuz yapılar için destek eklendi.

- **Entegrasyon:**

  - Kaydetme sırasında Unity'nin varlık veritabanını otomatik olarak yenileme desteği eklendi. Bu varsayılan olarak etkindir ve bir betik bir komut dosyası bir komut dosyası kaydedildiğinde Unity tarafında yeniden derlemeyi Visual Studio. Kaydetme sırasında Unity\Refresh Unity'nin AssetDatabase'i için Araçlar\Seçenekler\Araçlar'da bu özelliği devre dışı dilersiniz.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Tercih edilen dış Visual Studio seçili değilken köprü etkinleştirmesi düzeltildi.

  - Hatalı biçimlendirilmiş veya desteklenmeyen ifadelerle ifade değerlendirmesi düzeltildi.

## <a name="4000"></a>4.0.0.0

Yayın tarihi: 4 Aralık 2018

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Visual Studio 2019 desteği eklendi (Visual Studio 2019'un dış betik düzenleyicisi olarak kullanılayabilecek olması için en az Unity 2018.3 gerekir).

  - HDPI ölçeklendirme, Visual Studio mükemmel görüntüler ve theming için tam destekle, genel görüntü hizmeti ve kataloğu benimsedi.

### <a name="deprecated-features"></a>Kullanım dışı bırakılan özellikler

- **Tümleştirme**

  - Unity için Visual Studio Araçları, yalnızca unity 5.2 + ' ı destekler (unity 'nin yerleşik Visual Studio tümleştirmesiyle).

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

  - unity 'nin hata ayıklayıcı altyapısı ile iletişim kurmak için kullanılan kitaplıkta bir kilitlenme düzeltildi, özellikle ' Unity 'ye ekle ' veya oyunu yeniden başlatma sırasında Visual Studio veya Unity dondurma.

## <a name="3901"></a>3.9.0.1

Yayımlanma tarihi, 15 Kasım 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Başka bir varsayılan düzenleyici seçildiğinde, sabit Unity eklentisi etkinleştirmesi.

## <a name="3900"></a>3.9.0.0

Yayın tarihi, 13 Kasım 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Project Mesinden**

  - Unity tarafından düzeltilen bir Unity performans hatası için geçici çözümü geri alındı.

## <a name="3807"></a>3.8.0.7

Yayımlanma tarihi, 20 Eylül 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Sý**

  - (3.9.0.2 'ten geri alma) unity 'nin hata ayıklayıcı altyapısı ile iletişim kurmak için kullanılan kitaplıkta bir kilitlenme düzeltildi, özellikle ' Unity 'ye ekle ' veya oyunu yeniden başlatma sırasında Visual Studio veya Unity dondurma.

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

- **Project Mesinden**

  - (3.9.0.0 'ten geri alma) Unity tarafından düzeltilen bir Unity performans hatası için geçici çözümü geri alındı.

## <a name="3802"></a>3.8.0.2

Yayın tarihi 7 Temmuz 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Project Mesinden**

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

- **Project Mesinden**

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

  - düzenlenmiş hata ayıklama için destek eklendi (aynı Visual Studio oturum ile birden çok oynatıcı/düzenleyicide hata ayıklama).

  - Android USB oynatıcı hata ayıklama desteği eklendi.

  - UWP/IL2CPP Player hata ayıklama desteği eklendi.

- **Değerlendirmesinin**

  - Onaltılık tanımlayıcılar için destek eklendi.

  - Geliştirilmiş Gözcü penceresi değerlendirme deneyimi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Özel durum ayarlarının sabit kullanımı.

- **Project Mesinden**

  - Paket Yöneticisi derleme birimlerini oluşturma işleminden dışlayın.

## <a name="3605"></a>3.6.0.5

Yayın tarihi 13 Mart 2018

### <a name="new-features"></a>Yeni Özellikler

- **Project Mesinden**

  - Unity 2018,1 ' de yeni proje Oluşturucu desteği eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Özel projelerle bozulmuş durumları işleme düzeltildi.

- **Sý**

  - Next ifadesinin ayarlanması düzeltildi.

## <a name="3604"></a>3.6.0.4

Yayımlanma tarihi, 5 Mart 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Project Mesinden**

  - Sabit mono sürümü algılama.

- **Tümleştirme**

  - 2018,1 ve eklenti etkinleştirme ile ilgili sabit zamanlama sorunları.

## <a name="3603"></a>3.6.0.3

Yayın tarihi, 23 Şubat 2018

### <a name="new-features"></a>Yeni Özellikler

- **Project Mesinden**

  - .NET Standard için destek eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Project Mesinden**

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

- **Project Mesinden**

  - 2018,1 Monoadası başvuru modeli için destek eklendi.

- **Değerlendirmesinin**

  - $Exception tanımlayıcı için destek eklendi.

- **Sý**

  - Yeni Unity çalışma zamanına sahip öznitelikler aracılığıyla DebuggerHidden/Debuggerstepdesteği eklendi.

- **'Nı**

  - Sihirbazlar için ' en son ' sürümünü tanıtın.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Project Mesinden**

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

  - Unity düzenleyicisinde hata ayıklamak için Xamarin ve Mac için Visual Studio tarafından paylaşılan Mono hata ayıklayıcısını kullanma seçeneği eklendi.

  - Taşınabilir hata ayıklama sembol dosyaları için destek eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Düzeltilen kurulum bağımlılıkları sorunları.

  - Sabit Unity API Yardım menüsü gösterilmiyor.

- **Project Mesinden**

  - IL2CPP/. NET 4,6 arka ucu ile UWP oyunu üzerinde çalışırken düzeltilen oynatıcı proje üretimi.

  - Derleme dosya adına yanlışlıkla eklenmiş ek .dll uzantısı düzeltildi.

  - Genel bir tane yerine belirli bir Project API Uyumluluk düzeyinin sabit kullanımı.

  - Varsayılan olarak ' true ' olduğundan AllowAttachedDebuggingOfEditor Unity bayrağını zorlamayın.

## <a name="3402"></a>3.4.0.2

Yayın tarihi 19 Eylül 2017

### <a name="new-features"></a>Yeni Özellikler

- **Project Mesinden**

  - Derleme birimlerinde assembly.jsiçin destek eklendi.

  - Unity derlemelerinin proje klasörüne kopyalanması durduruldu.

- **Sý**

  - Yeni Unity çalışma zamanı ile sonraki ifadeyi ayarlamaya yönelik destek eklendi.

  - Yeni Unity çalışma zamanına sahip onlu tür için destek eklendi.

  - Örtük/açık dönüştürmeler için destek eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Değerlendirmesinin**

  - Örtük boyut ile sabit dizi oluşturma.

  - Sabit derleyici, Yerellerle oluşturulmuş öğeler.

- **Project Mesinden**

  - 4,6 API düzeyi için Microsoft. CSharp 'e yönelik sabit başvuru.

## <a name="3302"></a>3.3.0.2

15 Ağustos 2017 ' de yayınlandı

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Project Mesinden**

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

  - Visual Studio Watch 'a öğe eklerken oluşan sorunlar düzeltildi.

- **Project Mesinden**

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

- **Project Mesinden**

  - .NET 4,6 profili için destek eklendi.

  - MCS. rsp dosyaları için destek eklendi.

  - Unity 5,6 kullanıldığında her zaman güvenli olmayan derleme anahtarını etkinleştirin.

  - Windows Store platformu ve il2cpp arka ucu kullanılırken "oynatıcı" proje oluşturma desteği eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Kod Düzenleyicisi:**

  - Otomatik tamamlama ile Yöntem eklendikten sonra düzeltilen giriş işareti konumu.

- **Project Mesinden**

  - Derleme sürümü işleme sonrası kaldırıldı.

## <a name="3001"></a>3.0.0.1

Yayın tarihi 7 Mart 2017

### <a name="this-version-includes-all-new-features-and-bug-fixes-introduced-with-28x-series"></a>Bu sürüm, 2.8. x serisi ile tanıtılan tüm yeni özellikleri ve hata düzeltmelerini içerir.

## <a name="2820---30-preview-3"></a>2.8.2.0-3,0 Preview 3
25 Ocak 2017 tarihinde yayınlandı

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Project Mesinden**

  - İkinci kez bir ikili DLL olarak, önce bir proje başvurusu olarak başvurulan eklenti projelerinin bulunduğu bir sabit gerileme.

## <a name="2810---30-preview-2"></a>2.8.1.0-3,0 Preview 2
Yayın tarihi, 23 Ocak 2017

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Kod Düzenleyicisi:**

  - Küme ayracı tamamlanana gerek olmadan bir öznitelik bildirimi başlatıldığında kilitlenme düzeltildi.

- **Sý**

  - Yeni Unity derleyicisi/çalışma zamanı altındaki eş değerleri içeren sabit işlev kesme noktaları.

  - Bağlanabilir kesme noktası (karşılık gelen kaynak-konum bulunamadı) durumunda uyarı eklendi.

- **Project Mesinden**

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

- **Project Mesinden**

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

- **Project Mesinden**

  - Unity Web oynatıcı hedeflenirken derlemeyi önleyen hata düzeltildi.

  - Web kodlamalı dosya adı ile bir betiği derlerken derlemeyi önleyen hata düzeltildi.

## <a name="2300"></a>2.3.0.0

Yayın tarihi 14 Temmuz 2016

### <a name="new-features"></a>Yeni Özellikler

- **Genel**

  - Visual Studio hata listesindeki Unity konsol günlüklerini devre dışı bırakma seçeneği eklendi.

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

  - hata ayıklanırken Visual Studio dondurmasına neden olan bir sorun düzeltildi.

  - Visual Studio 2015 ' deki işlev kesme noktaları ile ilgili bir sorun düzeltildi.

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

- **Project oluşturma:**

  - Unity 4,6 ' de UnityEngine ve UnityEditor 'a yönelik sabit başvurular.

  - Unity, OSX üzerinde çalışırken proje dosyalarının sabit üretimi düzeltildi.

  - Diyez işareti (#) karakteri içeren proje adlarının sabit işlenmesi.

  - Kısıtlanmış oluşturulan projeler C# 4 ' e.

- **Sý**

  - Unity eş içinde hata ayıklanırken ifade değerlendirmesiyle ilgili bir sorun düzeltildi.

  - hata ayıklanırken Visual Studio dondurmasına neden olan bir sorun düzeltildi.

- **'SıNı**

  - [sekmeler Studio](https://tabsstudio.com/) Visual Studio uzantısıyla uyumsuzluk düzeltildi.

- **Yükleyicinin**

  - HKLM Kayıt defteri girişleri oluşturarak, bir VSTU (tüm kullanıcılar için yükleme) makine genelinde yüklemesini destekler.

  - Aynı VSTU sürümü birden çok Visual Studio farklı sürümü için yüklendiğinde VSTU 'nin kaldırılmasıyla ilgili sorunlar düzeltildi. Örneğin, VSTU **2015** 2.1.0.0 ve vstu **2013** 2.1.0.0 her ikisi de yüklüyse.

## <a name="2100"></a>2.1.0.0

Yayın tarihi, 8 Eylül 2015

### <a name="new-features"></a>Yeni Özellikler

- Unity 5,2 için destek

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Unity < 4,2 ' de menü öğelerini görüntüle

- Visual Studio XML ıntellisense dosyalarını kilitlediğinde bir hata iletisi artık görüntülenmiyor.

- \<When Changed>Koşullu bağımsız değişken bir Boole değeri olmadığında, koşullu kesme noktaları> <tanıtıcısı.

- Windows Store uygulamaları için UnityEngine ve unityeditor derlemeleriyle ilgili sabit başvurular.

- Hata ayıklayıcıda adımla düzeltilen hata: adım, genel özel durum.

- Visual Studio 2015 ' de sabit isabet sayısı kesme noktaları düzeltildi.

## <a name="2000"></a>2.0.0.0

Yayın tarihi 20 Temmuz 2015

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Unity tümleştirmesi:**

  - DLL ve hata ayıklama sembolleri (PDB) içeri aktarılırken Visual Studio 2015 ile oluşturulan hata ayıklama simgelerinin dönüştürülmesi düzeltildi.

  - Bir MDB dosyası da sağlanmasının dışında, bir DLL ve hata ayıklama sembolleri (PDB) içeri aktarırken her zaman MDB dosyaları oluştur.

  - Bir obj diziniyle Unity proje dizininin sabit bir şekilde kirmi düzeltildi.

  - System.Xml başvuruların sabit üretimi. LINK ve System. Runtime. Serialization.

  - Proje dosyası oluşturma API kancalarına birden çok abone desteği eklendi.

  - Oluşturulacak dosyalardan biri kilitlendiğinde bile proje dosya oluşturmayı her zaman doldurun.

  - C# projesine dahil edilecek dosyaları belirtirken uzantı filtresinde * joker karakterleri için destek eklendi.

- **Visual Studio tümleştirme:**

  - Üretkenlik güç araçlarıyla bir uyumluluk sorunu düzeltildi.

  - Olaylar ve temsilciler bildirimlerinin etrafında Monodavranışlar üretme düzeltildi.

- **Sý**

  - Hata ayıklanırken olası dondurma düzeltildi.

  - Belirli yığın çerçevelerinde Yerellerden görüntülenmeyen bir sorun düzeltildi.

  - Boş dizileri inceliyor düzeltildi.

## <a name="1990---20-preview-2"></a>1.9.9.0-2,0 Preview 2
Yayın 2 Nisan 2015

### <a name="new-features"></a>Yeni özellikler

- **Unity Project gezgini:**

  - Unity Project gezgininde bir dosyayı yeniden adlandırırken otomatik olarak sınıfı yeniden adlandır (bkz. **seçenekler** iletişim kutusu).

  - Unity Project gezgininde yeni oluşturulan betikleri otomatik olarak seçin.

  - Unity Project gezgini 'nde etkin betiği izleyin (bkz. **seçenekler** iletişim kutusu).

  - Visual Studio Çözüm Gezgini ikili olarak eşitler (bkz. **seçenekler** iletişim kutusu).

  - Unity Project gezgininde Visual Studio simgeleri benimseyin.

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

  - en iyi duruma getirilmiş Unity için Visual Studio Araçları uzantısı kaydı.

  - Unity 5 için Unity için Visual Studio Araçları paketini yükler.

- **Belgeler:** Belge oluşturma performansını geliştirir.

- **Sihirbazlar:** Unity 4,6 ve Unity 5 için yeni MonoBehavior yöntemlerini destekler.

- **Unity:** Proje dosyası oluşturma sırasında. rsp dosyalarında güvenli olmayan bayraklar ve özel tanımlar arama yapın.

- **Kullanıcı arabirimi:** Visual Studio Unity için Visual Studio Araçları **seçenekleri** iletişim kutusu eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Unity Project gezgini:**

  - dosyalar Visual Studio Çözüm Gezgini taşındıktan sonra veya yeniden adlandırıldıktan sonra Unity Project gezginini yenileyin.

  - Unity Project gezgini 'ndeki dosyaları yeniden adlandırırken seçimleri koru.

  - Unity Project gezgini 'nde dosyalar çift tıklandığında otomatik genişletmeyi önleyin ve daraltın.

  - yeni seçilen dosyaların Unity Project gezgini 'nde göründüğünden emin olun.

- **Sý**

  - hata ayıklayıcıda ifadeler değerlendirilirken olası bir Visual Studio dondurmasını önleyin.

  - Yöntem etkinleştirmeleri hata ayıklayıcıda doğru etki alanında gerçekleşdiğinden emin olun.

- **'Yi**

  - UnityVS. OpenFile konumunu Unity 5 ile düzeltin.

  - Pdb2mdb konumunu Unity 5 ile düzeltin.

  - Proje dosyası oluşturma sırasında olası bir özel durumu önleyin.

  - OSX üzerinde Unity çalıştırırken olası dondurma önleme.

  - İç özel durumları işleyin.

  - Unity konsol günlüklerini VS hata listesine gönderin.

- **Belgeler:** Yeni Unity belgeleri için doğru belge oluşturma.

- **Project:** Gerektiğinde de Unity. meta dosyalarını taşıyın ve yeniden adlandırın.

- **Sihirbazlar:** Kod oluştururken MonoBehavior yöntem parametrelerinin sırasını düzeltin.

- **Kullanıcı arabirimi:** bağlam menüsü ve simgeler için Visual Studio temalarını destekler.

## <a name="1980---20-preview"></a>1.9.8.0-2,0 Preview
Yayımlanma tarihi, 12 Kasım 2014

### <a name="new-features"></a>Yeni özellikler

- 2015 Visual Studio için destek.

- Visual Studio 2015 ' deki Unity gölgelendiriciler için kod renklendirme.

- Hata ayıklama sırasında değerlerin görselleştirilmesi geliştirildi:

  - ArrayLists, listeler, hashtables ve sözlükler için daha iyi görselleştirme.

  - Genel olmayan üyeleri ve statik üyeleri, izleme ve yerel görünümlerde kategori olarak gösterin.

  - Unity 'nin SerializedProperty özelliğinin yalnızca özellik için geçerli olan değer alanını değerlendirmek için iyileştirilmiş görünümü.

  - Sınıflar ve yapılar için DebuggerDisplayAttribute desteği.

  - DebuggerTypeProxyAttribute desteği.

- Kullanıcı kodlama kurallarına göre sihirbazları kullanarak Monodavranış yöntemlerinin eklenmesini sağlayın.

- UnityVS tarafından oluşturulan projelerde derleme zamanı metin şablonları için destek uygulayın.

- UnityVS tarafından oluşturulan projelerde ResX kaynakları için destek uygulayın.

- Unity 'den Visual Studio içinde gölgelendiriciler açmayı destekler.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Bağlama ve yürütme sonrasında Unity 'de oyuna başlamadan önce Yuvaları Temizleme Visual Studio. Bu, Attach ve Play kullanılırken Unity ile VS arasındaki bağlantının kararlılığı ile ilgili bazı sorunları düzeltir.

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

- Visual Studio dosyaları silerken veya yeniden adlandırırken. meta dosyaları silin ve yeniden adlandırın.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Visual Studio temalarını işlemeyi çözme. Daha önce, siyah temalardaki iletişim kutuları boş görünebilir.

- Unity yeniden derlenirken hata ayıklayıcıyı bağlarken Unity donması 'nı düzeltemedi.

- Başka bir sistemde derlenen uzak düzenleyicilerde veya yürütücülerde hata ayıklarken kesme noktalarını düzeltme.

- kesme noktası isabet edildiğinde olası Visual Studio kilitlenmeyi düzeltir.

- Kesme noktaları bağlantısını, bellekten kaldırılmamasına engel olmak için düzeltir.

- Kapsam dışında görünen canlı değişkenlerin önüne geçmek için hata ayıklayıcıda değişken kapsamının işlenmesini düzeltir.

- Hata ayıklayıcının Ifade değerlendirmesi içindeki statik üyelerin aramasını düzeltir.

- Statik alanları ve özellikleri göstermek için hata ayıklayıcının Ifade değerlendirmesinde türlerin görüntülenmesini düzeltir.

- Unity proje adları, yasaklıyor Visual Studio (Bağlan sorunu #948666) özel karakterler içerdiğinde, çözümün oluşturulmasını düzeltir.

- seçenek işaretlendikten sonra konsol olaylarının gönderilmesini hemen durdurmak için Visual Studio Araçları Unity paketini onarın (Bağlan sorunu #933357).

- UnityEngine. UI gibi yeni API 'Lerin başvurularını doğru şekilde yeniden oluşturmak için başvuruları algılamayı, UnityVS tarafından oluşturulan projelerde düzeltir.

- yükleyici, bozuk yüklemelerin olmaması için yüklemeden önce Visual Studio kapatılmasını gerektirecek şekilde düzeltilir.

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

- proje yeniden yüklendikten sonra Unity Project gezgini 'nin durumunu koru.

- Unity Project gezginini geçerli belgeyle eşitleyecek bir komut ekleyin.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Koşulu hata ayıklayıcıya başlamadan önce ayarlanan koşullu kesme noktalarını düzeltir.

- Uyarıları önlemek için UnityEngine başvurularını onarın.

- Unity betas için ayrıştırma sürümlerini onarma.

- Bir kesme noktasına veya adımlamayı vurarak değişkenlerin yerel değişkenler penceresinde gözükmesine neden olan sorunu giderme.

- Visual Studio 2013 değişkenleri araç ipuçlarını düzeltir.

- Unity 4,5 için IntelliSense belgelerinin oluşturulmasını düzeltir.

- bir etki alanı yeniden yüklendikten sonra unity/Visual Studio iletişimini onarın (unity 'de oynat/durdur).

- Visual Studio temalarının parçalarını işlemeyi çözme.

> [!IMPORTANT]
> C#, Unity ekosisteminde önceden baskın bir dil olmasını sağlar. yeni örnek varlıklar C# ' ta, Unity belgelerinin varsayılan değeri C# ' dir; C# deneyimine daha iyi odaklanmak için, Unityscrıpt ve Boo 'nun temel desteğini kaldırdık. Sonuç olarak, VSTU çözümleri artık C# ' dir ve yükleme için çok daha hızlıdır.

## <a name="1820"></a>1.8.2.0

Yayın tarihi 7 Ocak 2014

### <a name="new-features"></a>Yeni özellikler

- Düzenleyicilerin uzaktan bulunması için Unity'nin betik altyapısının Mavericks'te ağ katmanında bir soruna karşı çalışma.

- Uzak Unity oyuncularını bulmak için yeni bağlantı noktalarını işleme.

- Geçerli derleme hedefine özgü UnityEngine derlemesi başvurusu.

- Oluşturulan projelere dahil etmek için dosyaları filtreleme ayarı ekleyin.

- Konsol günlüklerinin hata listesine gönderilmesini devre dışı Visual Studio ayarı ekleyin. Konsol günlüklerini almak için Unity'de yalnızca bir geri çağırma Pro PlayMaker veya Console Pro kullanıyorsanız bu yararlı olur.

- mdb hata ayıklama sembollerinin neslini devre dışı bırakmak için ayar ekleyin. Bu, mdb'yi kendiniz üretiyorsanız kullanışlıdır.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Unity >= 4.2'den VS'de açılan dosyaların IntelliSense'i kaybetmesi durumunda ortaya çıkacak bir gerileme giderildi.

- Özel temaları işlemek için VS iletişim kutularımızı düzeltin.

- UPE'nin bağlam menüsünü kapatma sorunu giderildi.

- Sürüme özgü derleme eşit yoksa Unity'de kilitlenmeyi önle.

## <a name="1810"></a>1.8.1.0

Yayın tarihi: 21 Kasım 2013

### <a name="new-features"></a>Yeni özellikler

- Unity 4.3 API'leri ile MonoBehaviour sihirbazları ayarlandı.

- MonoBehaviour sihirbazları kullandığınız sürüme bağlı olarak Unity API'lerini filtreleiyor.

- System.Xml'a bir başvuru ekleyin. Unity > 4.1 projelerine linq.

- İletiye stacktrace başlangıcını dahil etmek için Debug.Log çağrılarımızı düzeltin.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Uygulama içinde JavaScript dosyalarının varsayılan işlenmesini engellemeye neden olan bir Visual Studio.

- Vs'de bu kez gerçek bir şekilde görünen beyaz piksel düzeltildi.

- SCM tarafından salt okunur olarak işaretlenmişse UnityVS.VersionSpecific derlemesi silindi.

- UnityVS paketinde yuva oluştururken ortaya çıkacak özel durumlar düzeltildi.

- Derlemelerden stok Visual Studio yüklenirken bir Visual Studio düzeltildi.

- Unity'nin kaynak derlemeleri için UnityVS.VersionSpecific neslinde bir hata düzeltildi.

- Unity paketinde yuva a açılışında olası bir donma düzeltildi.

- Unity projesinin adlarında tire (-) ile işlenmesi düzeltildi.

- Unity 4.2 ve üzeri için ALT+TAB sırası karıştırılamamak için Unity'den betiklerin açılması düzeltildi.

## <a name="1800"></a>1.8.0.0

Yayın tarihi: 24 Eylül 2013

### <a name="new-features"></a>Yeni özellikler

- Hata ayıklayıcı bağlantı hızı önemli ölçüde geliştirildi.

- Unity 4.2 ve üzeri dosya ve satırlarda gezinmeyi otomatik olarak işle.

- Koşullu kesme noktaları.

- Project oluşturucu artık T4 şablonlarını işlemeye başladı.

- MonBehavior sihirbazlarını yeni API'lerle güncelleştirin.

- Unity türleri için C# içinde IntelliSense belgeleri.

- Aritmetik ve mantıksal ifadeler değerlendirmesi.

- Uzaktan hata ayıklama önizlemesi için uzak düzenleyicileri daha iyi bulma.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Hata ayıklayıcının bağlantısını kesdikten sonra VS'de bir iş parçacığını sızdıran bir hata düzeltildi.

- VS'de görünen beyaz piksel düzeltildi.

- Durum çubuğu simgesine tıklamaların işlenmesi düzeltildi.

- Plugins klasörlerinde derlemelerle başvuru oluşturma düzeltildi.

- Özel durumlar durumunda UnityVS paketinden yuva oluşturma düzeltildi.

- UnityVS'nin yeni sürümlerinin algılanması düzeltildi.

- Lisansın süresi dolduğunda lisans yöneticisinin istemi düzeltildi.

- VS'nin işlem penceresine hata ayıklayıcısı eklemede işlem listesini boş hale getirdi hatası düzeltildi.

- Yerel görünümde Boole değerlerinin değiştirilmesi düzeltildi.

## <a name="1220"></a>1.2.2.0

Yayın tarihi: 9 Temmuz 2013

### <a name="bug-fixes"></a>Hata düzeltmeleri

- İfade değerlendiricisinde tam adları işleme.

- Unity betik altyapısının yanlış stackframe verileri gönderdiği özel durum işlemeyle ilgili bir donma düzeltildi.

- Web hedefleri için derleme işlemi düzeltildi.

- Bir dosya Visual Studio ve silinen bir dosya başlangıçta açılacak dosya listesinde yer alıyorsa, bu hata düzeltildi.

- Derlenmiş gölgelendiriciler gibi betik dışı dosyaları işlemek için UnityVS.OpenFile düzeltildi.

- Artık tüm C# projelerinden Boo.Lang ve UnityScript.Lang'e başvururuz.

- Projede özel karakterler varsa projelerde başvuru oluşturma düzeltildi.

- Geçici çözüm, atilen projelere yapılan yöntem çağrılarını birden çok NullReferenceException MessageBox tetikleyene bir VS sorunu.

- Unity 4.2 Beta derlemelerinin işlenmesi düzeltildi.

## <a name="1210"></a>1.2.1.0

Yayın tarihi: 9 Nisan 2013

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Bir IO hatası durumunda kod tamamlama için Unity derlemelerinin yerel dağıtımı düzeltildi (örneğin, salt okunur dosyalar veya kod tarafından kilitlenmiş dosyalar Visual Studio).

- Unity'den bir betiğin açılmasının dosyanın önceden açık olduğu bir dosyaya odaklanmaytiği bir regresyon Visual Studio.

- Yeni özel durum işlemenin performans sorunu düzeltildi.

- Bazı dış URL'lerde kesme noktaları bağlama düzeltildi.

## <a name="1200"></a>1.2.0.0

Yayın tarihi: 25 Mart 2013

### <a name="new-features"></a>Yeni özellikler

- Hata ayıklayıcı bağlantı hızı önemli ölçüde geliştirildi.

- Unity Project Explorer daha büyük projeler için iyileştirilmiş.

- İş Visual Studio özel durumlar için kesme (veya kesme) ayarlarını kullanın.

- Yerel değişkenler Visual Studio ToString'i çağıran bir varsayılan ayar kullanın.

- Unity oyuncularını hata ayıklamak > için kullanabileceğiniz Yeni Hata Ayıkla -veya Unity hata ayıklayıcısı ekle menüsü ekleyin.

- Çözüm dosyası oluşturma işlemi sırasında UnityVS çözümüne eklenen özel projeleri koruma.

- Unity işlevinin Unity belgelerini görüntülemek için CTRL+ALT+M -> CTRL+H klavye kısayolunu ekleyin.

- Derleyici yanıt dosyalarını (rsp) bir dosyadan derlerken dikkate Visual Studio.

- Oluşturucu yöntemlerinde hata ayıklarken değişkenleri göstermek için derleyici tarafından oluşturulan türlerin yok etme.

- Unity'de paylaşılan bir klasör yapılandırma ihtiyacı ortadan kaldırarak uzaktan hata ayıklamayı basitleştirin. Şimdi unity projenize yalnızca Windows.

- Standart bir .NET hedef profili olarak özel bir Unity profili yükleyin. Bu, ReSharper'ın göstere tüm hatalı pozitifleri düzeltir.

- Hata ayıklayıcının düzgün şekilde kayıtlı olmayan iş parçacıklarında kesmesi için Bir Unity betik altyapısı hatasına karşı çalışma.

- VS'de dosya açıcıyı yeniden çalışarak dosyaları açarken dosya açma isteğinin kilitlenmesi durumuyla karşılaşmasını önle.

- UnityVS artık VS projeyi derlemek için derlemeyi yenilemek istiyor, artık dosya kaydetmede değil.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Özel .NET profilimiz düzeltildi

- Tema tümleştirmesi düzeltildi. Bu, VS 2012 koyu temasıyla ilgili sorunlarımızı düzeltir.

- VS 2012'de hızlı davranış kısayolu düzeltildi.

- Hata ayıklama sırasında ve ana olmayan bir iş parçacığı bir kesme noktasıyla karşılaşan bir adımlama sorunu düzeltildi.

- Int gibi tür diğer adlarının UnityScript ve Boo tamamlaması düzeltildi.

- Yeni bir UnityScript veya Boo dizesi yazarken özel durum düzeltildi.

- Çözüm yüklenmemişken Unity menülerinde özel durumlar düzeltildi.

- BUGS-48 hatası düzeltildi: çift tırnak yazmak bazen hataya neden oluyor ve tüm işlevi bozabiliyor (kod tamamlama, söz dizimi vurgulama vb.).

- BUGS-46: Dosyanın Hata Listesi'ne tıklanan yinelenen açık betik dosyası (UnityScript) Visual Studio.

- BUGS-42 hatası düzeltildi: Durum çubuğundaki Unity bağlantı logosu VS 2012'de fare olaylarını işlemedi.

- BUGS-44 hatası düzeltildi: Hızlı MonoBehaviours için VS 2012'de CTRL+SHIFT+Q kullanılamıyor.

- BUGS-40 hatası düzeltildi: Pencere VS2012 "koyu" temasında etkin değilken Unity Project Gezgini'nde seçilen öğelerin okunamaz durumda olduğu düzeltildi.

- BUGS-39 hatası düzeltildi: Kaçan dizeleri belirteçlere akentleme sorunu.

- BUGS-35 hatası düzeltildi: Değişkenler incelerken nesnelerde ToString çağırma.

- BUGS-27 hatası düzeltildi: VS2012'de "koyu" temayla Sembol penceresi tutarsızlığı düzeltildi.

- BUGS-11 hatası düzeltildi: Yereller, coroutines içinde.

## <a name="1100---beta-release"></a>1.1.0.0 - Beta sürümü
Yayın tarihi: 9 Mart 2013

## <a name="10130"></a>1.0.13.0
Yayın tarihi: 21 Ocak 2013

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Hedef hata Visual Studio geçersiz iş parçacığı olayları gönderdiği durumda karşılaşan bir güvenlik kilitlenmesi düzeltildi. Bu durum genellikle OSX üzerinde uzak unity hata ayıklaması sırasında ortaya gider.

- Bir Visual Studio hata ayıklayıcısını kapatırsa karşılaşan bir güvenlik kilitlenmesi düzeltildi.

- Bir C# MonoBehavior ad alanı içinde olduğunda MonoBehavior yardımcılarımız düzeltildi.

- Visual Studio 2012'de UnityScript için hata ayıklayıcı araç ipucu düzeltildi.

- Unity'den yalnızca hata ayıklama sabitleri değiştiriken proje oluşturma düzeltildi.

- Unity Project Explorer'da klavyeyle gezinme düzeltildi.

- Kaçan dizeler için UnityScript renklendirmesi düzeltildi.

- Unity dışında kullanılırken proje adını daha iyi tahmin etmek için dosya açıcımız düzeltildi. Kullanıcı UnityVS'ye temsilci seçen Unity'de üçüncü parça dosya açıcıyı kullandığında bu gereklidir.

- Unity'den UnityVS'ye gönderilen uzun iletilerin işlenmesi düzeltildi. Bundan önce uzun iletiler UnityVS'nin mesajlaşma bölümü olarak kilitlenmeye neden olabilir. Sonuç olarak, bazen UnityVS Unity'den bir dosya açmaz.

## <a name="10120"></a>1.0.12.0
Yayın tarihi: 3 Ocak 2013

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Kesme Visual Studio silme işlemi olduğunda Visual Studio kilitlenmesi düzeltildi.

- Unity yeniden derleme oyun betikleri sonrasında bazı kesme noktalarına isabet edilmayna neden olan bir hata düzeltildi.

- Hata ayıklayıcı, kesme noktaları Visual Studio doğru şekilde bildirilecek şekilde düzeltildi.

- Hata ayıklayıcının yerel programlarda hata Visual Studio önleyen bir kayıt sorunu düzeltildi.

- UnityScript ve Boo ifadeleri değerlendirilmiştir.

- Unity'de .NET API düzeyinin değiştirilmesinin proje dosyalarının güncelleştirilerek tetiklenene bir regresyon düzeltildi.

- Kullanıcı kodunun günlük geri çağırma işleyiciye katılamama hatası düzeltildi.

## <a name="10110"></a>1.0.11.0
Yayın tarihi: 28 Kasım 2012

### <a name="new-features"></a>Yeni özellikler

- Unity 4'e resmi destek.

- Unity Project Explorer'dan betiklerin işlemesi.

- Visual Studio Git penceresinde tümleştirme.

- Bilgi konsolu iletisini ayrıştırma, böylece Hata Listesi'ne tıklarsanız sembollerle ilk yığın çerçevesine gelirsiniz.

- Kullanıcının proje oluşturmasına katılmasını sağlarken bir API ekleyin.

- Kullanıcının LogCallback'e katılmasını sağlarken bir API ekleyin.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Visual Studio 2012'de Unity Project Gezgini'nin arka planında gerileme düzeltildi.

- Tam .NET profilinin kullanıcıları için proje oluşturma düzeltildi.

- Web hedefi kullanıcıları için proje oluşturma düzeltildi.

- Proje oluşturma işlemi Unity'nin yaptığı gibi DEBUG ve TRACE derleme sembollerini içerecek şekilde düzeltildi.

- Goto Sembolü penceremizde özel karakterler kullanırken kilitlenme düzeltildi.

- Simgemizi uygulamanın durum çubuğuna Visual Studio kilitlenme düzeltildi.

## <a name="10100"></a>1.0.10.0
Yayın tarihi: 9 Ekim 2012

### <a name="bug-fixes"></a>Hata Düzeltmeleri

- Visual Studio 2010'da Unity Project Gezgini'nin arka planı düzeltildi.

- UnityVS Visual Studio hata ayıklayıcı arabirimi daha önce çöken bir Unity'ye eklemeye çalışsa ortaya çıkacak bir hata ayıklama hatası düzeltildi.

- Bir Visual Studio noktası ayarlanma ve AppDomain yeniden yüklemesi oluştuğunda ortaya çıkabilir bir hata hatası düzeltildi.

- Dosyaları kilitlememek ve Unity derleme işlemini karıştırmamak için derlemelerin Unity'den nasıl alınıp

## <a name="1090"></a>1.0.9.0

Yayın tarihi: 3 Ekim 2012

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Unity projesi gerçek JavaScript varlıkları içerirken proje oluşturma düzeltildi.

- İfade değerlendirmesinde hata işleme düzeltildi.

- Yeni değerleri değer türlerinin alanlarına ayarlama düzeltildi.

- Kod düzenleyicisinden ifadelerin üzerine gelindiğinde ortaya gelen olası yan etkiler düzeltildi.

- Yüklenen derlemelerde ifade değerlendirmesi için türlerin nasıl arandığı düzeltildi.

- BUGS-21 hatası düzeltildi: Unity nesnelerinde atama değerlendirmesinin hiçbir etkisi yoktur.

- UNITY MATH API'sine yöntem çağrısını değerlendirirken geçersiz işaretçi hatası düzeltildi.

## <a name="1080"></a>1.0.8.0

Yayın tarihi: 26 Eylül 2012

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Betik açıcımızın hem proje yolunu hem de betikleri aça olduğundan emin olmak için Visual Studio düzeltildi.

- Hata ayıklama oturumu çalışırken oluşturulan ve hata ayıklama oturumunun kilitlenmesini Visual Studio bir hata düzeltildi.

- UnityVS'nin 2010'da Visual Studio düzeltildi.

## <a name="1070"></a>1.0.7.0

Yayın tarihi: 14 Eylül 2012

### <a name="new-features"></a>Yeni özellikler

- Visual Studio 2012 desteği.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Editor ve Plugins proje dosyalarının oluşturması Unity'nin davranışıyla eş olacak şekilde düzeltildi.

- Unity 4'te .pdb sembollerinin çevirisi düzeltildi.

> [!IMPORTANT]
> 2012 Visual Studio nedeniyle birkaç dosyayı yeniden adlandırmamız ve birkaç dosyayı başka bir yere taşımamız gerekirdi. Unity'i içeri aktaracak UnityVS paketi artık sırasıyla Visual Studio 2010 ve 2012 için UnityVS 2010 veya UnityVS 2012 Visual Studio olarak adlandırılmıştır. Bu sürüm ayrıca UnityVS proje dosyalarının yeniden oluşturulmasını gerektirir.

## <a name="1060---internal-build"></a>1.0.6.0 - İç derleme
Yayın tarihi: 12 Eylül 2012

## <a name="1050"></a>1.0.5.0

Yayın tarihi: 10 Eylül 2012

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Betikler veya gölgelendiriciler geçersiz xml karakterine sahip olduğunda proje dosyalarının nesli düzeltildi.

- Unity Varlık sunucusuna bağlandığında Unity örneklerinin algılanması düzeltildi. Bu, Unity'den dosyaları açma hataları ve hata ayıklayıcısının otomatik Visual Studio tetikledi.

## <a name="1040"></a>1.0.4.0

Yayın tarihi: 5 Eylül 2012

### <a name="new-features"></a>Yeni özellikler

- Unity'de hata ayıklama sembollerini otomatik dönüştürme.

    Varlık klasörünüzdeki ilişkili .pdb ile bir .NET .dll derlemeniz varsa, derlemeyi yeniden içeri aktarmanız ve UnityVS'nin .pdb'i Unity'nin betik altyapısının antiği bir hata ayıklama sembolleri dosyasına dönüştürmesi ve UnityVS'den .NET derlemelerinize adım atabilirsiniz.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Unity içindeki yöntemler veya özellikler tarafından oluşan özel durumların neden olduğu hata ayıklama sırasında UnityVS kilitlenmesi düzeltildi.

## <a name="1030"></a>1.0.3.0

Yayın tarihi: 4 Eylül 2012

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
