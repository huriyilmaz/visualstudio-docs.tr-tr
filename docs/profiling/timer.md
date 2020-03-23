---
title: Zamanlayıcı | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1971868e-89fa-4452-8ee7-76e4daf31b66
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e1bed2715421948385a5b7eb1ddbbac064f3288b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778121"
---
# <a name="timer"></a>Zamanlayıcı
*VSPerfCmd.exe* **Timer** seçeneği, saat döngülerini işlemciye örnekleyen profil oluşturma olayını ayarlar ve isteğe bağlı olarak bir örnekleme aralığındaki döngü sayısını 10.000.000 varsayılanından değiştirir. 1GH (bir gigahertz) işlemcide, 10.000.000 saat döngüsü saniyede yaklaşık 100 örnektir. Belirtilebilen en az döngü sayısı 50.000'dir.

 **Zamanlayıcı** yalnızca örnekleme profil oluşturma yöntemini kullandığınızda kullanılabilir ve yalnızca **Başlat** veya **Ekle** seçeneğini de içeren bir komut satırında kullanılabilir.

 Varsayılan olarak, profiloluşturucu örnekleme olayı işlemci saat döngüleri olarak ayarlanır ve örnekleme aralığı 10.000.000 olarak ayarlanır. **Zamanlayıcı**, **PF**, **Sys**ve **Sayaç** seçenekleri örnekleme olayını ve örnekleme aralığını ayarlamanızı sağlar. **GC** seçeneği, her ayırma ve çöp toplama olayında .NET bellek verilerini toplar. Bu seçeneklerden yalnızca biri komut satırında belirtilebilir.

 Örnekleme olayı ve örnekleme aralığı yalnızca **Başlat** veya **Ekle** seçeneği içeren ilk komut satırında ayarlanabilir.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /Timer[:Cycles] [Options]
```

#### <a name="parameters"></a>Parametreler
 `Cycles`Örnekleme aralığındaişlemci saat döngülerinin sayısını belirten bir tamsayı değeri. `Cycles` Belirtilmemişse, aralık 10.000.000 olarak ayarlanır. Virgülsüz değeri belirtin.

## <a name="required-options"></a>Gerekli seçenekler
 **Zamanlayıcı** yalnızca aşağıdaki seçeneklerden birini içeren bir komut satırında belirtilebilir.

 **Başlatma:** `AppName` Profilleyiciyi ve tarafından `AppName`belirtilen uygulamayı başlatır.

 **Ekle:** `PID` Profiloluşturciyi işlem kimliğinde belirtilen işleme`PID`bağlar ( ).

## <a name="invalid-options"></a>Geçersiz seçenekler
 Aşağıdaki seçenekler **Timer**ile aynı komut satırında belirtilemez.

 **PF**[**:**`Events`] Örnekleme olayını sayfa hatalarına ayarlar ve `Events`isteğe bağlı olarak örnekleme aralığını .'a ayarlar Varsayılan PF aralığı 10'dur.

 **Sys**[**:**`Events`] Örnekleme olayını işletim sistemi çağrılarına ayarlar `Events`ve isteğe bağlı olarak örnekleme aralığını . Varsayılan Sys aralığı 10'dur.

 **Sayaç**[**:**`Name,Reload,FriendlyName`] Örnekleme olayını CPU `Name` performans sayacına ayarlar `Reload`ve örnekleme aralığını .

 **GC**[**:**{**Ayırma**&#124;**Ömür Boyu**}} .NET bellek verilerini toplar. Varsayılan olarak **(Ayırma),** veriler her bellek ayırma olayında toplanır. Ömür **boyu** parametresi belirtildiğinde, her çöp toplama olayında veriler de toplanır.

## <a name="example"></a>Örnek
 Bu örnek, profiloluşturucu örnekleme aralığının 1.000.000 işlemci döngüsüne nasıl ayarlanın gerektiğini göstermektedir.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Timer:1000000
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profil tek başına uygulamalar](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Web uygulamaları ASP.NET profil](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
