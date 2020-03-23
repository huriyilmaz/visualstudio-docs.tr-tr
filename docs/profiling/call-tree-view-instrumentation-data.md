---
title: Çağrı Ağacı Görünümü - Enstrümantasyon Verileri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Call Tree view
ms.assetid: 306bd176-0ce9-4a10-89ca-20b043d37d4e
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 7497f455ad3868f53758555aa28d305b6068e30d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773517"
---
# <a name="call-tree-view---instrumentation-data"></a>Çağrı Ağacı görünümü - enstrümantasyon verileri
Çağrı ağacındaki bir işlevin değerleri, çağrı ağacındaki üst işlev tarafından çağrılan işlev örneklerinin saatini gösterir. Yüzde değerleri, işlev örneklerinin değerini profil oluşturma çalışmasındaki tüm işlevlerin geçen toplam kapsayıcı süresiyle karşılaştırılarak hesaplanır.

## <a name="general"></a>Genel
 Genel sütunlar bir görünüm satırında işlevi tanımlar.

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
|**Zaman Özel Sonda Genel**|Enstrümantasyon nedeniyle bu işlev için zaman yükü. Sonda yükü tüm özel zamanlardan çıkarıldı.|
|**Zaman Dahil Prob Genel**|Bu işlev için zaman yükü ve enstrümantasyon neden olduğu alt işlevleri. Sonda yükü her şey dahil zamanlardan çıkarıldı.|
|**Düzey**|Çağrı ağacındaki işlevin derinliği. Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlarında.|

## <a name="elapsed-inclusive-values"></a>Geçen kapsayıcı değerler
 Geçen kapsayıcı değerler, çağrı ağacındaki üst işlev tarafından çağrılan işlevin bu örneklerinin çağrı yığınındaki zamanı gösterir. Zaman, işlev tarafından çağrılan alt işlevlerde ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Geçen Kapsayıcı Süre**|Bu bağlamda bu işleve yapılan tüm çağrıların toplam kapsayıcı süresi.|
|**Geçen Kapsayıcı Süre %**|Bu bağlamda, bu işlevin toplam geçen kapsayıcı süresi içinde harcanan profil oluşturma çalışmasının toplam geçen kapsayıcı süresinin yüzdesi.|
|**Avg Geçen Dahil Süresi**|Bu bağlamda bu işleve yapılan bir çağrının ortalama kapsayıcı süresi.|
|**Max Geçen Dahil Süresi**|Bu bağlamda bu işleve yapılan bir çağrının en fazla geçen kapsayıcı süresi.|
|**Min Geçen Kapsayıcı Süre**|Bu bağlamda bu işleve yapılan çağrının en az geçen kapsayıcı süresi.|

## <a name="elapsed-exclusive-values"></a>Geçen özel değerler
 Geçen özel değerler, çağrı ağacındaki üst işlev tarafından çağrılan bir işlevin örneklerinin işlev gövdesinde kodu yürütme süresini gösterir; diğer bir zamanda, işlev çağrı yığınının en üstündeyken. Bu süre, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan aramalarda süreyi içerir. Ancak, zaman işlevi tarafından çağrılan alt işlevlerde harcanan zamanı içermez.

|Sütun|Açıklama|
|------------|-----------------|
|**Geçen Özel Zaman**|Bu bağlamda bu işleve yapılan tüm çağrıların toplam geçen özel süresi.|
|**Geçen Özel Zaman %**|Bu bağlamda, bu işlevin toplam geçen özel zamanında harcanan profil oluşturma çalışmasının toplam geçen özel zamanının yüzdesi.|
|**Avg Geçen Özel Zaman**|Bu bağlamda bu işleve yapılan bir çağrının ortalama geçen özel süresi.|
|**Max Geçen Özel Zaman**|Bu bağlamda bu işleve yapılan bir çağrının en fazla geçen özel süresi.|
|**Min Geçen Özel Zaman**|Bu bağlamda bu işleve yapılan bir çağrının minimum geçen özel süresi.|

## <a name="application-inclusive-values"></a>Uygulama dahil değerleri
 Uygulama kapsayıcı değerleri, çağrı ağacındaki üst işlev tarafından çağrılan bir işlevin örneklerinin çağrı yığınında olduğu zamanı gösterir. Zaman, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan aramalarda harcanan zamanı içermez, Ancak, bu süre işlev tarafından çağrılan alt işlevlerde harcanan zamanı içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Uygulama Dahil Süresi**|Bu bağlamda bu işleve yapılan tüm çağrıların toplam uygulama kapsayıcı süresi.|
|**Uygulama Kapsayıcı Süresi %**|Bu bağlamda bu işlevin toplam uygulama kapsayıcı süresi içinde harcanan profil oluşturma çalışmasının toplam geçen kapsayıcı süresiyüzdesi.|
|**Avg Uygulama Dahil Süresi**|Bu bağlamda bu işleve yapılan çağrının ortalama uygulama kapsayıcı süresi.|
|**Max Uygulama Dahil Süresi**|Bu bağlamda bu işleve yapılan bir çağrının maksimum uygulama kapsayıcı süresi.|
|**Min Uygulama Dahil Süresi**|Bu bağlamda bu işleve yapılan çağrının minimum uygulama kapsayıcı süresi.|

## <a name="application-exclusive-values"></a>Uygulama özel değerleri
 Uygulama özel değerleri, çağrı ağacındaki üst işlev tarafından çağrılan bir işlevin örneklerinin işlev gövdesinde doğrudan kodu yürütme süresini gösterir; diğer bir zamanda, işlev çağrı yığınının en üstündeyken. Bu süre, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan aramalarda harcanan zamanı içermez. Ayrıca, işlev tarafından çağrılan alt işlevlerde harcanan zamanı da içermez.

|Sütun|Açıklama|
|------------|-----------------|
|**Uygulama Özel Zaman**|Bu bağlamda bu işleve yapılan tüm çağrıların toplam uygulama münhasır süresi.|
|**Uygulama Özel Zaman %**|Bu bağlamda bu işlevin toplam uygulama münhasır süresi harcanan profil oluşturma çalışmasının toplam geçen özel zaman yüzdesi.|
|**Avg Uygulama Özel Zaman**|Bu bağlamda bu işleve bir çağrının ortalama uygulama münhasır süresi.|
|**Max Uygulama Özel Zaman**|Bu bağlamda bu işleve yapılan bir çağrının maksimum uygulama münhasır süresi.|
|**Min Uygulama Özel Zaman**|Bu bağlamda bu işleve yapılan bir çağrının minimum uygulama münhasır süresi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kullanılır: Rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)
- [Çağrı Ağacı görünümü](../profiling/call-tree-view-sampling-data.md)
- [Çağrı Ağacı görünümü - enstrümantasyon](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)
- [Çağrı Ağacı görünümü - örnekleme](../profiling/call-tree-view-dotnet-memory-sampling-data.md)
