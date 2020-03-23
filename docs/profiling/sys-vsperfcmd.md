---
title: Sys (VSPerfCmd) | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778186"
---
# <a name="sys-vsperfcmd"></a>Sys (VSPerfCmd)
*VSPerfCmd.exe* **Sys** seçeneği, sistem arama olaylarına örneklenmiş profil oluşturma olayını (profilli uygulamadan işletim sistemine fonksiyon çağrıları) ayarlar ve isteğe bağlı olarak 10 varsayılanından bir örnekleme aralığındaki sistem çağrılarının sayısını değiştirir.

 **Sys** yalnızca **Başlat** veya **Ekle** seçeneğini de içeren bir komut satırında kullanılabilir.

 Varsayılan olarak, profiloluşturucu örnekleme olayı işlemci saat döngüleri olarak ayarlanır ve örnekleme aralığı 10.000.000 olarak ayarlanır. **Zamanlayıcı**, **PF**, **Sys**ve **Sayaç** seçenekleri örnekleme olayını ve örnekleme aralığını ayarlamanızı sağlar. **GC** seçeneği, her ayırma ve çöp toplama olayında .NET bellek verilerini toplar. Bu seçeneklerden yalnızca biri komut satırında belirtilebilir.

 Örnekleme olayı ve örnekleme aralığı yalnızca **Başlat** veya **Ekle** seçeneği içeren ilk komut satırında ayarlanabilir.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe {/Launch:AppName|Attach:PID} /Sys[:Events] [Options]
```

#### <a name="parameters"></a>Parametreler
 `Events`Örnekleme aralığındaki sistem çağrı olaylarının sayısını belirten bir tamsayı değeri. `Events` Belirtilmemişse, aralık 10 olarak ayarlanır.

## <a name="required-options"></a>Gerekli Seçenekler
 **Sys** aşağıdaki seçeneklerden birini gerektirir.

 **Başlatma:** `AppName` Profilleyiciyi ve tarafından `AppName`belirtilen uygulamayı başlatır.

 **Ekle:** `PID` Profiloluşturucuyu . `PID`

## <a name="invalid-options"></a>Geçersiz Seçenekler
 Aşağıdaki seçenekler **Sys**ile aynı komut satırında belirtilemez.

 **PF**[**:**`Events`] Örnekleme olayını sayfa hatalarına ayarlar ve `Events`isteğe bağlı olarak örnekleme aralığını .'a ayarlar Varsayılan PF aralığı 10'dur.

 **Zamanlayıcı**[**:**`Cycles`] Örnekleme olayını işlemci saat döngülerine ayarlar `Cycles`ve isteğe bağlı olarak örnekleme aralığını . Varsayılan Zamanlayıcı aralığı 10.000.000'dir.

 **Sayaç:** `Name``,Reload`[`,FriendlyName`[ ]] Örnekleme olayını CPU `Name` performans sayacına ayarlar `Reload`ve örnekleme aralığını .

 **GC**[**:**{**Ayırma**&#124;**Ömür Boyu**}} .NET bellek verilerini toplar. Varsayılan olarak **(Ayırma),** veriler her bellek ayırma olayında toplanır. Ömür **boyu** parametresi belirtildiğinde, her çöp toplama olayında veriler de toplanır.

## <a name="example"></a>Örnek
 Bu örnek, profilci örnekleme olayının sistem çağrılarına nasıl ayarlanını ve örnekleme aralığının örnek başına 20 çağrıya nasıl ayarlanıncaya kadar ayarlanıncagösterilmektedir.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Sys:20
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profil tek başına uygulamalar](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Web uygulamaları ASP.NET profil](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
