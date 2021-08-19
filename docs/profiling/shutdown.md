---
title: Kapatma | Microsoft Docs
description: Kapat seçeneğinin profili şu anda profili yapılan işlemlerin bitim veya ayırmasını nasıl bekleyeceğini öğrenin, ardından profil oluşturma veri dosyasını kapatarak profil oluşturma işlemini kapatır.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: a1e37500-4ad1-4670-9737-3d9a20536386
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5d342cc26ae920f343c1336abc2d52792187c9fb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122157299"
---
# <a name="shutdown"></a>Kapat
Kapat **seçeneği,** profili şu anda profili yapılan işlemlerin bitim veya ayırmasını bekler, ardından profil oluşturma veri dosyasını kapatır ve profil oluşturma işlemini kapatır. Kapatma **seçeneği,** profil oluşturma çalıştırması için son komut olabilir.

 Bir zaman out parametresi belirtilmezse Kapat **seçeneği** süresiz olarak bekler. Bir zaman out parametresi belirtilirse, seçenek profilleyiciyi kapatmadan veya veri dosyasını kapatmadan belirtilen sayıda saniye sonra döndürür.

 Kapatma  seçeneği, komut satırı üzerinde belirtilen tek seçenek olmalı.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /Shutdown[:Timeout]
```

#### <a name="parameters"></a>Parametreler
`Timeout`
- (İsteğe bağlı) Belirtilirse, seçenek profil oluşturma verilerini kapatmadan veya profil oluşturma veri dosyasını kapatmadan belirtilen sayıda saniye sonrasını döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Web ASP.NET profil oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
