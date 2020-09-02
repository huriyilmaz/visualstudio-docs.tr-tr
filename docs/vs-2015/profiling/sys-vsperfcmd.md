---
title: Sys (VSPerfCmd) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 294a6f9e-b49f-4c83-b322-5ac5411b66fb
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 981b37fe1ebaad5e45f0308143ab0384ef1d559b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145601"
---
# <a name="sys-vsperfcmd"></a>Sys (VSPerfCmd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPerfCmd.exe **sys** seçeneği, sistem çağrısı olaylarına örneklenmiş profil oluşturma olayını (profili oluşturulan uygulamadan işletim sistemine işlev çağrıları) ayarlar ve isteğe bağlı olarak, örnekleme aralığındaki sistem çağrılarının sayısını varsayılan değer olan 10 ' dan değiştirir.  
  
 **Sys** yalnızca **başlatma** veya **iliştirme** seçeneğini de içeren bir komut satırında kullanılabilir.  
  
 Varsayılan olarak, profil oluşturucu örnekleme olayı, işlemci saati döngüleri olarak ayarlanır ve örnekleme aralığı 10.000.000 olarak ayarlanır. **Zamanlayıcı**, **PF**, **sys**ve **sayaç** seçenekleri, örnekleme olayını ve örnekleme aralığını ayarlamanıza olanak sağlar. **GC** seçeneği, her bir ayırma ve çöp toplama olayında .net bellek verilerini toplar. Komut satırında bu seçeneklerden yalnızca biri belirtilebilir.  
  
 Örnekleme olayı ve örnekleme aralığı yalnızca bir **başlatma** veya **iliştirme** seçeneği içeren ilk komut satırında ayarlanabilir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```  
VSPerfCmd.exe {/Launch:AppName|Attach:PID} /Sys[:Events] [Options]  
```  
  
#### <a name="parameters"></a>Parametreler  
 `Events`  
 Bir örnekleme aralığındaki sistem çağrı olaylarının sayısını belirten bir tamsayı değeri. `Events`Belirtilmemişse, Aralık 10 olarak ayarlanır.  
  
## <a name="required-options"></a>Gerekli seçenekler  
 **Sys** , aşağıdaki seçeneklerden birini gerektirir.  
  
 **Başlatma:**`AppName`  
 Profil oluşturucuyu ve tarafından belirtilen uygulamayı başlatır `AppName` .  
  
 **Ekle:**`PID`  
 Profil oluşturucuyu tarafından belirtilen işleme iliştirir `PID` .  
  
## <a name="invalid-options"></a>Geçersiz seçenekler  
 Aşağıdaki seçenekler **sys**ile aynı komut satırında belirtilemez.  
  
 **PF**[**:** `Events` ]  
 Örnekleme olayını sayfa hatalarına ayarlar ve isteğe bağlı olarak örnekleme aralığını olarak ayarlar `Events` . Varsayılan PF aralığı 10 ' dur.  
  
 **Süreölçer**[**:** `Cycles` ]  
 Örnekleme olayını işlemci saati döngüleri olarak ayarlar ve isteğe bağlı olarak örnekleme aralığını olarak ayarlar `Cycles` . Varsayılan süreölçer aralığı 10.000.000 ' dir.  
  
 **Sayaç:** `Name` [`,Reload`[`,FriendlyName`]]  
 Örnekleme olayını tarafından belirtilen CPU performans sayacına ayarlar `Name` ve örnekleme aralığını olarak ayarlar `Reload` .  
  
 **GC**[**:**{**ayırma**&#124;**ömrü**}]  
 .NET bellek verilerini toplar. Varsayılan olarak,**Allocation**veriler her bellek ayırma olayında toplanır. **Ömür** parametresi belirtildiğinde her çöp toplama olayında de veriler toplanır.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, profil oluşturucu örnekleme olayının Sistem çağrılarına nasıl ayarlanacağı ve örnekleme aralığının örnek başına 20 çağrı olarak nasıl ayarlanacağı gösterilmektedir.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Sys:20  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web uygulamalarının profilini oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profil Oluşturma Hizmetleri](../profiling/command-line-profiling-of-services.md)
