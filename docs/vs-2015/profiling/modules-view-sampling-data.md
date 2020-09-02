---
title: Modüller görünümü-örnekleme verileri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Modules view
- sampling profiling method,Modules view
ms.assetid: 816f5633-65d7-41e5-aee1-033628d4e2df
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5c3aa55bfc521521e28686ebb248053350ae14a7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64822201"
---
# <a name="modules-view---sampling-data"></a>Modüller Görünümü - Örnekleme Verileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Örnekleme verilerinin Modüller görünümü, profil oluşturma verilerinde örneklendiği modüller tarafından gruplanmış performans verilerini görüntüler. Her modül hiyerarşik bir ağacın köküdür. Modülün örneklenmiş işlevleri modül düğümünün altında listelenir.  
  
> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. Windows Mağazası uygulamaları da yeni koleksiyon teknikleri gerektirir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 İşlev, örnekler toplandığında yürütülerek (yani, işlev çağrı yığınının en üstünde ise), yürütülen kaynak çizgiler ve yönerge adresleri işlev düğümünün altında listelenir. Satır veya yönerge yürütüldüğü zaman bir kaynak satırı veya yönerge işaretçisi için veri toplandığı için, hem satır hem de yönerge verileri için dahil ve dışlamalı değerler her zaman aynıdır.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Ad**|Modülün, işlevin, satır numarasının veya yönerge işaretçisi adresinin adı.|  
|**İşlem Kimliği**|Profil oluşturma çalıştırmasının işlem KIMLIĞI (PID).|  
|**İşlem adı**|Sürecin adı.|  
|**Modül Adı**|İşlevin, çizginin veya yönerge işaretçisinin bulunduğu modül adı.|  
|**Modül yolu**|Modülün, işlevin, çizginin veya yönerge işaretçisinin bulunduğu modül yolu.|  
|**Kaynak Dosya**|Bu işlevin tanımını içeren kaynak dosya.|  
|**İşlev satır numarası**|Kaynak dosyada bu işlevin başlangıcına ait satır numarası.|  
|**Kapsamlı örnekler**|-Bir işlev için, bu işlevin veya bu işlev tarafından çağrılan bir işlevin yürütüldüğü örneklerin sayısı; diğer bir deyişle, bu işlevi içeren çağrı yığını örneklerinin sayısı.<br />-Bir modül için, modüldeki en az bir işlevin yürütüldüğü örnek sayısı.<br />-Bir çizgi veya yönerge için, bu satır veya yönergenin yürütüldüğü örnek sayısı.|  
|**Kapsamlı örnekler%**|-Bir işlev veya modül için, bu işlevin veya modülün kapsamlı örnekleri olan profil oluşturma çalıştırmasında tüm örneklerin yüzdesi.<br />-Bir çizgi veya yönerge için, bu satır veya yönergenin yürütüldüğü profil oluşturma çalıştırmasında tüm örneklerin yüzdesi.|  
|**Dışlamalı örnekler**|-Bir işlev için, bu işlevin doğrudan yürütüldüğü çağrı yığını örneklerinin sayısı; diğer bir deyişle, bu işlevin çağrı yığınının en üstünde olduğu örneklerin sayısı.<br />-Bir modül için, modüldeki işlevlerin dışlamalı örneklerinin toplamı.<br />-Bir çizgi veya yönerge için, bu satır veya yönergenin yürütüldüğü örnek sayısı.|  
|**Dışlamalı örnekler%**|-Bir işlev veya modül için, bu işlevin veya modülün özel örnekleri olan profil oluşturma çalıştırmasında tüm örneklerin yüzdesi.<br />-Bir çizgi veya yönerge için, bu satır veya yönergenin yürütüldüğü profil oluşturma çalıştırmasında tüm örneklerin yüzdesi.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Modüller görünümü-örnekleme](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [Modüller görünümü-Izleme](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Modüller Görünümü](../profiling/modules-view-instrumentation-data.md)
