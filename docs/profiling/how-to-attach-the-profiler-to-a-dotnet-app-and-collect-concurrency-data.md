---
title: Eşzamanlılık verilerini toplamak için .NET 'e profil oluşturucu iliştirme
description: profil oluşturucuyu çalışan bir .NET Framework uygulamasına eklemek için Visual Studio Profil Oluşturma Araçları komut satırı araçlarını kullanarak işlem ve iş parçacığı eşzamanlılık verileri almayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: fdd41576-797e-4312-8520-fee7bb767e4a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 95c06dc9a043d0b11fb021ab8b1fadb33ec6dc830dfad4a0f0978fa5be8f85b1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121368519"
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-stand-alone-application-to-collect-concurrency-data-by-using-the-command-line"></a>nasıl yapılır: komut satırını kullanarak eşzamanlılık verileri toplamak için profil oluşturucuyu .NET Framework tek başına bir uygulamaya iliştirme
bu makalede [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , profil oluşturucuyu çalışan bir .NET Framework tek başına (istemci) uygulamasına eklemek ve işlem ve iş parçacığı eşzamanlılık verilerini toplamak için Profil Oluşturma Araçları komut satırı araçlarının nasıl kullanılacağı açıklanır.

> [!NOTE]
> Profil oluşturma araçlarının yolunu almak için bkz. [Walkthrough: Profiler API 'Leri kullanma](../profiling/walkthrough-using-profiler-apis.md). 64 bit bilgisayarlarda, araçların her ikisi de 64-bit ve 32 bit sürümleri mevcuttur. Profil oluşturucu komut satırı araçlarını kullanmak için araçlar yolunu komut istemi penceresinin PATH ortam değişkenine eklemeniz ya da komutun kendisine eklemeniz gerekir. Daha fazla bilgi için bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).

 Profil Oluşturucu uygulamaya iliştirirken, veri toplamayı duraklatabilir ve devam ettirebilirsiniz. Profil oluşturma oturumunu sonlandırmak için, profil oluşturucunun artık uygulamaya bağlı olmaması ve profil oluşturucunun açıkça kapatılması gerekir.

## <a name="attach-the-profiler"></a>Profil oluşturucuyu iliştirme

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>profil oluşturucuyu çalışan bir .NET Framework uygulamasına eklemek için

1. Bir komut istemi penceresi açın.

2. Profil oluşturucuyu başlatın. Şunu yazın:

     [VSPerfCmd](../profiling/vsperfcmd.md) **/Start: eşzamanlılık/çıkış:** `OutputFile` [ `Options` ]

     /Start ile [/output](../profiling/output.md)**:** `OutputFile` seçeneği gereklidir.  `OutputFile` profil oluşturma verileri (. vsp) dosyasının adını ve konumunu belirtir.

     Aşağıdaki seçeneklerden herhangi birini, **/Start: eşzamanlılık** seçeneğiyle kullanabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/WINCOUNTER](../profiling/wincounter.md) **:**`WinCounterPath`|profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir.|
    |[/AutoMark](../profiling/automark.md) **:**`Interval`|Yalnızca **/WINCOUNTER** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 MS 'dir.|
    |[/Events](../profiling/events-vsperfcmd.md) **:**`Config`|profil oluşturma sırasında toplanacak Windows (ETW) olayı için bir olay izleme olayı belirtir. ETW olayları ayrı bir (. etl) dosyasında toplanır.|

3. Hedef uygulamayı normal şekilde başlatın.

4. Profil oluşturucuyu hedef uygulamaya ekleyin. Şunu yazın:

     **VSPerfCmd/Attach:** `PID` [**/LineOff**] [**/targetclr:** `Version` ]

    - `PID` hedef uygulamanın işlem KIMLIĞINI belirtir. Windows görev yöneticisi 'nde çalışan tüm işlemlerin işlem kimliklerini görüntüleyebilirsiniz.

    - [/LineOff](../profiling/lineoff.md) satır numarası veri koleksiyonunu devre dışı bırakır.

    - [/targetclr](../profiling/targetclr.md) **:** `Version` bir uygulamaya çalışma zamanının birden fazla sürümü yüklendiğinde profil için ortak dil çalışma zamanının (CLR) sürümünü belirtir. İsteğe bağlı.

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hedef uygulama çalışırken, *VSPerfCmd.exe* seçeneklerini kullanarak verileri dosyaya yazmayı başlatıp durdurarak veri toplamayı kontrol edebilirsiniz. Veri toplamayı denetlemek, program yürütmesinin, uygulamanın başlatılması veya kapatılması gibi belirli bir bölümü için veri toplamanızı sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki *VSPerfCmd.exe* seçenek çiftleri veri toplamayı başlatır ve durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Tüm süreçler için veri toplamayı başlatır (**/GlobalOn**) veya Durdur (**/globaloff**).|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|İşlem KIMLIĞI () tarafından belirtilen işlem için (**/ProcessOn**) veya duraklar (**/ProcessOff**) veri toplamayı başlatır `PID` .|
    |[/Attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` } [/Detach](../profiling/detach.md)[**:**{ `PID`&#124;`ProcName` }]|**/Attach** işlem kimliği ( `PID` ) veya Işlem adı (ProcName) tarafından belirtilen işlem için veri toplamaya başlar. **/Detach** belirtilen işlem veya belirli bir işlem belirtilmemişse tüm işlemler için veri toplamayı durduruyor.|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu Sonlandır
 Profil oluşturma oturumunu sonlandırmak için, profil oluşturucunun veri toplamamalıdır. Uygulamayı kapatarak veya **VSPerfCmd/detach** seçeneğini çağırarak eşzamanlılık yöntemi ile profili oluşturulmuş bir uygulamadan veri toplamayı durdurabilirsiniz. Ardından, profil oluşturucuyu kapatmak ve profil oluşturma veri dosyasını kapatmak için **VSPerfCmd/shutdown** seçeneğini çağırın. **VSPerfCLREnv/off** komutu profil oluşturma ortam değişkenlerini temizler.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sonlandırmak için

1. Profil oluşturucuyu hedef uygulamadan ayırmak için aşağıdakilerden birini yapın.

    - **VSPerfCmd/detach** yazın

         -veya-

    - Hedef uygulamayı kapatın.

2. Profil oluşturucuyu kapatın. Şunu yazın:

     VSPerfCmd[/Shutdown](../profiling/shutdown.md)
