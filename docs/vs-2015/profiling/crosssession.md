---
title: CrossSession | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: b9fcb9c3-7903-478c-9b7c-dbd94092fcba
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 05e1f2360b3257e44fde1af8be3554dd7fd95115
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62537191"
---
# <a name="crosssession"></a>CrossSession
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPerfCmd.exe **CrossSession** seçeneği, profil oluşturucunun herhangi bir konsol oturumundan veri toplamasını sağlar. **CrossSession** seçeneği **Start** seçeneğiyle birlikte kullanılmalıdır.  
  
 **CrossSession**yerine **CS** kısaltması kullanabilirsiniz.  
  
## <a name="syntax"></a>Söz dizimi  
  
```  
VSPerfCmd.exe /Start:Method /CrossSession [Options]  
```  
  
#### <a name="parameters"></a>Parametreler  
 Hiçbiri  
  
## <a name="valid-options"></a>Geçerli seçenekler  
 Başka bir oturumda profil oluşturmayı etkinleştirmek için, **CrossSession** seçeneğinin **Start** seçeneğiyle belirtilmesi gerekir. **CrossSession** , sonraki **VSPerfCmd Attach** ve **Detach** komutlarında de belirtilmelidir.  
  
 **Başlangıç:**`Method`  
 **Başlat** seçeneği, profil oluşturucuyu belirtilen profil oluşturma yöntemine başlatır.  
  
 **İliştirme:** _pid_[**,**_pid_]  
 Belirtilen işlemlerin profilini oluşturmaya başlıyor.  
  
 **Ayır**[**:**_pid_[,_pid_]]  
 Belirtilen işlemlerin profilini oluşturmayı durduruyor.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, **CrossSession** seçeneği, başka bir konsol oturumunda başlatılan bir uygulamaya eklemek için kullanılır.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /CrossSession  
VSPerfCmd.exe /Attach:12345 /CS  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web uygulamalarının profilini oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profil Oluşturma Hizmetleri](../profiling/command-line-profiling-of-services.md)
