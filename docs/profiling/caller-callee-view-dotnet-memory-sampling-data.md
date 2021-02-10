---
title: Caller-Callee görünümü-.NET Bellek Örnekleme verileri | Microsoft Docs
description: Çağıran/çağrılan görünümü, seçilen bir işlev için .NET Bellek Örnekleme verilerini ve Performans Gezgini içindeki üst ve alt işlevlerini görüntüleme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Caller/Callee view
ms.assetid: 36f5b4de-5686-4f40-9e72-f4aee27d833c
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 58236bbacfaa262c23400506cb32331719000b81
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967533"
---
# <a name="callercallee-view---net-memory-sampling-data"></a>Arayan/Aranan görünümü-.NET Bellek Örnekleme verileri
Arayan/çağrılan görünümü seçili bir işlev ve üst ve alt işlevleri için .NET bellek profili oluşturma verilerini görüntüler. Arayan/çağrılan görünümü üç kılavuz içerir.

 **Geçerli işlev** ortadaki kılavuzda görüntülenir ve seçili işlevle ilgili bellek profili oluşturma bilgilerini gösterir. Değerler, işleve tüm örneklenmiş çağrıları içerir.

 **Geçerli işlevi çağıran işlevler** üst kılavuzda görüntülenir ve çağıran (üst) işlevden çağrılar tarafından oluşturulan seçili (geçerli) işlevin değerinin miktarını gösterir.

 **Geçerli işlev tarafından çağrılan işlevler** alt kılavuzda görüntülenir ve alt işlev geçerli işlev tarafından çağrıldığında seçili işlevin aranan (alt) işlevlerine yönelik bellek profili oluşturma verilerini gösterir.

 Bu satırı geçerli işlev haline getirmek için bir arayan veya çağrılan işlev satırına çift tıklayın.

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
|**Tür**|İşlevin bağlamı:<br /><br /> **0** -geçerli işlev<br /><br /> **1** -geçerli işlevi çağıran bir işlev<br /><br /> **2** -geçerli işlev tarafından çağrılan bir işlev<br /><br /> Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlarında.|
|**Düzeyde**|Çağrı ağacındaki işlevin derinliği. Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlarında.|
|**Kapsamlı ayırmalar**|-Geçerli işlev için, profil oluşturma çalıştırmasında işlev tarafından ayrılan nesne sayısı. Bu sayı, çağrılan işlevlerde oluşturulan nesneleri içerir.<br />-Bir çağıran işlevi için, bu işlevden çağrılar tarafından oluşturulan geçerli işlevin dahil olduğu ayırmaların sayısı.<br />-Bir çağrılan işlev için, bu işlevin geçerli işlev tarafından çağrılan örnekleri tarafından ayrılan nesne sayısı. Bu sayı, çağrılan işlev tarafından çağrılan işlevler tarafından yapılan ayırmaları içerir.|
|**Kapsamlı ayırmalar%**|Bu işlevin kapsamlı ayırmaları olan profil oluşturma çalıştırmasında oluşturulan tüm nesnelerin yüzdesi.|
|**Dışlamalı ayırmalar**|-Geçerli işlev için, işlev, işlev gövdesinin kodunu yürütürken oluşturulan nesne sayısı (yani, işlev çağrı yığınının en üstünde olduğunda). Bu sayı, işlev tarafından çağrılan işlevlerde oluşturulmuş nesneleri içermez.<br />-Bir çağıran işlevi için, bu işlevden çağrılar tarafından oluşturulan geçerli işlevin dışlamalı ayırmaların sayısı.<br />-Bir çağrılan işlev için, bu işlevin geçerli işlev tarafından çağrılan örnekleri tarafından oluşturulan nesne sayısı. Numara, çağrılan işlev tarafından çağrılan işlevler tarafından oluşturulan nesneleri içermez.|
|**Dışlamalı ayırmalar%**|Bu işlevin kapsamlı ayırmaları olan profil oluşturma çalıştırmasında oluşturulan tüm nesnelerin yüzdesi.|
|**Kapsamlı baytlar**|-Geçerli işlev için, profil oluşturma çalıştırmasında işlev tarafından ayrılan bellek bayt sayısı. Bu sayı, bu işlev tarafından çağrılan işlevlerde ayrılan belleği içerir.<br />-Çağıran işlevi için, çağıran işlevi tarafından yapılan çağrılardan oluşturulan geçerli işlevin dahil bayt sayısı.<br />-Bir çağrılan işlev için, bu işlevin, geçerli işlevden çağrılar tarafından oluşturulan örnekleri tarafından ayrılan bayt sayısı. Bu sayı, çağrılan işlev tarafından çağrılan işlevler tarafından ayrılan baytları içerir.|
|**Dahil edilen baytlar%**|Bu işlevin kapsamlı ayırmaları olan profil oluşturma çalıştırmasında ayrılan tüm bellek baytlarının yüzdesi.|
|**Dışlamalı baytlar**|-Geçerli işlev için, profil oluşturma çalıştırmasında işlev tarafından ayrılan bellek bayt sayısı. Bu sayı, geçerli işlev tarafından çağrılan işlevler tarafından ayrılan belleği içermez.<br />-Çağıran işlevi için, çağıran işlevden çağrılar tarafından oluşturulan geçerli işlevin özel bayt sayısı.<br />-Bir çağrılan işlev için, geçerli işlevden çağrılar tarafından oluşturulan işlevin örnekleri tarafından ayrılan bayt sayısı. Bu sayı, çağrılan işlev tarafından çağrılan işlevler tarafından ayrılan baytları içermez.|
|**Dışlamalı bayt yüzdesi**|Bu işlevin özel ayırmaları olan profil oluşturma çalıştırmasında ayrılan tüm bellek baytlarının yüzdesi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)
- [Arayan/Aranan görünümü-.NET bellek izleme verileri](../profiling/caller-callee-view-net-memory-instrumentation-data.md)
- [Çağıran/çağrılan görünümü-örnekleme verileri](../profiling/caller-callee-view-sampling-data.md)
- [Arayan/çağrılan görünümü-izleme verileri](../profiling/caller-callee-view-instrumentation-data.md)
