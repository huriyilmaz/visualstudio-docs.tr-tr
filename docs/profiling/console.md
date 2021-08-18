---
title: Konsol | Microsoft Docs
description: Belirtilen uygulamayı yeni bir komut VSPerfCmd.exe başlatmak için Konsol seçeneğini kullanın. Bunu Başlat seçeneğiyle birlikte kullansanız gerekir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: caaadb9329ef277cc5e82e787f56f9b3b2b96696
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122039520"
---
# <a name="console"></a>Konsol
Konsol VSPerfCmd.exe **seçeneği,** belirtilen uygulamayı yeni bir komut istemi penceresinde başlatır. **Konsol** yalnızca VSPerfCmd Başlatma **seçeneğiyle** kullanılabilir. Uygulama bir komut satırı uygulaması yoksa **Konsol'un** hiçbir etkisi yoktur.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /Launch:AppName /Console
```

#### <a name="parameters"></a>Parametreler
 Hiçbiri

## <a name="required-options"></a>Gerekli Seçenekler
 **Konsol** yalnızca Başlat seçeneğini de içeren bir komut satırı üzerinde **belirtilebilir.**

 **Başlatma:** `AppName` tarafından belirtilen profilleyiciyi ve uygulamayı `AppName` başlatır.

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Web ASP.NET profil oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
