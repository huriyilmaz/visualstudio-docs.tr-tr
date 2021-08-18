---
title: GlobalOn ve GlobalOff | Microsoft Docs
description: Aşağıdaki seçeneklerde GlobalOn ve GlobalOff VSPerfCmd.exe. Bu seçenekler, bir komut satırı profil oluşturma oturumunda işlemler ve iş parçacıkları için profil oluşturmayı duraklatma ve sürdürme.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 24b0ed68-d19e-473e-9af3-252c11d82bcf
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 93d20cd77d5aa6bde02a8bef922a21bdbf997e8f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122131501"
---
# <a name="globalon-and-globaloff"></a>GlobalOn ve GlobalOff
**GlobalOff** *VSPerfCmd.exe* **GlobalOn** seçenekleri, bir komut satırı profil oluşturma oturumunda tüm işlemler ve iş parçacıkları için profil oluşturmayı duraklatma ve sürdürme.

 GlobalOn  ve **GlobalOff** komutVSPerfCmd.exetek  seçenek olarak belirtebilirsiniz veya bunları **Başlat,** Başlat veya Ekle seçeneklerini de içeren komut satırlarına  dahilebilirsiniz.

 **GlobalOn** **ve GlobalOff,** **ProcessOn,** **ProcessOff,** **ThreadOn** ve **ThreadOff seçenekleriyle de birleştirilmiş** olabilir.

 **GlobalOn** ve **GlobalOff** seçenekleri, belirli bir işlem için veri toplamayı kontrol etmek üzere **ProcessOn** ve **ProcessOff** seçenekleriyle ve belirtilen bir iş parçacığı için veri toplamayı kontrol alan **ThreadOn** ve **ThreadOff** seçenekleriyle etkileşime geçmenizi sağlar.

 **GlobalOff ve** **GlobalOn** seçenekleri, profil oluşturmanın API işlevleri tarafından yönlendiren Genel Başlatma/Durdurma sayısını da etkiler.

- **GlobalOff,** Genel Başlangıç/Durdurma Sayısını hemen 0 olarak ayarlar ve bu nedenle profil oluşturmayı duraklattır.

- **GlobalOn,** Genel Başlangıç/Durdurma Sayısını hemen 1 olarak ayarlar ve bu nedenle profil oluşturmayı sürdürür.

  Daha fazla bilgi için [bkz. Profil oluşturma araçları API'leri.](../profiling/profiling-tools-apis.md)

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /{GlobalOff|GlobalOn}

VSPerfCmd.exe /Start:Method /{GlobalOff|GlobalOn} [Options]

VSPerfCmd.exe {Launch:AppName|Attach:PID} /{GlobalOff|GlobalOn}[Options]
```

#### <a name="parameters"></a>Parametreler
 Hiçbiri

## <a name="valid-options"></a>Geçerli Seçenekler
 **GlobalOn** **ve GlobalOff,** aşağıdaki seçenekleri de içeren komut satırlarında belirtilebilir.

 **Başlat:** `Method` Komut satırı profil oluşturma oturumunu başlatan ve belirtilen profil oluşturma yöntemini ayarlar.

 **Başlatma:** `AppName` Belirtilen uygulamayı başlatır ve örnekleme yöntemiyle profil oluşturmayı başlatır.

 **Ekleme:** `PID` Belirtilen işlem profilini oluşturmayı başlar.

 {**ProcessOff**&#124;**ProcessOn**} **:**`PID` Belirtilen işlem için profil oluşturmayı durdurur veya başlatır.

 {**ThreadOff**&#124;**ThreadOn**} **:**`TID` Belirtilen işlem için profil oluşturmayı durdurur veya başlatır (yalnızca ölçüm yöntemi).

## <a name="example"></a>Örnek
 Bu örnekte, uygulama başlatma ve kapatma için profil oluşturma verilerini toplamayı önlemek için **GlobalOff** ve **GlobalOn** seçenekleri kullanılır.

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
- [Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Web ASP.NET profil oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
