---
title: GC (VSPerfCmd) | Microsoft Docs
description: VSPerfCmd.exe aracında GC seçeneğini gözden geçirin. GC seçeneği, .NET Framework bellek ayırma ve nesne yaşam süresi verilerinin toplanmasını mümkün bir şekilde sunar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7c81e88b-a748-4cf5-a7a1-3429608e1b54
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 7245e75ac38d650bb40f9c21dc0a0ab642e0c721
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801349"
---
# <a name="gc-vsperfcmd"></a>GC (VSPerfCmd)
**GC** seçeneği, .NET Framework bellek ayırma ve nesne yaşam süresi verilerinin toplanmasını mümkün bir şekilde sunar. **GC** seçeneği yalnızca örnekleme profili oluşturma yöntemiyle ve yalnızca **başlatma** seçeneği ile kullanılabilir.

 **GC** seçeneğini kullanırken, VSPerfClrEnv **/sampleon** komutu gerekli değildir.

 Hiçbir parametre belirtilmemişse veya **ayırma** parametresi belirtilmişse yalnızca .NET Framework bellek ayırma verileri toplanır. **Ömür** parametresi belirtilirse, hem .NET Framework bellek ayırma hem de .NET Framework nesne yaşam süresi verileri toplanır.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /Launch:AppName /GC[:{Allocation|Lifetime}] [Options]
```

#### <a name="parameters"></a>Parametreler
 **Ayırma** Varsayılanını. .NET Framework bellek ayırma verilerini toplar.

 **Ömür** .NET Framework bellek ayırma verilerini ve .NET Framework nesne yaşam süresi verilerini toplar.

## <a name="required-options"></a>Gerekli seçenekler
 **GC** seçeneği yalnızca **başlatma** seçeneği ile kullanılabilir.

 **Başlatma:** `AppName` Belirtilen uygulamayı başlatır ve örnekleme yöntemiyle profil oluşturmaya başlar.

## <a name="example"></a>Örnek
 Aşağıdaki örnek bir uygulamayı başlatır ve .NET Framework bellek ayırma verilerini toplar.

```cmd
VSPerfCmd.exe /Launch:TestApp.exe /gc
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Tek başına uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET Web uygulamaları profili](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
