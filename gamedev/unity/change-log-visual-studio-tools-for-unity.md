---
title: değişiklik günlüğü (Unity için Visual Studio Araçları, Windows) | Microsoft Docs
description: Unity için Visual Studio Araçları, Windows için değişiklik günlüğünü görüntüleyin. 4.7.0.0 ve dışında 1.0.0.0 sürümündeki değişikliklere bakın.
ms.date: 9/28/2021
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: conceptual
ms.assetid: ea490b7e-fc0d-44b1-858a-a725ce20e396
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: a3f61560c15e21c15ee9cfa6534a30639076bec0
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129967840"
---
# <a name="change-log-visual-studio-tools-for-unity-windows"></a>değişiklik günlüğü (Unity için Visual Studio Araçları Windows)

Unity için Visual Studio Araçları değişiklik günlüğü.

## <a name="41140"></a>4.11.4.0
Yayın 4 Ekim 2021

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - Büyük Unity projeleri için varlık dizinlemesini otomatik olarak devre dışı bırakın.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Tanılama ile desteklenen ifade algılama düzeltildi [`UNT0024`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0024.md) .

## <a name="41130"></a>4.11.3.0
10 Ağustos 2021 tarihinde yayınlandı

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Varlıklar işlenirken azaltılan bellek tüketimi.

  - , Ve gizler ile iyileştirilmiş ayırmalar [`USP0008`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0008.md) [`USP0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0009.md) [`USP0010`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0010.md) [`USP0011`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0011.md) .

  - ,,, Tanılama ile iyileştirilmiş simge kullanımı [`UNT0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0002.md) [`UNT0003`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0003.md) [`UNT0012`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0012.md) [`UNT0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0014.md) .

## <a name="41120"></a>4.11.2.0
Yayın tarihi, 13 Temmuz 2021

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Gelişmiş ışık oluşturma süresi yalnızca, CS derleyici uyarılarını işleyecek şekilde çalışır. Diğer tüm çözümleyiciler çözüm analizi aracılığıyla çalışacaktır.

## <a name="41110"></a>4.11.1.0
Yayımlanma tarihi, 15 Haziran 2021

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - YAML varlıklarını ayrıştırırken azaltılan bellek tüketimi.

## <a name="41100"></a>4.11.0.0
Yayımlanma tarihi 25 Mayıs 2021

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - [`UNT0025`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0025.md)Tanılama eklendi. KeyCode bağımsız değişkeniyle Input. GetKey aşırı yüklerini tercih edin.

  - Tanılamanın daha fazla geçersiz kullanımı (statik ve salt okunur alanları) eklendi [`UNT0013`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0013.md) .

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Açık yöntem uygulamaları ve Tanılama ile ilgili sorunlar düzeltildi [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0006.md) .

## <a name="41030"></a>4.10.3.0
Yayın tarihi, 8 Haziran 2021

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - [Geri bağlantı] YAML varlıklarını ayrıştırırken azaltılan bellek tüketimi.

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

  - Eski özelliklerin özel durumlara neden olduğu filtreleme düzeltildi.

## <a name="4900"></a>4.9.0.0
Yayın tarihi: 20 Ocak 2021

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - , ve `raytrace shaders` dosyaları için destek `UXML` `USS` eklendi.

  - Oluşturma `.vsconfig` desteği eklendi. Visual Studio hangi bileşenlerin eksik olduğunu algılamalı ve Unity projelerini kullanırken bunları yüklemeniz istensin.

  - Unity iletileri API'si güncelleştirildi (coroutine olarak kullanılan tüm yöntemler için).

  - Güncelleştirme Android SDK algılama.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Örnek seçimi iletişim kutusu kullanırken işlem yenileme düzeltildi.

  - Tanılama [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0006.md) düzeltildi ve Coroutines ve için yanlış uyarılar `AssetPostprocessor.OnAssignMaterialModel` veriyor.

## <a name="4820"></a>4.8.2.0
Yayın tarihi: 10 Kasım 2020

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Yalnızca [`UNT0010`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0010.md) 'den devralınan her şeye uygulamak için geliştirilmiş `Component` `MonoBehaviour` tanılama.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - CodeLens iletisi geçersiz kılındı.

## <a name="4810"></a>4.8.1.0
Yayın tarihi: 13 Ekim 2020

### <a name="new-features"></a>Yeni Özellikler

- **Değerlendirme:**

  - Çağrılarla örtülü dönüştürme desteği eklendi. Daha önce değerlendirici katı tür denetimi uygulatarak uyarı `Failed to find a match for method([parameters...])` iletilerine neden oldu.

- **Entegrasyon:**

  - Tanılama [`UNT0018`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0018.md) eklendi. , , veya `System.Reflection` gibi performans açısından kritik iletilerde özellikleri `Update` `FixedUpdate` `LateUpdate` kullanmamanız `OnGUI` gerekir.

  - Tüm statik [`USP0003`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0003.md) yöntemleri destekleyen geliştirilmiş ve [`USP0005`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0005.md) `AssetPostprocessor` bastırıcılar.

  - için [`USP0016`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0016.md) suppressor `CS8618` eklendi. `C# 8.0` null değere değiştirilebilir başvuru türlerini ve null değerdilemez başvuru türlerini içerir. 'den devralınan türlerin `UnityEngine.Object` başlatma algılaması desteklenmez ve hatalara neden olur.

  - Şimdi hem Unity 2019.x hem de 2020.x+ için aynı oynatıcı ve asmdef proje oluşturma mekanizmasını kullanıyoruz.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Açıklamalarda iletiler için beklenmeyen tamamlama düzeltildi.

## <a name="4800"></a>4.8.0.0 
Yayın tarihi: 14 Eylül 2020

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Unity 2019.x ile oynatıcı projesi oluşturma düzeltildi.

## <a name="4710"></a>4.7.1.0
5 Ağustos 2020'de yayınlandı

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Varsayılan şablonlara ad alanı desteği eklendi.
  
  - Unity iletileri API'si 2019.4'e güncelleştirildi.

  - için [`USP0013`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0013.md) suppressor `CA1823` eklendi. veya özniteliklerine `SerializeField` sahip özel alanlar `SerializeReference` kullanılmamış (FxCop) olarak işaretlendi değil.
  
  - için [`USP0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0014.md) suppressor `CA1822` eklendi. Unity iletileri, değiştirici adayı `static` (FxCop) olarak işaretlenmemeli.

  - için [`USP0015`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0015.md) suppressor `CA1801` eklendi. Kullanılmayan parametreler Unity iletilerinden (FxCop) kaldırılmalıdır.
  
  - Suppressor'a MenuItem [`USP0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0009.md) desteği eklendi.  

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Ek [`USP0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0001.md) [`USP0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0002.md) parantezlerle veya yöntem bağımsız değişkenleriyle çalışmayan ve bastırıcılar düzeltildi.
  
  - Unity ayarlarında otomatik yenileme devre dışı bırakılabilirken bile zorunlu varlık veritabanı yenilemesi düzeltildi.

## <a name="4700"></a>4.7.0.0
Yayın tarihi: 23 Haziran 2020

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Unity çözüm ve projeleri yeniden oluştururken çözüm klasörlerini kalıcı yapmak için destek eklendi.

  - Tanılama [`UNT0015`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0015.md) eklendi. veya özniteliğiyle yanlış yöntem `InitializeOnLoadMethod` imzasını `RuntimeInitializeOnLoadMethod` algıla.

  - Tanılama [`UNT0016`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0016.md) eklendi. İlk `Invoke` bağımsız değişken dize değişmez değeri olan , veya kullanmak tür için güvenli `InvokeRepeating` `StartCoroutine` `StopCoroutine` değildir.

  - Tanılama [`UNT0017`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0017.md) eklendi. `SetPixels` çağrı yavaş.

  - Gölgelendirici dosyaları için blok açıklaması ve girintileme desteği eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Unity ileti sihirbazında iletileri filtrelerken seçimi sıfırlamayın.
  
  - Unity API belgelerini a açılırken her zaman varsayılan tarayıcıyı kullanın.
  
  - , ve bastırıcıları şu kurallarla düzeltildi: SerializeField özniteliğiyle dekore edilmiş tüm alanlar için gizleme [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0004.md) [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) `IDE0044` `IDE0051` (salt okunur), `CS0649` (kullanılmayan), (hiçbir zaman atanmamış). `Unity.Object` öğesini genişleten her türdeki genel alanlar için `CS0649` (hiçbir zaman atanmamış) öğesini gizleyin.

  - Tanılama için genel tür parametre [`UNT0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0014.md) denetimi düzeltildi.

- **Değerlendirme:**

  - Sabit numaralarla eşitlik karşılaştırması düzeltildi.

## <a name="4610"></a>4.6.1.0
Yayın tarihi: 19 Mayıs 2020

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Unity tarafında mesajlaşma sunucusu oluşturamadığımız için uyar.
  
  - Basit derleme sırasında çözümleyicileri düzgün çalıştırın.
  
  - UPE'den oluşturulan bir MonoBehaviour sınıfının dosya adıyla eşleşmeme sorunu düzeltildi.

## <a name="4600"></a>4.6.0.0
Yayın tarihi: 14 Nisan 2020

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - CodeLens (Unity betikleri ve iletileri) için destek eklendi.
  
  - Tanılama [`UNT0012`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0012.md) eklendi. içinde çağrılarını algıla ve `StartCoroutine()` sarmala.

  - Tanılama [`UNT0013`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0013.md) eklendi. Geçersiz veya yedekli özniteliği algıla ve `SerializeField` kaldır.

  - Tanılama [`UNT0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0014.md) eklendi. Bileşen `GetComponent()` olmayan veya Arabirim Türü olmayan çağrılır.
  
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
  
  - Unity iletileri için ilişkili belgeleri görüntüleyen bir hızlı araç ipucu eklendi.

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

  - Unity'ye özgü yeni tanılamalar ekleyerek Unity Visual Studio için sahip olduğu bilgileri derinden ekledik. Unity projeleri için geçerli olmayan genel C# tanılamalarını gizleyerek IDE’yi daha akıllı hale getirdik. Örneğin, IDE bir denetçi değişkenlerini değiştirmek için unity düzenleyicisinde değişkeni değiştirmenizi önleyen bir hızlı düzeltme `readonly` göstermez.
    - [`UNT0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0001.md): Unity iletileri boş olsalar bile çalışma zamanı tarafından çağrılır, Unity çalışma zamanı tarafından gereksiz işlemeyi önlemek için bunları bildirin.
    - [`UNT0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0002.md): Dize eşitliği kullanarak etiket karşılaştırması, yerleşik CompareTag yönteminden daha yavaştır.
    - [`UNT0003`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0003.md): Tür güvenliği için Genel GetComponent formunun kullanımı tercih edilir.
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

  - Dizi başlatıcılarda örtülü dönüştürme desteği eklendi, örneğin `new byte [] {1,2,3,4}` : .

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

  - Dosya uzantısının bilinen herhangi bir düzenleyici tarafından işlenmiş durumda olmadığının bir sorunu düzeltildi.

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

  - IntelliSense hataları ve uyarılarını kullanmak yerine Unity projeleri için tam derleme devre dışı bırakıldı. Hatta Unity, Unity Visual Studio yaptığı işi temsil eden sınıf kitaplığı projeleriyle birlikte bir çözüm oluşturur. Bununla birlikte derleme işlem hattı kapatılan Visual Studio unity tarafından hiçbir zaman kullanılmaz veya toplanmayacak. Bu Visual Studio yalnızca kaynakları hiçbir şey için tüketmektir. Tam derlemeye ihtiyacınız varsa, buna bağlı araçlar veya bir kurulum varsa, bu iyileştirmeyi devre dışı abilirsiniz (Unity için Araçlar/Seçenekler/Araçlar/Projelerin tam derlemesini devre dışı bırak).

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

Yayın tarihi: 26 Haziran 2018

### <a name="new-features"></a>Yeni Özellikler

- **Hata ayıklama:**

  - UserLog ve UserBreak komutları için destek eklendi.

  - Gecikmeli tür yükleme desteği eklendi (ağ yükünü ve hata ayıklayıcı yanıt gecikmesini iyileştirme).

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Değerlendirme:**

  - geliştirilmiş ikili işleç ifadesi değerlendirmesi ve yöntem araması.

## <a name="3800"></a>3.8.0.0

Yayın tarihi: 30 Mayıs 2018

### <a name="new-features"></a>Yeni Özellikler

- **Hata ayıklama:**

  - Zaman uyumsuz yapılarda değişkenleri görüntüleme desteği eklendi.

  - Derleyici yapılarında uyarıları önlemek için kesme noktaları ayarlarken iç içe türleri işleme desteği eklendi.

- **Entegrasyon:**

  - Gölgelendiriciler için textmate dil bilgisi desteği eklendi (C++ iş yükü artık Gölgelendirici kod renklendirmesi için gerekli değildir).

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Project Nesil:**

  - Yeni Unity çalışma zamanı kullanılırken artık taşınabilir pdb'yi mdb'ye dönüştürmiyoruz.

## <a name="3701"></a>3.7.0.1

Yayın tarihi: 7 Mayıs 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Yükleyici:**

  - Deneysel derlemeler kullanırken ortaya konu olan bağımlılık sorunu düzeltildi.

## <a name="3700"></a>3.7.0.0

Yayın tarihi: 7 Mayıs 2018

### <a name="new-features"></a>Yeni Özellikler

- **Hata ayıklama:**

  - Düzenlemeli hata ayıklama (aynı oturumda birden çok oyuncunun/düzenleyicinin hata ayıklaması) için Visual Studio eklendi.

  - Android USB oynatıcı hata ayıklama desteği eklendi.

  - UWP/IL2CPP oynatıcı hata ayıklama desteği eklendi.

- **Değerlendirme:**

  - Onaltılık belirleyiciler için destek eklendi.

  - Geliştirilmiş izleme penceresi değerlendirme deneyimi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Özel durum ayarlarının kullanımı düzeltildi.

- **Project Nesil:**

  - Paket yöneticisi derleme birimlerini oluşturmanın dışında tut.

## <a name="3605"></a>3.6.0.5

Yayın tarihi: 13 Mart 2018

### <a name="new-features"></a>Yeni Özellikler

- **Project Nesil:**

  - Unity 2018.1'de yeni proje oluşturucu desteği eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Özel projelerle bozuk durumların işlenmesi düzeltildi.

- **Hata ayıklayıcı:**

  - Sonraki deyimi ayarlama düzeltildi.

## <a name="3604"></a>3.6.0.4

Yayın tarihi: 5 Mart 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Project Nesil:**

  - Mono sürümü algılama düzeltildi.

- **Entegrasyon:**

  - 2018.1 ve eklenti etkinleştirme ile ilgili zamanlama sorunları düzeltildi.

## <a name="3603"></a>3.6.0.3

Yayın tarihi: 23 Şubat 2018

### <a name="new-features"></a>Yeni Özellikler

- **Project Nesil:**

  - Daha fazla .NET Standard.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Project Nesil:**

  - Unity hedef çerçevesi algılaması düzeltildi.

- **Hata ayıklayıcı:**

  - Kullanıcı kodunun dışından atılan özel durumlarda yeni bir durum düzeltildi.

## <a name="3602"></a>3.6.0.2

Yayın tarihi: 7 Şubat 2018

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - UnityMessage API'si yüzeyini 2017.3 için güncelleştirin.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Yalnızca dış değişiklikte projeleri yeniden yükleyin (azaltma ile).

## <a name="3601"></a>3.6.0.1

Yayın tarihi: 24 Ocak 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Otomatik pdb'den mdb hata ayıklama simgesine dönüştürme düzeltildi.

  - Dizi boyutunu değiştirmeye çalışırken EditorPrefs.GetBool'a yapılan dolaylı çağrının denetçiyi etkilemesi düzeltildi.

## <a name="3600"></a>3.6.0.0

Yayın tarihi: 10 Ocak 2018

### <a name="new-features"></a>Yeni Özellikler

- **Project Nesil:**

  - 2018.1 MonoIsland başvuru modeli desteği eklendi.

- **Değerlendirme:**

  - Tanımlayıcı için $exception eklendi.

- **Hata ayıklayıcı:**

  - Yeni Unity çalışma zamanı ile DebuggerHidden/DebuggerStepThrough öznitelikleri için destek eklendi.

- **Sihirbaz:**

  - Sihirbazlar için 'En son' sürümü tanıtma.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Project Nesil:**

  - Oynatıcı projeleri için proje guid hesaplaması düzeltildi.

- **Hata ayıklayıcı:**

  - Hataya neden olan olayları işleme yarışları düzeltildi.

- **Sihirbaz:**

  - Yöntemi eklemeden önce roslyn bağlamını yenileyin.

## <a name="3503"></a>3.5.0.3

Yayın tarihi: 9 Ocak 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Otomatik pdb'den mdb hata ayıklama simgesine dönüştürme düzeltildi.

## <a name="3502"></a>3.5.0.2

Yayın tarihi: 4 Aralık 2017

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Artık Unity'de bir betik eklediğinizde veya kaldırdığınızda Unity projeleri Visual Studio'da otomatik olarak yeniden yükleniyor.

- **Hata ayıklayıcı:**

  - Unity Düzenleyicisi'nde hata ayıklamak için Xamarin ve Mac için Visual Studio Mono hata ayıklayıcısını kullanma seçeneği eklendi.

  - Taşınabilir hata ayıklama sembol dosyaları için destek eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Kurulum bağımlılıkları sorunları düzeltildi.

  - Unity API yardım menüsünün göstermesi düzeltildi.

- **Project Nesil:**

  - IL2CPP/.NET 4.6 arka ucuyla UWP oyunu üzerinde çalışırken oyuncu projesi oluşturma düzeltildi.

  - Ek .dll derleme dosya adı yanlış eklenmiştir.

  - Genel api yerine belirli bir proje API uyumluluk düzeyinin kullanımı düzeltildi.

  - Varsayılan değer artık 'true' olduğu için AllowAttachedDebuggingOfEditor Unity bayrağını zorlamayın.

## <a name="3402"></a>3.4.0.2

Yayın tarihi: 19 Eylül 2017

### <a name="new-features"></a>Yeni Özellikler

- **Project Nesil:**

  - assembly.json derleme birimleri için destek eklendi.

  - Unity derlemelerini proje klasörüne kopyalama durduruldu.

- **Hata ayıklayıcı:**

  - Yeni Unity çalışma zamanıyla sonraki deyimi ayarlama desteği eklendi.

  - Yeni Unity çalışma zamanı ile Ondalık tür desteği eklendi.

  - Örtülü/açık dönüştürme desteği eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Değerlendirme:**

  - Örtülü boyut ile dizi oluşturma düzeltildi.

  - Derleyici tarafından yerel öğelerle oluşturulan öğeler düzeltildi.

- **Project Nesil:**

  - 4.6 API düzeyi için Microsoft.CSharp başvurusu düzeltildi.

## <a name="3302"></a>3.3.0.2

Yayın tarihi: 15 Ağustos 2017

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Project Nesil:**

  - Unity 5.5 ve önceki sürümlerde Visual Studio çözümü oluşturma sorunu düzeltildi.

## <a name="3300"></a>3.3.0.0

Yayın tarihi: 14 Ağustos 2017

### <a name="new-features"></a>Yeni Özellikler

- **Değerlendirme:**

  - Yeni Unity çalışma zamanıyla yapı oluşturma desteği eklendi.

  - İşaretçiler için support eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Değerlendirme:**

  - Temel öğelerde yöntem çağırma düzeltildi.

  - BeforeFieldInit ile işaretlenmiş türlerle alan değerlendirmesi düzeltildi.

  - İkili işleçler (alt) ile desteklenen olmayan çağrılar düzeltildi.

  - Visual Studio Watch'a öğe ekleme sorunları düzeltildi.

- **Project Nesil:**

  - mcs.rsp dosyalarıyla derleme adı başvuruları düzeltildi.

  - API düzeyleriyle tanımları düzeltildi.

## <a name="3200"></a>3.2.0.0

Yayın tarihi: 10 Mayıs 2017

### <a name="new-features"></a>Yeni Özellikler

- **Yükleyici:**

  - MEF önbelleğini temizleme desteği eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Kod Düzenleyicisi:**

  - Özel özniteliklerle sınıflandırma/tamamlama düzeltildi.

  - Unity iletileriyle titreşim düzeltildi.

## <a name="3100"></a>3.1.0.0

Yayın tarihi: 7 Nisan 2017

### <a name="new-features"></a>Yeni Özellikler

- **Hata ayıklayıcı:**

  - Yeni Unity çalışma zamanı için destek eklendi (.NET 4.6 / C# 6 uyumluluğuyla).

- **Project Nesil:**

  - .NET 4.6 profili için destek eklendi.

  - mcs.rsp dosyaları için destek eklendi.

  - Unity 5.6 kullanılırken her zaman güvenli olmayan derleme anahtarını etkinleştirin.

  - Windows Store platformu ve il2cpp arka ucu kullanırken "Oynatıcı" proje oluşturma desteği eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Kod Düzenleyicisi:**

  - Otomatik tamamlama ile yöntem ekleme sonrasındaki caret konumu düzeltildi.

- **Project Nesil:**

  - Derleme sürümü işleme sonrası kaldırıldı.

## <a name="3001"></a>3.0.0.1

Yayın tarihi: 7 Mart 2017

### <a name="this-version-includes-all-new-features-and-bug-fixes-introduced-with-28x-series"></a>Bu sürüm, 2.8.x serisiyle birlikte gelen tüm yeni özellikleri ve hata düzeltmelerini içerir.

## <a name="2820---30-preview-3"></a>2.8.2.0 - 3.0 Önizleme 3
Yayın tarihi: 25 Ocak 2017

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Project Nesil:**

  - Önce ikili DLL olarak, sonra da proje başvurusu olarak iki kez başvurulan Plugins projelerinin bulunduğu regresyon düzeltildi.

## <a name="2810---30-preview-2"></a>2.8.1.0 - 3.0 Önizleme 2
Yayın tarihi: 23 Ocak 2017

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Kod Düzenleyicisi:**

  - Küme ayracı tamamlanmadan öznitelik bildirimini başlatmaya ilişkin bir kilitlenme düzeltildi.

- **Hata ayıklayıcı:**

  - Yeni Unity derleyicisi/çalışma zamanı altında coroutines ile işlev kesme noktaları düzeltildi.

  - Bağlantız bir kesme noktası olması durumunda (karşılık gelen kaynak konumu bulunamadı olduğunda) uyarı eklendi.

- **Project Nesil:**

  - Özel/yerelleştirilmiş karakterlerle csproj oluşturma düzeltildi.

  - Varlıklar dışındaki Kitaplık (Facebook SDK'sı gibi) başvurular düzeltildi.

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

- Unity yeniden derleme sırasında hata ayıklayıcıyı bağlarken Unity donması sorunu giderildi.

- Uzak düzenleyicilerde veya başka bir sistemde derlenmiş olan oyuncuların hata ayıklaması sırasında kesme noktaları düzeltildi.

- Bir kesme Visual Studio kilitlenmesi olası bir hata düzeltmesi.

- Kesme noktası bağlaması, kesme noktaları yüklemeden kaldırıldı olarak gösterilememek için düzeltildi.

- Kapsam dışında görünen canlı değişkenleri önlemek için hata ayıklayıcıda değişken kapsamının işlenmesi düzeltildi.

- Hata ayıklayıcının İfade Değerlendirmesi'ne statik üyelerin aramasını düzeltin.

- Statik alanları ve özellikleri göstermek için hata ayıklayıcının İfade Değerlendirmesi'ne türlerin görüntülenmesi sorunu giderildi.

- Unity proje adları yasaklayan özel karakterler içeriyorken çözüm oluşturma Visual Studio (Bağlan sorunu #948666).

- seçenek Visual Studio Araçları konsol olaylarını göndermeyi hemen durdurmak için Unity paketini düzeltin (Bağlan sorunu #933357).

- UnityVS tarafından oluşturulan projelerde UnityEngine.UI gibi yeni API'lere yapılan başvuruları düzgün bir şekilde yeniden oluşturmak için başvuruların algılanması sorunu giderildi.

- Yükleyici, bozuk yüklemeleri önlemek Visual Studio önce yüklemenin kapatılması gerektirecek şekilde düzeltildi.

- Unity Başvuru Derlemelerini vsTU'nun tüm sürümleri arasında paylaşılan düzgün bir tek başına bileşen olarak yüklemek için yükleyiciyi düzeltin.

- Unity'nin 64 bit sürümlerinde VSTU ile betikleri açma sorunu giderildi.

## <a name="1900"></a>1.9.0.0

Yayın tarihi: 29 Temmuz 2014

### <a name="new-features"></a>Yeni özellikler

- Unity Hata Ayıklayıcısını Ekle penceresinde hata ayıklamak için özel bir IP ve bağlantı noktası girme olanağını ekleyin.

- Unity'yi arka planda çalıştıracak veya çalıştıracak şekilde ayarlamak için yapılandırma seçeneği ekleyin.

- Yalnızca çözüm ve proje dosyaları veya proje dosyaları oluşturmak için yapılandırma seçeneği ekleyin.

- Başlangıç hedefi: Unity'ye Ekle veya Unity'ye Ekle ve Oynat'ı seçin.

- Hata ayıklayıcısında çok boyutlu dizilerin görüntüsü.

- Yeni Unity Player hata ayıklama bağlantı noktalarını işleme.

- Unity'nin 4.6 GUI derlemeleri gibi yeni Unity derlemelerine yapılan başvuruları işle.

- Hata ayıklama sırasında yerel değişkenleri düzgün şekilde görüntülemek için kapatmaları yok eder.

- Hata ayıklama sırasında oluşturulan iterators değişkenlerini bağımsız değişkenlere yok eder.

- Proje yeniden Project sonra Unity gezgininin durumunu koruma.

- Unity Project Explorer'ı geçerli belgeyle eşitlemek için bir komut ekleyin.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Hata ayıklayıcıyı başlatmadan önce koşulları ayarlanmış koşullu kesme noktaları düzeltildi.

- Uyarılardan kaçınmak için UnityEngine başvurularını düzeltin.

- Unity beta sürümleri ayrıştırma sorunu giderildi.

- Bir kesme noktası veya adımlama ile yerel değişkenler penceresinde değişkenlerin görünmey durumuna neden olan sorun giderildi.

- Visual Studio 2013'daki değişken araç Visual Studio 2013.

- Unity 4.5 için IntelliSense belgelerinin nesli düzeltildi.

- Bir etki alanı yeniden Visual Studio (Unity'de oynat/durdur) Unity / etki alanı iletişimini düzeltin.

- Temaların parçalarının işlenmesi Visual Studio düzeltildi.

> [!IMPORTANT]
> C# Unity ekosisteminin baskın dilidir. Yeni Örnek Varlıklar C# dilindedir, Unity belgeleri varsayılan olarak C# olur; C# deneyimine daha iyi odaklanmak için UnityScript ve Boo için temel desteğimizi kaldırdık. Sonuç olarak, VSTU çözümleri artık yalnızca C# ve yüklemesi çok daha hızlıdır.

## <a name="1820"></a>1.8.2.0

Yayın tarihi: 7 Ocak 2014

### <a name="new-features"></a>Yeni özellikler

- Düzenleyicilerin uzaktan bulunması için Unity'nin betik altyapısının Mavericks'te ağ katmanında bir soruna karşı çalışma.

- Uzak Unity oyuncularını bulmak için yeni bağlantı noktalarını işleme.

- Geçerli derleme hedefine özgü UnityEngine derlemesi başvurusu.

- Oluşturulan projelere dahil etmek için dosyaları filtreleme ayarı ekleyin.

- Konsol günlüklerinin hata listesine gönderilmesini devre dışı Visual Studio ayarı ekleyin. Konsol günlüklerini almak için Unity'de kayıtlı yalnızca bir geri Pro PlayMaker veya Console Pro kullanıyorsanız bu yararlı olur.

- mdb hata ayıklama sembollerinin neslini devre dışı bırakmak için ayar ekleyin. Bu, mdb'yi kendiniz üretiyorsanız kullanışlıdır.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Unity >= 4.2'den VS'de açılan dosyaların IntelliSense'i kaybetmesi durumunda ortaya çıkacak bir gerileme giderildi.

- Özel temaları işlemek için VS iletişim kutularımızı düzeltin.

- UPE'nin bağlam menüsünü kapatma sorunu giderildi.

- Sürüme özgü derleme eşit dışında olduğunda Unity'de kilitlenmeyi önle.

## <a name="1810"></a>1.8.1.0

Yayın tarihi: 21 Kasım 2013

### <a name="new-features"></a>Yeni özellikler

- Unity 4.3 API'leri ile MonoBehaviour sihirbazları ayarlandı.

- MonoBehaviour sihirbazları kullandığınız sürüme bağlı olarak Unity API'lerini filtreleiyor.

- System.Xml'a bir başvuru ekleyin. Unity > 4.1 için linq to the projects.

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

- Unity projesi gerçek JavaScript varlıkları içerirken proje oluşturma düzeltildi.

- İfade değerlendirmesinde hata işleme düzeltildi.

- Yeni değerleri değer türlerinin alanlarına ayarlama düzeltildi.

- Kod düzenleyicisinden ifadelerin üzerine gelindiğinde ortaya gelen olası yan etkiler düzeltildi.

- Yüklenen derlemelerde ifade değerlendirmesi için türlerin nasıl arandığı düzeltildi.

- BUGS-21 hatası düzeltildi: Unity nesnelerinde atama değerlendirmesinin hiçbir etkisi yok.

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
> 2012 Visual Studio nedeniyle birkaç dosyayı yeniden adlandırmamız ve birkaç dosyayı başka bir yere taşımamız gerekirdi. Unity'i içeri aktaracak UnityVS paketi artık sırasıyla Visual Studio 2010 ve 2012 için UnityVS 2010 veya UnityVS 2012 olarak Visual Studio olarak adlandırılmıştır. Bu sürüm ayrıca UnityVS proje dosyalarının yeniden oluşturulmasını gerektirir.

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

    Varlık klasörünüzdeki ilişkili .pdb ile bir .NET .dll derlemeniz varsa, derlemeyi yeniden içeri aktarmanız ve UnityVS'nin .pdb'i Unity'nin betik altyapısının antiği bir hata ayıklama sembolleri dosyasına dönüştürmesi gerekir ve UnityVS'den .NET derlemelerinize adım atabilirsiniz.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Unity içindeki yöntemler veya özellikler tarafından oluşan özel durumların neden olduğu hata ayıklama sırasında UnityVS kilitlenmesi düzeltildi.

## <a name="1030"></a>1.0.3.0

Yayın tarihi: 4 Eylül 2012

### <a name="new-features"></a>Yeni özellikler

- Unity'den dosyaları açmak için UnityVS kullanımını devre dışı bırakmak için yeni yapılandırma seçeneği.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Düzenleyici olmayan projeler için UnityEditor'a başvuru oluşturma düzeltildi.

- Düzenleyici olmayan projeler UNITY_EDITOR sembollerinin tanımı düzeltildi.

- Özel durum çubuğumuzdan kaynaklanan rastgele VS kilitlenmesi düzeltildi.

## <a name="1020"></a>1.0.2.0

Yayın tarihi: 30 Ağustos 2012

### <a name="bug-fixes"></a>Hata düzeltmeleri

- PythonTools hata ayıklayıcısıyla çakışma düzeltildi.

- Mono.Olitik'e başvurular düzeltildi.

- Unity 4 b7 ile betik derlemelerinin Unity'den nasıl alınarak alınamadı.

## <a name="1010"></a>1.0.1.0

Yayın tarihi: 28 Ağustos 2012

### <a name="new-features"></a>Yeni özellikler

- Unity 4.0 Beta için önizleme desteği.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Özel durumların neden olduğu özelliklerin denetimi düzeltildi.

- Nesneleri incelerken temel nesnelere azalan düzende sabit.

- MonoBehavior sihirbazında ekleme noktası için boş açılan liste düzeltildi.

- UnityScript ve Boo için Varlık klasörünün içindeki dll dosyasının tamamlanması düzeltildi.

## <a name="1000---initial-release"></a>1.0.0.0 - İlk sürüm
Yayın tarihi: 22 Ağustos 2012
