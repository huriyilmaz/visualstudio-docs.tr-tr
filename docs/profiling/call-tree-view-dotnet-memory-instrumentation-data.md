---
title: Çağrı Ağacı Görünümü - .NET Bellek Enstrümantasyon Verileri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Call Tree view
ms.assetid: dd359707-245a-4a36-8305-2e980b9edd53
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 2066959578987e358f8c1c91dcbda1eeb6f79f26
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773603"
---
# <a name="call-tree-view---net-memory-instrumentation-data"></a>Çağrı Ağacı görünümü - .NET bellek enstrümantasyon verileri
Enstrümantasyon yöntemi kullanılarak toplanan .NET bellek ayırma profil oluşturma verilerinin Çağrı Ağacı görünümü, profilli uygulamada geçen işlev yürütme yollarını görüntüler. Ağacın kökü, uygulamanın veya bileşenin giriş noktasıdır. Her işlev düğümü, aradığı tüm işlevleri ve işlevin .NET bellek ve zamanlama verilerini listeler.

 Çağrı Ağacı görünümündeki değerler, çağrı ağacındaki üst işlev tarafından çağrılan işlev örnekleri içindir. Yüzde değerleri, işlev örneği değeri profil oluşturma çalışmasındaki ayırmaların toplam sayısı veya boyutuyla karşılaştırılarak hesaplanır.

## <a name="highlight-the-execution-hot-path"></a>Yürütme sıcak yolunu vurgulayın
 Çağrı Ağacı görünümü, en büyük veya en çok bellek nesnesini oluşturan işlemin veya işlevin yürütme yolunu genişletebilir ve vurgulayabilir. En etkin yolu görüntülemek için, işlemi veya işlevi sağ tıklatın ve ardından **Sıcak Yolu Genişlet'i**tıklatın.

## <a name="set-the-call-tree-root-node"></a>Çağrı Ağacı kök düğümünü ayarlama
 Profil oluşturma çalışmasındaki her işlem kök düğüm olarak görüntülenir. Başlangıç düğümü olarak ayarlamak istediğiniz düğümü sağ tıklatarak ve ardından **Root'u**Ayarla'yı seçerek Çağrı Ağacı görünümünün başlangıç düğümünü ayarlayabilirsiniz.

 Kök düğümünü ayarladığınızda, seçili düğümün alt ağacı dışında görünümdeki diğer tüm girişleri ortadan kaldırırsınız. Kök düğümünü görüntülediğiniz düğüme geri sıfırlayabilirsiniz; Çağrı Ağacı Görünümü penceresinde sağ tıklatın ve **Root'u Sıfırla'yı**seçin.

## <a name="general"></a>Genel

|Sütun|Açıklama|
|------------|-----------------|
|**Fonksiyon Adı**|İşlevin adı.|
|**Fonksiyon Adresi**|Fonksiyonun adresi.|
|**Fonksiyon Satır Numarası**|Kaynak dosyadaki bu işlevin başlangıcının satır numarası.|
|**Çağrı Sayısı**|Bu işleve yapılan toplam arama sayısı.|
|**Kaynak Dosya**|Bu işlevin tanımını içeren kaynak dosya.|
|**Modül Adı**|İşleviçeren modülün adı.|
|**Modül Yolu**|İşleviçeren modülün yolu.|
|**İşlem Kimliği**|Profil oluşturma çalışmasının işlem kimliği (PID).|
|**İşlem Adı**|İşleme atanan ad.|
|**Zaman Özel Sonda Genel**|Enstrümantasyonun neden olduğu bu işlev için gereken süre. Sonda yükü tüm özel zamanlardan çıkarıldı.|
|**Zaman Dahil Prob Genel**|Bu işlev için zaman yükü ve enstrümantasyon neden olduğu alt işlevleri. Sonda yükü her şey dahil zamanlardan çıkarıldı.|
|**Tür**|Fonksiyonun bağlamı:<br /><br /> -   **0** - geçerli fonksiyon<br />-   **1** - geçerli işlevi çağıran bir işlev<br />-   **2** - geçerli işlev tarafından çağrılan bir işlev<br /><br /> Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlarında.|
|**Kök Fonksiyon Adı**|Geçerli işlevin adı. Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlarında.|

## <a name="net-memory-values"></a>.NET bellek değerleri
 Bir işlevin kapsayıcı .NET bellek değerleri, işlev ve işlevler tarafından çağrılan işlevler tarafından oluşturulan nesnelerin sayısını (ayırmalarını) ve boyutunu (baytları) gösterir.

 Özel bellek değerleri, işlev gövdesinde kod tarafından oluşturulan nesnelerin sayısını ve boyutunu gösterir, işlev tarafından çağrılan işlevler tarafından değil.

|Sütun|Açıklama|
|------------|-----------------|
|**Kapsayıcı Tahsisatlar**|Çağrı ağacındaki üst işlev tarafından çağrılan bu işlevin örnekleri tarafından ayrılan nesnelerin sayısı. Bu sayı, alt işlevler tarafından yapılan ayırmaları içerir.|
|**Kapsayıcı Tahsisler %**|Çağrı ağacındaki üst işlev tarafından çağrılan işlev örneklerinin kapsayıcı ayırmaları olan profil oluşturma çalışmasında oluşturulan tüm nesnelerin yüzdesi.|
|**Özel Tahsisler**|Çağrı ağacındaki üst işlev tarafından çağrılan bu işlevin örnekleri tarafından ayrılan nesnelerin sayısı. Bu sayı, alt işlevler tarafından yapılan ayırmaları içermez.|
|**Özel Tahsisatlar %**|Çağrı ağacındaki üst işlev tarafından çağrılan işlev örneklerinin özel ayırmaları olan profil oluşturma çalışmasında oluşturulan tüm nesnelerin yüzdesi.|

