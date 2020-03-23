---
title: ProcessOn ve ProcessOff | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d3dc6a7e-bc0f-48a6-a4ec-f386348bb296
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 62c16c2d578a38187b4a58958466597a5e4d297d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778394"
---
# <a name="processon-and-processoff"></a>ProcessOn ve ProcessOff
VSPerfCmd.exe **ProcessOff** ve **ProcessOn** alt komutları bir komut satırı profil oluşturma oturumunda belirtilen işlem için profil oluşturmayı duraklatabilir ve devam ettirin. **ProcessOff** işlemin profilini çıkarmayı durdurur ve **ProcessOn** işlemin profilini çıkarmaya başlar.

 Çoğu durumda, Bir VSPerfCmd.exe komut satırında tek seçenek olarak **ProcessOn** veya **ProcessOff** belirtin, ancak onlar da **GlobalOn**ile kombine edilebilir , **GlobalOff**, **ThreadOn**, ve **ThreadOff** alt komutları.

 **ProcessOn** ve **ProcessOff** alt komutları, komut satırı profil oluşturma oturumundaki tüm işlemler için veri toplamayı kontrol eden **GlobalOn** ve **GlobalOff** alt komutları ile ve belirli bir iş parçacığı için veri toplamayı kontrol eden **ThreadOn** ve **ThreadOff** alt komutlarıyla etkileşime girmektedir.

 **ProcessOff** ve **ProcessOn** alt komutları, profil oluşturucu API işlevleri tarafından manipüle edilen İşlem Başlat/Durdur sayısını da etkiler.

- **ProcessOff,** İşlem Başlat/Durdur Sayısını hemen 0 olarak ayarlar ve bu nedenle profil oluşturmayı duraklatabilir.

- **ProcessOn** hemen İşlem Başlat/Durdur Sayısını 1 olarak ayarlar ve bu nedenle profil oluşturmaişlemine devam eder.

  Daha fazla bilgi için [Profil Oluşturma Araçları API'leri'ne](../profiling/profiling-tools-apis.md)bakın.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /{ProcessOff|ProcessOn}:PID [Options]

```

#### <a name="parameters"></a>Parametreler
 `PID`İşlemin başlangıç veya durdurma işleminin karşıt tanımlayıcısı. İşlem işleri Windows Gürüden'in **Süre**

## <a name="required-subcommands"></a>Gerekli Alt Komutlar
 None

## <a name="valid-subcommands"></a>Geçerli Alt Komutlar
 **ProcessOn** ve **ProcessOff,** aşağıdaki alt komutları da içeren komut satırlarında belirtilebilir.

 **Başlangıç:** `Method` Komut satırı profil oluşturma oturumunu başlatir ve belirtilen profil oluşturma yöntemini ayarlar.

 **Başlatma:** `AppName` Belirtilen uygulamayı başlatır ve örnekleme yöntemiyle profil oluşturmaya başlar.

 **Ekle:** `PID` Belirtilen işlemin profilini çıkarmaya başlar.

 **GlobalOff**&#124;**GlobalOn,** komut satırı profil oluşturma oturumundaki tüm işlemler için profil oluşturmayı durdurur veya başlatır.

 {**ThreadOff**&#124;**ThreadOn**} **:** `TID` Belirtilen iş parçacığı için profil oluşturmayı durdurur veya başlatır (yalnızca enstrümantasyon yöntemi).

## <a name="example"></a>Örnek
 Bu örnekte, **ProcessOff** alt komutu uygulama başlatma için profil oluşturma verileri toplamak için kullanılır.

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
- [Profil tek başına uygulamalar](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Web uygulamaları ASP.NET profil](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
