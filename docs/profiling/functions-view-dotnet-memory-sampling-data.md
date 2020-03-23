---
title: Fonksiyonlar Görünümü - .NET Bellek Örnekleme Verileri | Microsoft Dokümanlar
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
ms.openlocfilehash: cce13da0c2dfee61d70da8bc288d1f0ff4690deb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74780045"
---
# <a name="functions-view---net-memory-sampling-data"></a>İşlevler Görünüm - .NET bellek örnekleme verileri
Örnekleme yöntemi kullanılarak toplanan .NET bellek ayırma profil oluşturma verilerinin İşlevler görünümü, profil oluşturma çalışması sırasında belleği ayıran işlevleri listeler ve ayırmaların boyutunu ve sayısını bildirir.

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
|**Kapsayıcı Tahsisatlar**|Bu işlevde ayrılan nesnelerin toplam sayısı ve alt işlevleri.|
|**Kapsayıcı Tahsisler %**|Profil oluşturma çalışmasında ayrılan tüm nesnelerin yüzdesi, bu işlevin kapsayıcı ayırmalarıydı.|
|**Özel Tahsisler**|İşlev çağrı yığınının üst kısmında doğrudan yürütüldüğünde oluşturulan nesnelerin sayısı. Bu sayı, alt işlevlerde oluşturulan nesneleri içermez.|
|**Özel Tahsisatlar %**|Profil oluşturma çalışmasında ayrılan tüm nesnelerin yüzdesi, bu işlevin özel ayırmalarıdır.|
|**Dahil Baytlar**|Bu işlev ve alt işlevleri tarafından ayrılan bellek baytlarının sayısı.|
|**Dahil Bayt %**|Profil oluşturma çalışmasında ayrılan ve bu işlevin kapsayıcı baytları olan tüm bellek baytlarının yüzdesi.|
|**Özel Baytlar**|Bu işlev tarafından ayrılan ancak alt işlevleri tarafından değil, bellek baytlarının sayısı.|
|**Özel Bayt %**|Profil oluşturma çalışmasında ayrılan ve bu işlevin münhasır baytları olan tüm bellek baytlarının yüzdesi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Fonksiyonlar Görünümü - enstrümantasyon](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
- [Fonksiyonlar Görünümü](../profiling/functions-view-sampling-data.md)
- [Fonksiyonlar Görünümü](../profiling/functions-view-instrumentation-data.md)
