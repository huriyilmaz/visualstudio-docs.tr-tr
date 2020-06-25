---
title: WinCounter | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: ff319ffc-f249-4c3f-9eb2-06e392e3ae80
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 672d472d4e592782f7ae06920c518b154fba6cba
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85329880"
---
# <a name="wincounter"></a>WinCounter
**WinCounter** seçeneği, profil çalıştırması sırasında ayarlanan aralıklarda toplanacak bir Windows veya uygulama performans sayacı belirtir. Windows ve uygulama performansı sayaçları, profil oluşturma veri dosyasında işaretler olarak listelenir. Ayrı seçeneklerde toplanacak birden çok performans sayacı belirtebilirsiniz.

 Varsayılan olarak, sayaçlar her 500 milisaniyede toplanır. Farklı bir koleksiyon aralığı belirtmek için **otomatik işaret** seçeneğini kullanın.

 Yalnızca bir **otomatik işaret** seçeneği kullanılır. Birden çok **otomatik işaret** seçeneği belirtilirse, son bir tane kullanılır.

 **WinCounter** seçeneği yalnızca **Start** seçeneğiyle birlikte kullanılabilir.

## <a name="syntax"></a>Söz dizimi

```cmd
VSPerfCmd.exe /Start:Method /Wincounter:Path [/WinCounter:Path] [AutoMark:Milliseconds] [Options]
```

#### <a name="parameters"></a>Parametreler
 `Path`PDH sayaç yolu biçimindeki Windows performans sayacı.

## <a name="required-options"></a>Gerekli seçenekler
 **WinCounter** seçeneği yalnızca **Start** seçeneğiyle birlikte kullanılabilir.

 **Başlangıç:** `Method` **Başlat** seçeneği, profil oluşturucuyu belirtilen profil oluşturma yöntemine başlatır.

## <a name="exclusive-options"></a>Dışlamalı seçenekler
 **Otomatik işaret** seçeneği yalnızca **WinCounter** seçeneği ile kullanılabilir.

 **Otomatik işaret:** `Milliseconds` Windows performans sayacı veri toplama arasındaki milisaniye sayısını belirtir.

## <a name="example"></a>Örnek
 Aşağıdaki örnekte, iki Windows performans sayacı 1000 milisaniyede bir aralıkta toplanabilecek şekilde belirtilmiştir.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WinCounter:"\Processor(0)\% Processor Time" /WinCounter:"\System\Context Switches/sec" /AutoMark:1000
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Tek başına uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET Web uygulamaları profili](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
