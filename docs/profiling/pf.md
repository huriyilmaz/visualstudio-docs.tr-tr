---
title: PF | Microsoft Docs
description: VSPerfCmd.exe PF seçeneğinin, sayfa hatalarına örneklenmiş profil oluşturma olayını nasıl ayarladığından ve Örnekleme aralığındaki sayfa hatalarının sayısını değiştirdiği hakkında bilgi edinin.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: cdc0a094-a986-4629-bd1c-dd5fdca323dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b920b641a7bfc4583af7b0ec5a9692a25c19adb5
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98719558"
---
# <a name="pf"></a>PF
*VSPerfCmd.exe* **PF** seçeneği, sayfa hatalarına örneklenmiş profil oluşturma olayını ayarlar ve isteğe bağlı olarak Örnekleme aralığındaki sayfa hatalarının sayısını varsayılan değer olan 10 ' dan değiştirir.

> [!NOTE]
> **PF** , 64 bitlik sistemlerde kullanılamaz.

**PF** yalnızca **başlatma** veya **iliştirme** seçeneğini de içeren bir komut satırında kullanılabilir.

 Varsayılan olarak, örnekleme olayı durdurulmayan işlemci saati döngüleri olarak ayarlanır ve örnekleme aralığı 10.000.000 olarak ayarlanır. **Zamanlayıcı**, **PF**, **sys** ve **sayaç** seçenekleri, örnek olay ve örnekleme aralığını ayarlamanıza olanak sağlar. **GC** seçeneği, her bir ayırma ve çöp toplama olayında .net bellek verilerini toplar. Komut satırında bu seçeneklerden yalnızca biri belirtilebilir.

 Örnekleme olayı ve örnekleme aralığı yalnızca bir **başlatma** veya **iliştirme** seçeneği içeren ilk komut satırında ayarlanabilir.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /PF[:Events] [Options]
```

#### <a name="parameters"></a>Parametreler
 `Events` Bir örnekleme aralığındaki sayfa hatası olaylarının sayısını belirten bir tamsayı değeri. `Events`Belirtilmemişse, Aralık 10 olarak ayarlanır.

## <a name="required-options"></a>Gerekli seçenekler
 **PF** , yalnızca aşağıdaki seçeneklerden birini içeren bir komut satırında belirtilebilir.

 **Başlatma:** `AppName` Profil oluşturucuyu ve AppName tarafından belirtilen uygulamayı başlatır.

 **Ekle:** `PID` Profil oluşturucuyu AppName tarafından belirtilen işleme iliştirir.

## <a name="invalid-options"></a>Geçersiz seçenekler
 Aşağıdaki seçenekler, **PF** ile aynı komut satırında belirtilemez.

 **Süreölçer**[**:** `Cycles` ], örnekleme olayını işlemci saati döngüleri olarak ayarlar ve isteğe bağlı olarak örnekleme aralığını olarak ayarlar `Cycles` . Varsayılan süreölçer aralığı 10.000.000 ' dir.

 **Sys**[**:** `Events` ] örnekleme olayını, profili oluşturulmuş uygulamadan işletim sistemi çekirdeğine (syscalls) çağrı yapılacak şekilde ayarlar ve isteğe bağlı olarak örnekleme aralığını olarak ayarlar `Events` . Varsayılan sys aralığı 10 ' dur.

 **Sayaç:** `Name` [ `,Reload` [ `,FriendlyName` ]] Örnekleme olayını tarafından belirtilen CPU performans sayacına ayarlar `Name` ve örnekleme aralığını olarak ayarlar `Reload` .

 **GC**[**:**{**Allocation**&#124;**Lifetime**}] .net bellek verilerini toplar. Varsayılan olarak,veriler her bellek ayırma olayında toplanır. **Ömür** parametresi belirtildiğinde her çöp toplama olayında de veriler toplanır.

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
