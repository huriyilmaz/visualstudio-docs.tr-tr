---
title: GC (VSPerfCmd) | Microsoft Docs
description: VSPerfCmd.exe aracında GC seçeneğini gözden geçirme. GC seçeneği, bellek ayırma ve nesne .NET Framework veri toplamayı sağlar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7c81e88b-a748-4cf5-a7a1-3429608e1b54
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 512f9703da7a5a37e103c4732824d6cf40cb172994762bac2c81482117d86e05
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121333112"
---
# <a name="gc-vsperfcmd"></a>GC (VSPerfCmd)
**GC seçeneği,** bellek ayırma ve nesne .NET Framework veri toplamayı sağlar. **GC seçeneği** yalnızca örnekleme profil oluşturma yöntemiyle ve yalnızca Başlat **seçeneğiyle** kullanılabilir.

 **GC** seçeneğini kullanırken VSPerfClrEnv **/sampleon** komutu gerekli değildir.

 Parametre belirtilmezse veya Ayırma parametresi **belirtilirse,** yalnızca .NET Framework ayırma verileri toplanır. Yaşam süresi **parametresi** belirtilirse, hem bellek .NET Framework hem de .NET Framework yaşam süresi verileri toplanır.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /Launch:AppName /GC[:{Allocation|Lifetime}] [Options]
```

#### <a name="parameters"></a>Parametreler
 **Ayırma** Varsayılan. Bellek .NET Framework verileri toplar.

 **Yaşam süresi** Hem bellek ayırma .NET Framework hem de nesne yaşam .NET Framework verilerini toplar.

## <a name="required-options"></a>Gerekli Seçenekler
 **GC seçeneği** yalnızca Başlat **seçeneğiyle** kullanılabilir.

 **Başlatma:** `AppName` Belirtilen uygulamayı başlatır ve örnekleme yöntemiyle profil oluşturmayı başlatır.

## <a name="example"></a>Örnek
 Aşağıdaki örnek bir uygulamayı başlatıyor ve bellek .NET Framework verilerini toplar.

```cmd
VSPerfCmd.exe /Launch:TestApp.exe /gc
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Web ASP.NET profil oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
