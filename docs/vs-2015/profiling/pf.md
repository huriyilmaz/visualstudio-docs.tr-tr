---
title: PF | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: cdc0a094-a986-4629-bd1c-dd5fdca323dc
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 243d5fada7342bc05d8768a7e33cca6f55e309ef
ms.sourcegitcommit: fb8babf5cd72f1fc2f97ffe4ad7b62d91f325f61
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2020
ms.locfileid: "64811358"
---
# <a name="pf"></a>PF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPerfCmd.exe **PF** seçeneği, sayfa hatalarına örneklenmiş profil oluşturma olayını ayarlar ve isteğe bağlı olarak Örnekleme aralığındaki sayfa hatalarının sayısını varsayılan değer olan 10 ' dan değiştirir.  
  
> [!NOTE]
> PF, 64 bit sistemlerde kullanılamaz.  
  
 **Not PF** , 64 bit bilgisayarlarda desteklenmez. **PF** yalnızca **başlatma** veya **iliştirme** seçeneğini de içeren bir komut satırında kullanılabilir.  
  
 Varsayılan olarak, örnekleme olayı durdurulmayan işlemci saati döngüleri olarak ayarlanır ve örnekleme aralığı 10.000.000 olarak ayarlanır. **Zamanlayıcı**, **PF**, **sys**ve **sayaç** seçenekleri, örnek olay ve örnekleme aralığını ayarlamanıza olanak sağlar. **GC** seçeneği, her bir ayırma ve çöp toplama olayında .net bellek verilerini toplar. Komut satırında bu seçeneklerden yalnızca biri belirtilebilir.  
  
 Örnekleme olayı ve örnekleme aralığı yalnızca bir **başlatma** veya **iliştirme** seçeneği içeren ilk komut satırında ayarlanabilir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```  
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /PF[:Events] [Options]  
```  
  
#### <a name="parameters"></a>Parametreler  
 `Events`  
 Bir örnekleme aralığındaki sayfa hatası olaylarının sayısını belirten bir tamsayı değeri. `Events`Belirtilmemişse, Aralık 10 olarak ayarlanır.  
  
## <a name="required-options"></a>Gerekli seçenekler  
 **PF** , yalnızca aşağıdaki seçeneklerden birini içeren bir komut satırında belirtilebilir.  
  
 **Başlatma:**`AppName`  
 Profil oluşturucuyu ve AppName tarafından belirtilen uygulamayı başlatır.  
  
 **Ekle:**`PID`  
 Profil oluşturucuyu AppName tarafından belirtilen işleme iliştirir.  
  
## <a name="invalid-options"></a>Geçersiz seçenekler  
 Aşağıdaki seçenekler, **PF**ile aynı komut satırında belirtilemez.  
  
 **Süreölçer**[**:** `Cycles` ]  
 Örnekleme olayını işlemci saati döngüleri olarak ayarlar ve isteğe bağlı olarak örnekleme aralığını olarak ayarlar `Cycles` . Varsayılan süreölçer aralığı 10.000.000 ' dir.  
  
 **Sys**[**:** `Events` ]  
 , Profili oluşturulmuş uygulamadan işletim sistemi çekirdeğine (syscalls) çağrı yapmak için örnekleme olayını ayarlar ve isteğe bağlı olarak örnekleme aralığını olarak ayarlar `Events` . Varsayılan sys aralığı 10 ' dur.  
  
 **Sayaç:** `Name` [`,Reload`[`,FriendlyName`]]  
 Örnekleme olayını tarafından belirtilen CPU performans sayacına ayarlar `Name` ve örnekleme aralığını olarak ayarlar `Reload` .  
  
 **GC**[**:**{**ayırma**&#124;**ömrü**}]  
 .NET bellek verilerini toplar. Varsayılan olarak,**Allocation**veriler her bellek ayırma olayında toplanır. **Ömür** parametresi belirtildiğinde her çöp toplama olayında de veriler toplanır.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, profil oluşturma örnek olayının sayfa hatalarına nasıl ayarlanacağı ve örnekleme aralığı 20 sayfa hatalarına nasıl ayarlanacağı gösterilmiştir.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /PF:20  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web uygulamalarının profilini oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profil Oluşturma Hizmetleri](../profiling/command-line-profiling-of-services.md)
