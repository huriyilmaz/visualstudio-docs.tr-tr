---
title: Çağrı ağacı görünümü-örnekleme verileri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Call Tree view
- Call Tree view
ms.assetid: 5c4e8ec3-d0d3-485a-93bd-9060df4eb739
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 720f37afbeea3c7440ad2ced9649039d671b1f1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64805991"
---
# <a name="call-tree-view---sampling-data"></a>Çağrı Ağacı Görünümü - Örnekleme Verileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Çağrı ağacı görünümü, profili oluşturulmuş uygulamada geçen işlev yürütme yollarını görüntüler.  
  
> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. Windows Mağazası uygulamaları da yeni koleksiyon teknikleri gerektirir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 Ağacın kökü, uygulamanın veya bileşenin giriş noktasıdır. Her işlev düğümü, çağırdığı tüm işlevleri ve bu işlev çağrıları ile ilgili performans verilerini listeler.  
  
 Çağrı ağacı görünümündeki değerler, çağrı ağacındaki üst işlev tarafından çağrılan işlev örneklerine yöneliktir. Yüzde değerleri, işlev örneği değeri, profil oluşturma çalıştırmasında toplam örnek sayısı ile karşılaştırılarak hesaplanır.  
  
## <a name="highlighting-the-execution-hot-path"></a>Yürütmenin etkin yolunu vurgulama  
 Çağrı ağacı görünümü, en sık örneklenen işlemin veya işlevin yürütme yolunu genişletebilir ve vurgulayabilir. En etkin yolu göstermek için, işlem veya işleve sağ tıklayın ve ardından **etkin yolu genişlet**' e tıklayın.  
  
## <a name="setting-the-call-tree-root-node"></a>Çağrı ağacı kök düğümü ayarlanıyor  
 Profil oluşturma çalıştırmasında her işlem kök düğüm olarak görüntülenir. Çağrı ağacı görünümünün başlangıç düğümünü ayarlamak için, başlangıç düğümü olarak ayarlamak istediğiniz düğüme sağ tıklayın ve **kökü ayarla**' yı seçin.  
  
 Kök düğümü ayarladığınızda, seçili düğümün alt ağacı hariç diğer tüm girişleri görünümden ortadan kaldırabilirsiniz. Kök düğümü özgün düğüme geri sıfırlamak için, çağrı Ağacı Görünümü penceresine sağ tıklayın ve **kökü Sıfırla**' yı seçin.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**İşlem Kimliği**|Profil oluşturma çalıştırmasının işlem KIMLIĞI (PID).|  
|**İşlem adı**|Sürecin adı.|  
|**Modül Adı**|İşlevi içeren modülün adı.|  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)   
 [Çağrı Ağacı Görünümü-Profil Oluşturucu örnekleme verileri](../profiling/call-tree-view-sampling-data.md)   
 [Çağrı ağacı görünümü-örnekleme](../profiling/call-tree-view-dotnet-memory-sampling-data.md)   
 [Çağrı ağacı görünümü-Izleme](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Çağrı Ağacı Görünümü](../profiling/call-tree-view-instrumentation-data.md)
