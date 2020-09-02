---
title: Bağımsız değişkenler | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 20c35949-1f29-4282-ac75-4e6c237d71bc
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 65759da4363891c713f906e6cb10f00443bcbceb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197905"
---
# <a name="args"></a>Bağımsız Değişkenler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPerfCmd.exe **args** seçeneği, **Launch** alt komutunun hedef uygulamasına geçirilen bağımsız değişkenlerin bir listesini belirtir.  
  
 **Bağımsız değişkenler** yalnızca **başlatma** komut satırında de belirtildiğinde kullanılabilir. **Başlatma** belirtildiğinde **args** isteğe bağlıdır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```  
VSPerfCmd.exe /Launch:AppName /Args:Arguments [Options]  
```  
  
#### <a name="parameters"></a>Parametreler  
 `Arguments`  
 **Başlatma** komutunun hedef uygulamasına yönelik bağımsız değişkenlerin listesi.  
  
## <a name="required-options"></a>Gerekli seçenekler  
 **Başlatma:**`AppName`  
 Belirtilen uygulamayı başlatır ve örnekleme yöntemiyle profil oluşturmaya başlar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, TestApp.exe bağımsız değişkenleri geçirmek için **args** seçeneğini kullanır.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Args:"123, 'Hello World'"  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web uygulamalarının profilini oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profil Oluşturma Hizmetleri](../profiling/command-line-profiling-of-services.md)
