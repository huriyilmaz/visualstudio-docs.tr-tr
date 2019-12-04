---
title: Modüller görünümü-.NET Bellek Örnekleme verileri | Microsoft Docs
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74772733"
---
# <a name="modules-view---net-memory-sampling-data"></a>Modüller görünümü-.NET Bellek Örnekleme verileri
Örnekleme yöntemi kullanılarak toplanan .NET bellek ayırma verilerinin Modüller görünümü, bellek verilerini profil oluşturma çalıştırmasında yürütülen modüller tarafından gruplandırır. Her modül hiyerarşik bir ağacın köküdür. Modülün işlevleri modül düğümünün altında listelenir.

 Bellek ayıran deyimlerin kaynak dosya satır numaraları, işlev düğümünün altında listelenir ve ayırmayı yapan yönergelerin adresleri satır düğümünün altında listelenir. Satır verileri ve yönerge verileri için her zaman kapsamlı ve dışlamalı değerler aynıdır.

|Sütun|Açıklama|
|------------|-----------------|
|**Ad**|Modülün, işlevin, satır numarasının veya yönerge adresinin adı.|
|**İşlem KIMLIĞI**|Profil oluşturma çalıştırmasının işlem KIMLIĞI (PID).|
|**İşlem adı**|İşlemin adı.|
|**Modül adı**|İşlevi içeren modülün adı.|
|**Modül yolu**|Modülün yolu.|
|**Kaynak dosya**|Bu işlevin tanımını içeren kaynak dosya.|
|**İşlev satır numarası**|Kaynak dosyada bu işlevin başlangıcına ait satır numarası.|
|**Kapsamlı ayırmalar**|-Bir işlev için, işlev tarafından oluşturulan toplam nesne sayısı. Bu sayı, bu işlev tarafından çağrılan işlevlerde oluşturulan nesneleri içerir.<br />-Bir modül için, modülden en az bir işlev yürütüldüğü sırada ayrılan bir profil oluşturma çalıştırmasında nesne sayısı. Bu sayı, modül işlevleri tarafından çağrılan işlevlerde oluşturulan nesneleri içerir.<br />-Çizgi veya yönerge için, çizgi veya yönerge tarafından ayrılan toplam nesne sayısı.|
|**Kapsamlı ayırmalar%**|Profil oluşturma çalıştırmasında ayrılan, modülün, işlevin, çizginin veya yönergenin kapsamlı ayırmaları olan tüm nesnelerin yüzdesi.|
|**Dışlamalı ayırmalar**|-Geçerli işlev için, işlev, işlev gövdesinin kodunu yürütürken oluşturulan nesne sayısı (yani, işlev çağrı yığınının en üstünde olduğunda). Numara, bu işlev tarafından çağrılan işlevlerde oluşturulmuş nesneleri içermez.<br />-Bir modül için, modüldeki işlevlerin dışlamalı ayırmaların toplamı.<br />-Bir çizgi veya yönerge için, bu çizgi veya yönerge tarafından oluşturulan toplam nesne sayısı.|
|**Dışlamalı ayırmalar%**|Profil oluşturma çalıştırmasında ayrılan, modülün, işlevin, çizginin veya yönergenin özel ayırmaları olan tüm nesnelerin yüzdesi.|
|**Kapsamlı baytlar**|-Bir işlev için, işlev tarafından ayrılan bayt sayısı. Bu sayı, bu işlev tarafından çağrılan işlevlerde ayrılan baytları içerir.<br />-Bir modül için, modülden en az bir işlev yürütüldüğü sırada ayrılan bir profil oluşturma çalıştırmasında ayrılan bayt sayısı. Bu sayı, modül işlevleri tarafından çağrılan tüm işlevlerde oluşturulan nesneleri içerir.<br />-Çizgi veya yönerge için, çizgi veya yönerge tarafından oluşturulan toplam nesne sayısı.|
|**Dahil edilen baytlar%**|Profil oluşturma çalıştırmasında ayrılan, modülün, işlevin, çizginin veya yönergenin dahil olduğu baytların yüzdesi.|
|**Dışlamalı baytlar**|-Bir işlev için, işlev tarafından ayrılan toplam bayt sayısı. Numara, bu işlev tarafından çağrılan işlevlerde ayrılan baytları içermez.<br />-Bir modül için, modüldeki işlevlerle ayrılan özel baytlar toplamı.<br />-Bir çizgi veya yönerge için, bu çizgi veya yönergeyle ayrılan toplam nesne sayısı.|
|**Dışlamalı bayt yüzdesi**|Profil oluşturma çalıştırmasında ayrılan ve modülün, işlevin, çizginin veya yönergenin özel baytları olan tüm baytların yüzdesi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)
- [Modüller görünümü-izleme](../profiling/modules-view-dotnet-memory-instrumentation-data.md)
- [Modüller Görünümü](../profiling/modules-view-sampling-data.md)
- [Modüller Görünümü](../profiling/modules-view-instrumentation-data.md)
