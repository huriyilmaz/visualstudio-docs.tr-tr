---
title: ProcessOn ve ProcessOff | Microsoft Docs
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778394"
---
# <a name="processon-and-processoff"></a>ProcessOn ve ProcessOff
VSPerfCmd. exe **ProcessOff** ve **ProcessOn** alt komutları, komut satırı profil oluşturma oturumunda belirtilen işlem için profil oluşturmayı duraklatır ve devam ettirir. **ProcessOff** işlemin profilini oluşturmayı durduruyor ve **ProcessOn** , işlemin profilini oluşturmaya başlar.

 Çoğu durumda, bir VSPerfCmd. exe komut satırında tek seçenek olarak **ProcessOn** veya **ProcessOff** belirtirsiniz, ancak **GlobalOn**, **globaloff**, **ThreadOn**ve **ThreadOff** alt komutları ile de birleştirilebilir.

 **ProcessOn** ve **ProcessOff** alt komutları, bir komut satırı profil oluşturma oturumunda tüm işlemlere yönelik veri toplamayı denetleyen **GlobalOn** ve **globaloff** alt komutları ve belirtilen bir iş parçacığı Için veri toplamayı denetleyen **ThreadOn** ve **ThreadOff** alt komutları ile etkileşime geçin.

 **ProcessOff** ve **ProcessOn** alt komutları Ayrıca, profil oluşturucu API Işlevleri tarafından yönetilen işlem başlatma/durdurma sayısını da etkiler.

- **ProcessOff** , işlem başlatma/durdurma sayısını hemen 0 olarak ayarlar ve bu nedenle profil oluşturmayı duraklatır.

- **ProcessOn** , işlem başlatma/durdurma sayısını 1 olarak ayarlar ve bu nedenle profil oluşturma işlemine devam eder.

  Daha fazla bilgi için bkz. [profil oluşturma araçları API 'leri](../profiling/profiling-tools-apis.md).

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /{ProcessOff|ProcessOn}:PID [Options]

```

#### <a name="parameters"></a>Parametreler
 başlatılacak veya durdurulacak işlemin tamsayı tanımlayıcısını `PID`. İşlem kimlikleri Windows Görev Yöneticisi 'nin **işlem** sekmesinde listelenir.

## <a name="required-subcommands"></a>Gerekli alt komutlar
 Yok.

## <a name="valid-subcommands"></a>Geçerli alt komutlar
 Aşağıdaki alt komutları da içeren komut satırlarında **ProcessOn** ve **ProcessOff** belirtilebilir.

 **Başlat:** `Method` komut satırı profil oluşturma oturumunu başlatır ve belirtilen profil oluşturma yöntemini ayarlar.

 **Başlatma:** `AppName` belirtilen uygulamayı başlatır ve örnekleme yöntemiyle profil oluşturmaya başlar.

 **Attach:** `PID` belirtilen işlemin profilini oluşturmaya başlıyor.

 **Globaloff**&#124;**GlobalOn** , komut satırı profil oluşturma oturumunda tüm işlemlerde profil oluşturmayı durduruyor veya başlatır.

 {**ThreadOff**&#124;**ThreadOn**} **:** `TID` belirtilen iş parçacığı için profil oluşturmayı durduruyor veya başlatır (yalnızca izleme yöntemi).

## <a name="example"></a>Örnek
 Bu örnekte, uygulama başlatma için profil oluşturma verilerini toplamak üzere **ProcessOff** alt komutu kullanılır.

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
- [Tek başına uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET Web uygulamaları profili](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
