---
title: WinCounter | Microsoft Docs
description: WinCounter seçeneğini, özellikle profil çalıştırması sırasında belirli aralıklarla Windows bir uygulama performansı sayacını veya uygulama performansı sayacını belirtir.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: ff319ffc-f249-4c3f-9eb2-06e392e3ae80
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4b5f22674f1b66b31a03b2c30ed0e58a7b9f89e5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122156714"
---
# <a name="wincounter"></a>WinCounter
**WinCounter seçeneği,** profil Windows belirli aralıklarla toplamak için bir uygulama performansı sayacı belirtir. Windows ve uygulama performans sayaçları profil oluşturma veri dosyasında işaretler olarak listelenir. Ayrı seçeneklerde toplamak için birden çok performans sayacı belirtebilirsiniz.

 Varsayılan olarak, sayaçlar her 500 milisaniyede bir toplanır. Farklı bir koleksiyon aralığı belirtmek için **AutoMark** seçeneğini kullanın.

 Yalnızca bir **AutoMark** seçeneği kullanılır. Birden **çok AutoMark** seçeneği belirtilirse, son seçenek kullanılır.

 **WinCounter** seçeneği yalnızca Başlat **seçeneğiyle** kullanılabilir.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /Start:Method /Wincounter:Path [/WinCounter:Path] [AutoMark:Milliseconds] [Options]
```

#### <a name="parameters"></a>Parametreler
 `Path`PdH Windows biçimindeki performans sayacı.

## <a name="required-options"></a>Gerekli seçenekler
 **WinCounter** seçeneği yalnızca Başlat **seçeneğiyle** kullanılabilir.

 **Başlat:** `Method` Başlat **seçeneği,** profilleyiciyi belirtilen profil oluşturma yöntemiyle başlatıyor.

## <a name="exclusive-options"></a>Özel seçenekler
 **AutoMark** seçeneği yalnızca **WinCounter seçeneğiyle** kullanılabilir.

 **Otomatik İşaret:** `Milliseconds` Performans sayacı veri toplama ile Windows milisaniye sayısını belirtir.

## <a name="example"></a>Örnek
 Aşağıdaki örnekte, iki Windows sayaçlarının 1000 milisaniyelik bir aralıkta toplanacak şekilde belirtiliyor.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WinCounter:"\Processor(0)\% Processor Time" /WinCounter:"\System\Context Switches/sec" /AutoMark:1000
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Web ASP.NET profil oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
