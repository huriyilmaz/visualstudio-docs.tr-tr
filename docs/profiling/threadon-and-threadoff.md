---
title: ThreadOn ve ThreadOff | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 5cd5a695-0a14-484a-8952-ed47e13d8e92
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 906629eb24f6be097f3e24dfca3e6a231f42357f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778160"
---
# <a name="threadon-and-threadoff"></a>ThreadOn ve ThreadOff
*VSPerfCmd.exe* **ThreadOff** ve **ThreadOn** alt komutları yalnızca enstrümantasyon yöntemini kullanan komut satırı profil leme oturumlarında kullanılabilir. **ThreadOff** ve **ThreadOn** duraklatma ve belirtilen iş parçacığı için profil oluşturma devam. **ThreadOff** iş parçacığı profilleme durur ve **ThreadOn** iş parçacığı profilbaşlar.

 Çoğu durumda, *Bir VSPerfCmd.exe* komut satırında tek seçenek olarak **ThreadOn** veya **ThreadOff** belirtin, ancak onlar da **GlobalOn**ile kombine edilebilir , **GlobalOff**, **ProcessOn**, ve **ProcessOff** alt komutları.

 **ThreadOn** ve **ThreadOff** alt komutları, komut satırı profil oluşturma oturumundaki tüm işlemler için veri toplamayı kontrol eden **GlobalOn** ve **GlobalOff** alt komutları ile ve belirli bir işlem için veri toplamayı kontrol eden **ProcessOn** ve **ProcessOff** alt komutlarıyla etkileşime girmektedir.

 **ThreadOff** ve **ThreadOn** alt komutları, profil oluşturucu API işlevleri tarafından manipüle edilen İş Parçacığı Başlangıç/Durdurma sayısını da etkiler.

- **ThreadOff,** İş Parçacığı Başlangıç/Durdur Sayısını hemen 0 olarak ayarlar ve bu nedenle profil oluşturmayı duraklatabilir.

- **ThreadOn** hemen İş Parçacığı Başlangıç/Durdur Sayısı'nı 1 olarak ayarlar ve bu nedenle profil oluşturmaişlemine devam eder.

  Daha fazla bilgi için [Profil oluşturma araçları API'leri'ne](../profiling/profiling-tools-apis.md)bakın.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /{ThreadOff|ThreadOn}:TID [Options]

```

#### <a name="parameters"></a>Parametreler
 `TID`Başlayacak veya durdurmak için iş parçacığının tümseci tanımlayıcısı.

## <a name="valid-options"></a>Geçerli seçenekler
 **ThreadOn** ve **ThreadOff,** aşağıdaki alt komutları da içeren komut satırlarında belirtilebilir.

 **Başlangıç:** `Method` Komut satırı profil oluşturma oturumunu başlatir ve belirtilen profil oluşturma yöntemini ayarlar.

 **GlobalOff**&#124;**GlobalOn,** komut satırı profil oluşturma oturumundaki tüm işlemler için profil oluşturmayı durdurur veya başlatır.

 {**ProcessOff**&#124;**ProcessOn**} **:** `TID` Belirtilen işlem için profil oluşturmayı durdurur veya başlatır.

## <a name="example"></a>Örnek
 Bu örnekte, **ThreadOff** alt komutu, yalnızca uygulama başlangıç verilerinin toplanması için profil oluşturma verilerini durdurmak için kullanılır.

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
- [Profil tek başına uygulamalar](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Web uygulamaları ASP.NET profil](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
