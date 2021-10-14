---
title: Değişiklik Günlüğü (Unity için Visual Studio Araçları, Mac) | Microsoft Docs
description: Mac için değişiklik Unity için Visual Studio Araçları görüntüleme. Sürüm 1.0.0.0 ile 2.7.0.0 ve ötesindeki değişikliklere bakın.
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
ms.openlocfilehash: 2f48e50c6f9f6bb6fd9e7b710944c9da648f714b
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129970808"
---
# <a name="change-log-visual-studio-tools-for-unity-mac"></a>Değişiklik Günlüğü (Unity için Visual Studio Araçları, Mac)

Unity için Visual Studio Araçları günlüğünü değiştirme.

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

  - Unity iletileri API'si güncelleştirildi (coroutine olarak kullanılan tüm yöntemler için).

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
  
  - Ayarlar için yeni bir erişilebilir özellik kılavuzuna geçiş yaptı.

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

  - Unity iletileri için ilişkili belgeleri görüntüleyen bir hızlı araç ipucu eklendi.

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

  - Unity'ye özgü yeni tanılamalar ekleyerek Unity Visual Studio için sahip olduğu bilgileri derinden ekledik. Unity projeleri için geçerli olmayan genel C# tanılamalarını gizleyerek IDE’yi daha akıllı hale getirdik. Örneğin, IDE bir denetçi değişkenlerini değiştirmek için unity düzenleyicisinde değişkeni değiştirmenizi önleyen bir hızlı düzeltme `readonly` göstermez.
    - `UNT0001`: Unity iletileri boş olsalar bile çalışma zamanı tarafından çağrılır, Unity çalışma zamanı tarafından gereksiz işlemeyi önlemek için bunları bildirin.
    - `UNT0002`: Dize eşitliği kullanarak etiket karşılaştırması, yerleşik CompareTag yönteminden daha yavaştır.
    - `UNT0003`: Tür güvenliği için Genel GetComponent formunun kullanımı tercih edilir.
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

  - AVH Protocol 2,51 için destek eklendi.

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

  - sabit Unity Project gezgin performansı.

  - Hafif derleme etkinleştirildiğinde, çıktının düzeltilme uyarıları ve hataları düzeltildi.

  - Sabit basit derleme performansı.

## <a name="2100"></a>2.1.0.0

Yayın tarihi 20 Haziran 2019

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - IntelliSense hatalarının ve uyarılarının kullanımı açısından Unity projelerinin tam derlemesini devre dışı bıraktı. gerçekten unity, dahili olarak hangi Unity 'nin yaptığını temsil eden sınıf kitaplığı projeleriyle Visual Studio bir çözüm oluşturur. bu şekilde, derleme işlem hattı kapalı olduğundan Visual Studio derlemenin sonucu Unity tarafından hiçbir şekilde kullanılmaz veya alınmaz. Visual Studio oluşturma işlemi yalnızca hiçbir şey için kaynakları tüketiyor. kendisine bağlı araçlara veya kuruluma sahip olduğunuz için tam bir yapıya ihtiyacınız varsa, bu iyileştirmeyi devre dışı bırakabilirsiniz (Unity için Ayarlar/tools for projelerin tam derlemesini devre dışı bırakabilirsiniz).
  
  - UPE içinde Unity paketleri için destek eklendi. Yalnızca başvurulan paketler (klasöründe manifest. JSON kullanılarak `Packages` ) ve yerel paketler ( `Packages` klasöre katıştırılmış) görünür.

## <a name="2021"></a>2.0.2.1

Yayımlanma tarihi 30 Mayıs 2019

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - Unity yürütme hedefleri için özel simge eklendi.

## <a name="2020"></a>2.0.2.0

Yayın 2 Nisan 2019

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - Kayıt sırasında Unity 'nin varlık veritabanının otomatik olarak yenilenmesi için destek eklendi. Bu varsayılan olarak etkindir ve Visual Studio bir betiği kaydederken Unity tarafında yeniden derleme tetikleyecektir. Kayıt sırasında Unity 'nin Assetveritabanını yenilemek için Tools\Options\Tools içinde bu özelliği devre dışı bırakabilirsiniz.

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

- **Project Mesinden**

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

- **Project Mesinden**

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

  - Mac üzerindeki Unity hata ayıklayıcı, Windows aynı çekirdek Unity hata ayıklayıcısıyla değiştirildi.

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

  - unity 'nin hata ayıklayıcı altyapısı ile iletişim kurmak için kullanılan kitaplıkta bir kilitlenme düzeltildi, özellikle ' Unity 'ye ekle ' veya oyunu yeniden başlatma sırasında Visual Studio veya Unity dondurma.

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

