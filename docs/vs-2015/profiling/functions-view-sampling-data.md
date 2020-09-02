---
title: İşlevler Görünümü-Örnekleme verileri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Functions View
- Functions view
ms.assetid: 029d5ebb-e551-46b0-b64e-2c553d9dbb8e
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5aace03631cd768566dca8e314f280e20d9de77f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64808235"
---
# <a name="functions-view---sampling-data"></a>İşlevler Görünümü - Örnekleme Verileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Örnekleme profili yöntemi için Işlevler rapor görünümü profil oluşturma çalıştırması sırasında örneklendiği işlevleri listeler.  
  
> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. Windows Mağazası uygulamaları da yeni koleksiyon teknikleri gerektirir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
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
|**Kapsamlı örnekler**|Bu işlev yürütüldüğü zaman toplanan örneklerin toplam sayısı; diğer bir deyişle, bu işlev çağrı yığınında olduğunda toplanan örneklerin sayısı. Bu sayı, bu işlev tarafından çağrılan işlevler yürütüldüğü zaman toplanan örnekleri içerir.|  
|**Kapsamlı örnekler%**|Profil oluşturma çalıştırmasında, bu işlevin kapsamlı örnekleri olan tüm örneklerin yüzdesi.|  
|**Dışlamalı örnekler**|Bu işlevin gövdesinde kod yürütürken toplanan örneklerin toplam sayısı; diğer bir deyişle, bu işlev çağrı yığınının en üstünde olduğunda. Bu işlev tarafından çağrılan işlevlerde toplanan örnekler dahil değildir.|  
|**Dışlamalı örnekler%**|Bu işlevin özel örnekleri olan profil oluşturma çalıştırmasında tüm örneklerin yüzdesi.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)   
 [İşlevler görünümü-Izleme](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [İşlevler Görünümü-Örnekleme](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [İşlevler Görünümü](../profiling/functions-view-instrumentation-data.md)
