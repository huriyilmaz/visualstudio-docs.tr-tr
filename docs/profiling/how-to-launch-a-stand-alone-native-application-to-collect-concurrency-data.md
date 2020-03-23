---
title: 'Profiler komut satırı: Yerel istemci uygulamasını açın, eşzamanlılık verilerini alın'
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76726041"
---
# <a name="how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line"></a>Nasıl yapılır: Komut satırını kullanarak eşzamanlılık verileri toplamak için bağımsız bir yerel uygulamayı başlatma
Bu konu, yerel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bir tek başına (istemci) uygulama başlatmak ve işlem ve iş parçacığı eşzamanlılık verilerini toplamak için Profil Oluşturma Araçları komut satırı araçlarının nasıl kullanılacağını açıklar.

 Profil oluşturma oturumu aşağıdaki bölümlere sahiptir:

- Uygulamayı profiloluşturucu ile başlatma

- Veri toplamayı denetleme

- Profil oluşturma oturumunu sonlandırma

> [!NOTE]
> Profil oluşturma araçlarına giden yolu almak [için](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)bkz. 64 bit bilgisayarlarda, araçların hem 64 bit hem de 32 bit sürümleri kullanılabilir. Profil oluşturucu komut satırı araçlarını kullanmak için, komut istemi penceresinin PATH ortamı değişkenine araçlar yolunu eklemeniz veya komutun kendisine eklemeniz gerekir.

## <a name="start-the-application-with-the-profiler"></a>Uygulamayı profil oluşturucuyla başlatın
 Profil oluşturucuyla bir hedef uygulaması başlatmak için Profiler'ı başlatmak ve uygulamayı başlatmak için [VSPerfCmd.exe](../profiling/vsperfcmd.md)**/start** ve **/başlat** seçeneklerini kullanırsınız. **/başlat** ve **/başlat** ve ilgili seçeneklerini belirtebilirsiniz. Hedef uygulamanın başında veri toplamayı duraklatmak için **/globaloff** seçeneğini de ekleyebilirsiniz. Daha sonra veri toplamaya başlamak için **/globalon'u** kullanırsınız.

#### <a name="to-start-an-application-with-the-profiler"></a>Profil oluşturucuyla bir uygulama başlatmak için

1. Komut isteminde aşağıdaki komutu yazın:

     [VSPerfCmd](../profiling/vsperfcmd.md) **/start:eşzamanlılık /çıktı:** `OutputFile` [`Options`]

     [/output](../profiling/output.md)**:** `OutputFile` seçeneği **/start**ile gereklidir. `OutputFile`profil oluşturma verileri (.vsp) dosyasının adını ve konumunu belirtir.

     Aşağıdaki tablodaki seçeneklerden herhangi birini **/start:concurrency** seçeneği ile kullanabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/wincounter](../profiling/wincounter.md) **:**`WinCounterPath`|Profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir.|
    |[/automark](../profiling/automark.md) **:**`Interval`|Yalnızca **/wincounter** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500'dür.|
    |[/olaylar](../profiling/events-vsperfcmd.md) **:**`Config`|Profil oluşturma sırasında toplanacak windows için olay izleme (ETW) olayı belirtir. ETW olayları ayrı bir (.etl) dosyada toplanır.|

2. Yazarak hedef uygulamayı başlatın:

     **VSPerfCmd**  [/ başlatmak](../profiling/launch.md) **:** `AppName` [`Options`]

     **/başlat** seçeneği ile aşağıdaki tablodaki seçeneklerden herhangi birini kullanabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/args](../profiling/args.md) **:**`Arguments`|Hedef uygulamaya geçirilecek komut satırı bağımsız değişkenlerini içeren bir dize belirtir.|
    |[/konsol](../profiling/console.md)|Hedef komut satırı uygulamasını ayrı bir pencerede başlatır.|
    |[/targetclr](../profiling/targetclr.md) **:**`CLRVersion`|Uygulama CLR'nin birden fazla sürümünü yüklerse, profil için ortak dil çalışma zamanının (CLR) sürümünü belirtir.|

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hedef uygulama çalışırken, *VSPerfCmd.exe* seçenekleri ile dosyaya veri yazısını başlatıp durdurarak veri toplamayı denetleyebilirsiniz. Veri toplamayı denetleyerek, uygulamanın başlatılması veya kapatılması gibi program yürütmesinin belirli bir bölümü için veri toplayabilirsiniz.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki tablodaki seçenek çiftleri veri toplamayı başlatın ve durdurun. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Tüm işlemler için **(/globalon)** başlatır veya durur (**/globaloff**) veri toplama.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|İşlem Kimliğinin (`PID`) belirttiği işlem için **(/processon)** başlatır veya (**/processoff)** veri toplamayı durdurur.|
    |[/ekle](../profiling/attach.md) **:**:`PID` `ProcName`{&#124;} [/ayırma](../profiling/detach.md) `ProcName`[**:**{`PID`&#124;}]|**/ekle** işlem kimliği (`PID`) veya işlem adı *(ProcName)* belirttiği işlem için veri toplamaya başlar. **/detach,** belirtilen işlem için veya işlem belirtilmemişse tüm işlemler için veri toplamayı durdurur.|

- Veri dosyasına profil işareti eklemek için **VSPerfCmd.exe**[/mark](../profiling/mark.md) seçeneğini de kullanabilirsiniz. **/işareti** komutu bir tanımlayıcı, bir zaman damgası ve isteğe bağlı kullanıcı tanımlı metin dizesi ekler. Markalar, profil oluşturucu raporlarında ve veri görünümlerinde verileri filtrelemek için kullanılabilir.

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sonlandırma
 Profil oluşturma oturumunu sona erdirmek için profil oluşturucunun veri toplamaması gerekir. Profilli uygulamayı kapatarak veya **VSPerfCmd /detach** seçeneğini çağırarak eşzamanlılık verileri toplamayı durdurabilirsiniz. Daha sonra profil oluşturucuyu kapatmak ve profil oluşturma veri dosyasını kapatmak için **VSPerfCmd /shutdown** seçeneğini çağırırsınız.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdirmek için

1. Profilciyi kapatarak veya komut isteminde aşağıdaki komutu yazarak hedef uygulamadan ayırın:

     **VSPerfCmd /ayırma**

2. Bir komut isteminde aşağıdaki komutu yazarak profiloluşturucuyu kapatın:

     **VSPerfCmd**  [/kapatma](../profiling/shutdown.md)