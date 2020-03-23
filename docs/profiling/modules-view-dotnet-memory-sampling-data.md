---
title: Modülgörünümü - .NET Bellek Örnekleme Verileri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Modules view
ms.assetid: 9c05b51a-8382-44cf-a8f7-3fabdd2e8f1b
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 9d0d9b7ab681a266115673b48f2c2604c5ff869c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772733"
---
# <a name="modules-view---net-memory-sampling-data"></a>Modülgörünümü - .NET bellek örnekleme verileri
Örnekleme yöntemi kullanılarak toplanan .NET bellek ayırma verilerinin modülgörünümü, bellek verilerini profil oluşturma çalışmasında yürütülen modüller tarafından gruplandırır. Her modül hiyerarşik bir ağacın köküdür. Modülün işlevleri modül düğümünün altında listelenir.

 Bellek ayıran ifadelerin kaynak dosya satırı numaraları işlev düğümü altında listelenir ve ayırma yapmak yönergelerin adresleri satır düğümü altında listelenir. Satır verileri ve talimat verileri için kapsayıcı ve özel değerler her zaman aynıdır.

|Sütun|Açıklama|
|------------|-----------------|
|**Adı**|Modülün adı, işlevi, satır numarası veya talimat adresi.|
|**İşlem Kimliği**|Profil oluşturma çalışmasının işlem kimliği (PID).|
|**İşlem Adı**|Sürecin adı.|
|**Modül Adı**|İşleviçeren modülün adı.|
|**Modül Yolu**|Modülün yolu.|
|**Kaynak Dosya**|Bu işlevin tanımını içeren kaynak dosya.|
|**Fonksiyon Satır Numarası**|Kaynak dosyadaki bu işlevin başlangıcının satır numarası.|
|**Kapsayıcı Tahsisatlar**|- Bir işlev için, işlev tarafından oluşturulan nesnelerin toplam sayısı. Sayı, bu işlev tarafından çağrılan işlevlerde oluşturulan nesneleri içerir.<br />- Bir modül için, modülden en az bir işlev yürütülerken ayrılan profil oluşturma çalışmasındaki nesne sayısı. Sayı, modül işlevleri tarafından çağrılan işlevlerde oluşturulan nesneleri içerir.<br />- Bir satır veya yönerge için, satır veya yönerge tarafından ayrılan nesnelerin toplam sayısı.|
|**Kapsayıcı Tahsisler %**|Profil oluşturma çalışmasında ayrılan tüm nesnelerin yüzdesi, modülün, işlevin, çizginin veya yönergenin kapsayıcı ayırmalarıdır.|
|**Özel Tahsisler**|- Geçerli işlev için, işlev işlev gövdesinin kodunu yürütürken oluşturulan nesnelerin sayısı (diğer bir süre, işlev çağrı yığınının en üstündeyken). Sayı, bu işlev tarafından çağrılan işlevlerde oluşturulan nesneleri içermez.<br />- Bir modül için, modüldeki fonksiyonların münhasır tahsisatlarının toplamı.<br />- Bir satır veya yönerge için, bu satır veya yönerge tarafından oluşturulan nesnelerin toplam sayısı.|
|**Özel Tahsisatlar %**|Profil oluşturma çalışmasında ayrılan tüm nesnelerin yüzdesi, modülün, işlevin, çizginin veya talimatın özel ayırmalarıdır.|
|**Dahil Baytlar**|- Bir işlev için, işlev tarafından ayrılan bayt sayısı. Sayı, bu işlev tarafından çağrılan işlevlerde ayrılan baytları içerir.<br />- Bir modül için, modülden en az bir işlev yürütülerken ayrılan profil oluşturma çalışmasında ayrılan bayt sayısı. Sayı, modül işlevleri tarafından çağrılan tüm işlevlerde oluşturulan nesneleri içerir.<br />- Bir satır veya yönerge için, satır veya yönerge tarafından oluşturulan nesnelerin toplam sayısı.|
|**Dahil Bayt %**|Modül, işlev, çizgi veya yönergeden oluşan profil oluşturma çalışmasında ayrılan tüm baytların yüzdesi.|
|**Özel Baytlar**|- Bir işlev için, işlev tarafından ayrılan bayt ların toplam sayısı. Sayı, bu işlev tarafından çağrılan işlevlerde ayrılan baytları içermez.<br />- Bir modül için, modüldeki fonksiyonlar tarafından ayrılan münhasır baytların toplamı.<br />- Bir satır veya yönerge için, bu satır veya yönerge tarafından ayrılan nesnelerin toplam sayısı.|
|**Özel Bayt %**|Profil oluşturma çalışmasında ayrılan ve modül, işlev, çizgi veya yönergeye özel baytlar olarak ayrılan tüm baytların yüzdesi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kullanılır: Rapor Görünümü sütunlarını özelleştir](../profiling/how-to-customize-report-view-columns.md)
- [Modülgörünümü - enstrümantasyon](../profiling/modules-view-dotnet-memory-instrumentation-data.md)
- [Modüller Görünümü](../profiling/modules-view-sampling-data.md)
- [Modüller Görünümü](../profiling/modules-view-instrumentation-data.md)
