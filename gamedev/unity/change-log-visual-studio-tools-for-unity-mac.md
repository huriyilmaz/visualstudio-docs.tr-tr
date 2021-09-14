---
title: değişiklik günlüğü (Unity için Visual Studio Araçları, Mac) | Microsoft Docs
description: Unity için Visual Studio Araçları, Mac için değişiklik günlüğünü görüntüleyin. 2.7.0.0 ve dışında 1.0.0.0 sürümündeki değişikliklere bakın.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725505"
---
# <a name="change-log-visual-studio-tools-for-unity-mac"></a>Değişiklik Günlüğü (Unity için Visual Studio Araçları, Mac)

Unity için Visual Studio Araçları değişiklik günlüğü.

## <a name="21020"></a>2.10.2.0
Yayın 2 Haziran 2021

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - [`UNT0024`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0024.md)Tanılama eklendi. Vektör hesaplamaları üzerinde skalar hesaplamalar için öncelik verin.

- **Değerlendirmesinin**

  - Görünür yerelleri düzgün filtrelemek için taşınabilir pdb sembolleri kullanma desteği eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Son Unity sürümleriyle ayrıştırma ile sabit oynatıcı duyurusu.

## <a name="21010"></a>2.10.1.0
Piyasaya sürüldü 11 Mayıs 2021

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Hızlı düzeltme ile düzeltilen kararlılık sorunları [`UNT0008`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0008.md) .

  - İş parçacıklarında düzeltilen performans sorunları.

  - Hata listesindeki gizlenen uyarılar ve hatalar düzeltildi.

  - Unity arka plan işlemlerinde sabit filtreleme.

## <a name="21000"></a>2.10.0.0
Yayın tarihi, 13 Nisan 2021

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - [`UNT0019`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0019.md)Tanılama eklendi. İçin gereksiz yöneltme çağrısı `GameObject.gameObject` .

  - [`UNT0020`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0020.md)Tanılama eklendi. `MenuItem` statik olmayan yöntemde kullanılan öznitelik.

  - [`UNT0021`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0021.md)Tanılama eklendi. Unity iletisi korunmalıdır (OPT).

  - [`UNT0022`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0022.md)Tanılama eklendi. Konum ve döndürme ayarlamak için verimsiz yöntem.

  - [`UNT0023`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0023.md)Tanılama eklendi. Unity nesnelerinde birleştirme ataması.

  - [`USP0017`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0017.md)İçin Suppressor eklendi `IDE0074` . Unity nesneleri birleştirme atamasını kullanmamalıdır.

## <a name="2940"></a>2.9.4.0
Yayın tarihi, 6 Nisan 2021

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Test numaralandırmasındaki sorunları çözme

## <a name="2930"></a>2.9.3.0
Yayımlanma tarihi, 30 Mart 2021

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Test Çalıştırıcısı sorunlarını giderme 

## <a name="2920"></a>2.9.2.0
Yayımlanma tarihi 2 Mart 2021

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Unity ileti iletişim kutusunda sabit arama vurgulaması.

  - Unity proje TreeView ile ilgili sabit kararlılık sorunları.

- **Masının**

  - Koşullu kesme noktalarının sabit işlenmesi.

## <a name="2910"></a>2.9.1.0
Yayın tarihi 9 Şubat 2021

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - IDE 'den Unity testlerini çalıştırmaya ve hata ayıklamaya yönelik destek eklendi

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

  - Unity iletisi iletişim kutusuyla ilgili sabit kararlılık sorunları

  - TRK dil olmayan dillerde çeşitli kullanıcı arabirimi sorunları düzeltildi.

  - Tanılama ile ilgili sabit kararlılık sorunları [`UNT0018`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0018.md) .

- **Masının**

  - Yöntemler kullanılırken sabit VM bağlantısı kesme sorunları `Trace` .

- **Değerlendirmesinin**

  - Geçersiz özellikleri oluşturan özel durumlar düzeltildi.

## <a name="2900"></a>2.9.0.0
Yayın 20 Ocak 2021

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - `raytrace shaders`Ve dosyaları için destek `UXML` eklendi `USS` .

  - Unity iletileri API 'SI güncelleştirildi (eş yordam olarak kullanılan tüm yöntemler için).

  - Android SDK algılaması güncelleştirildi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Sabit [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0006.md) tanı, corlar ve için yanlış uyarılar veriliyor `AssetPostprocessor.OnAssignMaterialModel` .

