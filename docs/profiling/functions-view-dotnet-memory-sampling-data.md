---
title: İşlevler Görünümü - .NET Bellek Örnekleme Veri | Microsoft Docs
description: Örnekleme yöntemi kullanılarak toplanan .NET bellek ayırma profili oluşturma verilerine ilişkin İşlevler görünümü hakkında bilgi alın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: 5d9c6302-2ffd-430e-9535-13ce795f9f7c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 6b4503f2287030158e7790e4def8843ee3c29e0d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122033803"
---
# <a name="functions-view---net-memory-sampling-data"></a>İşlevler Görünümü - .NET bellek örnekleme verileri
Örnekleme yöntemi kullanılarak toplanan .NET bellek ayırma profili oluşturma verilerine ilişkin İşlevler görünümü, profil oluşturma çalıştırması sırasında bellek ayrılan işlevleri listeler ve ayırmaların boyutunu ve sayısını raporlar.

|Sütun|Açıklama|
|------------|-----------------|
|**İşlem Kimliği**|Profil oluşturma çalıştırmanın işlem kimliği (PID).|
|**İşlem Adı**|Sürecin adı.|
|**Modül Adı**|İşlevi içeren modülün adı.|
|**Modül Yolu**|İşlevi içeren modülün yolu.|
|**Kaynak Dosya**|Bu işlevin tanımını içeren kaynak dosya.|
|**İşlev Adı**|İşlevin tam adı.|
|**İşlev Satır Numarası**|Kaynak dosyada bu işlevin başlangıcının satır numarası.|
|**İşlev Adresi**|İşlevin adresi.|
|**Kapsayıcı Ayırmalar**|Bu işlevde ve onun alt işlevlerinde ayrılan nesnelerin toplam sayısı.|
|**Kapsayıcı Ayırma %**|Profil oluşturma çalıştırması içinde ayrılan ve bu işlevin kapsayıcı ayırmaları olan tüm nesnelerin yüzdesi.|
|**Özel Ayırmalar**|İşlev doğrudan çağrı yığınının en üstünde yürütücü olduğunda oluşturulan nesne sayısı. Bu sayı, alt işlevlerde oluşturulan nesneleri içermemektedir.|
|**Özel Ayırma %**|Profil oluşturma çalıştırması içinde ayrılan ve bu işlevin özel ayırmaları olan tüm nesnelerin yüzdesi.|
|**Kapsayıcı Bayt Sayısı**|Bu işlev ve onun alt işlevleri tarafından ayrılan bellek bayt sayısı.|
|**Kapsayıcı Bayt %**|Profil oluşturma çalıştırması içinde ayrılan ve bu işlevin kapsayıcı baytları olan tüm bellek baytlarının yüzdesi.|
|**Özel Bayt Sayısı**|Bu işlev tarafından ayrılan ancak alt işlevleri tarafından ayrılan bellek bayt sayısı.|
|**Özel Bayt %**|Profil oluşturma çalıştırması içinde ayrılan ve bu işlevin özel baytları olan tüm bellek baytlarının yüzdesi.|

## <a name="see-also"></a>Ayrıca bkz.
- [İşlevler Görünümü - ölçüm](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
- [İşlevler Görünümü](../profiling/functions-view-sampling-data.md)
- [İşlevler Görünümü](../profiling/functions-view-instrumentation-data.md)
