---
title: QueryCounters | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74771915"
---
# <a name="querycounters"></a>QueryCounters
**QueryCounters** seçeneği, bilgisayarda kullanılabilen CPU (donanım) performans sayaçlarını listeler.

 **QueryCounters** komut satırında tek seçenek olmalıdır.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /QueryCounters
```

#### <a name="parameters"></a>Parametreler
 None

## <a name="remarks"></a>Açıklamalar
 Enstrümantasyon yöntemini kullanırken, profil oluşturucu her veri toplama etkinliğinde bir veya daha fazla CPU performans sayacının değerlerini toplayabilir. Örnekleme profil oluşturma yöntemini kullanırken, örnekleme aralığı olarak kullanılacak bir sayaç olayı ve olay oluşumlarının sayısını belirtebilirsiniz.

 Farklı işlemciler farklı CPU performans sayaçlarını ortaya çıkarır. Profil oluşturucu, hemen hemen tüm işlemcilerde kullanılabilecek bir genel sayaç kümesi tanımlar. **QueryCounters** seçeneği, hem genel sayaçların adlarını hem de işlemciye özgü sayaçların adlarını listeler.

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profil tek başına uygulamalar](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Web uygulamaları ASP.NET profil](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
