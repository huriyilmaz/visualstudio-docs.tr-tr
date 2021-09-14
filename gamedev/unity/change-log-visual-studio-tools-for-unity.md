---
title: Değişiklik Günlüğü (Unity için Visual Studio Araçları, Windows) | Microsoft Docs
description: Unity için Visual Studio Araçları, Windows. Sürüm 1.0.0.0 ile 4.7.0.0 ve ötesindeki değişikliklere bakın.
ms.custom: ''
ms.date: 9/7/2021
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: conceptual
ms.assetid: ea490b7e-fc0d-44b1-858a-a725ce20e396
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 522d016e218b19d63cacd746128150b23734aa62
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726018"
---
# <a name="change-log-visual-studio-tools-for-unity-windows"></a>Değişiklik günlüğü (Unity için Visual Studio Araçları, Windows)

Unity için Visual Studio Araçları günlüğü değiştirme.

## <a name="41140"></a>4.11.4.0
Yayın tarihi: 14 Eylül 2021

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Büyük Unity projeleri için varlık dizini oluşturma özelliğini otomatik olarak devre dışı bırakma.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Tanılama ile desteklenen ifade algılama [`UNT0024`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0024.md) düzeltildi.

## <a name="41130"></a>4.11.3.0
Yayın tarihi: 10 Ağustos 2021

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Varlıkları işleme sırasında bellek tüketimi azaltıldı.

  - , ve gizleme [`USP0008`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0008.md) ile [`USP0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0009.md) [`USP0010`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0010.md) [`USP0011`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0011.md) iyileştirilmiş ayırmalar.

  - , , [`UNT0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0002.md) , tanılama [`UNT0003`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0003.md) ile sembol kullanımı [`UNT0012`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0012.md) [`UNT0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0014.md) iyileştirilmiş.

## <a name="41120"></a>4.11.2.0
Yayın tarihi: 13 Temmuz 2021

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Yalnızca CS derleyici uyarılarını işleyabilecek gizlemeler çalıştırarak geliştirilmiş ışık derleme süresi. Diğer tüm çözümleyiciler çözüm analizi aracılığıyla çalışır.

## <a name="41110"></a>4.11.1.0
Yayın tarihi: 15 Haziran 2021

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - YAML varlıklarını ayrıştıran bellek tüketimi azaltıldı.

## <a name="41100"></a>4.11.0.0
Yayın tarihi: 25 Mayıs 2021

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Tanılama [`UNT0025`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0025.md) eklendi. KeyCode bağımsız değişkeniyle Input.GetKey aşırı yüklemelerini tercih edin.

  - Tanılamaya daha fazla geçersiz kullanım (statik ve salt okunur alanlar) [`UNT0013`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0013.md) eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Açık yöntem uygulamaları ve tanılama ile ilgili sorunlar [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0006.md) düzeltildi.

## <a name="41030"></a>4.10.3.0
Yayın tarihi: 8 Haziran 2021

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - [Backported] YAML varlıklarını ayrıştıran bellek tüketimi azaltıldı.

## <a name="41020"></a>4.10.2.0
Yayın tarihi: 25 Mayıs 2021

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Tanılama [`UNT0024`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0024.md) eklendi. Vektör hesaplamaları üzerinden skaler hesaplamalara öncelik verme.

- **Değerlendirme:**

  - Görünür yerelleri düzgün filtrelemek için taşınabilir pdb sembolleri kullanma desteği eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Varlık başvurusu arama kararlılığı düzeltildi.

  - Oynatıcının son Unity sürümleriyle ayrıştırma duyurusu düzeltildi.

## <a name="41010"></a>4.10.1.0
Yayın tarihi: 11 Mayıs 2021

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Quickfix ile ilgili [`UNT0008`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0008.md) kararlılık sorunları düzeltildi.

  - İş parçacıklarıyla ilgili performans sorunları düzeltildi.

## <a name="41000"></a>4.10.0.0
Yayın tarihi: 13 Nisan 2021

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Tanılama [`UNT0019`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0019.md) eklendi. için gereksiz dolaylı `GameObject.gameObject` çağrı.

  - Tanılama [`UNT0020`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0020.md) eklendi. `MenuItem` özniteliği statik olmayan yöntemde kullanılır.

  - Tanılama [`UNT0021`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0021.md) eklendi. Unity iletisi korunmalıdır (kabul).

  - Tanılama [`UNT0022`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0022.md) eklendi. Konum ve döndürmeyi ayarlamak için verimsiz yöntem.

  - Tanılama [`UNT0023`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0023.md) eklendi. Unity nesnelerinde atamayı biriktirma.

  - için [`USP0017`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0017.md) suppressor `IDE0074` eklendi. Unity nesneleri biriktirma ataması kullanmaz.

  - Unity'yi hedef alan, en iyi olmayan C# projelerinin algılanması eklendi.

  - CodeLens'e Unity varlık başvurusu araması eklendi.

## <a name="4910"></a>4.9.1.0
Yayın tarihi: 2 Mart 2021

### <a name="new-features"></a>Yeni Özellikler

- **Değerlendirme:**

  - Kök `Active Scene` oyun nesnelerini gösteren yerellere eklendi.

  - `this.gameObject`Unity projelerinde yaygın olarak kullanılan yerellere eklendi.

  - Tüm `Children` nesne `Components` hiyerarşisini kolayca `GameObject` görüntüleyebiliyor olmak için tüm örneklere ve grupları eklendi.

  - Sahnenin `Scene Path` konumunu göstermek için tüm `GameObject` örneklere eklenir.

  - Kaynak oluşturucularla `JobEntityBatch` Varlıklar kullanılırken /Lambdas desteği eklendi.

  - Büyük dizileri görüntüleme desteği iyileştirildi (dizin demetleme kullanılarak).
  
  - 2019.4 API için eksik Unity iletileri eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - ENU dışı diller için çeşitli kullanıcı arabirimi sorunları düzeltildi.

  - Tanılama ile ilgili kararlılık sorunları [`UNT0018`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0018.md) düzeltildi.
  
- **Hata ayıklama:**

  - Yöntemler kullanırken karşılaşılan VM bağlantısı kesilmesi `Trace` sorunları düzeltildi.

- **Değerlendirme:**

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
  
  - için [`USP0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0009.md) suppressor `IDE0051` eklendi. Özniteliği olan veya özniteliği kullanılmayan bir alan tarafından `ContextMenu` başvurulan yöntemlere `ContextMenuItem` bayrak asma.

  - için [`USP0010`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0010.md) suppressor `IDE0051` eklendi. özniteliğine sahip alanlara kullanılmayan `ContextMenuItem` bayrağını attırma.
  
  - için [`USP0011`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0011.md) suppressor `IDE0044` eklendi. Salt okunur özniteliğine `ContextMenuItem` sahip alanlar yapma.
  
  - [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0004.md), [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) ve artık hem hem de öznitelikleri için [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) `SerializeReference` `SerializeField` çalışıyor.
  
### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Unity'ye yalnızca Düzenleyici iletişim kurayken başlatma/durdurma komutları gönderin.
  
  - Devralınan iletilere sahip QuickInfo belgeleri düzeltildi.
  
  - İletinin ileti kapsamı `CreateInspectorGUI` düzeltildi.

  - Çok [`UNT0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0001.md) biçimli değiştiriciler ile yöntemleri bildirme.

- **Değerlendirme:**

  - Diğer ad kullananların işlenmesi düzeltildi.

## <a name="4510"></a>4.5.1.0

Yayın tarihi: 16 Mart 2020

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - için [`USP0008`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0008.md) suppressor `IDE0051` eklendi. Invoke, InvokeRepeating, StartCoroutine veya StopCoroutine ile kullanılan özel yöntemler kullanılmamış olarak işaretlanmaz.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - OnDrawGizmos/OnDrawGizmosSelected belgeleri düzeltildi.

- **Değerlendirme:**

  - Lambda bağımsız değişken denetimi düzeltildi.

## <a name="4501"></a>4.5.0.1

Yayın tarihi: 19 Şubat 2020

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Hatalı [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0006.md) ileti imzası için tanılama denetimi düzeltildi. Birden çok devralma düzeyine sahip türleri incelerken, bu tanılama şu iletiyle başarısız olabilir: `warning AD0001: Analyzer 'Microsoft.Unity.Analyzers.MessageSignatureAnalyzer' threw an exception of type 'System.ArgumentException' with message 'An item with the same key has already been added` .

## <a name="4500"></a>4.5.0.0

Yayın tarihi: 22 Ocak 2020

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - HLSL dosyaları için destek eklendi.
  
  - için [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) suppressor `IDE0051` eklendi. özniteliğine sahip `SerializeField` özel alanlar kullanılmamış olarak işaretlendi değil.
  
  - için [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) suppressor `CS0649` eklendi. özniteliğine `SerializeField` sahip alanlar atanmamış olarak işaretlendi değil.  

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Proje oluşturma düzeltildi ( `GenerateTargetFrameworkMonikerAttribute` hedef her zaman doğru şekilde yer alammıştı).

## <a name="4420"></a>4.4.2.0

Yayın tarihi: 3 Aralık 2019

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Kullanıcı tanımlı arabirimlerle tanılama düzeltildi.

  - Hatalı biçimlendirilmiş ifadelerle hızlı araç ipucu düzeltildi.

## <a name="4410"></a>4.4.1.0

Yayın tarihi: 6 Kasım 2019

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Unity arka plan işlemleri için destek eklendi. (Hata ayıklayıcı, alt işlem yerine ana işleme otomatik olarak bağlanabilecektir).
  
  - Unity iletileri için ilişkili belgeleri görüntüleyen hızlı bir araç ipucu eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Gelişmiş ikili ve çağırma [`UNT0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0002.md) ifadeleriyle etiket karşılaştırma çözümleyicisi düzeltildi.

### <a name="deprecated-features"></a>Kullanım Dışı Özellikler

- **Entegrasyon:**

  - Daha sonra Unity için Visual Studio Araçları 2017+ Visual Studio destekleye devam edeceğiz.

## <a name="4400"></a>4.4.0.0

Yayın tarihi: 15 Ekim 2019

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Tüm [`USP0005`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0005.md) Unity iletileri için `IDE0060` (kullanılmayan parametre) suppressor eklendi.
  
  - ile etiketlenmiş alanlar için hızlı bir araç ipucu `TooltipAttribute` eklendi. (Bu, bu alanı kullanan basit bir get erişimcisi için de çalışır).

## <a name="4330"></a>4.3.3.0

Yayın tarihi: 23 Eylül 2019

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Basit derlemeler için hata ve uyarı raporlama düzeltildi.

## <a name="4320"></a>4.3.2.0

Yayın tarihi: 16 Eylül 2019

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Unity'ye özgü yeni tanılamalar ekleyerek Unity Visual Studio için sahip olduğu bilgileri daha derinden ifade ettik. Unity projeleri için geçerli olmayan genel C# tanılamalarını gizleyerek IDE’yi daha akıllı hale getirdik. Örneğin, IDE bir denetçi değişkenlerini değiştirmek için bir hızlı düzeltme göstermez ve bu da Unity Düzenleyicisi'nde değişkeni `readonly` değiştirmenizi önler.
    - [`UNT0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0001.md): Unity iletileri boş olsalar bile çalışma zamanı tarafından çağrılır, Unity çalışma zamanı tarafından gereksiz işlemeyi önlemek için bunları bildirin.
    - [`UNT0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0002.md): Dize eşitliği kullanarak etiket karşılaştırması, yerleşik CompareTag yönteminden daha yavaştır.
    - [`UNT0003`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0003.md): Tür güvenliği için GetComponent genel formunun kullanımı tercih edilir.
    - [`UNT0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0004.md): Güncelleştirme iletisi kare hızına bağlıdır ve Time.fixedDeltaTime yerine Time.deltaTime kullan gerekir.
    - [`UNT0005`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0005.md): FixedUpdate iletisi kare oranından bağımsızdır ve Time.deltaTime yerine Time.fixedDeltaTime kullandır.
    - [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0006.md): Bu Unity iletisi için yanlış bir yöntem imzası algılandı.
    - [`UNT0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0007.md): Unity, Unity nesneleri için null karşılaştırma işlecinin null birliğine dönüştürmeyle uyumsuz olduğunu geçersiz kılar.
    - [`UNT0008`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0008.md): Unity, Unity nesneleri için null yayma ile uyumsuz olan null karşılaştırma işlecini geçersiz kılar.
    - [`UNT0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0009.md): InitializeOnLoad özniteliğini bir sınıfa uygularken statik bir oluşturucu sağlamanız gerekir. InitializeOnLoad özniteliği, düzenleyici başlatıldığında bunun çağrılmasını sağlar.
    - [`UNT0010`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0010.md): MonoBehaviours yalnızca AddComponent() kullanılarak oluşturulacak. MonoBehaviour bir bileşendir ve bunun GameObject’e eklenmesi gerekir.
    - [`UNT0011`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0011.md): ScriptableObject yalnızca CreateInstance() kullanılarak oluşturul olmalıdır. Unity ileti yöntemlerinin işlenmesi için ScriptableObject’in Unity altyapısı tarafından oluşturulması gerekir.
    - [`USP0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0001.md) için: `IDE0029` Unity nesneleri null birliğine dönüştürme kullanmamalı.
    - [`USP0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0002.md) için: `IDE0031` Unity nesneleri null yayma kullanmaz.
    - [`USP0003`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0003.md) için: `IDE0051` Unity iletileri Unity çalışma zamanı tarafından çağrılır.
    - [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0004.md) for: `IDE0044` SerializeField özniteliğine sahip alanlar salt okunur hale getirilene sahip değildir.

## <a name="4310"></a>4.3.1.0

Yayın tarihi: 4 Eylül 2019

### <a name="new-features"></a>Yeni Özellikler

- **Değerlendirme:**

  - Daha iyi tür görüntüleme için destek eklendi, örneğin `List<object>` yerine `List'1[[System.Object, <corlib...>]]` .

  - İşaretçi üyesi erişimi için destek eklendi, örneğin `p->data->member` .

  - Dizi başlatıcılarında örtülü dönüştürme desteği eklendi, örneğin `new byte [] {1,2,3,4}` : .

## <a name="4300"></a>4.3.0.0

Yayın tarihi: 13 Ağustos 2019

### <a name="new-features"></a>Yeni Özellikler

- **Hata ayıklayıcı:**

  - 2.51 AVH için destek eklendi.

- **Entegrasyon:**

  - Sıralama, arama ve yenileme özellikleriyle "Unity örneğine ekle" penceresi geliştirildi. PiD artık yerel oyuncular için bile görüntülenir (sahip olan işlemi almak için sistemde dinleme yuvaları sorgular).

  - Asmdef dosyaları için destek eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Unity Players ile iletişim kurarken hatalı biçimlendirilmiş iletilerin işlenmesi düzeltildi.

- **Değerlendirme:**

  - İfadelerde ad alanlarının işlenmesi düzeltildi.

  - IntPtr türleriyle denetim düzeltildi.
  
  - Özel durumlarla ilgili adımlama sorunları düzeltildi.

  - Sahte tanımlayıcıların (örneğin, $exception).

  - Geçersiz adresler iptal edilirken kilitlenmeyi önle.  

  - Kaldırılan appdomains ile ilgili sorun düzeltildi.

## <a name="4201"></a>4.2.0.1

Yayın tarihi: 24 Temmuz 2019

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Unity Veri Gezgini'nde herhangi bir türde dosya oluşturmak için yeni Project eklendi.
  
  - Unity projeleri için hızlı derlemeler kullanırken tanılama önbelleğini geliştirin.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Dosya uzantısının bilinen herhangi bir düzenleyici tarafından işnmediği bir sorun düzeltildi.

  - Unity Project Explorer'da özel uzantı desteği düzeltildi.

  - Ayarları ana iletişim kutusunun dışına kaydetme düzeltildi.

  - Eski Microsoft.VisualStudio.MPF bağımlılığı kaldırıldı.

## <a name="4110"></a>4.1.1.0

Yayın tarihi: 24 Mayıs 2019

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - MonoBehaviour API'si 2019.1'e güncelleştirildi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Basit derleme etkinleştirildiğinde çıkış için raporlama uyarıları ve hataları düzeltildi.

  - Basit derleme performansı düzeltildi.

## <a name="4100"></a>4.1.0.0

Yayın tarihi: 21 Mayıs 2019

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Projeleri daha hızlı yeniden yüklemek için yeni batch API'si desteği eklendi.

  - IntelliSense hataları ve uyarılarını kullanmak yerine Unity projeleri için tam derleme devre dışı bırakıldı. Aslında Unity, Unity Visual Studio yaptığı işi temsil eden sınıf kitaplığı projeleriyle birlikte bir çözüm oluşturur. Bununla birlikte derleme işlem hattı kapatılan Visual Studio unity tarafından hiçbir zaman kullanılmaz veya toplanmayacak. Bu Visual Studio yalnızca kaynakları hiçbir şey için tüketmektir. Tam derlemeye ihtiyacınız varsa, buna bağlı araçlar veya bir kurulum varsa, bu iyileştirmeyi devre dışı abilirsiniz (Unity için Araçlar/Seçenekler/Araçlar/Projelerin tam derlemesini devre dışı bırak).

  - Unity projesi yüklendiğinde Unity Project Gezgini'ni (UPE) otomatik olarak göster. UPE, yüklemenin yanına Çözüm Gezgini.

  - Unity 2019.x ile proje adı ayıklama mekanizması güncelleştirildi.

  - UPE'de Unity paketleri için destek eklendi. Yalnızca Başvurulan paketler (klasöründe manifest.json kullanılarak) ve `Packages` Yerel paketler (klasöre `Packages` eklenmiş) görünür.

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

  - Kayıt sırasında Unity 'nin varlık veritabanının otomatik olarak yenilenmesi için destek eklendi. Bu varsayılan olarak etkindir ve Visual Studio bir betiği kaydederken Unity tarafında yeniden derleme tetikleyecektir. Kayıt sırasında Unity 'nin Assetveritabanını yenilemek için Tools\Options\Tools içinde bu özelliği devre dışı bırakabilirsiniz.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - tercih edilen harici düzenleyici olarak Visual Studio seçilmediğinde, sabit köprü etkinleştirme.

  - Hatalı biçimlendirilmiş veya desteklenmeyen ifadelerle ifade değerlendirmesi düzeltildi.

## <a name="4000"></a>4.0.0.0

Yayın tarihi 4 Aralık 2018

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - Visual Studio 2019 için destek eklendi (Visual Studio 2019 bir dış betik düzenleyicisi olarak kullanabilmeniz için en az Unity 2018,3 gerekir).

  - Visual Studio ımage hizmeti ve kataloğunu, hdpı ölçeklendirme, piksel kusursuz görüntüler ve tema için tam destek ile benimsemiştir.

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

- **Misc:**

  - Unity'nin yükleme veya kaldırma sırasında çalışmaması için denetim eklendi.

  - Uzak Unity belgelerini hedeflemek için https'ye geçiş yaptı.

## <a name="2800---30-preview"></a>2.8.0.0 - 3.0 Önizleme
Yayın tarihi: 17 Kasım 2016

### <a name="new-features"></a>Yeni Özellikler

- **Genel:**

  - 2017 Visual Studio desteği eklendi.

  - 2017 Visual Studio desteği eklendi.

  - Yerelleştirme desteği eklendi.

- **Kod Düzenleyicisi:**

  - Unity iletileri için C# IntelliSense eklendi.

  - Unity iletileri için C# kod renklendirmesi eklendi.

- **Hata ayıklayıcı:**

  - , `is` , doğrudan `as` döküm, , `default` ifadeleri için destek `new` eklendi.

  - Dize concat ifadeleri için destek eklendi.

  - Tamsayı değerlerinin onaltılık görüntüsü için destek eklendi.

  - Yeni geçici değişkenler (deyimler) oluşturma desteği eklendi.

  - Örtülü temel dönüştürmeler için destek eklendi.

  - Bir tür bekleniyorsa veya bulunamasa daha iyi hata iletileri eklendi.

- **Project Nesil:**

  - Proje adlarından CSharp soneki kaldırıldı.

  - Sistem genelinde msbuild hedefler dosyasına başvuru kaldırıldı.

- **Sihirbaz:**

  - Düzenleyici veya EditorWindow gibi Davranış dışı türlerde Unity iletileri için destek eklendi.

  - Unity iletilerini ekleme ve biçimlendirmek için Roslyn'e geçiş yaptı.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Hata ayıklayıcı:**

  - Genel türleri değerlendirirken Unity'nin kilitlenmesi hatası düzeltildi.

  - Null değere değiştirilebilir türlerin işlenmesi düzeltildi.

  - Sabit sabit sabitlerinin işlenmesi düzeltildi.

  - İç içe üye türlerinin işlenmesi düzeltildi.

  - Koleksiyon dizin oluşturma erişimi düzeltildi.

  - Yeni C# derleyicisi ile iterator çerçevelerinde hata ayıklama desteği düzeltildi.

- **Project Nesil:**

  - Unity Web oynatıcısını hedeflerken derlemeyi engelleyen hata düzeltildi.

  - Web kodlanmış dosya adıyla betik derlerken derlemeyi engelleyen hata düzeltildi.

## <a name="2300"></a>2.3.0.0

Yayın tarihi: 14 Temmuz 2016

### <a name="new-features"></a>Yeni Özellikler

- **Genel:**

  - Konsolunuzun hata listesinde Unity konsol günlüklerini devre Visual Studio için bir seçenek eklendi.

  - Oluşturulan proje özelliklerinin değiştirilmesine izin vermek için bir seçenek eklendi.

- **Hata ayıklayıcı:**

  - Metin, XML, HTML ve JSON dize görselleştiricileri eklendi.

- **Sihirbaz:**

  - Eksik MonoBehaviors eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Genel:**

  - ReSharper ile ilgili bir çakışma düzeltildi ve bu da Visual Studio denetimlerin görüntülenebilir.

  - Xamarin ile bazı durumlarda hata ayıklamayı engelleyen bir çakışma düzeltildi.

- **Hata ayıklayıcı:**

  - Hata ayıklama sırasında uygulamanın Visual Studio oluşan bir sorun düzeltildi.

  - Visual Studio 2015'te işlev kesme noktalarıyla ilgili bir sorun düzeltildi.

  - Çeşitli ifade değerlendirme sorunları düzeltildi.

## <a name="2200"></a>2.2.0.0

Yayın tarihi: 4 Şubat 2016

### <a name="new-features"></a>Yeni Özellikler

- **Sihirbaz:**

  - **MonoBehavior Uygulama sihirbazına akıllı arama** eklendi.

  - Sihirbazlar bağlamını fark etme; Örneğin, NetworkBehavior iletileri yalnızca bir NetworkBehavior ile çalışırken kullanılabilir.

  - Sihirbazlarda NetworkBehavior iletileri için destek eklendi.

- **UI:**

  - MonoBehavior iletilerinin görünürlüğünü yapılandırma seçeneği eklendi.

  - Unity Visual Studio ilgili bir özellik sayfası kaldırıldı.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Project oluşturma:**

  - Unity 4.6 üzerinde UnityEngine ve UnityEditor başvuruları düzeltildi.

  - Unity OSX üzerinde çalışıyorken proje dosyalarının nesli düzeltildi.

  - Karma işareti (#) karakterleri içeren proje adlarının işlenmesi düzeltildi.

  - Oluşturulan projeleri C# 4 ile kısıtla.

- **Hata ayıklayıcı:**

  - Unity coroutine içinde hata ayıklarken ifade değerlendirmesiyle ilgili bir sorun düzeltildi.

  - Hata ayıklama sırasında uygulamanın Visual Studio oluşan bir sorun düzeltildi.

- **UI:**

  - Tabs Studio uygulama uzantısıyla [uyumsuzluk](https://tabsstudio.com/) Visual Studio düzeltildi.

- **Yükleyici:**

  - HKLM kayıt defteri girdileri oluşturarak VSTU'nun makine genelinde yüklenmesine (tüm kullanıcılar için yükleme) destek sağlar.

  - VsTU'nun birden çok farklı sürümü için aynı VSTU sürümü yüklü olduğunda VSTU'nun kaldırılmasıyla ilgili sorunlar Visual Studio. Örneğin, VSTU **2015** 2.1.0.0 ve VSTU **2013** 2.1.0.0 her ikisi de yüklü olduğunda.

## <a name="2100"></a>2.1.0.0

Yayın tarihi: 8 Eylül 2015

### <a name="new-features"></a>Yeni Özellikler

- Unity 5.2 desteği

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Unity < 4.2'de menü öğelerini görüntüleme

- XML IntelliSense dosyalarını kilitleyen Visual Studio bir hata iletisi görüntülenmez.

- Koşullu <> bir boole değeri değilken koşullu \<When Changed> kesme noktalarına göre işle.

- Windows Store uygulamaları için UnityEngine ve UnityEditor derlemelerine başvurular düzeltildi.

- Hata ayıklayıcıda adımlarken hata düzeltildi: Adımlama, genel özel durum.

- 2015'te isabet Visual Studio noktaları düzeltildi.

## <a name="2000"></a>2.0.0.0

Yayın tarihi: 20 Temmuz 2015

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Unity Tümleştirmesi:**

  - Dll ve hata ayıklama sembolleri (PDB) içeri aktarılırken Visual Studio 2015 ile oluşturulan hata ayıklama sembollerinin dönüştürmesi düzeltildi.

  - Bir MDB dosyası da sağlanıyorsa dışında, dll ve hata ayıklama sembolleri (PDB) içeri aktarılırken her zaman MDB dosyaları oluşturun.

  - Unity proje dizininin obj diziniyle kirliliği düzeltildi.

  - System.Xml'a başvuru System.Xml. Bağlantı ve System.Runtime.Serialization.

  - Proje dosyası oluşturma API'si kancalarına birden çok abone için destek eklendi.

  - Oluşturullanacak dosyalardan biri kilitli olsa bile proje dosyası oluşturma işlemini her zaman tamamlar.

  - C# projesine dahil edilecek dosyaları belirtirken uzantı filtresinde * joker karakterleri için destek eklendi.

- **Visual Studio tümleştirme:**

  - Productivity Power Tools ile ilgili bir uyumluluk sorunu düzeltildi.

  - Olaylar ve temsilci bildirimleri etrafında MonoBehaviors oluşturma düzeltildi.

- **Hata ayıklayıcı:**

  - Hata ayıklama sırasında olası bir donma düzeltildi.

  - Yerellerin belirli yığın çerçevelerinde görüntülenmeyen bir sorun düzeltildi.

  - Boş dizilerin denetlenmesi düzeltildi.

## <a name="1990---20-preview-2"></a>1.9.9.0 - 2.0 Önizleme 2
Yayın tarihi: 2 Nisan 2015

### <a name="new-features"></a>Yeni özellikler

- **Unity Project Explorer:**

  - Unity Project Gezgini'nde bir dosyayı yeniden adlandırırken sınıfı otomatik olarak yeniden adlandırın (Bkz. **Seçenekler iletişim** kutusu).

  - Unity Project Explorer'da yeni oluşturulan betikleri otomatik olarak seçin.

  - Unity Project Explorer'da etkin betiği izleme (Seçenekler iletişim **kutusuna** bakın).

  - Dosya çift eşitlemesi Visual Studio Çözüm Gezgini (Seçenekler iletişim **kutusuna** bakın).

  - Unity Visual Studio Explorer'da Project kullanın.

- **Hata ayıklayıcı:**

  - Kayıtlı veya son kullanılan hata ayıklama hedefleri listesinden etkin hata ayıklama hedefini seçin (Bkz. **Seçenekler iletişim** kutusu).

  - MonoBehavior yöntemlerinde işlev kesme noktaları oluşturun ve bunları birden çok MonoBehavior sınıfına uygulama.

  - Hata ayıklayıcıda Nesne Kimliği Oluşturma desteği.

  - Hata ayıklayıcıda kesme noktası isabet sayısı desteği.

  - Hata ayıklayıcıda kesme özel durumu desteği (Deneysel. Bkz. **Seçenekler** İletişim Kutusu).

  - Hata ayıklayıcısında ifadeleri değerlendirirken nesnelerin ve dizilerin oluşturulmasını destekler.

  - Hata ayıklayıcıda değerlendirme ifadeleri olduğunda null karşılaştırmayı destekler.

  - Hata ayıklayıcı izleme pencerelerde eski üyeleri filtrele.

- **Yükleyici:**

  - Uzantı Unity için Visual Studio Araçları için iyileştirilmiş.

  - Unity 5 Unity için Visual Studio Araçları bir paket yükleyin.

- **Belgeler:** Belge oluşturma performansını geliştirme.

- **Sihirbazlar:** Unity 4.6 ve Unity 5 için yeni MonoBehavior yöntemlerini destekler.

- **Unity:** Proje dosyası oluşturma sırasında .rsp dosyalarında güvenli olmayan bayrakları ve özel değerleri arama.

- **Kullanıcı arabirimi:** Yeni Unity için Visual Studio Araçları **Seçenekler** iletişim kutusu Visual Studio.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Unity Project Explorer:**

  - Dosyalar taşındıktan veya Project yeniden adlandırıldıktan sonra Unity Visual Studio Çözüm Gezgini.

  - Unity Veri Gezgini'nde dosyaları yeniden Project.

  - Unity Veri Gezgini'nde dosyalara çift tıklarsanız otomatik genişletmeyi Project engelleyin.

  - Yeni seçilen dosyaların Unity Project Explorer'da görünür olduğundan emin olun.

- **Hata ayıklayıcı:**

  - Hata ayıklayıcısında Visual Studio değerlendirirken olası bir hatanın donmasını önle.

  - Yöntem çağrılarının hata ayıklayıcıda uygun etki alanında olduğundan emin olun.

- **Birlik:**

  - Unity 5 ile UnityVS.OpenFile konumunu düzeltin.

  - Unity 5 ile pdb2mdb konumunu düzeltin.

  - Proje dosyası oluşturma sırasında olası bir özel durumu önle.

  - Unity'i OSX üzerinde çalıştırmanın olası donmalarını önle.

  - İç özel durumları işleme.

  - Unity konsol günlüklerini VS hata listesine gönderin.

- **Belgeler:** Yeni Unity belgeleri için belge oluşturma doğru.

- **Project:** Unity .meta dosyalarını gerektiğinde klasörlerde bile taşıma ve yeniden adlandırma.

- **Sihirbazlar:** Kod oluşturmada MonoBehavior yöntem parametrelerinin sırası düzeltildi.

- **Kullanıcı arabirimi:** Bağlam Visual Studio simgeler için temaları destekleme.

## <a name="1980---20-preview"></a>1.9.8.0 - 2.0 Önizleme
Yayın tarihi: 12 Kasım 2014

### <a name="new-features"></a>Yeni özellikler

- 2015 Visual Studio desteği.

- Visual Studio 2015'te Unity gölgelendiricileri için Kod Renklendirmesi.

- Hata ayıklama sırasında değerlerin görselleştirmesi geliştirildi:

  - ArrayLists, Listeler, Karma Tablosu ve Sözlükler için daha iyi görselleştirme.

  - Genel Olmayan üyeleri ve Statik üyeleri izleme ve yerel görünümlerde kategoriler olarak göster.

  - Yalnızca özelliği için geçerli olan değer alanını değerlendirmek için Unity SerializedProperty'nin görüntüsü iyileştirildi.

  - Sınıflar ve yapılar için DebuggerDisplayAttribute desteği.

  - DebuggerTypeProxyAttribute desteği.

- Kullanıcı kodlama kurallarına uygun olarak sihirbazlarımızı kullanarak MonoBehaviour yöntemlerinin eklemesini yapma.

- UnityVS tarafından oluşturulan projelerde Derleme Zamanı Metin Şablonları için destek uygulama.

- UnityVS tarafından oluşturulan projelerde ResX kaynakları için destek uygulama.

- Unity'den Visual Studio açma desteği.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Attach ve Play sonrasında Unity'de oyun başlamadan önce yuvaları temizleme işlemi Visual Studio. Bu, Attach ve Play kullanırken Unity ile VS arasındaki bağlantının kararlılığıyla ilgili bazı sorunları düzeltir.

- Unity'nin betik altyapısı hata ayıklayıcısı arabiriminde Unity'nin donmasına neden olan yöntemleri çağırmayın. Bu, hata ayıklayıcıyı iliştirme sırasında Unity donmasını düzeltir.

- Sembol kullanılabilir durumda değilken çağrı yığınlarının görüntülenmesi sorunu giderildi.

- Gerekirse günlük geri aramasını kaydetmeyin.

## <a name="1920"></a>1.9.2.0

Yayın tarihi: 9 Ekim 2014

### <a name="new-features"></a>Yeni özellikler

- Unity oyuncularını algılamayı geliştirin.

- Dosya açıcımızı kullanırken Unity'nin hem satır numarasını hem de dosya adını iletir.

- Yerel belge yoksa varsayılan olarak çevrimiçi Unity belgeleri kullanılır.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Etki alanı yeniden yüklendikten sonra bir kesme noktasıyla ilgili olası Unity kilitlenmesi giderildi.

- Etki alanı yeniden yüklendikten sonra Yapılandırma veya Hakkında pencerelerimizi kapatırken Unity konsolunda gösterilen özel durumlar düzeltildi.

- Yerel olarak çalışan Unity 64bit algılaması düzeltildi.

- Sihirbazlarda Unity sürümü başına MonoBehaviours filtrelemesi düzeltildi.

- Uzantı filtresi boşsa proje dosyalarına tüm varlıkların dahil olduğu hata giderildi.

## <a name="1910"></a>1.9.1.0

Yayın tarihi: 22 Eylül 2014

### <a name="new-features"></a>Yeni özellikler

- Kaynak konumlara bağlama kesme noktası iyileştirme.

- Hata ayıklayıcının İfade Değerlendirmesi'ne aşırı yüklenmiş yöntemler için destek.

- Hata ayıklayıcının İfade Değerlendirmesi'ne ilkelleri ve değer türlerini kutulama desteği.

- Anonim yöntemlerde hata ayıklarken C# yerel değişkenleri ortamını yeniden oluşturma desteği.

- Dosya silme veya yeniden adlandırma işlemi gerçekleştirerek .meta dosyalarını silin ve yeniden Visual Studio.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Temaların işlenmesi Visual Studio düzeltildi. Daha önce, siyah temalarda iletişim kutuları boş görünebilirdi.

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

- , Düzenleyicilerin uzaktan keşfi için Mavericks adresindeki Ağ katmanında bir sorunu geçici olarak çözmek.

- Uzak Unity oynatıcılarını keşfetmeye yönelik yeni bağlantı noktalarını işleyin.

- Geçerli derleme hedefine özel UnityEngine derlemesine başvur.

- Oluşturulan projelere dahil edilecek dosyaları filtrelemek için ayar ekleyin.

- konsol günlüklerinin Visual Studio hata listesine gönderilmesini devre dışı bırakmak için ayar ekleyin. konsol günlüklerini almak için Unity 'de kayıtlı yalnızca bir geri çağırma olduğundan, playmaker veya konsol Pro kullanıyorsanız bu kullanışlıdır.

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

- System.Xml bir başvuru ekleyin. Unity > 4,1 için projelere LINQ.

- İletiye StackTrace 'in başlangıcını dahil etmek için hata ayıklama. log çağrılarımızın önmizi yapın.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Visual Studio içindeki JavaScript dosyalarının varsayılan işlemesini etkileyebilecek bir hata düzeltildi.

- Bu kez, gerçek zamanlı olarak VS. olarak görünen beyaz bir piksel düzeltildi.

- Bir SCM tarafından ReadOnly olarak işaretlenmişse UnityVS. VersionSpecific derlemesini silme işlemi düzeltildi.

- UnityVS paketinde yuva oluşturulurken oluşan özel durumlar düzeltildi.

- Visual Studio derlemelerinden hisse senedi görüntüleri yüklenirken Visual Studio çökme düzeltildi.

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

- Project dosya üreticisi artık T4 şablonlarını işler.

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

- Visual Studio başlatılmışsa ve silinen bir dosyanın başlangıçta açılacak dosya listesinde olması durumunda oluşabilecek bir hata düzeltildi.

- Derlenmiş gölgelendiriciler gibi betik olmayan dosyaları işlemek için fixed UnityVS. OpenFile.

- Şimdi tüm C# projelerinden Boo. lang ve UnityScript. lang başvurduk.

- Projede özel karakterler varsa, projelerdeki başvuruların sabit üretimi.

- Geçici çözüm, yöntemin atılmış projelere çağrı yaptığı bir VS sorunu, birden çok NullReferenceException MessageBox tetikleyecektir.

- Unity 4,2 Beta derlemelerinin sabit işlenmesi.

## <a name="1210"></a>1.2.1.0

Yayımlanma tarihi, 9 Nisan 2013

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Bir g/ç hatası (salt okuma dosyaları veya Visual Studio tarafından kilitlenen dosyalar gibi) durumunda kod tamamlama için Unity derlemelerinin sabit yerel dağıtımı.

- Unity 'den bir betik açan bir gerileme, Visual Studio zaten açıldıysa dosyayı odaklanmaz.

- Yeni özel durum işlemenin sabit performans sorunu.

- Bazı dış dll 'lerde kesme noktalarının sabit bağlaması.

## <a name="1200"></a>1.2.0.0

Yayımlanma tarihi, 25 Mart 2013

### <a name="new-features"></a>Yeni özellikler

- Büyük ölçüde geliştirilmiş hata ayıklayıcı bağlantı hızı.

- daha büyük projeler için iyileştirilmiş Unity Project Explorer.

- işlenmiş ve işlenmemiş özel durumları kesmek (veya not) için Visual Studio ayarlarını dikkate alır.

- yerel değişkenlerde ToString çağrısı yapmak için Visual Studio ayarını dikkate alır.

- Yeni menü hata ayıklama-> Unity oynatıcısında hata ayıklamak için kullanabileceğiniz Unity hata ayıklayıcısı ekleyin.

- Çözüm dosyası oluşturma sırasında UnityVS çözümüne eklenen özel projeleri koruma.

- Yeni klavye kısayolu Ekle CTRL + ALT + M->, CTRL + H tuşlarına basarak Unity işlevine veya üyesine yönelik Unity belgelerini giriş işareti konumunda görüntüleyin.

- Visual Studio derlenirken derleyici yanıt dosyalarını (rsp) hesaba alın.

- Oluşturucu metotlarında hata ayıklama sırasında değişkenleri göstermek için derleyicinin ürettiği türler kaldırılıyor.

- Paylaşılan bir klasörü Unity 'ye yapılandırma gereksinimini kaldırarak uzaktan hata ayıklamayı kolaylaştırın. Artık Windows Unity projenize erişiminizin olması yeterlidir.

- Özel bir Unity profilini standart .NET hedef profili olarak yükler. Bu, ReSharper tarafından gösterebilecek tüm hatalı pozitif durumları düzeltir.

- Bir Unity betik altyapısı hatasına geçici olarak çalışın, bu nedenle hata ayıklayıcı düzgün şekilde kaydedilmemiş iş parçacıklarında kesintiye uğramaz.

- Dosya açma isteği üzerinde kilitlenme sırasında dosyaları açmak için gereken yerde bir yarış durumu oluşmasını önlemek için dosyayı Opener 'da yeniden çalışın.

- UnityVS, artık projeyi oluştururken ve artık dosya Kaydet 'de değil derlemeyi yenilemeyi istiyor.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Özel .NET profiliniz düzeltildi

- Tema tümleştirmesi düzeltildi, bu, VS 2012 koyu temasıyla ilgili sorunlarımızı düzeltir.

- VS 2012 ' de sabit hızlı davranış kısayolu.

- Hata ayıklama ve ana olmayan iş parçacığı bir kesme noktasına isabet edildiğinde oluşabilecek bir Adımlama sorunu düzeltildi.

- İnt gibi tür diğer adların sabit Unityscrıpt ve Boo 'un tamamlanması.

- Yeni bir UnityScript veya Boo dizesi yazılırken düzeltilen özel durum.

- Bir çözüm yüklenmediği zaman Unity menülerindeki özel durumlar düzeltildi.

- Düzeltilen hata UVS-48: çift tırnak yazıldığında bazen hata oluşur ve tüm işlev kesilir (kod tamamlama, sözdizimi vurgusu vb.).

- Düzeltilen hata UVS-46: Visual Studio Hata Listesi tıklandığında yinelenen açık betik dosyası (UnityScript).

- Düzeltilen hata UVS-42: durum çubuğundaki Unity bağlantı logosu, VS 2012 ' de fare olaylarını işlemez.

- Sabit hata UVS-44: CTRL + SHIFT + Q, VS 2012 ' de hızlı MonoBehaviours için kullanılamaz.

- düzeltilen hata uvs-40: Unity Project gezgini 'ndeki seçili öğeler, pencere etkin olmadığında VS2012 "koyu" temada okunamaz.

- Düzeltilen hata UVS-39: atlanan dizeleri simgeleştirirken sorun.

- Düzeltilen hata UVS-35: değişkenleri incelerken nesnelerde ToString çağrısı yapın.

- Düzeltilen hata UVS-27: VS2012 içinde "koyu" temayla sembol penceresine git.

- Sabit hata UVS-11: eş öğelerdeki Yereller.

## <a name="1100---beta-release"></a>1.1.0.0-Beta sürümü
Çıkarılan, 9, 2013

## <a name="10130"></a>1.0.13.0
Yayımlanma tarihi 21 Ocak 2013

### <a name="bug-fixes"></a>Hata düzeltmeleri

- hedef hata ayıklanan geçersiz iş parçacığı olayları göndermesi durumunda oluşabilecek Visual Studio bir kilitleniyor düzeltildi. Bu, genellikle OSX üzerinde Uzak Unity hata ayıklaması yapılırken meydana gelir.

- bir özel durum hata ayıklayıcıyı kapdığı takdirde oluşabilecek Visual Studio bir kilitleniyor düzeltildi.

- C# MonoBehavior bir ad alanında olduğunda MonoBehavior yardımcılarımız düzeltildi.

- Visual Studio 2012 ' de unityscrıpt için düzeltilen hata ayıklayıcı araç ipuçları.

- Unity 'den yalnızca hata ayıklama sabitleri değiştirildiğinde düzeltilen proje oluşturma.

- Unity Project gezgininde sabit klavye gezintisi.

- Atlanan dizeler için kod renklendirme düzeltildi.

- Unity dışında kullanıldığında proje adını daha iyi tahmin etmek için dosya Openme düzeltildi. Bu, Kullanıcı Unity 'de UnityVS 'ye temsilci olarak üçüncü bir bölüm dosyası kullandığında gereklidir.

- Unity 'den UnityVS 'e gönderilen uzun mesajların sabit işlenmesi. Bundan önce, uzun iletiler ileti alımızın bir parçası olan mesajlaşma bölümünü çökebilir. Sonuç olarak, bazen Unity 'den bir dosya açılmaz.

## <a name="10120"></a>1.0.12.0
Yayımlanma tarihi 3 Ocak 2013

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Visual Studio bir kesme noktası silinirken oluşabilecek Visual Studio düzeltildi.

- Unity 'nin oyun betiklerini yeniden derlendikten sonra bazı kesme noktaları isabet ettirilmeyen bir hata düzeltildi.

- kesme noktaları ilişkisiz olduğunda Visual Studio düzgün şekilde bilgilendirmek için hata ayıklayıcı düzeltildi.

- Visual Studio hata ayıklayıcının yerel programlarda hata ayıklamasına engel olabilecek bir kayıt sorunu düzeltildi.

- UnityScript ve Boo ifadeleri değerlendirilirken oluşabilecek bir özel durum düzeltildi.

- Unity 'de .NET API düzeyinin değiştirilmesinin proje dosyalarının güncelleştirilmesini tetikleyemediğinde bir gerileme düzeltildi.

- Kullanıcı kodunun günlük geri çağırma işleyicisine katılabileceği bir API hatası düzeltildi.

## <a name="10110"></a>1.0.11.0
Yayın tarihi, 28 Kasım 2012

### <a name="new-features"></a>Yeni özellikler

- Unity 4 için resmi destek.

- Unity Project gezgini 'nden betikleri düzenleme.

- Visual Studio ' deki tümleştirme, pencereye git.

- Bilgi konsolu iletisini ayrıştırma, Hata Listesi tıklamak, simgeleri olan ilk StackFrame 'e götürür.

- Kullanıcının proje üretimine katılmasını sağlamak için bir API ekleyin.

- Kullanıcının LogCallback 'a katılmasını sağlamak için bir API ekleyin.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Visual Studio 2012 ' de Unity Project gezgini 'nin arka planında düzeltilen gerileme.

- Tam .NET profilinin kullanıcıları için sabit proje üretimi.

- Web hedefinin kullanıcıları için sabit proje üretimi.

- Unity olarak hata ayıklama ve Izleme derleme sembolleri dahil olmak üzere sabit proje üretimi.

- Goto symbol penceremizdeki özel karakterler kullanılırken oluşan kilitlenme düzeltildi.

- Visual Studio durum çubuğunda simgemizi ekleyeemiz için çökme düzeltildi.

## <a name="10100"></a>1.0.10.0
Yayın tarihi 9 Ekim 2012

### <a name="bug-fixes"></a>Hata Düzeltmeleri

- Visual Studio 2010 ' de Unity Project gezgini 'nin arka planı düzeltildi.

- hata ayıklayıcı arabirimi daha önce kilitlenen bir Unity 'ye hata ayıklayıcı eklemek denendiğinde oluşabilecek bir Visual Studio donması düzeltildi.

- bir kesme noktası ayarlandığında ve bir AppDomain yeniden yüklemesi gerçekleştiğinde oluşabilecek Visual Studio donması düzeltildi.

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

- komut dosyası opener, hem Visual Studio hem de betikleri açabildiğinden emin olmak için proje yolunu elde ediniyor.

- hata ayıklama oturumu çalışırken oluşturulan kesme noktalarıyla bir hata düzeltildi, bu, Visual Studio kilitlenmeye neden olabilir.

- Visual Studio 2010 ' de unityvs 'nin nasıl kaydedildiği düzeltildi.

## <a name="1070"></a>1.0.7.0

Yayın tarihi 14 Eylül 2012

### <a name="new-features"></a>Yeni özellikler

- Visual Studio 2012 desteği.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Unity 'nin davranışını eşleştirmek için, düzenleyici ve eklenti proje dosyalarının sabit üretimi.

- Unity 4 ' te. pdb sembolleri çevirisi düzeltildi.

> [!IMPORTANT]
> Visual Studio 2012 desteği nedeniyle, birkaç dosyayı yeniden adlandırdık ve başka bir dosya taşımanız gerekiyordu. Unity 'yi içeri aktarmaya yönelik unityvs paketi, sırasıyla Visual Studio 2010 ve 2012 Visual Studio için unityvs 2010 ya da unityvs 2012 olarak adlandırılıyordu. Bu sürüm ayrıca, UnityVS proje dosyalarının yeniden oluşturulmasını gerektirir.

## <a name="1060---internal-build"></a>1.0.6.0-iç derleme
12 Eylül 2012 ' de yayınlandı

## <a name="1050"></a>1.0.5.0

Yayın tarihi 10 Eylül 2012

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Betiklerin veya gölgelendiricilerin geçersiz bir XML karakteri olduğunda proje dosyalarının sabit üretimi düzeltildi.

- Unity varlık sunucusuna bağlıyken Unity örneklerinin sabit algılanması. bu, Unity 'den dosyaları açmak ve Visual Studio hata ayıklayıcının otomatik bağlantısı için hata tetikledi.

## <a name="1040"></a>1.0.4.0

Yayımlanma tarihi, 5 Eylül 2012

### <a name="new-features"></a>Yeni özellikler

- Unity 'de hata ayıklama sembollerini otomatik dönüştürme.

    Varlık klasörünüzde ilişkili. pdb ile bir .NET .dll derlemesi varsa, derlemeyi yeniden içeri aktarmanız yeterlidir ve UnityVS,. pdb 'yi Unity 'nin betik altyapısının anladığı bir hata ayıklama sembolleri dosyasına dönüştürür ve UnityVS 'den .NET derlemelerinize adım adım başlayabileceksiniz.

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
