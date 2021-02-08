---
title: Çağrı ağacı görünümü-.NET Bellek Örnekleme verileri | Microsoft Docs
description: Çağrı ağacı görünümü, profili oluşturulmuş uygulamada geçen işlev yürütme yolları için .NET Bellek Örnekleme verilerini görüntüleme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Call Tree view
ms.assetid: fbb6cb60-420b-4ca9-8306-2494f7d321fe
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 34e8f2e6148dc504e6dc8f25f81bc1ba8acb1f47
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839302"
---
# <a name="call-tree-view---net-memory-sampling-data"></a>Çağrı ağacı görünümü-.NET Bellek Örnekleme verileri
Çağrı ağacı görünümü, profili oluşturulmuş uygulamada geçen işlev yürütme yollarını görüntüler. Ağacın kökü, uygulamanın veya bileşenin giriş noktasıdır. Her işlev düğümü, çağırdığı tüm işlevleri ve bu işlev çağrıları hakkındaki .NET bellek ayırma verilerini listeler.

 Çağrı ağacı görünümündeki değerler, çağrı ağacındaki üst işlev tarafından çağrılan işlev örneklerine yöneliktir. Yüzde değerleri, işlev örneği değeri, profil oluşturma çalıştırmasında toplam sayı veya ayırma boyutuyla karşılaştırılarak hesaplanır.

## <a name="highlight-the-execution-hot-path"></a>Yürütme etkin yolunu Vurgula
 Çağrı ağacı görünümü, en büyük veya en fazla bellek nesnelerini oluşturan işlemin veya işlevin yürütme yolunu genişletebilir ve vurgulayabilir. En etkin yolu göstermek için, işlem veya işleve sağ tıklayın ve ardından **etkin yolu genişlet**' e tıklayın.

## <a name="set-the-call-tree-root-node"></a>Çağrı ağacı kök düğümünü ayarla
 Profil oluşturma çalıştırmasında her işlem kök düğüm olarak görüntülenir. Çağrı ağacı görünümünün başlangıç düğümünü farklı bir düğüme ayarlamak için, başlangıç düğümü olarak ayarlamak istediğiniz düğüme sağ tıklayın ve **kökü ayarla**' yı seçin.

 Kök düğümü ayarladığınızda, seçili düğümün alt ağacı hariç diğer tüm girişleri görünümden ortadan kaldırabilirsiniz. Kök düğümü, görüntülemekte olduğunuz düğüme geri sıfırlayabilirsiniz; Çağrı Ağacı Görünümü penceresine sağ tıklayın ve **kökü Sıfırla**' yı seçin.

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
|**Düzeyde**|Çağrı ağacındaki işlevin derinliği.|
|**Kapsamlı ayırmalar**|Çağrı ağacındaki üst işlev tarafından çağrılan bu işlevin örnekleri tarafından ayrılan nesne sayısı. Bu sayı, alt işlevler tarafından yapılan ayırmaları içerir.|
|**Kapsamlı ayırmalar%**|Bu işlevin kapsamlı ayırmaları olan profil oluşturma çalıştırmasında oluşturulan tüm nesnelerin yüzdesi.|
|**Dışlamalı ayırmalar**|Çağrı ağacındaki üst işlev tarafından çağrılan bu işlevin örnekleri tarafından ayrılan nesne sayısı. Bu sayı alt işlevler tarafından yapılan ayırmaları içermez.|
|**Dışlamalı ayırmalar%**|Profil oluşturma çalıştırmasında oluşturulan, çağrı ağacındaki üst işlev tarafından çağrılan işlev örneklerinin özel ayırmaları olan tüm nesnelerin yüzdesi.|
|**Kapsamlı baytlar**|Bu işlevin, çağrı ağacındaki üst işlev tarafından çağrılan örnekleri tarafından ayrılan bayt sayısı. Bu sayı, alt işlevler tarafından yapılan ayırmaları içerir.|
|**Dahil edilen baytlar%**|Bu işlevin kapsamlı ayırmaları olan profil oluşturma çalıştırmasında ayrılan tüm bellek baytlarının yüzdesi.|
|**Dışlamalı baytlar**|Bu işlevin, çağrı ağacındaki üst işlev tarafından çağrılan örnekleri tarafından ayrılan bayt sayısı. Bu sayı alt işlevler tarafından yapılan ayırmaları içermez.|
|**Dışlamalı bayt yüzdesi**|Bu işlevin özel ayırmaları olan profil oluşturma çalıştırmasında ayrılan tüm bellek baytlarının yüzdesi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Çağrı ağacı görünümü-izleme](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)
- [Çağrı ağacı görünümü](../profiling/call-tree-view-sampling-data.md)
- [Çağrı ağacı görünümü](../profiling/call-tree-view-instrumentation-data.md)