## <a name="elapsed-inclusive-values"></a>Geçen kapsayıcı değerler
 Geçen kapsayıcı değerler, bir işlevin çağrı yığınında olduğu zamanı gösterir. Zaman, işlev tarafından çağrılan işlevlerde ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Geçen Kapsayıcı Süre**|Çağrı ağacındaki üst işlev tarafından çağrıldığında bu işleve yapılan tüm çağrıların toplam kapsayıcı süresi.|
|**Geçen Kapsayıcı Süre %**|Çağrı ağacındaki üst işlev tarafından çağrıldığında, bu işlevin toplam geçen kapsayıcı süresi nde harcanan profil oluşturma çalışmasının toplam geçen kapsayıcı süresinin yüzdesi.|
|**Avg Geçen Dahil Süresi**|Çağrı ağacındaki üst işlev tarafından çağrıldığında, bu işleve yapılan çağrının ortalama kapsayıcı süresi.|
|**Max Geçen Dahil Süresi**|Çağrı ağacındaki üst işlev tarafından çağrıldığında bu işleve yapılan çağrının en fazla geçen kapsayıcı süresi.|
|**Min Geçen Kapsayıcı Süre**|Çağrı ağacındaki üst işlev tarafından çağrıldığında, bu işleve yapılan çağrının en az geçen kapsayıcı süresi.|

## <a name="elapsed-exclusive-values"></a>Geçen özel değerler
 Geçen özel değerler, bir işlevin çağrı yığınının üst kısmında doğrudan yürütüldettiği zamanı gösterir. Bu süre, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan aramalarda süreyi içerir. Ancak, zaman işlevi tarafından çağrılan işlevlerde harcanan zamanı içermez.

|Sütun|Açıklama|
|------------|-----------------|
|**Geçen Özel Zaman**|Çağrı ağacındaki üst işlev tarafından çağrıldığında bu işleve yapılan tüm çağrıların toplam geçen özel süresi.|
|**Geçen Özel Zaman %**|Çağrı ağacındaki ana işlev tarafından çağrıldığında, bu işlevin geçen özel süresinde harcanan profil oluşturma çalışmasının toplam geçen özel zamanının yüzdesi.|
|**Avg Geçen Özel Zaman**|Çağrı ağacındaki üst işlev tarafından çağrıldığında, bu işleve yapılan bir çağrının ortalama geçen özel süresi.|
|**Max Geçen Özel Zaman**|Çağrı ağacındaki üst işlev tarafından çağrıldığında bu işleve yapılan bir çağrının en fazla geçen özel süresi.|
|**Min Geçen Özel Zaman**|Çağrı ağacındaki üst işlev tarafından çağrıldığında bu işleve yapılan çağrının en az geçen özel süresi.|

## <a name="application-inclusive-values"></a>Uygulama dahil değerleri
 Uygulama kapsayıcı değerleri, bir işlevin çağrı yığınında olduğu zamanı gösterir. Bu süre, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan aramalarda harcanan zamanı içermez. Zaman, işlev tarafından çağrılan alt işlevlerde harcanan zamanı içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Uygulama Dahil Süresi**|Çağrı ağacındaki üst işlev tarafından çağrıldığında bu işleve yapılan tüm çağrıların toplam uygulama kapsayıcı süresi.|
|**Uygulama Kapsayıcı Süresi %**|Çağrı ağacındaki üst işlev tarafından çağrıldığında, bu işlevin toplam uygulama kapsayıcı süresi içinde harcanan profil oluşturma çalışmasının toplam geçen kapsayıcı süresinin yüzdesi.|
|**Avg Uygulama Dahil Süresi**|Çağrı ağacındaki üst işlev tarafından çağrıldığında bu işleve çağrının ortalama uygulama kapsayıcı süresi.|
|**Max Uygulama Dahil Süresi**|Çağrı ağacındaki üst işlev tarafından çağrıldığında bu işleve yapılan çağrının maksimum uygulama kapsayıcı süresi.|
|**Min Uygulama Dahil Süresi**|Çağrı ağacındaki üst işlev tarafından çağrıldığında bu işleve çağrının minimum uygulama kapsayıcı süresi.|

## <a name="application-exclusive-values"></a>Uygulama özel değerleri
 Uygulama özel değerleri, işlev tarafından çağrılan alt işlevlerde harcanan süre hariç, işlevde harcanan zamanı gösterir. Bu süre, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıları da dışlar.

|Sütun|Açıklama|
|------------|-----------------|
|**Uygulama Özel Zaman**|Çağrı ağacındaki üst işlev tarafından çağrıldığında bu işleve yapılan tüm çağrıların toplam uygulama münhasır süresi.|
|**Uygulama Özel Zaman %**|Çağrı ağacındaki üst işlev tarafından çağrıldığında, bu işlevin toplam uygulama münhasır süresi içinde harcanan profil oluşturma çalışmasının toplam geçen münhasır zamanının yüzdesi.|
|**Avg Uygulama Özel Zaman**|Çağrı ağacındaki üst işlev tarafından çağrıldığında bu işleve yapılan çağrının ortalama uygulama münhasır süresi.|
|**Max Uygulama Özel Zaman**|Çağrı ağacındaki üst işlev tarafından çağrıldığında bu işleve yapılan çağrının maksimum uygulama münhasır süresi.|
|**Min Uygulama Özel Zaman**|Çağrı ağacındaki üst işlev tarafından çağrıldığında bu işleve yapılan çağrının minimum uygulama münhasır süresi.|
