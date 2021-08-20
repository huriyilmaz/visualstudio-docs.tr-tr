---
title: Eşzamanlılık verileri toplamak için & uygulama profili oluşturma
description: Profil Visual Studio Profil Oluşturma Araçları çalışan yerel (C/C++) tek başına bir uygulamaya eklemek ve iş parçacığı musiki verilerini almak için komut satırı araçlarını kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 12d3e0f3-4b74-4e66-8fbf-8ac99bd4f91c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: a7d1fbbe7ed499e1171a80663b204560d58ae80c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122107855"
---
# <a name="how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-concurrency-data-by-using-the-command-line"></a>Nasıl kullanılır: Profilleyiciyi yerel bir tek başına uygulamaya ekleme ve komut satırı kullanarak eşzamanlılık verileri toplama
Bu makalede, profil Profil Oluşturma Araçları çalışan bir yerel (C/C++) tek başına uygulamaya eklemek ve iş parçacığı musiki verilerini toplamak için Profil Oluşturma Araçları komut satırı araçlarının nasıl [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] kullanımı açıklanmıştır.

> [!NOTE]
> Profil oluşturma araçlarının yolunu almak için [bkz. Komut satırı araçlarının yolunu belirtme.](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md) 64 bit bilgisayarlarda, araçların hem 64 bit hem de 32 bit sürümleri kullanılabilir. Profil oluşturma komut satırı araçlarını kullanmak için, araç yolunu Komut İstemi penceresinin PATH ortam değişkenine eklemeniz veya komutun kendisine eklemeniz gerekir.

 Profiler uygulamaya bağlıyken veri toplamayı duraklatabilir ve sürdürebilirsiniz. Profil oluşturma oturumunu sona erdirmak için Profiler'ın uygulamaya artık bağlı kalmaması ve Profiler'ın açıkça kapanması gerekir.

## <a name="attach-the-profiler-to-a-running-native-application"></a>Profilleyiciyi çalışan bir yerel uygulamaya ekleme

#### <a name="to-attach-the-profiler-to-a-running-native-application"></a>Profilleyiciyi çalışan bir yerel uygulamaya eklemek için

1. Komut isteminde aşağıdaki komutu yazın:

     [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency**

     Aşağıdaki tabloda yer alan seçeneklerden herhangi birini **/start:concurrency seçeneğiyle kullanabilirsiniz.**

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/user](../profiling/user-vsperfcmd.md) **:**[ `Domain\` ]`Username`|Profil oluşturma için erişim izni verilen hesabın isteğe bağlı etki alanını ve kullanıcı adını belirtir.|
    |[/crosssession](../profiling/crosssession.md)|Diğer oturum açma oturumlarında işlemlerin profil oluşturmasını sağlar.|
    |[/wincounter:](../profiling/wincounter.md) `WinCounterPath`|Profil oluşturma Windows toplanacak bir performans sayacı belirtir.|
    |[/automark:](../profiling/automark.md) `Interval`|Yalnızca **/wincounter ile** kullanın. Performans sayacı toplama olayları arasındaki milisaniye Windows sayısını belirtir. Varsayılan değer 500'dür.|
    |[/events](../profiling/events-vsperfcmd.md) **:**`Config`|Profil oluşturma sırasında toplanacak Windows (ETW) olayı için bir Olay İzleme belirtir. ETW olayları ayrı bir (.etl) dosyasında toplanır.|

2. Aşağıdaki komutu yazarak profilleyiciyi hedef uygulamaya iliştirin:

     **VSPerfCmd**[/attach:](../profiling/attach.md) { `PID`&#124;`ProcName` }  

     `PID` hedef uygulamanın işlem kimliğini belirtir. Görev Yöneticisi'nde çalışan tüm işlemlerin işlem kimliklerini Windows görüntüebilirsiniz.

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hedef uygulama çalışırken veri toplamayı, veri toplama seçeneklerini kullanarak dosyada veri yazmayı başlatarak *ve durdurarakVSPerfCmd.exe* yapabilirsiniz. Veri toplamayı denetleyerek, uygulamanın başlatılıyor veya kapatılıyor gibi program yürütmenin belirli bir bölümü için veri toplayabilirsiniz.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki tabloda yer alan seçenek çiftleri veri toplamayı başlatacak ve durduracak. Her seçeneği ayrı bir komut satırı üzerinde belirtin. Veri toplamayı birden çok kez açabilirsiniz ve kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Tüm işlemler **için veri toplamayı** başlatır ( /globalon ) veya durdurur (**/globaloff).**|
    |[/processon:](../profiling/processon-and-processoff.md)  `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|İşlem kimliğinin ( ) tarafından belirtilen işlem için veri koleksiyonunu (**/processon**) veya durdurur (**/processoff).** `PID`|
    |[/attach:](../profiling/attach.md) { `PID`&#124;`ProcName` } [/detach](../profiling/detach.md)[**:**{ `PID`&#124;`ProcName` }]|**/attach,** işlem kimliği ( ) veya işlem adı ( `PID` *ProcName*) tarafından belirtilen işlem için veri toplamaya başlar. **/detach,** belirtilen işlem için veya herhangi bir işlem belirtilmezse tüm işlemler için veri toplamayı durdurur.|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sona er
 Profil oluşturma oturumunu sona erdirecek şekilde profil oluşturma, veri toplamama gerekir. Uygulamayı kapatarak veya **VSPerfCmd /detach** seçeneğini kullanarak örnekleme yöntemiyle profili yapılan bir uygulamanın verilerini toplamayı durdurabilirsiniz. Ardından, profil oluşturma veri dosyasını kapatmak ve profil oluşturma verilerini kapatmak için **VSPerfCmd /shutdown** seçeneğini çağırabilirsiniz.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdir

1. Kapatarak veya aşağıdaki komutu yazarak profilleyiciyi hedef uygulamadan ayırabilirsiniz:

     **VSPerfCmd /detach**

2. Aşağıdaki komutu yazarak profilleyiciyi kapatın:

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)
