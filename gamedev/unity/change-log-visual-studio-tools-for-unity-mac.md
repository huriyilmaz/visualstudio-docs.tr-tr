---
title: Değişiklik Günlüğü (Unity için Visual Studio Araçları, Mac) | Microsoft Docs
description: Mac için değişiklik Unity için Visual Studio Araçları görüntüleme. Sürüm 1.0.0.0 ile 2.7.0.0 ve ötesindeki değişikliklere bakın.
ms.custom: ''
ms.date: 6/3/2021
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: conceptual
ms.assetid: 33a6ac54-d997-4308-b5a0-af7387460849
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 2d3faf8e5231ca5d2e99bcf80dc18b6d4f4607cd
ms.sourcegitcommit: f430d014f912aa7874e1db65026dc72688b973e4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2021
ms.locfileid: "111448304"
---
# <a name="change-log-visual-studio-tools-for-unity-mac"></a>Değişiklik Günlüğü (Unity için Visual Studio Araçları, Mac)

Unity için Visual Studio Araçları günlüğü değiştirme.

## <a name="21020"></a>2.10.2.0
Yayın tarihi: 2 Haziran 2021

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Tanılama [`UNT0024`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0024.md) eklendi. Vektör hesaplamaları üzerinden skaler hesaplamalara öncelik verme.

- **Değerlendirme:**

  - Görünür yerelleri düzgün filtrelemek için taşınabilir pdb sembolleri kullanma desteği eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Oynatıcının son Unity sürümleriyle ayrıştırma duyurusu düzeltildi.

## <a name="21010"></a>2.10.1.0
Yayın tarihi: 11 Mayıs 2021

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Quickfix ile ilgili [`UNT0008`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0008.md) kararlılık sorunları düzeltildi.

  - İş parçacıklarıyla ilgili performans sorunları düzeltildi.

  - Hatalistesinde gizlenen uyarıları ve hataları filtreleme düzeltildi.

  - Unity arka plan işlemlerini filtreleme düzeltildi.

## <a name="21000"></a>2.10.0.0
Yayın tarihi: 13 Nisan 2021

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Tanılama [`UNT0019`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0019.md) eklendi. için gereksiz dolaylı `GameObject.gameObject` çağrı.

  - Tanılama [`UNT0020`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0020.md) eklendi. `MenuItem` özniteliği statik olmayan yöntemde kullanılır.

  - Tanılama [`UNT0021`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0021.md) eklendi. Unity iletisi korunmalıdır (kabul).

  - Tanılama [`UNT0022`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0022.md) eklendi. Konum ve döndürmeyi ayarlamak için verimsiz yöntem.

  - Tanılama [`UNT0023`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0023.md) eklendi. Unity nesnelerinde atamayı biriktirma.

  - için [`USP0017`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0017.md) suppressor `IDE0074` eklendi. Unity nesneleri biriktirma ataması kullanmaz.

## <a name="2940"></a>2.9.4.0
Yayın tarihi: 6 Nisan 2021

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Test sabitleriyle ilgili sorunları düzeltme

## <a name="2930"></a>2.9.3.0
Yayın tarihi: 30 Mart 2021

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Test çalıştırıcısı ile ilgili sorunları düzeltme 

## <a name="2920"></a>2.9.2.0
Yayın tarihi: 2 Mart 2021

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Unity ileti iletişim kutusunda arama vurgulama düzeltildi.

  - Unity proje ağaç görünümü ile ilgili kararlılık sorunları düzeltildi.

- **Hata ayıklama:**

  - Koşullu kesme noktaları düzeltildi.

## <a name="2910"></a>2.9.1.0
Yayın tarihi: 9 Şubat 2021

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - IDE'den Unity testlerini çalıştırma ve hata ayıklama desteği eklendi

- **Değerlendirme:**

  - Kök `Active Scene` oyun nesnelerini gösteren yerellere eklendi.

  - `this.gameObject`Unity projelerinde yaygın olarak kullanılan yerellere eklendi.

  - Tüm `Children` nesne `Components` hiyerarşisini kolayca `GameObject` görüntüleyebiliyor olmak için tüm örneklere ve grupları eklendi.

  - Sahnenin `Scene Path` konumunu göstermek için tüm `GameObject` örneklere eklenir.

  - Kaynak oluşturucularla `JobEntityBatch` Varlıklar kullanılırken /Lambdas desteği eklendi.

  - Büyük dizileri görüntüleme desteği iyileştirildi (dizin demetleme kullanılarak).

  - 2019.4 API'si için eksik Unity iletileri eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Unity ileti iletişim kutusuyla ilgili kararlılık sorunları düzeltildi

  - ENU dışı diller için çeşitli kullanıcı arabirimi sorunları düzeltildi.

  - Tanılama ile ilgili kararlılık sorunları [`UNT0018`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0018.md) düzeltildi.

