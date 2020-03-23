---
title: WinCounter | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ff319ffc-f249-4c3f-9eb2-06e392e3ae80
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9455d596e27526f6075ad3b667ac441b12511d58
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779850"
---
# <a name="wincounter"></a>WinCounter
**WinCounter** seçeneği, profil çalışması sırasında belirli aralıklarla toplamak için bir Windows veya uygulama performans sayacı belirtir. Windows ve uygulama performans sayaçları profil oluşturma veri dosyasında işaret olarak listelenir. Ayrı seçeneklerde toplamak için birden çok performans sayacı belirtebilirsiniz.

 Varsayılan olarak, sayaçlar her 500 milisaniyede bir toplanır. Farklı bir toplama aralığı belirtmek için **AutoMark** seçeneğini kullanın.

 Yalnızca bir **AutoMark** seçeneği kullanılır. Birden çok **AutoMark** seçeneği belirtilirse, sonuncusu kullanılır.

 **WinCounter** seçeneği yalnızca **Başlat** seçeneği yle kullanılabilir.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /Start:Method /Wincounter:Path [/WinCounter:Path] [AutoMark:Milliseconds] [Options]
```

#### <a name="parameters"></a>Parametreler
 `Path`PDH sayaç yolu biçimindeki Windows performans sayacı.

## <a name="required-options"></a>Gerekli seçenekler
 **WinCounter** seçeneği yalnızca **Başlat** seçeneği yle kullanılabilir.

 **Başlangıç:** `Method` **Başlat** seçeneği profil oluşturucuyu belirtilen profil oluşturma yöntemine başlatir.

## <a name="exclusive-options"></a>Özel seçenekler
 **AutoMark** seçeneği yalnızca **WinCounter** seçeneği ile kullanılabilir.

 **AutoMark:** `Milliseconds` Windows performans sayacı veri toplama arasındaki milisaniye sayısını belirtir.

## <a name="example"></a>Örnek
 Aşağıdaki örnekte, iki Windows performans sayacının 1000 milisaniye aralıkla toplandığı belirtilir.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WinCounter:"\Processor(0)\% Processor Time" /WinCounter:"\System\Context Switches/sec" /AutoMark:1000
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profil tek başına uygulamalar](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Web uygulamaları ASP.NET profil](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
