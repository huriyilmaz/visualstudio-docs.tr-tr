---
title: İşlevler görünümü-.NET Bellek Örnekleme verileri | Microsoft Docs
description: Örnekleme yöntemi kullanılarak toplanan .NET bellek ayırma profil oluşturma verilerinin Işlevler görünümü hakkında bilgi alın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: 5d9c6302-2ffd-430e-9535-13ce795f9f7c
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 2fe4f011a88ab4cf293626fe01f708b3cf5bc68f
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801518"
---
# <a name="functions-view---net-memory-sampling-data"></a>İşlevler görünümü-.NET Bellek Örnekleme verileri
Örnekleme yöntemi kullanılarak toplanan .NET bellek ayırma profil oluşturma verilerinin Işlevleri, profil oluşturma çalışması sırasında belleği ayrılan işlevleri listeler ve ayırma boyutunu ve sayısını raporlar.

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
|**Kapsamlı ayırmalar**|Bu işlevde ve onun alt işlevlerinde ayrılan toplam nesne sayısı.|
|**Kapsamlı ayırmalar%**|Bu işlevin kapsamlı ayırmaları olan profil oluşturma çalıştırmasında ayrılan tüm nesnelerin yüzdesi.|
|**Dışlamalı ayırmalar**|İşlev, çağrı yığınının en üstünde doğrudan yürütüldüğü zaman oluşturulan nesne sayısı. Bu sayı alt işlevlerde oluşturulmuş nesneleri içermez.|
|**Dışlamalı ayırmalar%**|Bu işlevin özel ayırmaları olan profil oluşturma çalıştırmasında ayrılan tüm nesnelerin yüzdesi.|
|**Kapsamlı baytlar**|Bu işlev ve alt işlevleri tarafından ayrılan bellek bayt sayısı.|
|**Dahil edilen baytlar%**|Bu işlevin kapsamlı baytları olan profil oluşturma çalıştırmasında ayrılan tüm bellek baytlarının yüzdesi.|
|**Dışlamalı baytlar**|Bu işlev tarafından ayrılan ancak alt işlevlerine göre olmayan belleğin bayt sayısı.|
|**Dışlamalı bayt yüzdesi**|Bu işlevin özel baytları olan profil oluşturma çalıştırmasında ayrılan tüm bellek baytlarının yüzdesi.|

## <a name="see-also"></a>Ayrıca bkz.
- [İşlevler görünümü-izleme](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
- [İşlevler Görünümü](../profiling/functions-view-sampling-data.md)
- [İşlevler Görünümü](../profiling/functions-view-instrumentation-data.md)
