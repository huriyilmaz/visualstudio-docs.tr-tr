---
title: GC (VSPerfCmd) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7c81e88b-a748-4cf5-a7a1-3429608e1b54
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2bdb28f74dd305dc497521e95d38e00192c21c54
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193597"
---
# <a name="gc-vsperfcmd"></a>GC (VSPerfCmd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**GC** seçeneği, .NET Framework bellek ayırma ve nesne yaşam süresi verilerinin toplanmasını mümkün bir şekilde sunar. **GC** seçeneği yalnızca örnekleme profili oluşturma yöntemiyle ve yalnızca **başlatma** seçeneği ile kullanılabilir.  
  
 **GC** seçeneğini kullanırken, VSPerfClrEnv **/sampleon** komutu gerekli değildir.  
  
 Hiçbir parametre belirtilmemişse veya **ayırma** parametresi belirtilmişse yalnızca .NET Framework bellek ayırma verileri toplanır. **Ömür** parametresi belirtilirse, hem .NET Framework bellek ayırma hem de .NET Framework nesne yaşam süresi verileri toplanır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```  
VSPerfCmd.exe /Launch:AppName /GC[:{Allocation|Lifetime}] [Options]  
```  
  
#### <a name="parameters"></a>Parametreler  
 **Ayırma**  
 Varsayılan. .NET Framework bellek ayırma verilerini toplar.  
  
 **Ömür**  
 .NET Framework bellek ayırma verilerini ve .NET Framework nesne yaşam süresi verilerini toplar.  
  
## <a name="required-options"></a>Gerekli seçenekler  
 **GC** seçeneği yalnızca **başlatma** seçeneği ile kullanılabilir.  
  
 **Başlatma:**`AppName`  
 Belirtilen uygulamayı başlatır ve örnekleme yöntemiyle profil oluşturmaya başlar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir uygulamayı başlatır ve .NET Framework bellek ayırma verilerini toplar.  
  
```  
VSPerfCmd.exe /Launch:TestApp.exe /gc  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web uygulamalarının profilini oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profil Oluşturma Hizmetleri](../profiling/command-line-profiling-of-services.md)
