---
title: WinCounter | Microsoft Docs
description: Özel olarak, profil çalıştırması sırasında ayarlanan aralıklarda toplanacak bir Windows veya uygulama performans sayacı belirten WinCounter seçeneği hakkında bilgi edinin.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: ff319ffc-f249-4c3f-9eb2-06e392e3ae80
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 595a8003992c92871a8476743288d3072aff63c8
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98723055"
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
 `Path` PDH sayaç yolu biçimindeki Windows performans sayacı.

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