- **Project Mesinden**

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

  - Unity Project gezgininde ek şablonlar için destek eklendi.

## <a name="1500"></a>1.5.0.0

Yayımlanma tarihi 21 Mart 2018

### <a name="new-features"></a>Yeni Özellikler

- **Tümleştirme**

  - USB üzerinden bağlı Android oyuncularını algılama ve ekleme desteği eklendi.

## <a name="1403"></a>1.4.0.3

Yayımlanma tarihi, 5 Mart 2018

### <a name="new-features"></a>Yeni Özellikler

- **Project Mesinden**

  - Unity 2018,1 ' de yeni proje Oluşturucu desteği eklendi.

- **Tümleştirme**

  - Adanmış ayarlar için seçenek paneli eklendi.

## <a name="1402"></a>1.4.0.2

24 Ocak 2018 ' de yayınlandı

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Project Mesinden**

  - Sabit mono sürümü algılama.

- **Tümleştirme**

  - 2018,1 ve eklenti etkinleştirme ile ilgili sabit zamanlama sorunları.

  - Yeni bir oyuncu algılayan bildirimler düzeltildi.

## <a name="1401"></a>1.4.0.1

Yayın tarihi: 23 Ocak 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Çift tıklamada klasörleri genişletme/daraltma düzeltildi

## <a name="1400"></a>1.4.0.0

Yayın tarihi: 13 Aralık 2017

### <a name="new-features"></a>Yeni Özellikler

- **Project Nesil:**

  - Daha fazla .NET Standard.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Otomatik pdb'den mdb hata ayıklama simgesine dönüştürme düzeltildi.

## <a name="1301"></a>1.3.0.1

Yayın tarihi: 12 Aralık 2017

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Dizi boyutunu değiştirmeye çalışırken EditorPrefs.GetBool'a yapılan dolaylı çağrının denetçiyi etkilemesi düzeltildi.

- **Sihirbaz:**

  - Yöntemi eklemeden önce roslyn bağlamını yenileyin.

## <a name="1300"></a>1.3.0.0

Yayın tarihi: 20 Kasım 2017

### <a name="new-features"></a>Yeni Özellikler

- **Sihirbaz:**

  - "Unity iletisi uygulama" sihirbazı eklendi.

  - Mac için VS 7.4'te yeni tamamlanma API'si desteği eklendi.

## <a name="1200"></a>1.2.0.0

Yayın tarihi: 23 Ekim 2017

### <a name="new-features"></a>Yeni Özellikler

- **Hata ayıklayıcı:**

  - Taşınabilir hata ayıklama sembol dosyaları için destek eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Project Nesil:**

  - Ek .dll derleme dosya adı yanlış eklenmiştir.

  - Varsayılan değer artık 'true' olduğu için AllowAttachedDebuggingOfEditor Unity bayrağını zorlamayın.

## <a name="1103"></a>1.1.0.3

Yayın tarihi: 23 Ekim 2017

### <a name="new-features"></a>Yeni Özellikler

- **Project Nesil:**

  - .NET 4.6 profili için destek eklendi.

## <a name="1102"></a>1.1.0.2

Yayın tarihi: 8 Ağustos 2017

### <a name="new-features"></a>Yeni Özellikler

- **Hata ayıklayıcı:**

  - Hangi Unity'ye ekli olduğundan emin değilsanız işleme ekle iletişim kutusunu açın.

- **Project Nesil:**

  - Unity 5.6 kullanılırken her zaman güvenli olmayan derleme anahtarını etkinleştirin.

## <a name="1101"></a>1.1.0.1

Yayın tarihi: 20 Temmuz 2017

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Yerelleştirilmiş kaynaklar için destek eklendi.

## <a name="1100"></a>1.1.0.0

Yayın tarihi: 12 Temmuz 2017

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - İşleme ekle penceresi aracılığıyla oyunculara ve düzenleyicilere ekleme desteği eklendi.

- **Project Nesil:**

  - mcs.rsp dosyalarıyla derleme adı başvuruları düzeltildi.

  - assembly.json derleme birimleri için destek eklendi.

  - API düzeyleriyle tanımları düzeltildi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Derleme sırasında gölgelendirici hata iletisi düzeltildi.

## <a name="1001"></a>1.0.0.1

Yayın tarihi: 4 Mayıs 2017

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Karma ve normal projelerle etkin belge izleme düzeltildi.

## <a name="1000"></a>1.0.0.0

Yayın tarihi: 3 Mayıs 2017
