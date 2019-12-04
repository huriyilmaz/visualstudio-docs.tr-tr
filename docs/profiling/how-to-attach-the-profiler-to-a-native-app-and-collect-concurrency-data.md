---
title: Profil oluşturucuyu yerel uygulamaya ekleyin ve eşzamanlılık verilerini toplayın
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 12d3e0f3-4b74-4e66-8fbf-8ac99bd4f91c
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: 367c91035f5d37bd8b0c20f1df84c7a2ee2d487a
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74776933"
---
# <a name="how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-concurrency-data-by-using-the-command-line"></a>Nasıl yapılır: profil oluşturucuyu yerel bir tek başına uygulamaya Iliştirme ve komut satırını kullanarak eşzamanlılık verileri toplama
Bu makalede, çalışan bir yerel (C/C++) tek başına uygulamaya profil oluşturucu eklemek ve iş parçacığı çakışması verilerini toplamak için [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] profil oluşturma araçları komut satırı araçlarının nasıl kullanılacağı açıklanır.

> [!NOTE]
> Profil oluşturma araçlarının yolunu almak için, bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). 64 bit bilgisayarlarda, araçların her ikisi de 64-bit ve 32 bit sürümleri mevcuttur. Profil oluşturucu komut satırı araçlarını kullanmak için araçlar yolunu komut Istemi penceresinin PATH ortam değişkenine eklemeniz ya da komutun kendisine eklemeniz gerekir.

 Profil Oluşturucu uygulamaya iliştirirken, veri toplamayı duraklatabilir ve devam ettirebilirsiniz. Profil oluşturma oturumunu sonlandırmak için, profil oluşturucunun artık uygulamaya bağlı olmaması ve profil oluşturucunun açıkça kapatılması gerekir.

## <a name="attach-the-profiler-to-a-running-native-application"></a>Profil oluşturucuyu çalışan bir yerel uygulamaya ekleyin

#### <a name="to-attach-the-profiler-to-a-running-native-application"></a>Profil oluşturucuyu çalışan bir yerel uygulamaya eklemek için

1. Komut isteminde aşağıdaki komutu yazın:

     [VSPerfCmd](../profiling/vsperfcmd.md) **/Start: eşzamanlılık**

     Aşağıdaki tabloda bulunan seçeneklerden herhangi birini, **/Start: eşzamanlılık** seçeneğiyle kullanabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/User](../profiling/user-vsperfcmd.md) **:** [`Domain\`]`Username`|Profil oluşturucuya erişim verilecek hesabın isteğe bağlı etki alanını ve Kullanıcı adını belirtir.|
    |[/CrossSession](../profiling/crosssession.md)|Diğer oturum oturumlarda işlemlerin profilini oluşturmayı mümkün.|
    |[/WINCOUNTER](../profiling/wincounter.md) **:** `WinCounterPath`|Profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir.|
    |[/AutoMark](../profiling/automark.md) **:** `Interval`|Yalnızca **/WINCOUNTER** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 ' dir.|
    |[/Events](../profiling/events-vsperfcmd.md) **:** `Config`|Profil oluşturma sırasında toplanacak bir Windows için olay Izleme (ETW) olayı belirtir. ETW olayları ayrı bir (. etl) dosyasında toplanır.|

2. Aşağıdaki komutu yazarak profil oluşturucuyu hedef uygulamaya ekleyin:

     **VSPerfCmd**[/Attach](../profiling/attach.md) **:** {`PID`&#124;`ProcName`}

     `PID` hedef uygulamanın işlem KIMLIĞINI belirtir. Windows Görev Yöneticisi 'nde çalışan tüm işlemlerin işlem kimliklerini görüntüleyebilirsiniz.

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hedef uygulama çalışırken, *VSPerfCmd. exe* seçeneklerini kullanarak verileri dosyaya yazmayı başlatıp durdurarak veri toplamayı kontrol edebilirsiniz. Veri toplamayı denetleyerek, program yürütmesinin, uygulamanın başlatılması veya kapatılması gibi belirli bir bölümü için veri toplayabilirsiniz.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki tabloda bulunan seçenek çiftleri veri toplamayı başlatır ve durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Tüm süreçler için veri toplamayı başlatır ( **/GlobalOn**) veya Durdur ( **/globaloff**).|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:** `PID`|İşlem KIMLIĞININ (`PID`) belirttiği işlem için ( **/ProcessOn**) veya duraklar ( **/ProcessOff**) veri toplamayı başlatır.|
    |[/Attach](../profiling/attach.md) **:** {`PID`&#124;`ProcName`} [/Detach](../profiling/detach.md)[ **:** {`PID`&#124;`ProcName`}]|**/Attach** işlem kimliği (`PID`) veya işlem adı (*ProcName*) tarafından belirttiği işlem için veri toplamaya başlar. **/Detach** belirtilen işlem için veya hiçbir işlem belirtilmemişse tüm işlemler için veri toplamayı durduruyor.|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu Sonlandır
 Profil oluşturma oturumunu sonlandırmak için, profil oluşturucunun veri toplamamalıdır. Uygulamayı kapatarak veya **VSPerfCmd/detach** seçeneğini çağırarak örnekleme yöntemiyle profili oluşturulmuş bir uygulamadan veri toplamayı durdurabilirsiniz. Ardından, profil oluşturucuyu kapatmak ve profil oluşturma veri dosyasını kapatmak için **VSPerfCmd/shutdown** seçeneğini çağırın.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sonlandırmak için

1. Uygulamayı kapatarak veya aşağıdaki komutu yazarak profil oluşturucuyu hedef uygulamadan ayırın:

     **VSPerfCmd/detach**

2. Aşağıdaki komutu yazarak profil oluşturucuyu kapatın:

     **VSPerfCmd**  [/Shutdown](../profiling/shutdown.md)
