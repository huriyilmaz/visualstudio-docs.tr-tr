---
title: ProcessOn ve ProcessOff | Microsoft Docs
description: ProcessOff ve ProcessOn VSPerfCmd.exe komut satırı profil oluşturma oturumunda belirtilen işlem için profil oluşturmayı duraklatma ve sürdürme hakkında bilgi edinmek.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d3dc6a7e-bc0f-48a6-a4ec-f386348bb296
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c61f997d0c006c9cc29850be65555fe5b5dc9d04
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122131241"
---
# <a name="processon-and-processoff"></a>ProcessOn ve ProcessOff
**ProcessOff** VSPerfCmd.exe **ProcessOn** alt komutlarında, bir komut satırı profil oluşturma oturumunda belirtilen işlem için profil oluşturma duraklatılır ve sürdürılır. **ProcessOff,** işlem profilini oluşturmayı durdurur ve **ProcessOn** işlemi profil oluşturmayı başlatır.

 Çoğu durumda, bir VSPerfCmd.exe komut satırı içinde tek seçenek olarak **ProcessOn** veya **ProcessOff** belirtirsiniz, ancak **bunlar GlobalOn,** **GlobalOff,** **ThreadOn** ve **ThreadOff** alt komutlarla da birleştirilmiş olabilir.

 **ProcessOn** ve **ProcessOff** alt komutlarının, bir komut satırı profil oluşturma oturumunda tüm işlemler için veri toplamayı kontrol eden **GlobalOn** ve **GlobalOff** alt komutlarıyla ve belirtilen bir iş parçacığı için veri toplamayı kontrol eden **ThreadOn** ve **ThreadOff** alt komutlarıyla etkileşime geçmeleri.

 **ProcessOff ve** **ProcessOn** alt işlevleri, profil oluşturma API'si işlevleri tarafından yönlendiren İşlem Başlatma/Durdurma sayısını da etkiler.

- **ProcessOff,** İşlem Başlatma/Durdurma Sayısını hemen 0 olarak ayarlar ve bu nedenle profil oluşturmayı duraklatar.

- **ProcessOn,** İşlem Başlatma/Durdurma Sayısını hemen 1 olarak ayarlar ve bu nedenle profil oluşturmayı sürdürür.

  Daha fazla bilgi için [bkz. Profil Oluşturma Araçları API'leri.](../profiling/profiling-tools-apis.md)

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /{ProcessOff|ProcessOn}:PID [Options]

```

#### <a name="parameters"></a>Parametreler
 `PID` Başlatma veya durdurma işleminin tamsayı tanımlayıcısı. İşlem kimlikleri, Görev **Yöneticisi'nin** Windows listelenir.

## <a name="required-subcommands"></a>Gerekli AltCommands
 Hiçbiri

## <a name="valid-subcommands"></a>Geçerli AltCommands
 **ProcessOn** **ve ProcessOff,** aşağıdaki alt komutlar da içeren komut satırlarında belirtilebilir.

 **Başlat:** `Method` Komut satırı profil oluşturma oturumunu başlatılır ve belirtilen profil oluşturma yöntemini ayarlar.

 **Başlatma:** `AppName` Belirtilen uygulamayı başlatır ve örnekleme yöntemiyle profil oluşturmayı başlatır.

 **Ekleme:** `PID` Belirtilen işlem profilini oluşturmayı başlar.

 **GlobalOff**&#124;**GlobalOn** komut satırı profil oluşturma oturumunda tüm işlemler için profil oluşturmayı durdurur veya başlatır.

 {**ThreadOff**&#124;**ThreadOn**} **:**`TID` Belirtilen iş parçacığı için profil oluşturmayı durdurur veya başlatır (yalnızca ölçüm yöntemi).

## <a name="example"></a>Örnek
 Bu örnekte, uygulama başlatma için profil oluşturma verilerini toplamak için **ProcessOff** altkod kullanılır.

```cmd
; Initialize the profiler.
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp
; Start the instrumented application.
; Stop profiling the process after startup.
VSPerfCmd.exe /ProcessOff:12345
; Shut down the target application.
; Close the profiler.
VSPerfCmd /Shutdown

```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Web ASP.NET profil oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
