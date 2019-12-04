---
title: WinCounter | Microsoft Docs
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779850"
---
# <a name="wincounter"></a>WinCounter
**WinCounter** seçeneği, profil çalıştırması sırasında ayarlanan aralıklarda toplanacak bir Windows veya uygulama performans sayacı belirtir. Windows ve uygulama performansı sayaçları, profil oluşturma veri dosyasında işaretler olarak listelenir. Ayrı seçeneklerde toplanacak birden çok performans sayacı belirtebilirsiniz.

 Varsayılan olarak, sayaçlar her 500 milisaniyede toplanır. Farklı bir koleksiyon aralığı belirtmek için **otomatik işaret** seçeneğini kullanın.

 Yalnızca bir **otomatik işaret** seçeneği kullanılır. Birden çok **otomatik işaret** seçeneği belirtilirse, son bir tane kullanılır.

 **WinCounter** seçeneği yalnızca **Start** seçeneğiyle birlikte kullanılabilir.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /Start:Method /Wincounter:Path [/WinCounter:Path] [AutoMark:Milliseconds] [Options]
```

#### <a name="parameters"></a>Parametreler
 Windows performans sayacını PDH sayaç yolu biçiminde `Path`.

## <a name="required-options"></a>Gerekli seçenekler
 **WinCounter** seçeneği yalnızca **Start** seçeneğiyle birlikte kullanılabilir.

 **Başlat:** **Başlat** seçeneği `Method` profil oluşturucuyu belirtilen profil oluşturma yöntemine başlatır.

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