## <a name="2840"></a>2.8.4.0
Yayın tarihi, 15 Aralık 2020

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Unity olay oluşturma Sihirbazı kapatılırken bir güvenilirlik sorunu düzeltildi.

## <a name="2830"></a>2.8.3.0
Yayın tarihi 10 Kasım 2020

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Sý**

  - Çözümde bir VSTU projesi olmasa bile Unity 'ye ekleme düzeltildi.

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
5 Ağustos 2020'de yayınlandı

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Unity iletileri API'si 2019.4'e güncelleştirildi.

  - için [`USP0013`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0013.md) suppressor `CA1823` eklendi. veya özniteliklerine `SerializeField` sahip özel alanlar `SerializeReference` kullanılmamış (FxCop) olarak işaretlendi değil.
  
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
  
  - Null değerlerin işlenmesi düzeltildi.  

## <a name="2520"></a>2.5.2.0

Yayın tarihi: 23 Mart 2020

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Hata ayıklayıcı:**

  - Eklemeden sonra iş parçacıklarının kaydı düzeltildi.

## <a name="2510"></a>2.5.1.0

Yayın tarihi: 3 Mart 2020

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - için [`USP0008`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0008.md) suppressor `IDE0051` eklendi. Invoke, InvokeRepeating, StartCoroutine veya StopCoroutine ile kullanılan özel yöntemler kullanılmamış olarak işaretlanmaz.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - OnDrawGizmos/OnDrawGizmosSelected belgeleri düzeltildi.

- **Değerlendirme:**

  - Lambda bağımsız değişken denetimi düzeltildi.

## <a name="2501"></a>2.5.0.1

Yayın tarihi: 19 Şubat 2020

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Hatalı [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0006.md) ileti imzası için tanılama denetimi düzeltildi. Birden çok devralma düzeyine sahip türleri incelerken, bu tanılama şu iletiyle başarısız olabilir: `warning AD0001: Analyzer 'Microsoft.Unity.Analyzers.MessageSignatureAnalyzer' threw an exception of type 'System.ArgumentException' with message 'An item with the same key has already been added` .

## <a name="2500"></a>2.5.0.0

Yayın tarihi: 22 Ocak 2020

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - HLSL dosyaları için destek eklendi.
  
  - Yeni bir klasör iletişim kutusu kullanıcı arabirimine geçiş.
  
  - Ayarlar için yeni bir erişilebilir özellik kılavuzuna geçiş.

  - için [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) suppressor `IDE0051` eklendi. özniteliğine sahip `SerializeField` özel alanlar kullanılmamış olarak işaretlendi değil.

  - için [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) suppressor `CS0649` eklendi. özniteliğine `SerializeField` sahip alanlar atanmamış olarak işaretlendi değil.  

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Proje oluşturma düzeltildi ( `GenerateTargetFrameworkMonikerAttribute` hedef her zaman doğru şekilde yer alammıştı).

- **Değerlendirme:**

  - Dize değerlendirmesi düzeltildi (ToString() çağrıları kullanmıyor)

## <a name="2420"></a>2.4.2.0

Yayın tarihi: 3 Aralık 2019

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Kullanıcı tanımlı arabirimlerle tanılama düzeltildi.

  - Hatalı biçimlendirilmiş ifadelerle hızlı araç ipucu düzeltildi.
  
## <a name="2410"></a>2.4.1.0

Yayın tarihi: 6 Kasım 2019

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Unity arka plan işlemleri için destek eklendi. (Hata ayıklayıcı, alt işlem yerine ana işleme otomatik olarak bağlanabilecektir).

  - Unity iletileri için ilişkili belgeleri görüntüleyen hızlı bir araç ipucu eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Gelişmiş ikili ve çağırma `UNT0002` ifadeleriyle etiket karşılaştırma çözümleyicisi düzeltildi.

### <a name="deprecated-features"></a>Kullanım Dışı Özellikler

