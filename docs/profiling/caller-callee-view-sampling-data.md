---
title: Arayan - Callee View - Örnekleme Verileri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Caller/Callee view
- Caller/Callee view
ms.assetid: 28e85ed5-1512-4b59-bb84-138a2abca7dd
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 008aa6bd9402cde760ffc61a613aba778c8ec96f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773276"
---
# <a name="callercallee-view---sampling-data"></a>Arayan/Callee görünümü - veri örneklemesi
Arayan/Callee görünümü, seçili bir işlev ve üst ve alt işlevleri için profil oluşturma bilgilerini görüntüler. Arayan/Callee görünümü üç ızgara içerir.

 **Geçerli işlev** orta kılavuzda görüntülenir ve seçili işleviçin profil oluşturma bilgilerini gösterir. Değerler, işleve örneklenmiş tüm çağrıları içerir.

 **Geçerli işlev olarak adlandırılan işlevler** üst kılavuzda görüntülenir ve arayan (üst) işlevlerin seçili (geçerli) işlevdeğerlerine bireysel katkılarını gösterir.

 **Geçerli işlev tarafından çağrılan işlevler** alt kılavuzda görüntülenir ve alt işlev geçerli işlev tarafından çağrıldığında seçili işlevin callee (alt) işlevleri için profil oluşturma bilgilerini gösterir.

> [!NOTE]
> Windows 8 ve Windows Server 2012'deki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturucusu bu platformlarda veri toplama şeklinde önemli değişiklikler gerektiriyordu. UWP uygulamaları da yeni toplama teknikleri gerektirir. [Bkz. Windows 8 ve Windows Server 2012 uygulamalarında Performans araçları.](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)

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
|**Tür**|Fonksiyonun bağlamı:<br /><br /> -   **0** - geçerli fonksiyon<br />-   **1** - geçerli işlevi çağıran bir işlev<br />-   **2** - geçerli işlev tarafından çağrılan bir işlev|
|**Kök Fonksiyon Adı**|Geçerli işlevin adı.|
|**Dahil Örnekler**|- Geçerli işlev için, bu işlev veya alt işlevlerinden biri yürütülmesine rağmen toplanan örnek sayısı.<br />- Bir arayan işlevi için, bu işlev geçerli işlevi aradığında toplanan geçerli işlevin kapsayıcı örneklerinin sayısı.<br />- Bir callee işlevi için, geçerli işlev bu işlevi aradığında toplanan bu işlevin kapsayıcı örneklerinin sayısı.|
|**Kapsayıcı Örnekler %**|Profil oluşturma çalışmasındaki tüm örneklerin yüzdesi, bu işlevin kapsayıcı örnekleriydi.|
|**Özel Örnekler**|- Geçerli işlev için, bu işlev doğrudan yürütüldüğünde toplanan profil oluşturma çalışmasındaki örnek sayısı; diğer bir tarihte, bu işlev çağrı yığınının en üstündeyken. Bu işlevin alt işlevleri yürütüldüğünde toplanan örnekler münhasır sayımlarda sayılmaz.<br />- Bir arayan işlevi için, bu işlev geçerli işlevi aradığında toplanan geçerli işlevin özel örneklerinin sayısı.<br />- Bir callee işlevi için, geçerli işlev bu işlevi aradığında toplanan bu işlevin özel örneklerinin sayısı.|
|**Özel Örnekler %**|Profil oluşturma çalışmasındaki tüm örneklerin yüzdesi, bu işlevin özel örnekleriydi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Arayan/Callee görünümü - .NET bellek örnekleme verileri](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)
- [Arayan/Callee görünümü - .NET bellek enstrümantasyon verileri](../profiling/caller-callee-view-net-memory-instrumentation-data.md)
- [Arayan/Callee görünümü - enstrümantasyon verileri](../profiling/caller-callee-view-instrumentation-data.md)
