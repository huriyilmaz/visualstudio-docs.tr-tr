---
title: ThreadOn ve ThreadOff | Microsoft Docs
description: ThreadOff VSPerfCmd.exe ThreadOn alt komutlarının yalnızca instrumentation yöntemini kullanan komut satırı profil oluşturma oturumlarında nasıl kullanılabilir olduğunu öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 5cd5a695-0a14-484a-8952-ed47e13d8e92
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 42bd10647ce5ba9a6e1a62a8c1df17f204a086ddab2583cd1107c9897693d1e5
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121396363"
---
# <a name="threadon-and-threadoff"></a>ThreadOn ve ThreadOff
**ThreadOff** *VSPerfCmd.exe* **ThreadOn** alt komutlarını yalnızca, ölçüm yöntemini kullanan komut satırı profil oluşturma oturumlarında kullanılabilir. **ThreadOff** ve **ThreadOn belirtilen** iş parçacığı için profil oluşturmayı duraklatma ve sürdürme. **ThreadOff,** iş parçacığının profilini oluşturmayı durdurur ve **ThreadOn** iş parçacığının profilini oluşturmayı başlatır.

 Çoğu durumda, bir *VSPerfCmd.exe* komut satırı içinde tek seçenek olarak **ThreadOn** veya **ThreadOff** belirtirsiniz, ancak **bunlar GlobalOn,** **GlobalOff,** **ProcessOn** ve **ProcessOff** alt komutlarla da birleştirilmiş olabilir.

 **ThreadOn** ve **ThreadOff** alt komutlarının, bir komut satırı profil oluşturma oturumunda tüm işlemler için veri toplamayı kontrol eden **GlobalOn** ve **GlobalOff** alt komutlarıyla ve belirtilen bir işlem için veri toplamayı kontrol eden **ProcessOn** ve **ProcessOff** alt komutlarıyla etkileşime geçmeleri.

 **ThreadOff ve** **ThreadOn** alt işlevleri, profil oluşturma API'si işlevleri tarafından yönlendiren İş Parçacığı Başlatma/Durdurma sayısını da etkiler.

- **ThreadOff,** İş Parçacığı Başlatma/Durdurma Sayısını hemen 0 olarak ayarlar ve bu nedenle profil oluşturmayı duraklatar.

- **ThreadOn,** İş Parçacığı Başlatma/Durdurma Sayısını hemen 1 olarak ayarlar ve bu nedenle profil oluşturmayı sürdürür.

  Daha fazla bilgi için [bkz. Profil oluşturma araçları API'leri.](../profiling/profiling-tools-apis.md)

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /{ThreadOff|ThreadOn}:TID [Options]

```

#### <a name="parameters"></a>Parametreler
 `TID` Başlat veya durduracak iş parçacığının tamsayı tanımlayıcısı.

## <a name="valid-options"></a>Geçerli seçenekler
 **ThreadOn** ve **ThreadOff,** aşağıdaki alt komutlar da içeren komut satırlarında belirtilebilir.

 **Başlat:** `Method` Komut satırı profil oluşturma oturumunu başlatılır ve belirtilen profil oluşturma yöntemini ayarlar.

 **GlobalOff**&#124;**GlobalOn komut** satırı profil oluşturma oturumunda tüm işlemler için profil oluşturmayı durdurur veya başlatır.

 {**ProcessOff**&#124;**ProcessOn**} **:**`TID` Belirtilen işlem için profil oluşturmayı durdurur veya başlatır.

## <a name="example"></a>Örnek
 Bu örnekte, **yalnızca uygulama başlatma** verileri toplanacak şekilde profil oluşturma verilerini toplamayı durdurmak için ThreadOff altkod kullanılır.

```cmd
; Initialize the profiler.
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp
; Start the instrumented application.
; Stop profiling the thread after startup.
VSPerfCmd.exe /ThreadOff:12345
; Shut down the target application.
; Close the profiler.
VSPerfCmd /Shutdown

```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Web ASP.NET profil oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