- **Hata ayıklama:**

  - Yöntemler kullanırken karşılaşılan VM bağlantısı kesilmesi `Trace` sorunları düzeltildi.

- **Değerlendirme:**

  - Eski özelliklerin özel durumlara neden olduğu filtreleme düzeltildi.

## <a name="2900"></a>2.9.0.0
Yayın tarihi: 20 Ocak 2021

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - , ve `raytrace shaders` dosyaları için destek `UXML` `USS` eklendi.

  - Unity iletileri API'si güncelleştirildi (tüm yöntemler için coroutines olarak kullanılır).

  - Güncelleştirme Android SDK algılama.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Tanılama [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0006.md) düzeltildi ve Coroutines ve için yanlış uyarılar `AssetPostprocessor.OnAssignMaterialModel` veriyor.

## <a name="2840"></a>2.8.4.0
Yayın tarihi: 15 Aralık 2020

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Unity Olay oluşturma sihirbazı kapatılıyorken ortaya gelen güvenilirlik sorunu düzeltildi.

## <a name="2830"></a>2.8.3.0
Yayın tarihi: 10 Kasım 2020

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Hata ayıklayıcı:**

  - Çözümde VSTU projesi yoksa bile Unity'ye ekleme düzeltildi.

## <a name="2820"></a>2.8.2.0
Yayın tarihi: 27 Ekim 2020

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Yalnızca [`UNT0010`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0010.md) 'den devralınan her şeye uygulamak için geliştirilmiş `Component` `MonoBehaviour` tanılama.

## <a name="2810"></a>2.8.1.0
Yayın tarihi: 13 Ekim 2020

### <a name="new-features"></a>Yeni Özellikler

- **Değerlendirme:**

  - Çağrılarla örtülü dönüştürme desteği eklendi. Daha önce değerlendirici katı tür denetimi uygulatarak uyarı `Failed to find a match for method([parameters...])` iletilerine neden oldu.

- **Entegrasyon:**

  - Tanılama [`UNT0018`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0018.md) eklendi. , , veya `System.Reflection` gibi performans açısından kritik iletilerde özellikleri `Update` `FixedUpdate` `LateUpdate` kullanmamanız `OnGUI` gerekir.

  - Tüm statik [`USP0003`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0003.md) yöntemleri destekleyen geliştirilmiş ve [`USP0005`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0005.md) `AssetPostprocessor` bastırıcılar.

  - için [`USP0016`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0016.md) suppressor `CS8618` eklendi. `C# 8.0` null değere değiştirilebilir başvuru türlerini ve null değerdilemez başvuru türlerini içerir. 'den devralınan türlerin `UnityEngine.Object` başlatma algılaması desteklenmez ve hatalara neden olur.

  - Şimdi hem Unity 2019.x hem de 2020.x+ için aynı oynatıcı ve asmdef proje oluşturma mekanizmasını kullanıyoruz.
  
  - Sihirbazla Unity iletileri oluşturulurken kullanıcı deneyimi iyileştirildi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Açıklamalarda iletiler için beklenmeyen tamamlama düzeltildi.

## <a name="2800"></a>2.8.0.0 
Yayın tarihi: 14 Eylül 2020

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Unity 2019.x ile oynatıcı projesi oluşturma düzeltildi.

## <a name="2710"></a>2.7.1.0
Yayın tarihi: 5 Ağustos 2020

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Unity iletileri API'si 2019.4'e güncelleştirildi.

  - için [`USP0013`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0013.md) suppressor `CA1823` eklendi. veya özniteliklerine `SerializeField` sahip özel alanlar `SerializeReference` kullanılmamış (FxCop) olarak işaretlanmaz.
  
  - için [`USP0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0014.md) suppressor `CA1822` eklendi. Unity iletileri, değiştirici adayı `static` (FxCop) olarak işaretlenmemeli.

  - için [`USP0015`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0015.md) suppressor `CA1801` eklendi. Kullanılmayan parametreler Unity iletilerinden (FxCop) kaldırılmalıdır.
  
  - `MenuItem`Bastırıcıya [`USP0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0009.md) destek eklendi.  

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Ek [`USP0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0001.md) [`USP0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0002.md) parantezlerle veya yöntem bağımsız değişkenleriyle çalışmayan ve bastırıcılar düzeltildi.
  
  - Unity ayarlarında otomatik yenileme devre dışı bırakılabilirken bile zorunlu varlık veritabanı yenilemesi düzeltildi.

