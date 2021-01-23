---
title: Sys (VSPerfCmd) | Microsoft Docs
description: VSPerfCmd.exe sys seçeneğinin sistem çağrı olaylarına örneklendiği profil oluşturma olayını nasıl ayarlacağınızı öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 294a6f9e-b49f-4c83-b322-5ac5411b66fb
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5e8090a39426455e0f6d877c26a7f0a50f00f10c
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98719766"
---
# <a name="sys-vsperfcmd"></a>Sys (VSPerfCmd)
*VSPerfCmd.exe* **sys** seçeneği, sistem çağrısı olaylarına örneklenmiş profil oluşturma olayını (profili oluşturulan uygulamadan işletim sistemine işlev çağrıları) ayarlar ve isteğe bağlı olarak, örnekleme aralığındaki sistem çağrılarının sayısını varsayılan değer olan 10 ' dan değiştirir.

 **Sys** yalnızca **başlatma** veya **iliştirme** seçeneğini de içeren bir komut satırında kullanılabilir.

 Varsayılan olarak, profil oluşturucu örnekleme olayı, işlemci saati döngüleri olarak ayarlanır ve örnekleme aralığı 10.000.000 olarak ayarlanır. **Zamanlayıcı**, **PF**, **sys** ve **sayaç** seçenekleri, örnekleme olayını ve örnekleme aralığını ayarlamanıza olanak sağlar. **GC** seçeneği, her bir ayırma ve çöp toplama olayında .net bellek verilerini toplar. Komut satırında bu seçeneklerden yalnızca biri belirtilebilir.

 Örnekleme olayı ve örnekleme aralığı yalnızca bir **başlatma** veya **iliştirme** seçeneği içeren ilk komut satırında ayarlanabilir.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe {/Launch:AppName|Attach:PID} /Sys[:Events] [Options]
```

#### <a name="parameters"></a>Parametreler
 `Events` Bir örnekleme aralığındaki sistem çağrı olaylarının sayısını belirten bir tamsayı değeri. `Events`Belirtilmemişse, Aralık 10 olarak ayarlanır.

## <a name="required-options"></a>Gerekli seçenekler
 **Sys** , aşağıdaki seçeneklerden birini gerektirir.

 **Başlatma:** `AppName` Profil oluşturucuyu ve tarafından belirtilen uygulamayı başlatır `AppName` .

 **Ekle:** `PID` Profil oluşturucuyu tarafından belirtilen işleme iliştirir `PID` .

## <a name="invalid-options"></a>Geçersiz seçenekler
 Aşağıdaki seçenekler **sys** ile aynı komut satırında belirtilemez.

 **PF**[**:** `Events` ] örnekleme olayını sayfa hatalarına ayarlar ve isteğe bağlı olarak örnekleme aralığını olarak ayarlar `Events` . Varsayılan PF aralığı 10 ' dur.

 **Süreölçer**[**:** `Cycles` ], örnekleme olayını işlemci saati döngüleri olarak ayarlar ve isteğe bağlı olarak örnekleme aralığını olarak ayarlar `Cycles` . Varsayılan süreölçer aralığı 10.000.000 ' dir.

 **Sayaç:** `Name` [ `,Reload` [ `,FriendlyName` ]] Örnekleme olayını tarafından belirtilen CPU performans sayacına ayarlar `Name` ve örnekleme aralığını olarak ayarlar `Reload` .

 **GC**[**:**{**Allocation**&#124;**Lifetime**}] .net bellek verilerini toplar. Varsayılan olarak,veriler her bellek ayırma olayında toplanır. **Ömür** parametresi belirtildiğinde her çöp toplama olayında de veriler toplanır.

## <a name="example"></a>Örnek
 Bu örnekte, profil oluşturucu örnekleme olayının Sistem çağrılarına nasıl ayarlanacağı ve örnekleme aralığının örnek başına 20 çağrı olarak nasıl ayarlanacağı gösterilmektedir.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Sys:20
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Tek başına uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET Web uygulamaları profili](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
