---
title: Sys (VSPerfCmd) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 294a6f9e-b49f-4c83-b322-5ac5411b66fb
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 435393ac536eb70f2f3f6d38b16eaab645848704
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778186"
---
# <a name="sys-vsperfcmd"></a>Sys (VSPerfCmd)
*VSPerfCmd. exe* **sys** seçeneği, sistem çağrı olaylarına örneklenmiş profil oluşturma olayını ayarlar (profili oluşturulan uygulamadan işletim sistemine işlev çağrıları) ve isteğe bağlı olarak, bir örnekleme aralığındaki sistem çağrılarının sayısını varsayılan değer olan 10 ' dan değiştirir.

 **Sys** yalnızca **başlatma** veya **iliştirme** seçeneğini de içeren bir komut satırında kullanılabilir.

 Varsayılan olarak, profil oluşturucu örnekleme olayı, işlemci saati döngüleri olarak ayarlanır ve örnekleme aralığı 10.000.000 olarak ayarlanır. **Zamanlayıcı**, **PF**, **sys**ve **sayaç** seçenekleri, örnekleme olayını ve örnekleme aralığını ayarlamanıza olanak sağlar. **GC** seçeneği, her bir ayırma ve çöp toplama olayında .net bellek verilerini toplar. Komut satırında bu seçeneklerden yalnızca biri belirtilebilir.

 Örnekleme olayı ve örnekleme aralığı yalnızca bir **başlatma** veya **iliştirme** seçeneği içeren ilk komut satırında ayarlanabilir.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe {/Launch:AppName|Attach:PID} /Sys[:Events] [Options]
```

#### <a name="parameters"></a>Parametreler
 bir örnekleme aralığındaki sistem çağrı olaylarının sayısını belirten bir tamsayı değeri `Events`. `Events` belirtilmemişse, Aralık 10 olarak ayarlanır.

## <a name="required-options"></a>Gerekli seçenekler
 **Sys** , aşağıdaki seçeneklerden birini gerektirir.

 **Başlat:** `AppName` profil oluşturucuyu ve `AppName`tarafından belirtilen uygulamayı başlatır.

 **Ekle:** `PID` profil oluşturucuyu `PID`belirtilen işleme iliştirir.

## <a name="invalid-options"></a>Geçersiz seçenekler
 Aşağıdaki seçenekler **sys**ile aynı komut satırında belirtilemez.

 **PF**[ **:** `Events`] örnekleme olayını sayfa hatalarına ayarlar ve isteğe bağlı olarak örnekleme aralığını `Events`olarak ayarlar. Varsayılan PF aralığı 10 ' dur.

 **Süreölçer**[ **:** `Cycles`] örnekleme olayını işlemci saati döngüleri olarak ayarlar ve isteğe bağlı olarak örnekleme aralığını `Cycles`olarak ayarlar. Varsayılan süreölçer aralığı 10.000.000 ' dir.

 **Sayaç:** `Name`[`,Reload`[`,FriendlyName`]] örnekleme olayını `Name` tarafından belirtilen CPU performans sayacına ayarlar ve örnekleme aralığını `Reload`olarak ayarlar.

 **GC**[ **:** {**Allocation**&#124;**Lifetime**}] .net bellek verilerini toplar. Varsayılan olarak,veriler her bellek ayırma olayında toplanır. **Ömür** parametresi belirtildiğinde her çöp toplama olayında de veriler toplanır.

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
