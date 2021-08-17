---
title: Arayan-çağrılan görünümü-örnekleme verileri | Microsoft Docs
description: Çağıran/çağrılan görünümünün seçili bir işlev için profil oluşturma bilgilerini ve onun üst ve alt işlevlerini Performans Gezgini nasıl görüntülediğini okuyun.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Caller/Callee view
- Caller/Callee view
ms.assetid: 28e85ed5-1512-4b59-bb84-138a2abca7dd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5a4c00bb9e0e190d165656e691064ee86c3789d46faf22b9c55166ccf092b3ca
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121397039"
---
# <a name="callercallee-view---sampling-data"></a>Çağıran/çağrılan görünümü-örnekleme verileri
Arayan/çağrılan görünümü seçili bir işlev ve üst ve alt işlevleri için profil oluşturma bilgilerini görüntüler. Arayan/çağrılan görünümü üç kılavuz içerir.

 **Geçerli işlev** ortadaki kılavuzda görüntülenir ve seçili işlev için profil oluşturma bilgilerini gösterir. Değerler, işleve tüm örneklenmiş çağrıları içerir.

 **Geçerli işlevi çağıran işlevler** üst kılavuzda görüntülenir ve arayan (ana) işlevlerinin tek tek katkıları seçili (geçerli) işlevin değerlerine gösterilir.

 **Geçerli işlev tarafından çağrılan işlevler** alt kılavuzda görüntülenir ve alt işlev geçerli işlev tarafından çağrıldığında seçili işlevin aranan (alt) işlevlerine ilişkin profil oluşturma bilgilerini gösterir.

> [!NOTE]
> Windows 8 ve Windows Server 2012 gelişmiş güvenlik özellikleri Visual Studio profiler 'ın bu platformlarda verileri topladıkları şekilde gerekli önemli değişikliklere sahiptir. UWP uygulamaları için de yeni koleksiyon teknikleri gerekir. bkz. [Windows 8 ve Windows Server 2012 uygulamalarda performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

|Sütun|Açıklama|
|------------|-----------------|
|**İşlem Kimliği**|Profil oluşturma çalıştırmasının işlem KIMLIĞI (PID).|
|**İşlem adı**|Sürecin adı.|
|**Modül adı**|İşlevi içeren modülün adı.|
|**Modül yolu**|İşlevi içeren modülün yolu.|
|**Kaynak Dosya**|Bu işlevin tanımını içeren kaynak dosya.|
|**İşlev adı**|İşlevin tam adı.|
|**İşlev satır numarası**|Kaynak dosyada bu işlevin başlangıcına ait satır numarası.|
|**İşlev adresi**|İşlevin adresi.|
|**Tür**|İşlevin bağlamı:<br /><br /> -   **0** -geçerli işlev<br />-   **1** -geçerli işlevi çağıran bir işlev<br />-   **2** -geçerli işlev tarafından çağrılan bir işlev|
|**Kök Işlev adı**|Geçerli işlevin adı.|
|**Kapsamlı örnekler**|-Geçerli işlev için, bu işlev veya alt işlevlerinden biri yürütüldüğü halde toplanan örneklerin sayısı.<br />-Çağıran işlevi için, bu işlev geçerli işlevi çağırdığında toplanan geçerli işlevin kapsamlı örnek sayısı.<br />-Bir çağrılan işlev için, bu işlevin, bu işlev çağrıldığında toplanan kapsamlı örnek sayısı.|
|**Kapsamlı örnekler%**|Profil oluşturma çalıştırmasında, bu işlevin kapsamlı örnekleri olan tüm örneklerin yüzdesi.|
|**Dışlamalı örnekler**|-Geçerli işlev için, bu işlev doğrudan çalıştırıldığında toplanan profil oluşturma çalıştırmasında örnek sayısı; diğer bir deyişle, bu işlev çağrı yığınının en üstünde olduğunda. Bu işlevin alt işlevleri yürütüldüğü zaman toplanan örnekler, özel sayımlar halinde sayılmaz.<br />-Çağıran işlevi için, bu işlev geçerli işlevi çağırdığında toplanan geçerli işlevin dışlamalı örnek sayısı.<br />-Bir çağrılan işlev için, bu işlevin geçerli işlev çağrıldığında toplanan dışlamalı örnek sayısı.|
|**Dışlamalı örnekler%**|Bu işlevin özel örnekleri olan profil oluşturma çalıştırmasında tüm örneklerin yüzdesi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Arayan/Aranan görünümü-.NET Bellek Örnekleme verileri](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)
- [Arayan/Aranan görünümü-.NET bellek izleme verileri](../profiling/caller-callee-view-net-memory-instrumentation-data.md)
- [Arayan/çağrılan görünümü-izleme verileri](../profiling/caller-callee-view-instrumentation-data.md)
