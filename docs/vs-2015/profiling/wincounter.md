---
title: WinCounter | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: ff319ffc-f249-4c3f-9eb2-06e392e3ae80
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9424eb099516761866ec459888ff830fcf56a28b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154749"
---
# <a name="wincounter"></a>WinCounter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**WinCounter** seçeneği, profil çalıştırması sırasında ayarlanan aralıklarda toplanacak bir Windows veya uygulama performans sayacı belirtir. Windows ve uygulama performansı sayaçları, profil oluşturma veri dosyasında işaretler olarak listelenir. Ayrı seçeneklerde toplanacak birden çok performans sayacı belirtebilirsiniz.  
  
 Varsayılan olarak, sayaçlar her 500 milisaniyede toplanır. Farklı bir koleksiyon aralığı belirtmek için **otomatik işaret** seçeneğini kullanın.  
  
 Yalnızca bir **otomatik işaret** seçeneği kullanılır. Birden çok **otomatik işaret** seçeneği belirtilirse, son bir tane kullanılır.  
  
 **WinCounter** seçeneği yalnızca **Start** seçeneğiyle birlikte kullanılabilir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```  
VSPerfCmd.exe /Start:Method /Wincounter:Path [/WinCounter:Path] [AutoMark:Milliseconds] [Options]  
```  
  
#### <a name="parameters"></a>Parametreler  
 `Path`  
 PDH sayaç yolu biçimindeki Windows performans sayacı.  
  
## <a name="required-options"></a>Gerekli seçenekler  
 **WinCounter** seçeneği yalnızca **Start** seçeneğiyle birlikte kullanılabilir.  
  
 **Başlangıç:**`Method`  
 **Başlat** seçeneği, profil oluşturucuyu belirtilen profil oluşturma yöntemine başlatır.  
  
## <a name="exclusive-options"></a>Dışlamalı seçenekler  
 **Otomatik işaret** seçeneği yalnızca **WinCounter** seçeneği ile kullanılabilir.  
  
 **Otomatik işaret:**`Milliseconds`  
 Windows performans sayacı veri toplama arasındaki milisaniye sayısını belirtir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, iki Windows performans sayacı 1000 milisaniyede bir aralıkta toplanabilecek şekilde belirtilmiştir.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WinCounter:"\Processor(0)\% Processor Time" /WinCounter:"\System\Context Switches/sec" /AutoMark:1000  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web uygulamalarının profilini oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profil Oluşturma Hizmetleri](../profiling/command-line-profiling-of-services.md)