- **Entegrasyon:**

  - Daha sonra Unity için Visual Studio Araçları 2017+ Visual Studio destekleye devam edeceğiz.

## <a name="2400"></a>2.4.0.0

Yayın tarihi: 15 Ekim 2019

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Tüm [`USP0005`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0005.md) Unity iletileri için `IDE0060` (kullanılmayan parametre) suppressor eklendi.

  - ile etiketlenmiş alanlar için hızlı bir araç ipucu `TooltipAttribute` eklendi. (Bu, bu alanı kullanan basit bir get erişimcisi için de çalışır).

## <a name="2330"></a>2.3.3.0

Yayın tarihi: 23 Eylül 2019

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - IDE'nin kullanılmayan parametreleri kaldırmak için hızlı düzeltme göstermesini önlemek için IDE0060 için yeni bir bastırıcı eklendi.
    - `USP0005` için: `IDE0060` Unity iletileri Unity çalışma zamanı tarafından çağrılır.

## <a name="2320"></a>2.3.2.0

Yayın tarihi: 16 Eylül 2019

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Unity'ye özgü yeni tanılamalar ekleyerek Unity Visual Studio için sahip olduğu bilgileri derinden ekledik. Unity projeleri için geçerli olmayan genel C# tanılamalarını gizleyerek IDE’yi daha akıllı hale getirdik. Örneğin, IDE bir denetçi değişkenlerini değiştirmek için bir hızlı düzeltme göstermez ve bu da Unity Düzenleyicisi'nde değişkeni `readonly` değiştirmenizi önler.
    - `UNT0001`: Unity iletileri boş olsalar bile çalışma zamanı tarafından çağrılır, Unity çalışma zamanı tarafından gereksiz işlemeyi önlemek için bunları bildirin.
    - `UNT0002`: Dize eşitliği kullanarak etiket karşılaştırması, yerleşik CompareTag yönteminden daha yavaştır.
    - `UNT0003`: Tür güvenliği için GetComponent genel formunun kullanımı tercih edilir.
    - `UNT0004`: Güncelleştirme iletisi kare hızına bağlıdır ve Time.fixedDeltaTime yerine Time.deltaTime kullan gerekir.
    - `UNT0005`: FixedUpdate iletisi kare oranından bağımsızdır ve Time.deltaTime yerine Time.fixedDeltaTime kullandır.
    - `UNT0006`: Bu Unity iletisi için yanlış bir yöntem imzası algılandı.
    - `UNT0007`: Unity, Unity nesneleri için null karşılaştırma işlecinin null birliğine dönüştürmeyle uyumsuz olduğunu geçersiz kılar.
    - `UNT0008`: Unity, Unity nesneleri için null yayma ile uyumsuz olan null karşılaştırma işlecini geçersiz kılar.
    - `UNT0009`: InitializeOnLoad özniteliğini bir sınıfa uygularken statik bir oluşturucu sağlamanız gerekir. InitializeOnLoad özniteliği, düzenleyici başlatıldığında bunun çağrılmasını sağlar.
    - `UNT0010`: MonoBehaviours yalnızca AddComponent() kullanılarak oluşturulacak. MonoBehaviour bir bileşendir ve bunun GameObject’e eklenmesi gerekir.
    - `UNT0011`: ScriptableObject yalnızca CreateInstance() kullanılarak oluşturul olmalıdır. Unity ileti yöntemlerinin işlenmesi için ScriptableObject’in Unity altyapısı tarafından oluşturulması gerekir.
    - `USP0001` için: `IDE0029` Unity nesneleri null birliğine dönüştürme kullanmamalı.
    - `USP0002` için: `IDE0031` Unity nesneleri null yayma kullanmaz.
    - `USP0003` için: `IDE0051` Unity iletileri Unity çalışma zamanı tarafından çağrılır.
    - `USP0004` for: `IDE0044` SerializeField özniteliğine sahip alanlar salt okunur hale getirilene sahip değildir.

## <a name="2310"></a>2.3.1.0

Yayın tarihi: 4 Eylül 2019

### <a name="new-features"></a>Yeni Özellikler

