---
title: PF | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: cdc0a094-a986-4629-bd1c-dd5fdca323dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 07ec6d636ec087386fdc9462ae09db55400957a9
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778420"
---
# <a name="pf"></a>PF
*VSPerfCmd. exe* **PF** seçeneği, sayfa hatalarına örneklenmiş profil oluşturma olayını ayarlar ve isteğe bağlı olarak, bir örnekleme aralığındaki sayfa hatalarının sayısını varsayılan değer olan 10 ' dan değiştirir.

> [!NOTE]
> **PF** , 64 bitlik sistemlerde kullanılamaz.

**PF** yalnızca **başlatma** veya **iliştirme** seçeneğini de içeren bir komut satırında kullanılabilir.

 Varsayılan olarak, örnekleme olayı durdurulmayan işlemci saati döngüleri olarak ayarlanır ve örnekleme aralığı 10.000.000 olarak ayarlanır. **Zamanlayıcı**, **PF**, **sys**ve **sayaç** seçenekleri, örnek olay ve örnekleme aralığını ayarlamanıza olanak sağlar. **GC** seçeneği, her bir ayırma ve çöp toplama olayında .net bellek verilerini toplar. Komut satırında bu seçeneklerden yalnızca biri belirtilebilir.

 Örnekleme olayı ve örnekleme aralığı yalnızca bir **başlatma** veya **iliştirme** seçeneği içeren ilk komut satırında ayarlanabilir.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /PF[:Events] [Options]
```

#### <a name="parameters"></a>Parametreler
 Örnekleme aralığındaki sayfa hatası olaylarının sayısını belirten bir tamsayı değeri `Events`. `Events` belirtilmemişse, Aralık 10 olarak ayarlanır.

## <a name="required-options"></a>Gerekli seçenekler
 **PF** , yalnızca aşağıdaki seçeneklerden birini içeren bir komut satırında belirtilebilir.

 **Başlat:** `AppName` profil oluşturucuyu ve AppName tarafından belirtilen uygulamayı başlatır.

 **Attach:** `PID` profil oluşturucuyu AppName tarafından belirtilen işleme iliştirir.

## <a name="invalid-options"></a>Geçersiz seçenekler
 Aşağıdaki seçenekler, **PF**ile aynı komut satırında belirtilemez.

 **Süreölçer**[ **:** `Cycles`] örnekleme olayını işlemci saati döngüleri olarak ayarlar ve isteğe bağlı olarak örnekleme aralığını `Cycles`olarak ayarlar. Varsayılan süreölçer aralığı 10.000.000 ' dir.

 **Sys**[ **:** `Events`] örnekleme olayını, profili oluşturulmuş uygulamadan işletim sistemi çekirdeğine (syscalls) çağrı yapılacak şekilde ayarlar ve isteğe bağlı olarak örnekleme aralığını `Events`olarak ayarlar. Varsayılan sys aralığı 10 ' dur.

 **Sayaç:** `Name`[`,Reload`[`,FriendlyName`]] örnekleme olayını `Name` tarafından belirtilen CPU performans sayacına ayarlar ve örnekleme aralığını `Reload`olarak ayarlar.

 **GC**[ **:** {**Allocation**&#124;**Lifetime**}] .net bellek verilerini toplar. Varsayılan olarak,veriler her bellek ayırma olayında toplanır. **Ömür** parametresi belirtildiğinde her çöp toplama olayında de veriler toplanır.

## <a name="example"></a>Örnek
 Bu örnekte, profil oluşturma örnek olayının sayfa hatalarına nasıl ayarlanacağı ve örnekleme aralığı 20 sayfa hatalarına nasıl ayarlanacağı gösterilmiştir.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /PF:20
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Tek başına uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET Web uygulamaları profili](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
