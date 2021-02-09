---
title: GlobalOn ve GlobalOff | Microsoft Docs
description: VSPerfCmd.exe 'teki GlobalOn ve GlobalOff seçeneklerini gözden geçirin. Bu seçenekler, komut satırı profil oluşturma oturumunda süreçler ve iş parçacıkları için profil oluşturmayı duraklatır ve devam ettirir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 24b0ed68-d19e-473e-9af3-252c11d82bcf
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c940cc06142fc69460ed1e4a32303a6e3f919164
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907295"
---
# <a name="globalon-and-globaloff"></a>GlobalOn ve GlobalOff
*VSPerfCmd.exe* **globaloff** ve **GlobalOn** seçenekleri, komut satırı profil oluşturma oturumunda tüm süreçler ve iş parçacıkları için profil oluşturmayı duraklatır ve devam ettirir.

 *VSPerfCmd.exe* komut satırında tek seçenekler olarak **GlobalOn** ve **globaloff** belirtebilir ya da bunları **Başlat**, **Başlat** veya **Ekle** seçeneklerini içeren komut satırlarına dahil edebilirsiniz.

 **GlobalOn** ve **globaloff** Ayrıca **ProcessOn**, **ProcessOff**, **ThreadOn** ve **ThreadOff** seçenekleriyle birleştirilebilir.

 **GlobalOn** ve **globaloff** seçenekleri, belirtilen bir işlem Için veri toplamayı denetleyen **ProcessOn** ve **ProcessOff** seçenekleriyle, belirtilen Iş parçacığı Için de veri toplamayı denetleyen **ThreadOn** ve **ThreadOff** seçenekleriyle etkileşime geçin.

 **Globaloff** ve **GlobalOn** SEÇENEKLERI Ayrıca profil oluşturucunun API Işlevleri tarafından yönetilen genel başlatma/durdurma sayısını da etkiler.

- **Globaloff** , genel Başlat/Durdur sayısını hemen 0 olarak ayarlar ve bu nedenle profil oluşturmayı duraklatır.

- **GlobalOn** , genel Başlat/Durdur sayısını hemen 1 olarak ayarlar ve bu nedenle profil oluşturma işlemine devam eder.

  Daha fazla bilgi için bkz. [profil oluşturma araçları API 'leri](../profiling/profiling-tools-apis.md).

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /{GlobalOff|GlobalOn}

VSPerfCmd.exe /Start:Method /{GlobalOff|GlobalOn} [Options]

VSPerfCmd.exe {Launch:AppName|Attach:PID} /{GlobalOff|GlobalOn}[Options]
```

#### <a name="parameters"></a>Parametreler
 Hiçbiri

## <a name="valid-options"></a>Geçerli seçenekler
 **GlobalOn** ve **globaloff** , aşağıdaki seçenekleri de içeren komut satırlarında belirtilebilir.

 **Başlangıç:** `Method` Komut satırı profil oluşturucu oturumunu başlatır ve belirtilen profil oluşturma yöntemini ayarlar.

 **Başlatma:** `AppName` Belirtilen uygulamayı başlatır ve örnekleme yöntemiyle profil oluşturmaya başlar.

 **Ekle:** `PID` Belirtilen işlemin profilini oluşturmaya başlıyor.

 {**ProcessOff**&#124;**ProcessOn**} **:**`PID` Belirtilen işlem için profil oluşturmayı durduruyor veya başlatır.

 {**ThreadOff**&#124;**ThreadOn**} **:**`TID` Belirtilen işlem için profil oluşturmayı durduruyor veya başlatır (yalnızca izleme yöntemi).

## <a name="example"></a>Örnek
 Bu örnekte, uygulama başlatma ve kapatma için profil oluşturma verilerinin toplanmasını önlemek için **globaloff** ve **GlobalOn** seçenekleri kullanılır.

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
- [Tek başına uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET Web uygulamaları profili](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
