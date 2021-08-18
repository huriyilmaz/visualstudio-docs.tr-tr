---
title: Çağıran - Çağrılı Görünümü - Örnekleme Verileri | Microsoft Docs
description: Çağıran/Çağrılı görünümünün seçilen bir işlev için profil oluşturma bilgilerini ve bu işlevin üst ve alt işlevlerini Performans Gezgini.
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
ms.openlocfilehash: 936c7bec8c4c07a3e90414ed9a75ce6a113d9809
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122084642"
---
# <a name="callercallee-view---sampling-data"></a>Arayan/Çağrılı görünümü - örnekleme verileri
Çağıran/Çağrılı görünümü seçilen bir işlev ve üst ve alt işlevleri için profil oluşturma bilgilerini görüntüler. Çağıran/Çağrılı görünümü üç kılavuz içerir.

 **Geçerli işlev** orta kılavuzda görüntülenir ve seçilen işlev için profil oluşturma bilgilerini gösterir. Değerler işleve yapılan tüm örnekli çağrıları içerir.

 **Geçerli işlevi çağıran** işlevler üst kılavuzda görüntülenir ve çağıranın (üst) işlevlerin seçilen (geçerli) işlevin değerlerine tek tek katkılarını gösterir.

 **Geçerli işlev tarafından** çağrılan işlevler alt kılavuzda görüntülenir ve alt işlev geçerli işlev tarafından çağrıldıklarında seçili işlevin çağrılır (alt) işlevleri için profil oluşturma bilgilerini gösterir.

> [!NOTE]
> Windows 8 ve Windows Server 2012'daki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturmanın bu platformlarda veri toplaması sırasında önemli değişiklikler gerektirmektedir. UWP uygulamaları için yeni koleksiyon teknikleri de gerekir. Bkz. [Uygulama ve Windows 8 performans Windows Server 2012.](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)

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
|**Tür**|İşlevin bağlamı:<br /><br /> -   **0** - geçerli işlev<br />-   **1** - geçerli işlevi çağıran bir işlev<br />-   **2** - geçerli işlev tarafından çağrılan bir işlev|
|**Kök İşlev Adı**|Geçerli işlevin adı.|
|**Kapsayıcı Örnekler**|- Geçerli işlev için, bu işlev veya onun alt işlevlerinden biri yürütülse de toplanan örnek sayısı.<br />- Bir çağıranın işlevi için, bu işlev geçerli işlevi çağıran zaman toplanan geçerli işlevin kapsayıcı örneklerinin sayısı.<br />- Bir callee işlevi için, geçerli işlev bu işlevi çağıran olduğunda toplanan bu işlevin kapsayıcı örneklerinin sayısı.|
|**Kapsayıcı Örnekler %**|Profil oluşturma çalıştırması içinde yer alan ve bu işlevin kapsayıcı örnekleri olan tüm örneklerin yüzdesi.|
|**Özel Örnekler**|- Geçerli işlev için, profil oluşturma çalıştırması içinde bu işlev doğrudan yürüttükleri zaman toplanan örnek sayısı; diğer bir ifadeyle, bu işlev çağrı yığınının en üstündeyken. Bu işlevin alt işlevleri yürütücü olduğunda toplanan örnekler özel sayılarda sayılmaz.<br />- Bir çağıranın işlevi için, bu işlev geçerli işlevi çağıran zaman toplanan geçerli işlevin özel örnek sayısı.<br />- Bir çağrılı işlev için, geçerli işlev bu işlevi çağırana kadar toplanan bu işlevin özel örneklerinin sayısıdır.|
|**Özel Örnekler %**|Profil oluşturma çalıştırması içinde yer alan ve bu işlevin özel örnekleri olan tüm örneklerin yüzdesi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Arayan/Çağrılı görünümü - .NET bellek örnekleme verileri](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)
- [Arayan/Çağrılı görünümü - .NET bellek ölçüm verileri](../profiling/caller-callee-view-net-memory-instrumentation-data.md)
- [Arayan/Çağrılı görünümü - ölçüm verileri](../profiling/caller-callee-view-instrumentation-data.md)
