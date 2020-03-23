---
title: PF | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778420"
---
# <a name="pf"></a>PF
*VSPerfCmd.exe* **PF** seçeneği, sayfa hatalarına örneklenmiş profil oluşturma olayını ayarlar ve isteğe bağlı olarak bir örnekleme aralığındaki sayfa hatasayısını 10 varsayılanından değiştirir.

> [!NOTE]
> **PF** 64-bit sistemlerde kullanılamaz.

**PF** yalnızca **Başlat** veya **Ekle** seçeneğini de içeren bir komut satırında kullanılabilir.

 Varsayılan olarak, örnekleme olayı durdurulmayan işlemci saat döngüleri olarak ayarlanır ve örnekleme aralığı 10.000.000 olarak ayarlanır. **Zamanlayıcı**, **PF**, **Sys**ve **Sayaç** seçenekleri örnek olay ve örnekleme aralığı ayarlamanızı sağlar. **GC** seçeneği, her ayırma ve çöp toplama olayında .NET bellek verilerini toplar. Bu seçeneklerden yalnızca biri komut satırında belirtilebilir.

 Örnekleme olayı ve örnekleme aralığı yalnızca **Başlat** veya **Ekle** seçeneği içeren ilk komut satırında ayarlanabilir.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /PF[:Events] [Options]
```

#### <a name="parameters"></a>Parametreler
 `Events`Örnekleme aralığındaki sayfa hata olaylarının sayısını belirten bir tamsayı değeri. `Events` Belirtilmemişse, aralık 10 olarak ayarlanır.

## <a name="required-options"></a>Gerekli seçenekler
 **PF** yalnızca aşağıdaki seçeneklerden birini içeren bir komut satırında belirtilebilir.

 **Başlatma:** `AppName` AppName tarafından belirtilen profiloluşturucuyu ve uygulamayı başlatır.

 **Ekle:** `PID` AppName tarafından belirtilen işleme profil oluşturucu ekler.

## <a name="invalid-options"></a>Geçersiz seçenekler
 Aşağıdaki seçenekler **PF**ile aynı komut satırında belirtilemez.

 **Zamanlayıcı**[**:**`Cycles`] Örnekleme olayını işlemci saat döngülerine ayarlar `Cycles`ve isteğe bağlı olarak örnekleme aralığını . Varsayılan Zamanlayıcı aralığı 10.000.000'dir.

 **Sys**[**:**`Events`] Örnekleme olayını profilli uygulamadan işletim sistemi çekirdeğine (syscalls) gelen çağrılara `Events`ayarlar ve isteğe bağlı olarak örnekleme aralığını . Varsayılan Sys aralığı 10'dur.

 **Sayaç:** `Name``,Reload`[`,FriendlyName`[ ]] Örnekleme olayını CPU `Name` performans sayacına ayarlar `Reload`ve örnekleme aralığını .

 **GC**[**:**{**Ayırma**&#124;**Ömür Boyu**}} .NET bellek verilerini toplar. Varsayılan olarak **(Ayırma),** veriler her bellek ayırma olayında toplanır. Ömür **boyu** parametresi belirtildiğinde, her çöp toplama olayında veriler de toplanır.

## <a name="example"></a>Örnek
 Bu örnek, profil oluşturma örnek olayının sayfa hatalarına nasıl ayarlanını ve örnekleme aralığını 20 sayfa hatalarına nasıl ayarlayabileceğimizi gösterir.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /PF:20
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profil tek başına uygulamalar](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Web uygulamaları ASP.NET profil](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
