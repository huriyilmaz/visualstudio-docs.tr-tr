---
title: Kapanıyor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: a1e37500-4ad1-4670-9737-3d9a20536386
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 64bad66491588178dc7d80655a8e517d6daed053
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85330999"
---
# <a name="shutdown"></a>Kapat
**Kapatma** seçeneği, şu anda profili oluşturulmuş herhangi bir işlemin bitmesini veya ayrılmasını bekler ve sonra profil oluşturucuyu kapatır ve profil oluşturma veri dosyasını kapatır. **Kapalı** seçeneği, bir profil oluşturma çalıştırmasının son komutu olmalıdır.

 Bir zaman aşımı parametresi belirtilmemişse, **kapatma** seçeneği süresiz olarak bekler. Bir zaman aşımı parametresi belirtilirse, seçenek profil oluşturucuyu kapatmadan veya veri dosyasını kapatmadan belirtilen saniye sayısından sonra döndürür.

 **Kapalı** seçeneği, komut satırında belirtilen tek seçenek olmalıdır.

## <a name="syntax"></a>Söz dizimi

```cmd
VSPerfCmd.exe /Shutdown[:Timeout]
```

#### <a name="parameters"></a>Parametreler
`Timeout`
- Seçim Belirtilmişse, seçenek profil oluşturucuyu kapatmak veya profil oluşturma veri dosyasını kapatmak zorunda kalmadan, belirtilen sayıda saniyeden sonra döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Tek başına uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET Web uygulamaları profili](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
