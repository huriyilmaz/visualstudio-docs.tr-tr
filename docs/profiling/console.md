---
title: Konsol | Microsoft Docs
description: Yeni bir komut istemi penceresinde belirtilen uygulamayı başlatmak için VSPerfCmd.exe konsol seçeneğini kullanın. Bunu başlatma seçeneğiyle kullanmanız gerekir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 93c39bfb503bec9858e33b7acf04e0f0433264b9
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720916"
---
# <a name="console"></a>Konsol
VSPerfCmd.exe **konsolu** seçeneği, yeni bir komut istemi penceresinde belirtilen uygulamayı başlatır. **Konsol** yalnızca VSPerfCmd **başlatma** seçeneğiyle birlikte kullanılabilir. Uygulama bir komut satırı uygulaması değilse, **konsolunun** hiçbir etkisi olmaz.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /Launch:AppName /Console
```

#### <a name="parameters"></a>Parametreler
 Hiçbiri

## <a name="required-options"></a>Gerekli seçenekler
 **Konsol** , yalnızca **başlatma** seçeneğini de içeren bir komut satırında belirtilebilir.

 **Başlatma:** `AppName` Profil oluşturucuyu ve tarafından belirtilen uygulamayı başlatır `AppName` .

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Tek başına uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET Web uygulamaları profili](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
