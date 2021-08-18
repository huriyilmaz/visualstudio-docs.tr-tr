---
title: PF | Microsoft Docs
description: VSPerfCmd.exe PF seçeneğinin, örnek alınan profil oluşturma olaylarını sayfa hatalarının nasıl ayar olduğunu ve bir örnekleme aralığındaki sayfa hatalarının sayısını nasıl değiştirmesi olduğunu öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: cdc0a094-a986-4629-bd1c-dd5fdca323dc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b782e630e04e5e490d56bc3a4830404c79a2c26a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122060914"
---
# <a name="pf"></a>PF
VSPerfCmd.exe **PF** seçeneği, örnek alınan profil oluşturma olaylarını sayfa hatalarından ayarlar ve isteğe bağlı olarak bir örnekleme aralığındaki sayfa hatalarının sayısını varsayılan değer olan 10'dan değiştirir.

> [!NOTE]
> **PF** 64 bit sistemlerde kullanılamaz.

**PF** yalnızca Başlat veya Ekle seçeneğini de içeren bir **komut** satırı **içinde** kullanılabilir.

 Örnekleme olayı varsayılan olarak durdurulan işlemci saat döngüleri olarak, örnekleme aralığı ise 10.000.000 olarak ayarlanır. **Zamanlayıcı,** **PF,** **Sys** ve **Sayaç** seçenekleri, örnek olay ve örnekleme aralığını ayarlamaya olanak sağlar. **GC seçeneği** her ayırma ve çöp toplama olayında .NET bellek verilerini toplar. Bu seçeneklerden yalnızca biri bir komut satırı üzerinde belirtilebilir.

 Örnekleme olayı ve örnekleme aralığı yalnızca Başlat veya Ekle  seçeneğini içeren ilk komut **satırına ayarlanabilir.**

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /PF[:Events] [Options]
```

#### <a name="parameters"></a>Parametreler
 `Events` Örnekleme aralığındaki sayfa hatası olaylarının sayısını belirten bir tamsayı değeri. `Events`Belirtilmezse, aralık 10 olarak ayarlanır.

## <a name="required-options"></a>Gerekli seçenekler
 **PF** yalnızca aşağıdaki seçeneklerden birini içeren bir komut satırı üzerinde belirtilebilir.

 **Başlatma:** `AppName` Profilleyiciyi ve AppName tarafından belirtilen uygulamayı başlatır.

 **Ekleme:** `PID` Profilleyiciyi AppName tarafından belirtilen işleme iliştirer.

## <a name="invalid-options"></a>Geçersiz seçenekler
 Aşağıdaki seçenekler PF ile aynı komut satırı üzerinde **belirtilmez.**

 **Zamanlayıcı**[**:** `Cycles` ] Örnekleme olaylarını işlemci saat döngüleri olarak ayarlar ve isteğe bağlı olarak örnekleme aralığını olarak `Cycles` ayarlar. Varsayılan Zamanlayıcı aralığı 10.000.000'tir.

 **Sys**[**:**] Örnekleme olaylarını, profili profili yapılan uygulamanın işletim sistemi `Events` çekirdeğine (syscalls) yapılan çağrılara ayarlar ve isteğe bağlı olarak örnekleme aralığını olarak `Events` ayarlar. Varsayılan Sys aralığı 10'dır.

 **Sayaç:** `Name` [ `,Reload` [ `,FriendlyName` ]] Örnekleme olaylarını tarafından belirtilen CPU performans sayacına ayarlar `Name` ve örnekleme aralığını olarak `Reload` ayarlar.

 **GC**[**:**{**Ayırma**&#124;**Ömrü**}] .NET bellek verilerini toplar. Varsayılan olarak (**Ayırma),** veriler her bellek ayırma olayında toplanır. Yaşam süresi **parametresi** belirtilirse, her çöp toplama olayında veriler de toplanır.

## <a name="example"></a>Örnek
 Bu örnek, profil oluşturma örnek olayı için sayfa hatalarını ayarlamayı ve örnekleme aralığını 20 sayfa hatası olarak ayarlamayı gösterir.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /PF:20
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Web ASP.NET profil oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
