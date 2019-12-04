---
title: Konsol | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 6ec56665b546f962e8b3f4fd35460715390aee30
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74777822"
---
# <a name="console"></a>Konsolu
VSPerfCmd. exe **konsol** seçeneği, belirtilen uygulamayı yeni bir komut istemi penceresinde başlatır. **Konsol** yalnızca VSPerfCmd **başlatma** seçeneğiyle birlikte kullanılabilir. Uygulama bir komut satırı uygulaması değilse, **konsolunun** hiçbir etkisi olmaz.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /Launch:AppName /Console
```

#### <a name="parameters"></a>Parametreler
 Yok.

## <a name="required-options"></a>Gerekli seçenekler
 **Konsol** , yalnızca **başlatma** seçeneğini de içeren bir komut satırında belirtilebilir.

 **Başlat:** `AppName` profil oluşturucuyu ve `AppName`tarafından belirtilen uygulamayı başlatır.

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Tek başına uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET Web uygulamaları profili](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
