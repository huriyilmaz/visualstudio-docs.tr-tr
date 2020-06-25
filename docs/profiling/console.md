---
title: Konsol | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b70c44f72d8f9d8fb25eb1c459946797cfb97913
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85331576"
---
# <a name="console"></a>Konsol
VSPerfCmd.exe **konsolu** seçeneği, yeni bir komut istemi penceresinde belirtilen uygulamayı başlatır. **Konsol** yalnızca VSPerfCmd **başlatma** seçeneğiyle birlikte kullanılabilir. Uygulama bir komut satırı uygulaması değilse, **konsolunun** hiçbir etkisi olmaz.

## <a name="syntax"></a>Söz dizimi

```cmd
VSPerfCmd.exe /Launch:AppName /Console
```

#### <a name="parameters"></a>Parametreler
 Yok

## <a name="required-options"></a>Gerekli seçenekler
 **Konsol** , yalnızca **başlatma** seçeneğini de içeren bir komut satırında belirtilebilir.

 **Başlatma:** `AppName` Profil oluşturucuyu ve tarafından belirtilen uygulamayı başlatır `AppName` .

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Tek başına uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET Web uygulamaları profili](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
