---
title: ThreadOn ve ThreadOff | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 5cd5a695-0a14-484a-8952-ed47e13d8e92
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 77868ea7082c1b9118b70062f19195d94b4ca20a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145551"
---
# <a name="threadon-and-threadoff"></a>ThreadOn ve ThreadOff
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPerfCmd.exe **ThreadOff** ve **ThreadOn** alt komutları yalnızca, izleme yöntemini kullanan komut satırı profil oluşturma oturumlarında kullanılabilir. Belirtilen iş parçacığı için, duraklatma ve devam etmeyi devam ettirmeye yönelik **ThreadOff** ve **Thread.** **ThreadOff** , iş parçacığının profilini oluşturmayı durduruyor ve **üzerinde Threadın** iş parçacığı profilini oluşturmaya başlar.  
  
 Çoğu durumda, VSPerfCmd.exe komut satırında tek seçenek olarak **ThreadOn** veya **ThreadOff** belirtirsiniz, ancak **GlobalOn**, **globaloff**, **ProcessOn**ve **ProcessOff** alt komutları ile de birleştirilebilir.  
  
 **ThreadOn** ve **ThreadOff** alt komutları, bir komut satırı profil oluşturma oturumunda tüm işlemler Için veri toplamayı denetleyen **GlobalOn** ve **globaloff** alt komutları ve belirli bir Işlem Için veri toplamayı denetleyen **ProcessOn** ve **ProcessOff** alt komutları ile etkileşim kurar.  
  
 **ThreadOff** ve **ThreadOn** alt komutları Ayrıca profil oluşturucu API Işlevleri tarafından yönetilen Iş parçacığı başlatma/durdurma sayısını da etkiler.  
  
- **ThreadOff** Iş parçacığı başlatma/durdurma sayısını hemen 0 olarak ayarlar ve bu nedenle profil oluşturmayı duraklatır.  
  
- **ThreadOn** hemen Iş parçacığı başlatma/durdurma sayısını 1 olarak ayarlar ve bu nedenle profil oluşturmayı sürdürür.  
  
  Daha fazla bilgi için bkz. [profil oluşturma araçları API 'leri](../profiling/profiling-tools-apis.md).  
  
## <a name="syntax"></a>Söz dizimi  
  
```  
VSPerfCmd.exe /{ThreadOff|ThreadOn}:TID [Options]  
  
```  
  
#### <a name="parameters"></a>Parametreler  
 `TID`  
 Başlatılacak veya durdurulacak iş parçacığının tamsayı tanımlayıcısı.  
  
## <a name="valid-options"></a>Geçerli seçenekler  
 Aşağıdaki alt komutları da içeren komut satırlarında **ThreadOn** ve **ThreadOff** belirtilebilir.  
  
 **Başlangıç:**`Method`  
 Komut satırı profil oluşturma oturumunu başlatır ve belirtilen profil oluşturma yöntemini ayarlar.  
  
 **GlobalOff** Globalon&#124;**GlobalOn**  
 Komut satırı profil oluşturma oturumunda tüm süreçler için profil oluşturmayı durduruyor veya başlatır.  
  
 {**ProcessOff**&#124;**ProcessOn**} **:**`TID`  
 Belirtilen işlem için profil oluşturmayı durduruyor veya başlatır.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, yalnızca uygulama başlatma verilerinin toplanması için profil oluşturma verilerinin toplanmasını durdurmak üzere **ThreadOff** alt komutu kullanılır.  
  
```  
; Initialize the profiler.  
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp   
; Start the instrumented application.  
; Stop profiling the thread after startup.  
VSPerfCmd.exe /ThreadOff:12345  
; Shut down the target application.  
; Close the profiler.  
VSPerfCmd /Shutdown  
  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web uygulamalarının profilini oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profil Oluşturma Hizmetleri](../profiling/command-line-profiling-of-services.md)
