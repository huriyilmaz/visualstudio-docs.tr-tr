---
title: GC (VSPerfCmd) | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7c81e88b-a748-4cf5-a7a1-3429608e1b54
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e14fef1cfdc2dfc5f0d737ac09a08d90ab1de309
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74776985"
---
# <a name="gc-vsperfcmd"></a>GC (VSPerfCmd)
**GC** seçeneği .NET Framework bellek ayırma ve nesne yaşam boyu verilerinin toplanmasını sağlar. **GC** seçeneği yalnızca örnekleme profil oluşturma yöntemiyle ve yalnızca **Başlatma** seçeneğiyle kullanılabilir.

 **GC** seçeneğini kullanırken VSPerfClrEnv **/sampleon komutu** gerekmez.

 Parametreler belirtilmemişse veya **Ayırma** parametresi belirtilmişse, yalnızca .NET Framework bellek ayırma verileri toplanır. Ömür **boyu** parametresi belirtilirse, hem .NET Framework bellek ayırma hem de .NET Framework nesne yaşam boyu verileri toplanır.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /Launch:AppName /GC[:{Allocation|Lifetime}] [Options]
```

#### <a name="parameters"></a>Parametreler
 **Tahsisat** Varsayılan. .NET Framework bellek ayırma verilerini toplar.

 **Ömür boyu** Hem .NET Framework bellek ayırma verilerini hem de .NET Framework nesnesi yaşam boyu verilerini toplar.

## <a name="required-options"></a>Gerekli Seçenekler
 **GC** seçeneği yalnızca **Başlat** seçeneği yle kullanılabilir.

 **Başlatma:** `AppName` Belirtilen uygulamayı başlatır ve örnekleme yöntemiyle profil oluşturmaya başlar.

## <a name="example"></a>Örnek
 Aşağıdaki örnekbir uygulama başlatıyor ve .NET Framework bellek ayırma verilerini toplar.

```cmd
VSPerfCmd.exe /Launch:TestApp.exe /gc
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profil tek başına uygulamalar](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Web uygulamaları ASP.NET profil](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