- **Değerlendirme:**

  - Daha iyi tür görüntüleme için destek eklendi, örneğin `List<object>` yerine `List'1[[System.Object, <corlib...>]]` .

  - İşaretçi üyesi erişimi için destek eklendi, örneğin `p->data->member` .

  - Dizi başlatıcılarında örtülü dönüştürme desteği eklendi, örneğin `new byte [] {1,2,3,4}` : .

  - Byte dizileri ve dizeleri incelerken onaltılık düzenleyici desteği eklendi.

## <a name="2300"></a>2.3.0.0

Yayın tarihi: 13 Ağustos 2019

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Değerlendirme:**

  - Özel durumlarla ilgili adımlama sorunları düzeltildi.

  - Sahte tanımlayıcıların (örneğin, $exception).

  - Geçersiz adresler iptal edilirken kilitlenmeyi önle.  

  - Kaldırılan appdomains ile ilgili sorun düzeltildi.

## <a name="2200"></a>2.2.0.0

Yayın tarihi: 25 Temmuz 2019

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Değerlendirme:**

  - IntPtr türleriyle denetim düzeltildi.

- **Hata ayıklayıcı:**

  - Yakalama noktaları ve işlev kesme noktaları düzeltildi.

## <a name="2130"></a>2.1.3.0

Yayın tarihi: 9 Temmuz 2019

### <a name="new-features"></a>Yeni Özellikler

- **Hata ayıklayıcı:**

  - Özel durumların alt sınıflarını yakalamak için destek eklendi.

  - 2.51 AVH için destek eklendi.

- **Entegrasyon:**

  - Asmdef dosyaları için destek eklendi.

  - Şablondan bir dosya ekleniyorsa (Unity Düzenleyicisi davranışını taklit etmek için) yeniden adlandırma moduna geçiş.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Unity Players ile iletişim kurarken hatalı biçimlendirilmiş iletilerin işlenmesi düzeltildi.

- **Değerlendirme:**

  - İfadelerde ad alanlarının işlenmesi düzeltildi.

## <a name="2120"></a>2.1.2.0

Yayın tarihi: 2 Temmuz 2019

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Değerlendirme:**

  - Ayrıştırılamaz ifadelerle hata raporlama düzeltildi.

## <a name="2110"></a>2.1.1.0

Yayın tarihi: 27 Haziran 2019

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - MonoBehaviour API'si 2019.1'e güncelleştirildi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Unity Project Explorer performansı düzeltildi.

  - Basit derleme etkinleştirildiğinde çıkış için raporlama uyarıları ve hataları düzeltildi.

  - Basit derleme performansı düzeltildi.

## <a name="2100"></a>2.1.0.0

Yayın tarihi: 20 Haziran 2019

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - IntelliSense hataları ve uyarılarını kullanmak yerine Unity projeleri için tam derleme devre dışı bırakıldı. Aslında Unity, Unity Visual Studio yaptığı işi temsil eden sınıf kitaplığı projeleriyle birlikte bir çözüm oluşturur. Bununla birlikte derleme işlem hattı kapatılan Visual Studio unity tarafından hiçbir zaman kullanılmaz veya toplanmayacak. Bu Visual Studio yalnızca kaynakları hiçbir şey için tüketmektir. Tam derlemeye ihtiyacınız varsa, buna bağlı araçlar veya bir kurulum varsa, bu iyileştirmeyi (Unity için Ayarlar/Araçlar/Projelerin tam derlemesini devre dışı bırak) devre dışı abilirsiniz.
  
  - UPE'de Unity paketleri için destek eklendi. Yalnızca Başvurulan paketler (klasöründe manifest.json kullanılarak) ve `Packages` Yerel paketler (klasöre `Packages` eklenmiş) görünür.

## <a name="2021"></a>2.0.2.1

Yayın tarihi: 30 Mayıs 2019

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Unity yürütme hedefleri için özel simge eklendi.

## <a name="2020"></a>2.0.2.0

Yayın tarihi: 2 Nisan 2019

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Kaydetme sırasında Unity'nin varlık veritabanını otomatik olarak yenileme desteği eklendi. Bu varsayılan olarak etkindir ve bir betik bir betik Visual Studio. Kaydetme sırasında Unity\Refresh Unity'nin AssetDatabase'i için Araçlar\Seçenekler\Araçlar'da bu özelliği devre dışı dilersiniz.

  - Çevrimdışı belgeler için tercih edilen Unity yüklemesini ayarlama desteği eklendi.

  - Yeni Düzenleyici için bağlam menüsü eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Hata ayıklayıcı:**

  - Boş çerçevelerle derleme filtreleme ve çerçeve denetimi düzeltildi.

