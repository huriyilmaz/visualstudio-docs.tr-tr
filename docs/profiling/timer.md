---
title: Süreölçer | Microsoft Docs
description: VSPerfCmd.exe Zamanlayıcı seçeneğinin, işlemci saati döngülerine örneklendiği profil oluşturma olayını nasıl ayarlacağınızı öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1971868e-89fa-4452-8ee7-76e4daf31b66
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 8ed930b323f4b0a3983b102483135b4dde3c5aa1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122141083"
---
# <a name="timer"></a>Zamanlayıcı
*VSPerfCmd.exe* **Zamanlayıcı** seçeneği, işlemci saati döngüleri olarak örneklenen profil oluşturma olayını ayarlar ve isteğe bağlı olarak bir örnekleme aralığındaki döngü sayısını varsayılan 10.000.000 ' dan değiştirir. 1GH (bir gigahertz) işlemcisinde 10.000.000 saat döngüsü yaklaşık 100 örnek/saniye. Belirtime için en az döngü sayısı 50.000 ' dir.

 **Süreölçer** yalnızca örnekleme profil oluşturma yöntemini kullandığınızda kullanılabilir ve yalnızca **başlatma** veya **iliştirme** seçeneğini de içeren bir komut satırında kullanılabilir.

 Varsayılan olarak, profil oluşturucu örnekleme olayı, işlemci saati döngüleri olarak ayarlanır ve örnekleme aralığı 10.000.000 olarak ayarlanır. **Zamanlayıcı**, **PF**, **sys** ve **sayaç** seçenekleri, örnekleme olayını ve örnekleme aralığını ayarlamanıza olanak sağlar. **GC** seçeneği, her bir ayırma ve çöp toplama olayında .net bellek verilerini toplar. Komut satırında bu seçeneklerden yalnızca biri belirtilebilir.

 Örnekleme olayı ve örnekleme aralığı yalnızca bir **başlatma** veya **iliştirme** seçeneği içeren ilk komut satırında ayarlanabilir.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /Timer[:Cycles] [Options]
```

#### <a name="parameters"></a>Parametreler
 `Cycles` Bir örnekleme aralığındaki işlemci saati döngüsü sayısını belirten bir tamsayı değeri. `Cycles`Belirtilmemişse, aralık 10.000.000 olarak ayarlanır. Değeri virgül olmadan belirtin.

## <a name="required-options"></a>Gerekli seçenekler
 **Süreölçer** , yalnızca aşağıdaki seçeneklerden birini içeren bir komut satırında belirtilebilir.

 **Başlatma:** `AppName` Profil oluşturucuyu ve tarafından belirtilen uygulamayı başlatır `AppName` .

 **Ekle:** `PID` Profil oluşturucuyu işlem KIMLIĞI () tarafından belirtilen işleme iliştirir `PID` .

## <a name="invalid-options"></a>Geçersiz seçenekler
 Aşağıdaki seçenekler **Zamanlayıcı** ile aynı komut satırında belirtilemez.

 **PF**[**:** `Events` ] örnekleme olayını sayfa hatalarına ayarlar ve isteğe bağlı olarak örnekleme aralığını olarak ayarlar `Events` . Varsayılan PF aralığı 10 ' dur.

 **Sys**[**:** `Events` ] örnekleme olayını işletim sistemi çağrılarına ayarlar ve isteğe bağlı olarak örnekleme aralığını olarak ayarlar `Events` . Varsayılan sys aralığı 10 ' dur.

 [**:** `Name,Reload,FriendlyName` ] Sayacı, örnekleme olayını tarafından belirtilen CPU performans sayacına ayarlar `Name` ve örnekleme aralığını olarak ayarlar `Reload` .

 **GC**[**:**{**Allocation**&#124;**Lifetime**}] .net bellek verilerini toplar. Varsayılan olarak,veriler her bellek ayırma olayında toplanır. **Ömür** parametresi belirtildiğinde her çöp toplama olayında de veriler toplanır.

## <a name="example"></a>Örnek
 Bu örnekte, profil oluşturucu örnekleme aralığının 1.000.000 işlemci döngüleri olarak nasıl ayarlanacağı gösterilmektedir.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Timer:1000000
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Tek başına uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [web uygulamalarının profilini ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
