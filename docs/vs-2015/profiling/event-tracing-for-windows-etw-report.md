---
title: Windows için olay Izleme (ETW) raporu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Event tracing for Windows profiling report
- ETW profiling report
ms.assetid: 81e88162-b88a-40b6-8b85-a232c8096a47
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bc0e139644a0b3df29109c1543140e57c5378f31
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64795405"
---
# <a name="event-tracing-for-windows-etw-report"></a>Windows için Olay İzleme (ETW) Raporu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows için olay Izleme (ETW) raporu, Profil Oluşturma Araçları Performans oturumunda kaydedilmiş olan ETW olaylarını listeler [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . ETW verileri bir ikili (. etl) dosyasında toplanır.  
  
> [!NOTE]
> Arabiriminde ETW raporlarını görüntüleyemezsiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
- Arabiriminden Profil Oluşturma Araçları kullanarak ETW 'nin nasıl toplanacağı hakkında daha fazla bilgi için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bkz. [nasıl yapılır: Windows Için olay Izleme (ETW) verileri toplama](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).  
  
- [VSPerfCmd](../profiling/vsperfcmd.md) komut satırı araçlarını kullanarak ETW verilerinin nasıl toplanacağı hakkında daha fazla bilgi için bkz. [Olaylar](../profiling/events-vsperfcmd.md).  
  
- **VSReport/Summary: ETW** komutunu kullanarak ETW raporunu oluşturabilirsiniz. Daha fazla bilgi için bkz. [VSPerfReport](../profiling/vsperfreport.md).  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Zaman damgası**|Olayın ne zaman oluştuğunu tanımlar.|  
|**İşlem Kimliği**|Olayı oluşturan işlemi tanımlar.|  
|**İş parçacığı KIMLIĞI**|Olayı oluşturan iş parçacığını tanımlar.|  
|**Açıklama**|Olay sağlayıcısını tanımlar.|  
|**Tür**|Olay türünü tanımlar.|  
|**Özellikler**|Etkinliğin özellikleri. Her olay, köşeli ayraçlar içine alınmış, virgülle ayrılmış bir ad-değer çiftidir.|
