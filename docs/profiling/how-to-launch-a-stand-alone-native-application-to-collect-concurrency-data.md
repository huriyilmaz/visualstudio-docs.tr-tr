---
title: 'Profil oluşturucu komut satırı: yerel istemci uygulamasını açın, eşzamanlılık verilerini alın'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e5aed651-afed-4b70-9a7e-1a6032cc614f
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: 1bb8baed0d9154c02f23738944de2d3e84b7402b
ms.sourcegitcommit: 0c3c4bd38455f7046c5c5a448eaaa5e407ad5bf4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76726041"
---
# <a name="how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line"></a>Nasıl yapılır: komut satırını kullanarak eşzamanlılık verileri toplamak için Profil Oluşturucu ile tek başına yerel uygulamayı başlatma
Bu konu, yerel bir tek başına (istemci) uygulamayı başlatmak ve işlem ve iş parçacığı eşzamanlılık verilerini toplamak için [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Oluşturma Araçları komut satırı araçlarının nasıl kullanılacağını açıklar.

 Profil oluşturma oturumu aşağıdaki bölümlere sahiptir:

- Uygulamayı Profil Oluşturucu ile başlatma

- Veri toplamayı denetleme

- Profil oluşturma oturumu sonlandırılıyor

> [!NOTE]
> Profil oluşturma araçlarının yolunu almak için, bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). 64-bit bilgisayarlarda araçların 64-bit hem 32-bit sürümleri kullanılabilir. Profil oluşturucu komut satırı araçlarını kullanmak için Araçlar yolunu komut istemi penceresinin PATH ortam değişkenine ekleyin veya komutun kendisine eklemeniz gerekir.

## <a name="start-the-application-with-the-profiler"></a>Uygulamayı Profil Oluşturucu ile başlatma
 Bir hedef uygulamayı profil Oluşturucu ile başlatmak için [VSPerfCmd. exe](../profiling/vsperfcmd.md) **/Start** ve **/Launch** seçeneklerini kullanarak profil oluşturucuyu başlatabilir ve uygulamayı başlatabilirsiniz. **/Start** ve **/Launch** ' i ve ilgili seçeneklerini belirtebilirsiniz. Ayrıca ekleyebilirsiniz **/globaloff** hedef uygulamanın başlatıldığı sırada veri toplamayı duraklatma seçeneğinin. Ardından, veri toplamaya başlamak için **/GlobalOn** kullanın.

#### <a name="to-start-an-application-with-the-profiler"></a>Profil Oluşturucu ile bir uygulamayı başlatmak için

1. Bir komut isteminde aşağıdaki komutu yazın:

     [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency/Output:** `OutputFile` [`Options`]

     [/Output](../profiling/output.md) **:** `OutputFile` ile seçeneği gereklidir **/start**. `OutputFile` Profil oluşturma veri (.vsp) dosyasının konumunu ve adını belirtir.

     Aşağıdaki tabloda seçeneklerden herhangi birini kullanabilirsiniz **/start:concurrency** seçeneği.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Profil oluşturma sırasında Tahsil edilecek Windows performans sayacı belirtir.|
    |[/automark](../profiling/automark.md) **:** `Interval`|İle kullanma **/wincounter** yalnızca. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500'dür.|
    |[/Events](../profiling/events-vsperfcmd.md) **:** `Config`|Profil oluşturma sırasında Tahsil edilecek bir olay izleme için Windows (ETW) olayı belirtir. ETW olayları ayrı (.etl) dosyasında toplanır.|

2. Şunu yazarak hedef uygulamayı başlatın:

     **VSPerfCmd**  [/Launch](../profiling/launch.md) **:** `AppName` [`Options`]

     Aşağıdaki tablodaki seçeneklerden herhangi birini **/Launch** seçeneğiyle kullanabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/args](../profiling/args.md) **:** `Arguments`|Hedef Uygulamaya geçirilecek komut satırı bağımsız değişkenlerini içeren bir dize belirtir.|
    |[/Console](../profiling/console.md)|Hedef komut satırı uygulamasını ayrı bir pencerede başlatır.|
    |[/ targetclr](../profiling/targetclr.md) **:** `CLRVersion`|Uygulama CLR 'nin birden fazla sürümünü yüklerse profil için ortak dil çalışma zamanının (CLR) sürümünü belirtir.|

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hedef uygulama çalışırken, *VSPerfCmd. exe* seçenekleriyle dosyadaki verilerin yazılmasını başlatıp durdurarak veri toplamayı kontrol edebilirsiniz. Denetleme veri toplama işlemi tarafından program yürütmenin, uygulamanın başlatılması ya da kapatılması gibi özel bir bölümü için veri toplayabilir.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı durdurmak ve başlatmak

- Aşağıdaki tabloda seçenekleri çiftlerini başlatın ve veri toplama işlemini durdurun. Her seçeneği ayrı bir komut satırında belirtin. Veri Toplama'ı, birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/ globalon /globaloff](../profiling/globalon-and-globaloff.md)|Başlar ( **/globalon**) veya durdurur ( **/globaloff**) tüm işlemler için veri toplama.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Başlar ( **/processon**) veya durdurur ( **/processoff**) veri toplama işlemi için işlem kimliği (`PID`) belirtir.|
    |[/ ekleme](../profiling/attach.md) **:** {`PID`&#124;`ProcName`} [/ detach](../profiling/detach.md)[ **:** {`PID`&#124;`ProcName`}]|**/ ekleme** işlem için veri toplamaya başlar, işlem kimliği (`PID`) veya işlem adı (*ProcName*) belirtir. **/ detach** belirlenmiş bir işlem için belirtilen işlem veya tüm işlemler için veri toplamayı durdurur.|

- Ayrıca **VSPerfCmd.exe**[/mark](../profiling/mark.md) veri dosyasına bir profil oluşturma işareti eklemek için seçeneği. **/Mark** komut tanımlayıcı, bir zaman damgası ve isteğe bağlı kullanıcı tanımlı bir metin dizesi ekler. İşaretler profil oluşturucu raporlar ve veri görünümlerindeki verilere filtre için kullanılabilir.

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sona erdirme
 Profil oluşturma oturumunu sona erdirmek için Profil Oluşturucu veri toplamıyor olmalıdır. Profili oluşturulmuş uygulamayı kapatarak veya **VSPerfCmd/detach** seçeneğini çağırarak eşzamanlılık verilerinin toplanmasını durdurabilirsiniz. Ardından çağırmak **VSPerfCmd/shutdown** profil oluşturucuyu devre dışı bırakırsınız ve profil oluşturma veri dosyasını kapatırsınız.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdirmek için

1. Uygulamayı kapatarak veya bir komut isteminde aşağıdaki komutu yazarak profil oluşturucuyu hedef uygulamadan ayırın:

     **VSPerfCmd / detach**

2. Bir komut isteminde aşağıdaki komutu yazarak profil oluşturucuyu kapatın:

     **VSPerfCmd** [ /Shutdown](../profiling/shutdown.md)