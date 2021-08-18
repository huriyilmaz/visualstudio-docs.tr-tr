---
title: Modüller Görünümü - .NET Bellek Örnekleme Verileri | Microsoft Docs
description: Örnekleme yöntemi kullanılarak toplanan .NET bellek ayırma verilerini modüller görünümü hakkında bilgi alın.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Modules view
ms.assetid: 9c05b51a-8382-44cf-a8f7-3fabdd2e8f1b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 1f1fcb71e16daa3cb483f281d2af4130fc676acb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122107359"
---
# <a name="modules-view---net-memory-sampling-data"></a>Modüller Görünümü - .NET bellek örnekleme verileri
Örnekleme yöntemi kullanılarak toplanan .NET bellek ayırma verileri Modüller görünümü, bellek verilerini profil oluşturma çalıştırması içinde yürütülen modüllere göre gruplar. Her modül hiyerarşik ağacın köküdür. Modülün işlevleri modül düğümünün altında listelenir.

 Bellek ayıran deyimlerin kaynak dosya satır numaraları işlev düğümünün altında listelenir ve ayırmayı yapmak için yönergelerin adresleri satır düğümünün altında listelenir. Satır verileri ve yönerge verileri için kapsayıcı ve dış değerler her zaman aynıdır.

|Sütun|Açıklama|
|------------|-----------------|
|**Ad**|Modülün adı, işlev, satır numarası veya yönerge adresi.|
|**İşlem Kimliği**|Profil oluşturma çalıştırmanın işlem kimliği (PID).|
|**İşlem Adı**|Sürecin adı.|
|**Modül Adı**|İşlevi içeren modülün adı.|
|**Modül Yolu**|Modülün yolu.|
|**Kaynak Dosya**|Bu işlevin tanımını içeren kaynak dosya.|
|**İşlev Satır Numarası**|Kaynak dosyada bu işlevin başlangıcının satır numarası.|
|**Kapsayıcı Ayırmalar**|- Bir işlev için, işlev tarafından oluşturulan nesnelerin toplam sayısı. Sayı, bu işlev tarafından çağrılan işlevlerde oluşturulan nesneleri içerir.<br />- Bir modül için, bir profil oluşturma çalıştırması içinde modülden en az bir işlev yürüt yaparken ayrılan nesne sayısı. Sayı, modül işlevleri tarafından çağrılan işlevlerde oluşturulan nesneleri içerir.<br />- Bir satır veya yönerge için, satır veya yönerge tarafından ayrılan toplam nesne sayısı.|
|**Kapsayıcı Ayırma %**|Profil oluşturma çalıştırması içinde ayrılan ve modülün, işlevin, satırın veya yönergenin kapsayıcı ayırmaları olan tüm nesnelerin yüzdesi.|
|**Özel Ayırmalar**|- Geçerli işlev için, işlev işlev gövdesinin kodunu yürütürken oluşturulan nesne sayısı (yani işlev çağrı yığınının en üstündeyken). Sayı, bu işlev tarafından çağrılan işlevlerde oluşturulan nesneleri içermez.<br />- Bir modül için, modülde işlevlerin özel ayırmalarının toplamı.<br />- Bir satır veya yönerge için, bu satır veya yönerge tarafından oluşturulan toplam nesne sayısı.|
|**Özel Ayırma %**|Profil oluşturma çalıştırması içinde ayrılan ve modülün, işlevin, satırın veya yönergenin özel ayırmaları olan tüm nesnelerin yüzdesi.|
|**Kapsayıcı Bayt Sayısı**|- Bir işlev için, işlev tarafından ayrılan bayt sayısı. Sayı, bu işlev tarafından çağrılan işlevlerde ayrılan baytları içerir.<br />- Bir modül için, modülden en az bir işlev yürüt yaparken ayrılan profil oluşturma çalıştırması içinde ayrılan bayt sayısı. Bu sayı, modül işlevleri tarafından çağrılan tüm işlevlerde oluşturulan nesneleri içerir.<br />- Bir satır veya yönerge için, satır veya yönerge tarafından oluşturulan toplam nesne sayısı.|
|**Kapsayıcı Bayt %**|Profil oluşturma çalıştırması içinde ayrılan ve modülün, işlevin, satırın veya yönergenin kapsayıcı baytları olan tüm baytların yüzdesi.|
|**Özel Bayt Sayısı**|- Bir işlev için, işlev tarafından ayrılan toplam bayt sayısı. Sayı, bu işlev tarafından çağrılan işlevlerde ayrılan baytları içermez.<br />- Bir modül için, modülde işlevler tarafından ayrılan özel baytların toplamı.<br />- Bir satır veya yönerge için, bu satır veya yönerge tarafından ayrılan toplam nesne sayısı.|
|**Özel Bayt %**|Profil oluşturma çalıştırması içinde ayrılan ve modülün, işlevin, satırın veya yönergenin özel baytları olan tüm baytların yüzdesi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl: Rapor Görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)
- [Modüller Görünümü - ölçüm](../profiling/modules-view-dotnet-memory-instrumentation-data.md)
- [Modüller Görünümü](../profiling/modules-view-sampling-data.md)
- [Modüller Görünümü](../profiling/modules-view-instrumentation-data.md)
