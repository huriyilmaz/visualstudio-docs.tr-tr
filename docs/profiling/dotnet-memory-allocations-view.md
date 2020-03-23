---
title: .NET Bellek Ayırmaları Görünümü | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.allocation
helpviewer_keywords:
- performance reports, allocation view
- Allocations view
- profiling tools, Allocation view
- profiling tools reports, Allocation view
ms.assetid: 01eb876e-c413-4516-977b-4f896929e8a6
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ce16f65947fd69b5a54e564ba6bec061bc68e328
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777383"
---
# <a name="net-memory-allocations-view"></a>.NET Bellek Ayırma Görünümü
Tahsisler görünümü profil oluşturma çalışması sırasında oluşturulan türleri listeler. Her tür, türün ayırmaları ile sonuçlanan işlev yürütme yollarını görüntüleyen bir çağrı ağacının kök düğümüdür.

 Tür satırındaki veriler, profil oluşturma çalışmasında oluşturulan türün toplam nesne sayısını ve bu tür nesneler için ayrılan toplam bayt sayısını görüntüler. Bir tür için kapsayıcı ve özel değerler her zaman aynıdır.

- Kapsayıcı değerler, çağrı ağacındaki üst işlev tarafından çağrılan işlev ve alt işlevleri örneklerinde oluşturulan nesneler içindir.

- Özel değerler, üst işlev tarafından çağrıldıklarında işlev tarafından doğrudan oluşturulan nesneler içindir. Alt işlevlerde oluşturulan nesneler dahil edilmez.

  Bir işlevin verileri, oluşturulan nesne sayısını ve üst türün nesneleri için ayrılan bayt sayısını görüntüler.

## <a name="highlight-the-execution-hot-path"></a>Yürütme sıcak yolunu vurgulayın
 Ana türün en çok nesnesini oluşturan çağrı ağacının yürütme yolunu bulabilirsiniz.

- En etkin yolu görüntülemek için türü veya işlevi sağ tıklatın ve ardından **Sıcak Yolu Genişlet'i**tıklatın.

|Sütun|Açıklama|
|------------|-----------------|
|**Adı**|Ayrılan tür veya işlevin adı.|
|**İşlem Kimliği**|Profil oluşturma çalışmasının işlem kimliği (PID).|
|**İşlem Adı**|Sürecin adı.|
|**Modül Adı**|Türü veya işlevi içeren modülün adı.|
|**Modül Yolu**|Türü veya işlevi içeren modülün yolu.|
|**Kaynak Dosya**|Tür veya işlev tanımını içeren kaynak dosya.|
|**Fonksiyon Satır Numarası**|Kaynak dosyadaki bu tür tanımının veya işlevinin başlangıç satır numarası.|
|**Düzey**|Verilerin bir tür veya işlev için olup olmadığını gösterir.|
|**Kapsayıcı Tahsisatlar**|- Bir işlev için, işlev tarafından oluşturulan üst türnesnelerin toplam sayısı. Bu sayı, alt işlevlerde oluşturulan nesneleri içerir.<br />- Bir tür için, oluşturulan bu türdeki örneklerin toplam sayısı.|
|**Kapsayıcı Tahsisler %**|- Bir işlev için, profil oluşturma çalışmasında oluşturulan tüm nesnelerin işlevi tarafından üst türün kapsayıcı ayırmaları olan yüzdesi.<br />- Bir tür için, profil oluşturma çalışmasında oluşturulan nesnelerin toplam sayısının yüzdesi, türün örnekleridir.|
|**Özel Tahsisler**|- Bir işlev için, işlev doğrudan çağrı yığınının üst kısmında yürütüldüğünde oluşturulan nesnelerin sayısı. Bu sayı alt işlevlerde oluşturulan nesneleri içermez.<br />- Bir tür için, oluşturulan bu türdeki örneklerin toplam sayısı.|
|**Özel Tahsisatlar %**|- Bir işlev için, profil oluşturma çalışmasında oluşturulan tüm nesnelerin yüzdesi, işlev tarafından ana türün özel ayırmalarıdır.<br />- Bir tür için, profil oluşturma çalışmasında oluşturulan nesnelerin toplam sayısının yüzdesi, türün örnekleridir.|
|**Dahil Baytlar**|- Bir işlev için, üst türdeki nesneler için işlev tarafından ayrılan bellek baytlarının sayısı. Bu sayı, alt işlevleri tarafından ayrılan belleği içerir.<br />- Bir tür için, profil oluşturma çalışmasına ayrılan bayt sayısı türü örnekleri için.|
|**Dahil Bayt %**|- Bir işlev için, profil oluşturma çalışmasında ayrılan tüm bellek yüzdesi işlevi tarafından üst türde kapsayıcı ayırmalar oldu.<br />- Bir tür için, tür örnekleri için ayrılan profil oluşturma çalışmasında ayrılan tüm bellek yüzdesi.|
|**Özel Baytlar**|- Bir işlev için, üst türdeki nesneler için işlev tarafından ayrılan bellek baytlarının sayısı. Bu sayı, alt işlevleri tarafından ayrılan belleği içermez.<br />- Bir tür için, profil oluşturma çalışmasına ayrılan bayt sayısı türü örnekleri için.|
|**Özel Bayt %**|- Bir işlev için, profil oluşturma çalışmasında ayrılan tüm bellek yüzdesi işlevi tarafından üst türözel tahsisleri oldu.<br />- Bir tür için, tür örnekleri için ayrılan profil oluşturma çalışmasında ayrılan tüm bellek yüzdesi.|
