---
title: Profil oluşturma komut satırı - Yerel istemci uygulamasını açın, eşzamanlılık verilerini al
description: Yerel bir tek başına istemci Visual Studio Profil Oluşturma Araçları ve işlem ve iş parçacığı eşzamanlılık verileri toplamak için komut satırı araçlarını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e5aed651-afed-4b70-9a7e-1a6032cc614f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: cd633c38efd241f1721f35ef0153826604a18661
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122141889"
---
# <a name="how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line"></a>Nasıl yapılır: Komut satırını kullanarak eşzamanlılık verileri toplamak için bağımsız bir yerel uygulamayı başlatma
Bu konuda, yerel bir tek Profil Oluşturma Araçları (istemci) uygulaması başlatmak ve işlem ve iş parçacığı eşzamanlılık verileri toplamak için tek başına komut satırı araçlarının [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nasıl kullanımı açıklanmıştır.

 Profil oluşturma oturumu aşağıdaki bölümleri içerir:

- Uygulamayı profil oluşturma ile başlatma

- Veri toplamayı denetleme

- Profil oluşturma oturumunu sonlandırma

> [!NOTE]
> Profil oluşturma araçlarının yolunu almak için [bkz. Komut satırı araçlarının yolunu belirtme.](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md) 64 bit bilgisayarlarda, araçların hem 64 bit hem de 32 bit sürümleri kullanılabilir. Profil oluşturma komut satırı araçlarını kullanmak için, araç yolunu Komut İstemi penceresinin PATH ortam değişkenine eklemeniz veya komutun kendisine eklemeniz gerekir.

## <a name="start-the-application-with-the-profiler"></a>Uygulamayı profil oluşturma ile başlatma
 Profilleyici ile bir hedef uygulamayı başlatmak [](../profiling/vsperfcmd.md)içinVSPerfCmd.exe **ve /launch** seçeneklerini kullanarak Profiler'i başlatarak uygulamayı başlatabilirsiniz.  **/start ve /launch** **seçeneklerini ve** bunların seçeneklerini belirtebilirsiniz. Hedef uygulamanın başında veri toplamayı duraklatmak için **/globaloff** seçeneğini de ekebilirsiniz. Ardından veri **toplamaya başlamak için /globalon** kullanırsanız.

#### <a name="to-start-an-application-with-the-profiler"></a>Bir uygulamayı profil oluşturma ile başlatmak için

1. Komut isteminde aşağıdaki komutu yazın:

     [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency /output:** `OutputFile` [ `Options` ]

     [/output](../profiling/output.md)**: seçeneği** / start ile `OutputFile` **gereklidir.** `OutputFile` profil oluşturma verileri (.vsp) dosyasının adını ve konumunu belirtir.

     Aşağıdaki tabloda yer alan seçeneklerden herhangi birini **/start:concurrency seçeneğiyle kullanabilirsiniz.**

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/wincounter:](../profiling/wincounter.md) `WinCounterPath`|Profil oluşturma Windows toplanacak bir performans sayacı belirtir.|
    |[/automark:](../profiling/automark.md) `Interval`|Yalnızca **/wincounter ile** kullanın. Performans sayacı toplama olayları arasındaki milisaniye Windows sayısını belirtir. Varsayılan değer 500'dür.|
    |[/events](../profiling/events-vsperfcmd.md) **:**`Config`|Profil oluşturma sırasında toplanacak Windows (ETW) olayı için bir Olay İzleme belirtir. ETW olayları ayrı bir (.etl) dosyasında toplanır.|

2. Aşağıdakini yazarak hedef uygulamayı başlatma:

     **VSPerfCmd**[/launch:](../profiling/launch.md)  `AppName` [ `Options` ]  

     Aşağıdaki tabloda yer alan seçeneklerden herhangi birini **/launch seçeneğiyle kullanabilirsiniz.**

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/args:](../profiling/args.md) `Arguments`|Hedef uygulamaya geçirilen komut satırı bağımsız değişkenlerini içeren bir dize belirtir.|
    |[/console](../profiling/console.md)|Hedef komut satırı uygulamasını ayrı bir pencerede başlatır.|
    |[/targetclr](../profiling/targetclr.md) **:**`CLRVersion`|Uygulama CLR'nin birden fazla sürümünü yüklerse profili oluşturmak için ortak dil çalışma zamanının (CLR) sürümünü belirtir.|

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hedef uygulama çalışırken, veri toplamayı, veri toplama seçenekleriyle dosyada veri yazmayı başlatarak *ve durdurarakVSPerfCmd.exe* yapabilirsiniz. Veri toplamayı denetleyerek, uygulamanın başlatılıyor veya kapatılıyor gibi program yürütmenin belirli bir bölümü için veri toplayabilirsiniz.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki tabloda yer alan seçenek çiftleri veri toplamayı başlatacak ve durduracak. Her seçeneği ayrı bir komut satırı üzerinde belirtin. Veri toplamayı birden çok kez açabilirsiniz ve kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Tüm işlemler **için veri toplamayı** başlatır ( /globalon ) veya durdurur (**/globaloff).**|
    |[/processon:](../profiling/processon-and-processoff.md)  `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|İşlem kimliğinin ( ) tarafından belirtilen işlem için veri toplamayı başlatır (**/processon**) veya durdurur (**/processoff).** `PID`|
    |[/attach:](../profiling/attach.md) { `PID`&#124;`ProcName` } [/detach](../profiling/detach.md)[**:**{ `PID`&#124;`ProcName` }]|**/attach,** işlem kimliği ( ) veya işlem adı ( `PID` *ProcName*) tarafından belirtilen işlem için veri toplamaya başlar. **/detach,** belirtilen işlem için veya herhangi bir işlem belirtilmezse tüm işlemler için veri toplamayı durdurur.|

- Veri dosyasına profil **VSPerfCmd.exe** [/mark](../profiling/mark.md) seçeneğini de kullanabilirsiniz. **/mark komutu** bir tanımlayıcı, zaman damgası ve isteğe bağlı bir kullanıcı tanımlı metin dizesi ekler. İşaretler, profil oluşturma raporlarında ve veri görünümlerde verileri filtrelemek için kullanılabilir.

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sona er
 Profil oluşturma oturumunu sona erdirecek şekilde, profil oluşturmanın veri toplaması gerekir. Profili yapılan uygulamayı kapatarak veya **VSPerfCmd /detach** seçeneğini kullanarak eşzamanlılık verilerini toplamayı durdurabilirsiniz. Ardından **VSPerfCmd /shutdown** seçeneğini çağırarak profil oluşturma verilerini kapatabilirsiniz.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdir

1. Profil oluşturma profilini kapatarak veya komut istemine aşağıdaki komutu yazarak hedef uygulamadan ayırabilirsiniz:

     **VSPerfCmd /detach**

2. Komut istemine aşağıdaki komutu yazarak profil oluşturma profilini kapatın:

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)