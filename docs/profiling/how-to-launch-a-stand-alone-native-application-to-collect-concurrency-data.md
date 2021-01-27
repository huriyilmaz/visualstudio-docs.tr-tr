---
title: Profil oluşturucu komut satırı-yerel istemci uygulamasını aç, eşzamanlılık verileri al
description: Yerel bir tek başına istemci uygulaması başlatmak ve işlem ve iş parçacığı eşzamanlılık verilerini toplamak için Visual Studio Profil Oluşturma Araçları komut satırı araçlarının nasıl kullanılacağını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e5aed651-afed-4b70-9a7e-1a6032cc614f
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: ce8c16c3c895c0538f91bdb27af08e003b1450cf
ms.sourcegitcommit: 8e15b434bf5db3e0f719320ca82682df1a3da110
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98883513"
---
# <a name="how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line"></a>Nasıl yapılır: Komut satırını kullanarak eşzamanlılık verileri toplamak için bağımsız bir yerel uygulamayı başlatma
Bu konu, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] yerel bir tek başına (istemci) uygulamayı başlatmak ve işlem ve iş parçacığı eşzamanlılık verilerini toplamak için profil oluşturma araçları komut satırı araçlarının nasıl kullanılacağını açıklar.

 Profil oluşturma oturumu aşağıdaki bölümlere sahiptir:

- Uygulamayı Profil Oluşturucu ile başlatma

- Veri toplamayı denetleme

- Profil oluşturma oturumu sonlandırılıyor

> [!NOTE]
> Profil oluşturma araçlarının yolunu almak için, bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). 64 bit bilgisayarlarda, araçların her ikisi de 64-bit ve 32 bit sürümleri mevcuttur. Profil oluşturucu komut satırı araçlarını kullanmak için araçlar yolunu komut Istemi penceresinin PATH ortam değişkenine eklemeniz ya da komutun kendisine eklemeniz gerekir.

## <a name="start-the-application-with-the-profiler"></a>Uygulamayı Profil Oluşturucu ile başlatma
 Bir hedef uygulamayı profil Oluşturucu ile başlatmak için, [VSPerfCmd.exe](../profiling/vsperfcmd.md) **/Start** ve **/Launch** seçeneklerini kullanarak profil oluşturucuyu başlatabilir ve uygulamayı başlatabilirsiniz. **/Start** ve **/Launch** ' i ve ilgili seçeneklerini belirtebilirsiniz. Ayrıca, hedef uygulamanın başlangıcında veri toplamayı duraklatmak için **/globaloff** seçeneğini de ekleyebilirsiniz. Ardından, veri toplamaya başlamak için **/GlobalOn** kullanın.

#### <a name="to-start-an-application-with-the-profiler"></a>Profil Oluşturucu ile bir uygulamayı başlatmak için

1. Komut isteminde aşağıdaki komutu yazın:

     [VSPerfCmd](../profiling/vsperfcmd.md) **/Start: eşzamanlılık/çıkış:** `OutputFile` [ `Options` ]

     /Start ile [/output](../profiling/output.md)**:** `OutputFile` seçeneği gereklidir.  `OutputFile` profil oluşturma verileri (. vsp) dosyasının adını ve konumunu belirtir.

     Aşağıdaki tabloda bulunan seçeneklerden herhangi birini, **/Start: eşzamanlılık** seçeneğiyle kullanabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/WINCOUNTER](../profiling/wincounter.md) **:**`WinCounterPath`|Profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir.|
    |[/AutoMark](../profiling/automark.md) **:**`Interval`|Yalnızca **/WINCOUNTER** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500'dür.|
    |[/Events](../profiling/events-vsperfcmd.md) **:**`Config`|Profil oluşturma sırasında toplanacak bir Windows için olay Izleme (ETW) olayı belirtir. ETW olayları ayrı bir (. etl) dosyasında toplanır.|

2. Şunu yazarak hedef uygulamayı başlatın:

     **VSPerfCmd**  [/Launch](../profiling/launch.md) **:** `AppName` [ `Options` ]

     Aşağıdaki tablodaki seçeneklerden herhangi birini **/Launch** seçeneğiyle kullanabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/args](../profiling/args.md) **:**`Arguments`|Hedef Uygulamaya geçirilecek komut satırı bağımsız değişkenlerini içeren bir dize belirtir.|
    |[/Console](../profiling/console.md)|Hedef komut satırı uygulamasını ayrı bir pencerede başlatır.|
    |[/targetclr](../profiling/targetclr.md) **:**`CLRVersion`|Uygulama CLR 'nin birden fazla sürümünü yüklerse profil için ortak dil çalışma zamanının (CLR) sürümünü belirtir.|

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hedef uygulama çalışırken, *VSPerfCmd.exe* seçenekleriyle dosyaya yazmayı başlatıp durdurarak veri toplamayı kontrol edebilirsiniz. Veri toplamayı denetleyerek, program yürütmesinin, uygulamanın başlatılması veya kapatılması gibi belirli bir bölümü için veri toplayabilirsiniz.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki tabloda bulunan seçenek çiftleri veri toplamayı başlatır ve durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Tüm süreçler için veri toplamayı başlatır (**/GlobalOn**) veya Durdur (**/globaloff**).|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|İşlem KIMLIĞI () tarafından belirttiği işlem için (**/ProcessOn**) veya duraklar (**/ProcessOff**) veri toplamayı başlatır `PID` .|
    |[/Attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` } [/Detach](../profiling/detach.md)[**:**{ `PID`&#124;`ProcName` }]|**/Attach** işlem kimliği ( `PID` ) veya Işlem adı (*ProcName*) tarafından belirttiği işlem için veri toplamaya başlar. **/Detach** belirtilen işlem için veya hiçbir işlem belirtilmemişse tüm işlemler için veri toplamayı durduruyor.|

- Veri dosyasına bir profil oluşturma işareti eklemek için **VSPerfCmd.exe** [/Mark](../profiling/mark.md) seçeneğini de kullanabilirsiniz. **/Mark** komutu bir tanımlayıcı, bir zaman damgası ve Kullanıcı tanımlı isteğe bağlı bir metin dizesi ekler. İşaretler, profil oluşturucu raporlarında ve veri görünümlerinde verileri filtrelemek için kullanılabilir.

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu Sonlandır
 Profil oluşturma oturumunu sonlandırmak için, profil oluşturucunun veri toplamamalıdır. Profili oluşturulmuş uygulamayı kapatarak veya **VSPerfCmd/detach** seçeneğini çağırarak eşzamanlılık verilerinin toplanmasını durdurabilirsiniz. Ardından, profil oluşturucuyu kapatmak ve profil oluşturma veri dosyasını kapatmak için **VSPerfCmd/shutdown** seçeneğini çağırın.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sonlandırmak için

1. Uygulamayı kapatarak veya bir komut isteminde aşağıdaki komutu yazarak profil oluşturucuyu hedef uygulamadan ayırın:

     **VSPerfCmd/detach**

2. Komut istemine aşağıdaki komutu yazarak profil oluşturucuyu kapatın:

     **VSPerfCmd**  [/Shutdown](../profiling/shutdown.md)