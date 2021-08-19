---
title: Çağrı ağacı görünümü-çekişme verileri | Microsoft Docs
description: Profili oluşturulmuş uygulamada geçen işlev yürütme yolları için çekişme verilerini gösteren çağrı ağacı görünümünü gözden geçirin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Call Tree view
ms.assetid: 9bd4bde2-2ca3-446c-9ccc-7421522e03ae
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 28cd7b22e64afbfb4c7c4100bd44c28e6dec6bb6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122084785"
---
# <a name="call-tree-view---contention-data"></a>Çağrı ağacı görünümü-çakışma verileri
Çağrı ağacı görünümü, profili oluşturulmuş uygulamada geçen işlev yürütme yollarını görüntüler. Ağacın kökü, uygulamanın veya bileşenin giriş noktasıdır. Her işlev düğümü, çağırdığı tüm işlevleri, işlevin engellenme sayısını ve diğer iş parçacıkları veya süreçlerine sahip bir kaynak için devam ettiğinden işlevin engellendiğini belirten süreyi listeler.

 Çağrı ağacı görünümündeki değerler, çağrı ağacındaki üst işlev tarafından çağrılan işlev örneklerine yöneliktir. Yüzde değerleri, işlev örneği değeri, profil oluşturma çalıştırmasında toplam çekişmeler sayısıyla karşılaştırılarak hesaplanır.

## <a name="highlight-the-execution-hot-path"></a>Yürütme etkin yolunu Vurgula
 Çağrı ağacı görünümü, en fazla çekişmeleri oluşturan işlemin veya işlevin yürütme yolunu genişletebilir ve vurgulayabilir.

- En etkin yolu göstermek için, işlem veya işleve sağ tıklayın ve ardından **etkin yolu genişlet**' e tıklayın.

## <a name="set-the-call-tree-root-node"></a>Çağrı ağacı kök düğümünü ayarla
 Profil oluşturma çalıştırmasında her işlem kök düğüm olarak görünür. Çağrı ağacı görünümünün başlangıç düğümünü ayarlamak için, başlangıç düğümü olarak ayarlamak istediğiniz düğüme sağ tıklayın ve ardından **kökü ayarla**' ya tıklayın.

 Kök düğümü ayarladığınızda, seçtiğiniz düğümün alt ağacı hariç diğer tüm girişleri görünümden ortadan kaldırabilirsiniz. Kök düğümü özgün düğüme geri sıfırlamak için çağrı ağacı görünümüne sağ tıklayın ve ardından **kökü Sıfırla**' ya tıklayın.

|Sütun|Açıklama|
|------------|-----------------|
|**Dışlamalı engellenme süresi**|Bu yürütme yolundaki bu işlevin örneklerinin, profil oluşturma çalıştırmasında yürütülmesi engellenmiş olduğu zaman. Süre, işlev tarafından çağrılan alt işlevlerin engellenme süresini içermez.|
|**Dışlamalı engellenme süresi yüzdesi**|Bu yürütme yolundaki bu işlev için özel olarak engellenme süresi olan profil oluşturma çalıştırmasında tüm engellenen sürenin yüzdesi.|
|**Dışlamalı çekişmeler**|Bu işlevin bu yürütme yolundaki örneklerinde gerçekleşen çekişmeler sayısı. Bu sayı, işlev tarafından çağrılan alt işlevlerin çekişmelerini içermez.|
|**Dışlamalı çekişmeler yüzdesi**|Bu işlevin çağrı ağacındaki üst işlev tarafından çağrılan örneklerinin Dışlamalar olan, profil oluşturma çalıştırmasında tüm çekişmelerin yüzdesi.|
|**İşlev adresi**|İşlevin adresi.|
|**İşlev adı**|İşlevin tam adı.|
|**Kapsamlı engellenme süresi**|Bu yürütme yolundaki bu işlevin örneklerinin profil oluşturma çalıştırmasında yürütülmesi engellenmiş toplam süre. Süre, işlev tarafından çağrılan alt işlevlerin engellenme süresini içerir.|
|**Kapsamlı engellenme süresi%**|Bu yürütme yolundaki bu işlevin örnekleri için kapsamlı engellenme süresi olan profil oluşturma çalıştırmasında tüm engellenen sürenin yüzdesi.|
|**Kapsamlı çekişmeler**|Bu yürütme yolundaki bu işlevin örneklerinin engellediği toplam çekişmeler sayısı. Bu sayı, işlev tarafından çağrılan alt işlevlerin çekişmelerini içerir.|
|**Kapsamlı çekişmeler yüzdesi**|Bu yürütme yolundaki bu işlevin örneklerinin dahil olduğu, profil oluşturma çalıştırmasının tüm çekişmelerinin yüzdesi.|
|**Düzeyde**|Çağrı ağacındaki işlevin düzeyi. Yalnızca VSReport komut satırı raporlarında. Daha fazla bilgi için bkz. [VSPerfReport](../profiling/vsperfreport.md).|
|**İşlev satır numarası**|Kaynak dosyada bu işlevin başlangıcına ait satır numarası.|
|**Modül adı**|İşlevi içeren modülün adı.|
|**Modül yolu**|İşlevi içeren modülün yolu.|
|**İşlem Kimliği**|Profil oluşturma çalıştırmasının işlem KIMLIĞI (PID).|
|**İşlem adı**|Sürecin adı.|
|**Kaynak Dosya**|Bu işlevin tanımını içeren kaynak dosya.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)
- [Çağrı ağacı görünümü](../profiling/call-tree-view.md)
- [Çağrı ağacı görünümü-izleme](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)
- [Çağrı ağacı görünümü-örnekleme](../profiling/call-tree-view-dotnet-memory-sampling-data.md)
- [Çağrı ağacı görünümü](../profiling/call-tree-view-instrumentation-data.md)
- [Çağrı ağacı görünümü](../profiling/call-tree-view-sampling-data.md)
