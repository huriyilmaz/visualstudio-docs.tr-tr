---
title: GlobalOn ve GlobalOff | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 24b0ed68-d19e-473e-9af3-252c11d82bcf
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 518f41557809cdeaaae9f9e1ac79e3797a854395
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74776972"
---
# <a name="globalon-and-globaloff"></a>GlobalOn ve GlobalOff
*VSPerfCmd.exe* **GlobalOff** ve **GlobalOn** seçenekleri, komut satırı profil oluşturma oturumundaki tüm işlemler ve iş parçacıkları için profil oluşturmayı duraklatır ve devam ettirin.

 **GlobalOn** ve **GlobalOff'u** *VSPerfCmd.exe* komut satırındaki tek seçenek olarak belirtebilir veya bunları **Başlat,** **Başlat**veya **Ekle** seçeneklerini de içeren komut satırlarına ekleyebilirsiniz.

 **GlobalOn** ve **GlobalOff** da **ProcessOn**, **ProcessOff**, **ThreadOn**ve **ThreadOff** seçenekleri ile kombine edilebilir.

 **GlobalOn** ve **GlobalOff** seçenekleri, belirli bir işlem için veri toplamayı kontrol eden **ProcessOn** ve **ProcessOff** seçenekleri yle ve belirli bir iş parçacığı için veri toplamayı kontrol eden **ThreadOn** ve **ThreadOff** seçenekleriyle etkileşime girsin.

 **GlobalOff** ve **GlobalOn** seçenekleri, profiloluşturucunun API işlevleri tarafından manipüle edilen Global Start/Stop sayısını da etkiler.

- **GlobalOff,** Global Start/Stop Count'u hemen 0 olarak ayarlar ve bu nedenle profil oluşturmayı duraklatabilir.

- **GlobalOn,** Global Start/Stop Count'u hemen 1 olarak ayarlar ve bu nedenle profil oluşturmaya devam eder.

  Daha fazla bilgi için [Profil oluşturma araçları API'leri'ne](../profiling/profiling-tools-apis.md)bakın.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /{GlobalOff|GlobalOn}

VSPerfCmd.exe /Start:Method /{GlobalOff|GlobalOn} [Options]

VSPerfCmd.exe {Launch:AppName|Attach:PID} /{GlobalOff|GlobalOn}[Options]
```

#### <a name="parameters"></a>Parametreler
 None

## <a name="valid-options"></a>Geçerli Seçenekler
 **GlobalOn** ve **GlobalOff,** aşağıdaki seçenekleri de içeren komut satırlarında belirtilebilir.

 **Başlangıç:** `Method` Komut satırı profil oluşturucu oturumunu başlatir ve belirtilen profil oluşturma yöntemini ayarlar.

 **Başlatma:** `AppName` Belirtilen uygulamayı başlatır ve örnekleme yöntemiyle profil oluşturmaya başlar.

 **Ekle:** `PID` Belirtilen işlemin profilini çıkarmaya başlar.

 {**ProcessOff**&#124;**ProcessOn**} **:** `PID` Belirtilen işlem için profil oluşturmayı durdurur veya başlatır.

 {**ThreadOff**&#124;**ThreadOn**} **:** `TID` Belirtilen işlem için profil oluşturmayı durdurur veya başlatır (yalnızca enstrümantasyon yöntemi).

## <a name="example"></a>Örnek
 Bu örnekte, **GlobalOff** ve **GlobalOn** seçenekleri, uygulama başlatma ve kapatma için profil oluşturma verilerini toplamayı önlemek için kullanılır.

```cmd
; Initialize the profiler with profiling stopped.
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp /GlobalOff
; Start an instrumented application and wait for it to warm up.
; Start profiling.
VSPerfCmd.exe /GlobalOn
; Exercise the application functionality that you want to profile.
; Stop profiling.
VSPerfCmd.exe /GlobalOff
; Shut down the target application.
; Close the profiler.
VSPerfCmd /Shutdown

```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profil tek başına uygulamalar](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Web uygulamaları ASP.NET profil](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