## <a name="2011"></a>2.0.1.1
 
 Yayın tarihi: 26 Mart 2019

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Mono'ya bu özel sürüm için geçici olarak varsayılan ve yalnızca kullanılabilir hata ayıklayıcısını yapma.

## <a name="2006"></a>2.0.0.6

Yayın tarihi: 26 Mart 2019

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - "Unity'ye Ekle ve Oynat" desteği eklendi.

## <a name="2005"></a>2.0.0.5

Yayın tarihi: 20 Mart 2019

### <a name="new-features"></a>Yeni Özellikler

- **Project Nesil:**

  - Çözüm dosyasını işlerken dış özellikleri koruma.
  
- **Değerlendirme:**

  - Diğer adlar için destek eklendi (şimdilik yalnızca genel ad alanı). Bu nedenle ifade değerlendiricisi artık global::namespace.type formunu kullanarak türleri kabul ediyor.

  - İşaretçi `pointer[index]` başvuru formuyla benzer olan form desteği `*(pointer+index)` eklendi.

## <a name="2004"></a>2.0.0.4

Yayın tarihi: 5 Mart 2019

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - API `ScriptableObject` güncelleştirildi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Şablonlardan ad alanları kaldırıldı.

## <a name="2003"></a>2.0.0.3
 
 Yayın tarihi: 5 Mart 2019

### <a name="new-features"></a>Yeni Özellikler

- **Project Nesil:**

  - Genel ve serileştirilmiş alanlar artık uyarılara neden olmaz. Bu iletileri oluşturan Unity projelerinde `CS0649` `IDE0051` ve derleyici uyarılarını otomatik olarak bastırmıştık.

- **Entegrasyon:**

  - Bir Unity işleminin daha fazla çalışıyorsa belirli bir örneği ekleme istemi.

- **Değerlendirme:**

  - Yerel işlevler için destek eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Hata ayıklayıcı:**

  - Eski protokol sürümleri kullanırken adlandırılmış bağımsız değişkenler üzerinde özel özniteliğin okunması düzeltildi.

## <a name="2002"></a>2.0.0.2

Yayın tarihi: 4 Şubat 2019

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - MonoBehaviour API'si güncelleştirildi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Hata ayıklayıcı:**

  - Hata ayıklayıcıda ilkel değerlerin ayarı düzeltildi.

## <a name="2001"></a>2.0.0.1

Yayın tarihi: 4 Aralık 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Yükleme paketinin kendi kendine içermesi düzeltildi.

## <a name="2000"></a>2.0.0.0
 Yayın tarihi: 4 Aralık 2018

### <a name="new-features"></a>Yeni Özellikler

