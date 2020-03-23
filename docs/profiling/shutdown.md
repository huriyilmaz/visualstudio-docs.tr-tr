---
title: Kapatma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a1e37500-4ad1-4670-9737-3d9a20536386
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 89a08808387067b934bfd826feb2dcfbcf949aab
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778290"
---
# <a name="shutdown"></a>Kapat
**Kapatma** seçeneği, şu anda profilli herhangi bir işlemin sona ermesini veya ayrılmasını bekler ve ardından profil oluşturucuyu kapatır ve profil oluşturma veri dosyasını kapatır. **Kapatma** seçeneği profil oluşturma çalışmasının son komutu olmalıdır.

 Zaman sonu parametresi belirtilmemişse, **Kapatma** seçeneği süresiz olarak bekler. Zaman ayırma parametresi belirtilirse, seçenek profil oluşturucuyu kapatmadan veya veri dosyasını kapatmadan belirtilen saniye sayısından sonra geri döner.

 **Kapatma** seçeneği komut satırında belirtilen tek seçenek olmalıdır.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /Shutdown[:Timeout]
```

#### <a name="parameters"></a>Parametreler
`Timeout`
- (İsteğe bağlı) Belirtilirse, seçenek profil oluşturucuyu kapatmadan veya profil oluşturma veri dosyasını kapatmadan belirtilen saniye sayısından sonra döner.

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profil tek başına uygulamalar](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Web uygulamaları ASP.NET profil](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
