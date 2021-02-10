---
title: Kapanıyor | Microsoft Docs
description: Kapatma seçeneğinin, profili oluşturulmuş herhangi bir işlemin bitmesini veya ayrılmasını nasıl bekleyeceğini öğrenin ve ardından profil oluşturucuyu kapatır ve profil oluşturma veri dosyasını kapatır.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: a1e37500-4ad1-4670-9737-3d9a20536386
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 455278f7fccbc9e4f80ce4f11a167e5b433ca8ab
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950045"
---
# <a name="shutdown"></a>Kapat
**Kapatma** seçeneği, şu anda profili oluşturulmuş herhangi bir işlemin bitmesini veya ayrılmasını bekler ve sonra profil oluşturucuyu kapatır ve profil oluşturma veri dosyasını kapatır. **Kapalı** seçeneği, bir profil oluşturma çalıştırmasının son komutu olmalıdır.

 Bir zaman aşımı parametresi belirtilmemişse, **kapatma** seçeneği süresiz olarak bekler. Bir zaman aşımı parametresi belirtilirse, seçenek profil oluşturucuyu kapatmadan veya veri dosyasını kapatmadan belirtilen saniye sayısından sonra döndürür.

 **Kapalı** seçeneği, komut satırında belirtilen tek seçenek olmalıdır.

## <a name="syntax"></a>Sözdizimi

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