## <a name="2700"></a>2.7.0.0
Yayın tarihi: 23 Haziran 2020

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Unity çözüm ve projeleri yeniden oluştururken çözüm klasörlerini kalıcı yapmak için destek eklendi.

  - Tanılama [`UNT0015`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0015.md) eklendi. veya özniteliğiyle yanlış yöntem `InitializeOnLoadMethod` imzasını `RuntimeInitializeOnLoadMethod` algıla.

  - Tanılama [`UNT0016`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0016.md) eklendi. İlk `Invoke` bağımsız değişken dize değişmez değeri olan , veya kullanmak tür için güvenli `InvokeRepeating` `StartCoroutine` `StopCoroutine` değildir.

  - Tanılama [`UNT0017`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0017.md) eklendi. `SetPixels` çağrı yavaş.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Hata ayıklayıcı:**

  - Oyun eski çalışma sırasında kesme noktaları oluşturma Mono çalışma zamanı (Kesme noktası oluşturulur oluşturulmaz bağlamaya çalışıldı). 
  
- **Entegrasyon:**

  - Unity ileti sihirbazında iletileri filtrelerken seçimi sıfırlamayın.
  
  - , ve bastırıcıları şu kurallarla düzeltildi: SerializeField özniteliğiyle dekore edilmiş tüm alanlar için gizleme [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0004.md) [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) `IDE0044` `IDE0051` (salt okunur), `CS0649` (kullanılmayan), (hiçbir zaman atanmamış). `Unity.Object` öğesini genişleten her türdeki genel alanlar için `CS0649` (hiçbir zaman atanmamış) öğesini gizleyin.

  - için genel tür parametre denetimi [`UNT0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0014.md) düzeltildi.

- **Değerlendirme:**

  - Sabit numaralarla eşitlik karşılaştırması düzeltildi.

## <a name="2610"></a>2.6.1.0
Yayın tarihi: 19 Mayıs 2020

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Unity tarafında mesajlaşma sunucusu oluşturamadığımız için uyar.

  - Basit derleme sırasında çözümleyicileri düzgün çalıştırın.

  - Unity Hub yüklemeleriyle API belgeleri düzeltildi.
  
  - Hata ayıklayıcı görselleştiricisi kilitlenmeleri düzeltildi.

## <a name="2600"></a>2.6.0.0
Yayın tarihi: 14 Nisan 2020

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Tanılama [`UNT0012`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0012.md) eklendi. içinde coroutines çağrılarını algıla ve `StartCoroutine()` sarmala.

  - Tanılama [`UNT0013`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0013.md) eklendi. Geçersiz veya yedekli özniteliği algıla ve `SerializeField` kaldır.

  - Tanılama [`UNT0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0014.md) eklendi. Bileşen `GetComponent()` olmayan veya Arabirim Türü olmayan çağrılır.

  - için [`USP0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0009.md) suppressor `IDE0051` eklendi. Özniteliği olan veya özniteliği kullanılmayan bir alan tarafından `ContextMenu` başvurulan yöntemlere `ContextMenuItem` bayrak asma.

  - için [`USP0010`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0010.md) suppressor `IDE0051` eklendi. özniteliğine sahip alanlara kullanılmayan `ContextMenuItem` bayrağını attırma.

  - için [`USP0011`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0011.md) suppressor `IDE0044` eklendi. Salt okunur özniteliğine sahip `ContextMenuItem` alanlar yapma.

  - [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0004.md), [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) ve artık hem hem de öznitelikleri için [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) `SerializeReference` `SerializeField` çalışıyor.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Unity'ye yalnızca Düzenleyici iletişim kurayken başlatma/durdurma komutları gönderin.

  - Devralınan iletilere sahip QuickInfo belgeleri düzeltildi.

  - İletinin ileti kapsamı `CreateInspectorGUI` düzeltildi.

  - Çok [`UNT0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0001.md) biçimli değiştiriciler ile yöntemleri bildirme.

- **Değerlendirme:**

  - Diğer ad kullananların işlenmesi düzeltildi.
  
  - Null değerlerin işlenmesi düzeltildi.  

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

  - Derleme dosya adına yanlışlıkla eklenmiş ek .dll uzantısı düzeltildi.

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
