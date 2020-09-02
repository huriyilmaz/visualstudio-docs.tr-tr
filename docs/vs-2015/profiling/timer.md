---
title: Süreölçer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 1971868e-89fa-4452-8ee7-76e4daf31b66
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1e5f6c6db903b3ecced2ac3ebc4aaa0a3e60910c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145495"
---
# <a name="timer"></a>Zamanlayıcı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPerfCmd.exe **Zamanlayıcı** seçeneği, işlemci saati döngüleri olarak örneklenen profil oluşturma olayını ayarlar ve isteğe bağlı olarak bir örnekleme aralığındaki döngü sayısını varsayılan 10.000.000 ' dan değiştirir. 1GH (bir gigahertz) işlemcisinde 10.000.000 saat döngüsü yaklaşık 100 örnek/saniye. Belirtime için en az döngü sayısı 50.000 ' dir.  
  
 **Süreölçer** yalnızca örnekleme profil oluşturma yöntemini kullandığınızda kullanılabilir ve yalnızca **başlatma** veya **iliştirme** seçeneğini de içeren bir komut satırında kullanılabilir.  
  
 Varsayılan olarak, profil oluşturucu örnekleme olayı, işlemci saati döngüleri olarak ayarlanır ve örnekleme aralığı 10.000.000 olarak ayarlanır. **Zamanlayıcı**, **PF**, **sys**ve **sayaç** seçenekleri, örnekleme olayını ve örnekleme aralığını ayarlamanıza olanak sağlar. **GC** seçeneği, her bir ayırma ve çöp toplama olayında .net bellek verilerini toplar. Komut satırında bu seçeneklerden yalnızca biri belirtilebilir.  
  
 Örnekleme olayı ve örnekleme aralığı yalnızca bir **başlatma** veya **iliştirme** seçeneği içeren ilk komut satırında ayarlanabilir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```  
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /Timer[:Cycles] [Options]  
```  
  
#### <a name="parameters"></a>Parametreler  
 `Cycles`  
 Bir örnekleme aralığındaki işlemci saati döngüsü sayısını belirten bir tamsayı değeri. `Cycles`Belirtilmemişse, aralık 10.000.000 olarak ayarlanır. Değeri virgül olmadan belirtin.  
  
## <a name="required-options"></a>Gerekli seçenekler  
 **Süreölçer** , yalnızca aşağıdaki seçeneklerden birini içeren bir komut satırında belirtilebilir.  
  
 **Başlatma:**`AppName`  
 Profil oluşturucuyu ve tarafından belirtilen uygulamayı başlatır `AppName` .  
  
 **Ekle:**`PID`  
 Profil oluşturucuyu işlem KIMLIĞI () tarafından belirtilen işleme iliştirir `PID` .  
  
## <a name="invalid-options"></a>Geçersiz seçenekler  
 Aşağıdaki seçenekler **Zamanlayıcı**ile aynı komut satırında belirtilemez.  
  
 **PF**[**:** `Events` ]  
 Örnekleme olayını sayfa hatalarına ayarlar ve isteğe bağlı olarak örnekleme aralığını olarak ayarlar `Events` . Varsayılan PF aralığı 10 ' dur.  
  
 **Sys**[**:** `Events` ]  
 Örnekleme olayını işletim sistemi çağrılarına ayarlar ve isteğe bağlı olarak örnekleme aralığını olarak ayarlar `Events` . Varsayılan sys aralığı 10 ' dur.  
  
 **Counter**[**:** `Name,Reload,FriendlyName` ] Sayacı  
 Örnekleme olayını tarafından belirtilen CPU performans sayacına ayarlar `Name` ve örnekleme aralığını olarak ayarlar `Reload` .  
  
 **GC**[**:**{**ayırma**&#124;**ömrü**}]  
 .NET bellek verilerini toplar. Varsayılan olarak,**Allocation**veriler her bellek ayırma olayında toplanır. **Ömür** parametresi belirtildiğinde her çöp toplama olayında de veriler toplanır.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, profil oluşturucu örnekleme aralığının 1.000.000 işlemci döngüleri olarak nasıl ayarlanacağı gösterilmektedir.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Timer:1000000  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web uygulamalarının profilini oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profil Oluşturma Hizmetleri](../profiling/command-line-profiling-of-services.md)
