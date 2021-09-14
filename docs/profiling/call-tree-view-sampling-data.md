---
title: Çağrı ağacı görünümü-örnekleme verileri | Microsoft Docs
description: Çağrı ağacı görünümünün, Performans Gezgini içindeki profili oluşturulan uygulamada geçen işlev yürütme yollarının örnekleme verilerini nasıl görüntülediğini okuyun.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Call Tree view
- Call Tree view
ms.assetid: 5c4e8ec3-d0d3-485a-93bd-9060df4eb739
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 44aaa125b464b90a101693f7dd6357123e6f7afa
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637238"
---
# <a name="call-tree-view---sampling-data"></a>Çağrı ağacı görünümü-örnekleme verileri
Çağrı ağacı görünümü, profili oluşturulmuş uygulamada geçen işlev yürütme yollarını görüntüler.

> [!NOTE]
> Windows 8 ve Windows Server 2012 gelişmiş güvenlik özellikleri Visual Studio profiler 'ın bu platformlarda verileri topladıkları şekilde gerekli önemli değişikliklere sahiptir. UWP uygulamaları için de yeni koleksiyon teknikleri gerekir. bkz. [Windows 8 ve Windows Server 2012 uygulamalarda performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

 Ağacın kökü, uygulamanın veya bileşenin giriş noktasıdır. Her işlev düğümü, çağırdığı tüm işlevleri ve bu işlev çağrıları ile ilgili performans verilerini listeler.

 Çağrı ağacı görünümündeki değerler, çağrı ağacındaki üst işlev tarafından çağrılan işlev örneklerine yöneliktir. Yüzde değerleri, işlev örneği değeri, profil oluşturma çalıştırmasında toplam örnek sayısı ile karşılaştırılarak hesaplanır.

## <a name="highlight-the-execution-hot-path"></a>Yürütme etkin yolunu Vurgula
 Çağrı ağacı görünümü, en sık örneklenen işlemin veya işlevin yürütme yolunu genişletebilir ve vurgulayabilir. En etkin yolu göstermek için, işlem veya işleve sağ tıklayın ve ardından **etkin yolu genişlet**' e tıklayın.

## <a name="set-the-call-tree-root-node"></a>Çağrı ağacı kök düğümünü ayarla
 Profil oluşturma çalıştırmasında her işlem kök düğüm olarak görüntülenir. Çağrı ağacı görünümünün başlangıç düğümünü ayarlamak için, başlangıç düğümü olarak ayarlamak istediğiniz düğüme sağ tıklayın ve **kökü ayarla**' yı seçin.

 Kök düğümü ayarladığınızda, seçili düğümün alt ağacı hariç diğer tüm girişleri görünümden ortadan kaldırabilirsiniz. Kök düğümü özgün düğüme geri sıfırlamak için, çağrı Ağacı Görünümü penceresine sağ tıklayın ve **kökü Sıfırla**' yı seçin.

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
|**Düzeyde**|Bu işlevin çağrı ağacındaki derinliği. Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlarında.|
|**Dışlamalı örnekler**|Bu işlevde, çağrı ağacındaki üst işlev tarafından çağrıldığında toplanan örneklerin sayısı. Bu sayı, işlev tarafından çağrılan işlevlerde toplanan örnekleri içermez.|
|**Dışlamalı örnekler%**|Profil oluşturma çalıştırmasında, çağrı ağacındaki üst işlev tarafından çağrıldığında bu işlevin özel örnekleri olan tüm örneklerin yüzdesi.|
|**Kapsamlı örnekler**|Bu işlevde, çağrı ağacındaki üst işlev tarafından çağrıldığında toplanan örneklerin sayısı. Bu sayı, işlev tarafından çağrılan işlevlerde toplanan örnekleri içerir.|
|**Kapsamlı örnekler%**|Profil oluşturma çalıştırmasında, çağrı ağacındaki üst işlev tarafından çağrıldığında bu işlevin kapsamlı örnekleri olan tüm örneklerin yüzdesi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)
- [Çağrı Ağacı Görünümü-Profil Oluşturucu örnekleme verileri](../profiling/call-Tree-view-sampling-data.md)
- [Çağrı ağacı görünümü-örnekleme](../profiling/call-tree-view-dotnet-memory-sampling-data.md)
- [Çağrı ağacı görünümü-izleme](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)
- [Çağrı ağacı görünümü](../profiling/call-tree-view-instrumentation-data.md)