- **Hata ayıklayıcı:**

  - Mac'te Unity hata ayıklayıcısı, hata ayıklayıcıdan aynı temel Unity hata ayıklayıcısıyla Windows.

  - İfade değerlendirmesi için Roslyn yerine NRefactory değiştirildi.

  - İşaretçiler için destek eklendi: başvuru, atama ve işaretçi aritmetiği (bunun için hem Unity 2018.2+ hem de yeni çalışma zamanı gereklidir).

  - Dizi işaretçisi görünümü için destek eklendi (C++'da olduğu gibi). Bir işaretçi ifadesi alıp virgül ve görmek istediğiniz öğe sayısını girin.

  - Zaman uyumsuz yapılar için destek eklendi.

  - Sahte değişkenler (özel durum ve nesne tanımlayıcıları) için destek eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Hata ayıklayıcı:**

  - Hatalı biçimlendirilmiş veya desteklenmeyen ifadelerle ifade değerlendirmesi düzeltildi.

## <a name="1700"></a>1.7.0.0

Yayın tarihi: 13 Kasım 2018

### <a name="new-features"></a>Yeni Özellikler

- **Hata ayıklayıcı:**

  - Ekleme iletişim kutusuna daha fazla istemci bilgisi (IP, makine adı) eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Hata ayıklayıcı:**

  - Özellikle 'Unity'ye Ekle'ye basıldı veya oyun yeniden başlatılırken Unity'nin hata ayıklayıcı altyapısıyla iletişim kurmak için kullanılan kitaplıkta Visual Studio veya Unity donması düzeltildi.

- **Entegrasyon:**

  - Başka bir varsayılan düzenleyici seçildiğinde Unity eklenti etkinleştirmesi düzeltildi.

  - Unity dosya şablonu oluşturma düzeltildi.

## <a name="1602"></a>1.6.0.2

Yayın tarihi: 24 Temmuz 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Unity tarafından düzeltilmiştir Unity performans hatası için geçici çözümü geri alın.

## <a name="1601"></a>1.6.0.1

Yayın tarihi: 10 Temmuz 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Gölgelendirici kod renklendirme desteği düzeltildi.

## <a name="1600"></a>1.6.0.0

Yayın tarihi: 26 Haziran 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Sihirbaz:**

  - OnApplicationFocus iletisiyle ilgili yazım hatası düzeltildi.

- **Project Nesil:**

  - Unity performans hatası için geçici çözüm: proje oluşturmada MonoIslands önbelleği.

  - Yeni Unity çalışma zamanı kullanılırken artık taşınabilir pdb'yi mdb'ye dönüştürmiyoruz.

## <a name="1502"></a>1.5.0.2

Yayın tarihi: 18 Nisan 2018

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Temel Gölgelendirici kodu tamamlama desteği eklendi.

  - Gölgelendirici dosyalarında açıklamalarını toplama desteği eklendi.

## <a name="1501"></a>1.5.0.1

Yayın tarihi: 28 Mart 2018

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Unity Project Explorer'da ek şablonlar için destek eklendi.

## <a name="1500"></a>1.5.0.0

Yayın tarihi: 21 Mart 2018

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - USB üzerinden bağlanan Android oyuncularını algılama ve ekleme desteği eklendi.

## <a name="1403"></a>1.4.0.3

Yayın tarihi: 5 Mart 2018

### <a name="new-features"></a>Yeni Özellikler

- **Project Nesil:**

  - Unity 2018.1'de yeni proje oluşturucu desteği eklendi.

- **Entegrasyon:**

  - Ayrılmış ayarlar için seçenek paneli eklendi.

## <a name="1402"></a>1.4.0.2

Yayın tarihi: 24 Ocak 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Project Nesil:**

  - Mono sürümü algılama düzeltildi.

- **Entegrasyon:**

  - 2018.1 ve eklenti etkinleştirme ile ilgili zamanlama sorunları düzeltildi.

  - Yeni bir oynatıcı algılanırken uyarı düzeltildi.

## <a name="1401"></a>1.4.0.1

Yayın tarihi, 23 Ocak 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Çift tıklama üzerinde klasörleri sabit Genişlet/Daralt

## <a name="1400"></a>1.4.0.0

Yayın tarihi, 13 Aralık 2017

### <a name="new-features"></a>Yeni Özellikler

- **Project Mesinden**

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

- **Project Mesinden**

  - Derleme dosya adına yanlışlıkla eklenmiş ek .dll uzantısı düzeltildi.

  - Varsayılan olarak ' true ' olduğundan AllowAttachedDebuggingOfEditor Unity bayrağını zorlamayın.

## <a name="1103"></a>1.1.0.3

Yayın tarihi, 23 Ekim 2017

### <a name="new-features"></a>Yeni Özellikler

- **Project Mesinden**

  - .NET 4,6 profili için destek eklendi.

## <a name="1102"></a>1.1.0.2

Yayın tarihi, 8 Ağustos 2017

### <a name="new-features"></a>Yeni Özellikler

- **Sý**

  - Hangi Unity 'nin iliştirilemiyor olduğundan emin olmak için işleme İliştir iletişim kutusunu başlatın.

- **Project Mesinden**

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

- **Project Mesinden**

  - MCS. rsp dosyalarıyla düzeltilen derleme adı başvuruları.

  - Assembly. JSON derleme birimleri için destek eklendi.

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
