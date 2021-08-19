---
title: ThreadOn ve ThreadOff | Microsoft Docs
description: VSPerfCmd.exe ThreadOff ve ThreadOn alt komutlarını yalnızca izleme yöntemini kullanan komut satırı profil oluşturma oturumlarında nasıl kullanabileceğinizi öğrenin.
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
ms.openlocfilehash: 48c40d24c10c4370c8d35eebc89d6b438059f3f9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122157026"
---
# <a name="threadon-and-threadoff"></a>ThreadOn ve ThreadOff
*VSPerfCmd.exe* **ThreadOff** ve **ThreadOn** alt komutları yalnızca, izleme yöntemini kullanan komut satırı profil oluşturma oturumlarında kullanılabilir. Belirtilen iş parçacığı için, duraklatma ve devam etmeyi devam ettirmeye yönelik **ThreadOff** ve **Thread.** **ThreadOff** , iş parçacığının profilini oluşturmayı durduruyor ve **üzerinde Threadın** iş parçacığı profilini oluşturmaya başlar.

 Çoğu durumda, *VSPerfCmd.exe* komut satırında tek seçenek olarak **ThreadOn** veya **ThreadOff** belirtirsiniz, ancak **globalon**, **globaloff**, **ProcessOn** ve **ProcessOff** alt komutları ile de birleştirilebilir.

 **ThreadOn** ve **ThreadOff** alt komutları, bir komut satırı profil oluşturma oturumunda tüm işlemler Için veri toplamayı denetleyen **GlobalOn** ve **globaloff** alt komutları ve belirli bir Işlem Için veri toplamayı denetleyen **ProcessOn** ve **ProcessOff** alt komutları ile etkileşim kurar.

 **ThreadOff** ve **ThreadOn** alt komutları Ayrıca profil oluşturucu API Işlevleri tarafından yönetilen Iş parçacığı başlatma/durdurma sayısını da etkiler.

- **ThreadOff** Iş parçacığı başlatma/durdurma sayısını hemen 0 olarak ayarlar ve bu nedenle profil oluşturmayı duraklatır.

- **ThreadOn** hemen Iş parçacığı başlatma/durdurma sayısını 1 olarak ayarlar ve bu nedenle profil oluşturmayı sürdürür.

  Daha fazla bilgi için bkz. [profil oluşturma araçları API 'leri](../profiling/profiling-tools-apis.md).

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /{ThreadOff|ThreadOn}:TID [Options]

```

#### <a name="parameters"></a>Parametreler
 `TID` Başlatılacak veya durdurulacak iş parçacığının tamsayı tanımlayıcısı.

## <a name="valid-options"></a>Geçerli seçenekler
 Aşağıdaki alt komutları da içeren komut satırlarında **ThreadOn** ve **ThreadOff** belirtilebilir.

 **Başlangıç:** `Method` Komut satırı profil oluşturma oturumunu başlatır ve belirtilen profil oluşturma yöntemini ayarlar.

  Globalon&#124;**GlobalOn** , komut satırı profil oluşturma oturumunda tüm işlemlerde profil oluşturmayı durduruyor veya başlatır.

 {**ProcessOff**&#124;**ProcessOn**} **:**`TID` Belirtilen işlem için profil oluşturmayı durduruyor veya başlatır.

## <a name="example"></a>Örnek
 Bu örnekte, yalnızca uygulama başlatma verilerinin toplanması için profil oluşturma verilerinin toplanmasını durdurmak üzere **ThreadOff** alt komutu kullanılır.

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
- [Tek başına uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [web uygulamalarının profilini ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
