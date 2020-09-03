---
title: QueryCounters | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 8059d4b2-af61-4a47-a6c2-8da5c0741c74
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cdd2707a6af2b9d03e73c696884dc12413437b04
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68178280"
---
# <a name="querycounters"></a>QueryCounters
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**QueryCounters** seçeneği, BILGISAYARDAKI kullanılabilir CPU (donanım) performans sayaçlarını listeler.  
  
 **QueryCounters** , komut satırındaki tek seçenek olmalıdır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```  
VSPerfCmd.exe /QueryCounters  
```  
  
#### <a name="parameters"></a>Parametreler  
 Hiçbiri  
  
## <a name="remarks"></a>Açıklamalar  
 İzleme yöntemini kullanırken, Profil Oluşturucu her bir veri toplama olayında bir veya daha fazla CPU performans sayacının değerlerini toplayabilir. Örnekleme profil oluşturma yöntemini kullanırken, bir sayaç olayı ve örnekleme aralığı olarak kullanılacak olay tekrarlarının sayısını belirtebilirsiniz.  
  
 Farklı işlemciler farklı CPU performans sayaçlarını kullanıma sunar. Profiler, neredeyse tüm işlemcilerde kullanılabilecek bir dizi genel sayaç tanımlar. **QueryCounters** seçeneği, genel sayaçların adlarını ve işlemciye özgü sayaçların adlarını listeler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web uygulamalarının profilini oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profil Oluşturma Hizmetleri](../profiling/command-line-profiling-of-services.md)
