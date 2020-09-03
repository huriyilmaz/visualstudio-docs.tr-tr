---
title: QueryCounters | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8059d4b2-af61-4a47-a6c2-8da5c0741c74
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 24379a720ccaa3405cbe5c127f3b8abaf12e49aa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74771915"
---
# <a name="querycounters"></a>QueryCounters
**QueryCounters** seçeneği, BILGISAYARDAKI kullanılabilir CPU (donanım) performans sayaçlarını listeler.

 **QueryCounters** , komut satırındaki tek seçenek olmalıdır.

## <a name="syntax"></a>Söz dizimi

```cmd
VSPerfCmd.exe /QueryCounters
```

#### <a name="parameters"></a>Parametreler
 Hiçbiri

## <a name="remarks"></a>Açıklamalar
 İzleme yöntemini kullanırken, Profil Oluşturucu her bir veri toplama olayında bir veya daha fazla CPU performans sayacının değerlerini toplayabilir. Örnekleme profil oluşturma yöntemini kullanırken, bir sayaç olayı ve örnekleme aralığı olarak kullanılacak olay tekrarlarının sayısını belirtebilirsiniz.

 Farklı işlemciler farklı CPU performans sayaçlarını kullanıma sunar. Profiler, neredeyse tüm işlemcilerde kullanılabilecek bir dizi genel sayaç tanımlar. **QueryCounters** seçeneği, genel sayaçların adlarını ve işlemciye özgü sayaçların adlarını listeler.

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Tek başına uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET Web uygulamaları profili](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
