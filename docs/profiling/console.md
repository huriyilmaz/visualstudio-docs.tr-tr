---
title: Konsol | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777822"
---
# <a name="console"></a>Konsol
VSPerfCmd.exe **Console** seçeneği, belirtilen uygulamayı yeni bir komut istemi penceresinde başlatır. **Konsol** sadece VSPerfCmd **Başlatma** seçeneği ile kullanılabilir. Uygulama bir komut satırı uygulaması değilse, **Konsol'un** hiçbir etkisi yoktur.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /Launch:AppName /Console
```

#### <a name="parameters"></a>Parametreler
 None

## <a name="required-options"></a>Gerekli Seçenekler
 **Konsol** yalnızca **Başlat** seçeneğini de içeren bir komut satırında belirtilebilir.

 **Başlatma:** `AppName` Profilleyiciyi ve tarafından `AppName`belirtilen uygulamayı başlatır.

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profil tek başına uygulamalar](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Web uygulamaları ASP.NET profil](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
