---
title: Kapanıyor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a1e37500-4ad1-4670-9737-3d9a20536386
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fbbbd27cfe7d720349592050419f5c73d1843c70
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160221"
---
# <a name="shutdown"></a>Kapat
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Kapatma** seçeneği, şu anda profili oluşturulmuş herhangi bir işlemin bitmesini veya ayrılmasını bekler ve sonra profil oluşturucuyu kapatır ve profil oluşturma veri dosyasını kapatır. **Kapalı** seçeneği, bir profil oluşturma çalıştırmasının son komutu olmalıdır.  
  
 Bir zaman aşımı parametresi belirtilmemişse, **kapatma** seçeneği süresiz olarak bekler. Bir zaman aşımı parametresi belirtilirse, seçenek profil oluşturucuyu kapatmak veya veri dosyasını kapatmak zorunda kalmadan, belirtilen sayıda saniyeden sonra döndürür.  
  
 **Kapalı** seçeneği, komut satırında belirtilen tek seçenek olmalıdır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```  
VSPerfCmd.exe /Shutdown[:Timeout]  
```  
  
#### <a name="parameters"></a>Parametreler  
`Timeout`  
- Seçim Belirtilmişse, seçenek profil oluşturucuyu kapatmak veya profil oluşturma veri dosyasını kapatmak zorunda kalmadan, belirtilen sayıda saniyeden sonra döndürür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web uygulamalarının profilini oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profil Oluşturma Hizmetleri](../profiling/command-line-profiling-of-services.md)
