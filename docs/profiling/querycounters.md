---
title: QueryCounters | Microsoft Docs
description: QueryCounters seçeneğinin, bilgisayardaki kullanılabilir CPU (donanım) performans sayaçlarını nasıl listeleyeceğinizi öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8059d4b2-af61-4a47-a6c2-8da5c0741c74
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9e93546c97b2ddec0e944314c51c87da05a725db
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950175"
---
# <a name="querycounters"></a>QueryCounters
**QueryCounters** seçeneği, BILGISAYARDAKI kullanılabilir CPU (donanım) performans sayaçlarını listeler.

 **QueryCounters** , komut satırındaki tek seçenek olmalıdır.

## <a name="syntax"></a>Sözdizimi

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
