---
title: Çağrı ağacı görünümü-çekişme verileri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Call Tree view
ms.assetid: 9bd4bde2-2ca3-446c-9ccc-7421522e03ae
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5d12f1a2343018f05f0e741222b844c562b50f5e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189359"
---
# <a name="call-tree-view---contention-data"></a>Çağrı Ağacı Görünümü - Çakışma Verileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Çağrı ağacı görünümü, profili oluşturulmuş uygulamada geçen işlev yürütme yollarını görüntüler. Ağacın kökü, uygulamanın veya bileşenin giriş noktasıdır. Her işlev düğümü, çağırdığı tüm işlevleri, işlevin engellenme sayısını ve diğer iş parçacıkları veya süreçlerine sahip bir kaynak için devam ettiğinden işlevin engellendiğini belirten süreyi listeler.  
  
 Çağrı ağacı görünümündeki değerler, çağrı ağacındaki üst işlev tarafından çağrılan işlev örneklerine yöneliktir. Yüzde değerleri, işlev örneği değeri, profil oluşturma çalıştırmasında toplam çekişmeler sayısıyla karşılaştırılarak hesaplanır.  
  
## <a name="highlighting-the-execution-hot-path"></a>Yürütmenin etkin yolunu vurgulama  
 Çağrı ağacı görünümü, en fazla çekişmeleri oluşturan işlemin veya işlevin yürütme yolunu genişletebilir ve vurgulayabilir.  
  
- En etkin yolu göstermek için, işlem veya işleve sağ tıklayın ve ardından **etkin yolu genişlet**' e tıklayın.  
  
## <a name="setting-the-call-tree-root-node"></a>Çağrı ağacı kök düğümü ayarlanıyor  
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
|**Modül Adı**|İşlevi içeren modülün adı.|  
|**Modül yolu**|İşlevi içeren modülün yolu.|  
|**İşlem Kimliği**|Profil oluşturma çalıştırmasının işlem KIMLIĞI (PID).|  
|**İşlem adı**|Sürecin adı.|  
|**Kaynak Dosya**|Bu işlevin tanımını içeren kaynak dosya.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)   
 [Çağrı ağacı görünümü](../profiling/call-tree-view.md)   
 [Çağrı ağacı görünümü-Izleme](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Çağrı ağacı görünümü-örnekleme](../profiling/call-tree-view-dotnet-memory-sampling-data.md)   
 [Çağrı ağacı görünümü](../profiling/call-tree-view-instrumentation-data.md)   
 [Çağrı Ağacı Görünümü](../profiling/call-tree-view-sampling-data.md)
