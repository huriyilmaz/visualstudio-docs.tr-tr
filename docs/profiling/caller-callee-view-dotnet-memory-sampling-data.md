---
title: Arayan-Callee Görünümü - .NET Bellek Örnekleme Verileri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Caller/Callee view
ms.assetid: 36f5b4de-5686-4f40-9e72-f4aee27d833c
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 50e278e858ea086c83b29ef4eebf6b48ee8e477e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773315"
---
# <a name="callercallee-view---net-memory-sampling-data"></a>Arayan/Callee görünümü - .NET bellek örnekleme verileri
Arayan/Callee görünümü, seçili bir işlev ve üst ve alt işlevleri için .NET bellek profil oluşturma verilerini görüntüler. Arayan/Callee görünümü üç ızgara içerir.

 **Geçerli işlev** orta kılavuzda görüntülenir ve seçili işlev hakkında bellek profil oluşturma bilgilerini gösterir. Değerler, işleve örneklenmiş tüm çağrıları içerir.

 **Geçerli işlev olarak adlandırılan işlevler** üst kılavuzda görüntülenir ve arayan (üst) işlevinden gelen çağrılar tarafından oluşturulan seçili (geçerli) işlevin değerini gösterir.

 **Geçerli işlev tarafından çağrılan işlevler** alt kılavuzda görüntülenir ve alt işlev geçerli işlev tarafından çağrıldığında seçili işlevin callee (alt) işlevleri için bellek profil oluşturma verilerini gösterir.

 Bu satırı geçerli işlev yapmak için bir arayanın veya callee işlev satırına çift tıklayın.

|Sütun|Açıklama|
|------------|-----------------|
|**İşlem Kimliği**|Profil oluşturma çalışmasının işlem kimliği (PID).|
|**İşlem Adı**|Sürecin adı.|
|**Modül Adı**|İşleviçeren modülün adı.|
|**Modül Yolu**|İşleviçeren modülün yolu.|
|**Kaynak Dosya**|Bu işlevin tanımını içeren kaynak dosya.|
|**Fonksiyon Adı**|İşlevin tam nitelikli adı.|
|**Fonksiyon Satır Numarası**|Kaynak dosyadaki bu işlevin başlangıcının satır numarası.|
|**Fonksiyon Adresi**|Fonksiyonun adresi.|
|**Tür**|Fonksiyonun bağlamı:<br /><br /> **0** - geçerli fonksiyon<br /><br /> **1** - geçerli işlevi çağıran bir işlev<br /><br /> **2** - geçerli işlev tarafından çağrılan bir işlev<br /><br /> Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlarında.|
|**Düzey**|Çağrı ağacındaki işlevin derinliği. Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlarında.|
|**Kapsayıcı Tahsisatlar**|- Geçerli işlev için, profil oluşturma çalışmasında işlev tarafından ayrılan nesnelerin sayısı. Bu sayı, callee işlevlerinde oluşturulan nesneleri içerir.<br />- Bir arayan işlevi için, bu işlevden gelen çağrılar tarafından oluşturulan geçerli işlevin kapsayıcı ayırmalarının sayısı.<br />- Bir callee işlevi için, geçerli işlev tarafından çağrılan bu işlevin örnekleri tarafından ayrılan nesnelerin sayısı. Sayı, callee işlevi tarafından çağrılan işlevler tarafından yapılan ayırmaları içerir.|
|**Kapsayıcı Tahsisler %**|Profil oluşturma çalışmasında oluşturulan tüm nesnelerin yüzdesi, bu işlevin kapsayıcı ayırmalarıydı.|
|**Özel Tahsisler**|- Geçerli işlev için, işlev işlev gövdesinin kodunu yürütürken oluşturulan nesnelerin sayısı (diğer bir süre, işlev çağrı yığınının en üstündeyken). Sayı, işlev tarafından çağrılan işlevlerde oluşturulan nesneleri içermez.<br />- Bir arayan işlevi için, bu işlevden gelen çağrılar tarafından oluşturulan geçerli işlevin özel ayırmalarının sayısı.<br />- Bir callee işlevi için, geçerli işlev tarafından çağrılan bu işlevin örnekleri tarafından oluşturulan nesnelerin sayısı. Sayı, callee işlevi tarafından çağrılan işlevler tarafından oluşturulan nesneleri içermez.|
|**Özel Tahsisatlar %**|Profil oluşturma çalışmasında oluşturulan tüm nesnelerin yüzdesi, bu işlevin kapsayıcı ayırmalarıydı.|
|**Dahil Baytlar**|- Geçerli işlev için, profil oluşturma çalışmasındaki işlev tarafından ayrılan bellek baytlarının sayısı. Sayı, bu işlev tarafından çağrılan işlevlerde ayrılan belleği içerir.<br />- Bir arayan işlevi için, arayan işlevi tarafından yapılan çağrılardan oluşturulan geçerli işlevin kapsayıcı baytlarının sayısı.<br />- Bir callee işlevi için, geçerli işlevden gelen çağrılar tarafından oluşturulan bu işlevin örnekleri tarafından ayrılan bayt sayısı. Sayı, callee işlevi tarafından çağrılan işlevler tarafından ayrılan baytları içerir.|
|**Dahil Bayt %**|Profil oluşturma çalışmasında ayrılan ve bu işlevin kapsayıcı ayırmaları olan tüm bellek baytlarının yüzdesi.|
|**Özel Baytlar**|- Geçerli işlev için, profil oluşturma çalışmasındaki işlev tarafından ayrılan bellek baytlarının sayısı. Bu sayı, geçerli işlev tarafından çağrılan işlevler tarafından ayrılan belleği içermez.<br />- Bir arayan işlevi için, arayan işlevinden gelen aramalar tarafından oluşturulan geçerli işlevin özel bayt sayısı.<br />- Bir callee işlevi için, geçerli işlevden gelen çağrılar tarafından oluşturulan işlev örnekleri tarafından ayrılan bayt sayısı. Sayı, callee işlevi tarafından çağrılan işlevler tarafından ayrılan baytları içermez.|
|**Özel Bayt %**|Profil oluşturma çalışmasında ayrılan ve bu işlevin özel ayırmaları olan tüm bellek baytlarının yüzdesi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kullanılır: Rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)
- [Arayan/Callee görünümü - .NET bellek enstrümantasyon verileri](../profiling/caller-callee-view-net-memory-instrumentation-data.md)
- [Arayan/Callee görünümü - veri örneklemesi](../profiling/caller-callee-view-sampling-data.md)
- [Arayan/Callee görünümü - enstrümantasyon verileri](../profiling/caller-callee-view-instrumentation-data.md)
