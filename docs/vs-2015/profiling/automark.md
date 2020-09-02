---
title: Otomatik Işaret | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: c4de965e-0364-4f78-9936-1f509e85df74
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4fb849b43e21010d9183f53e31ccf6bbc70736b6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157196"
---
# <a name="automark"></a>AutoMark
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Otomatik işaret** seçeneği, Windows yazılım performansı sayaç olaylarının toplanması arasındaki milisaniye sayısını belirtir. Windows performans sayaçları **WinCounter** seçeneğinde belirtilmiştir.  
  
 Komut satırında yalnızca bir **otomatik işaret** seçeneği belirtilebilir. **Otomatik işaret** tarafından belirtilen **WinCounter** örnekleme aralığının, ana örnekleme aralığından bağımsız olduğunu unutmayın.  
  
## <a name="syntax"></a>Söz dizimi  
  
```  
VSPerfCmd.exe /Start:Method /WinCounter:Path /AutoMark:Milliseconds  
```  
  
#### <a name="parameters"></a>Parametreler  
 `Milliseconds`  
 Windows performans sayacı olaylarının koleksiyonları arasındaki milisaniye sayısını belirtir.  
  
## <a name="required-options"></a>Gerekli seçenekler  
 **WinCounter:**`Path`  
 Toplanacak Windows performans sayacını belirtir. İzleme yöntemini kullanırken, birden çok Windows sayacı belirtilebilir. Örnekleme yöntemini kullanırken yalnızca bir yazılım sayacı belirtilebilir. **WinCounter** seçeneği, **Start** seçeneğini içeren bir komut satırında belirtilmelidir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, iki Windows performans sayacı için 1000 milisaniyelik bir örnekleme aralığı ayarlanır.  
  
```  
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /WinCounter:"\Process(*)\% Processor Time" /WinCounter:"\ASP.NET\Pages/sec" /AutoMark:1000  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web uygulamalarının profilini oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profil Oluşturma Hizmetleri](../profiling/command-line-profiling-of-services.md)
