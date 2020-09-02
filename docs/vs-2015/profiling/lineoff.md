---
title: Satır kapalı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 76082063-20ef-47ae-ad64-81b43b654865
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fbe8a715c5bb179c5293dd666f1879c07068d8b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62583177"
---
# <a name="lineoff"></a>LineOff
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Varsayılan olarak, profil oluşturucu, örnekleme profil oluşturma yöntemini kullanırken kaynak kodu satır numarasını ve satır numarası fark verileri ' ni toplar. VSPerfCmd giriş **kapalı** seçeneği, VSPerfCmd, uygulamayı başlatmak için kullanıldığında satır numarası veri toplamayı devre dışı bırakır. **Satır dışı** belirtildiğinde profil oluşturma verileri işlev düzeyine toplanır.  
  
 Yalnızca **Başlat seçeneğiyle ve** yalnızca profil oluşturucu **başlatma**:**örnek** seçeneğini kullanarak örnekleme için başlatıldığında, **LineOff** özelliğini kullanabilirsiniz.  
  
## <a name="syntax"></a>Söz dizimi  
  
```  
VSPerfCmd.exe /Launch:AppName /LineOff [Options]  
```  
  
#### <a name="parameters"></a>Parametreler  
 Hiçbiri  
  
## <a name="required-options"></a>Gerekli seçenekler  
 **LineOff** seçeneği yalnızca **başlatma** seçeneğini içeren bir komut satırında kullanılabilir.  
  
 **Başlatma:**`AppName`  
 Belirtilen uygulamayı başlatır ve örnekleme yöntemiyle profil oluşturmaya başlar.  
  
## <a name="example"></a>Örnek  
 Bu örnek, uygulamayı ve profil oluşturucuyu başlatır ve satır düzeyinde örneklemeyi devre dışı bırakır.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /LineOff  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web uygulamalarının profilini oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profil Oluşturma Hizmetleri](../profiling/command-line-profiling-of-services.md)
