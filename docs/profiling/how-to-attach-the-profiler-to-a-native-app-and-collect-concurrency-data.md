---
title: Profil oluşturucuyu yerel uygulamaya takın ve eşzamanlılık verileri toplayın
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74776933"
---
# <a name="how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-concurrency-data-by-using-the-command-line"></a>Nasıl kullanılır: Profiloluşturucuyu yerel tek başına bir uygulamaya takın ve komut satırını kullanarak eşzamanlılık verileri toplayın
Bu makalede, profil [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oluşturucuyu çalışan bir yerel (C/C++) bağımsız uygulamaya eklemek ve iş parçacığı çekişme verilerini toplamak için Profil Oluşturma Araçları komut satırı araçlarının nasıl kullanılacağı açıklanmaktadır.

> [!NOTE]
> Profil oluşturma araçlarına giden yolu almak [için](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)bkz. 64 bit bilgisayarlarda, araçların hem 64 bit hem de 32 bit sürümleri kullanılabilir. Profil oluşturucu komut satırı araçlarını kullanmak için, komut istemi penceresinin PATH ortamı değişkenine araçlar yolunu eklemeniz veya komutun kendisine eklemeniz gerekir.

 Profil oluşturucu uygulamaya bağlı yken, veri toplamayı duraklatabilir ve devam ettirebilirsiniz. Profil oluşturma oturumunu sona erdirmek için Profiler'ın uygulamaya artık eklenmemesi ve Profiler'ın açıkça kapatılması gerekir.

## <a name="attach-the-profiler-to-a-running-native-application"></a>Profil oluşturucuyu çalışan bir yerel uygulamaya ekleme

#### <a name="to-attach-the-profiler-to-a-running-native-application"></a>Profil oluşturucuyu çalışan bir yerel uygulamaya eklemek için

1. Komut isteminde aşağıdaki komutu yazın:

     [VSPerfCmd](../profiling/vsperfcmd.md) **/başlangıç:eşzamanlılık**

     Aşağıdaki tablodaki seçeneklerden herhangi birini **/start:concurrency** seçeneği ile kullanabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/kullanıcı](../profiling/user-vsperfcmd.md) **:**[ ]`Domain\``Username`|Profiloluşturucuya erişim hakkı verilecek isteğe bağlı etki alanını ve hesabın kullanıcı adını belirtir.|
    |[/çapraz oturum](../profiling/crosssession.md)|Diğer oturum oturumlarında işlemlerin profilini çıkarmasağlar.|
    |[/wincounter](../profiling/wincounter.md) **:**`WinCounterPath`|Profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir.|
    |[/automark](../profiling/automark.md) **:**`Interval`|Yalnızca **/wincounter** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500'dür.|
    |[/olaylar](../profiling/events-vsperfcmd.md) **:**`Config`|Profil oluşturma sırasında toplanacak windows için olay izleme (ETW) olayı belirtir. ETW olayları ayrı bir (.etl) dosyada toplanır.|

2. Aşağıdaki komutu yazarak profiloluşturucuyu hedef uygulamaya takın:

     **VSPerfCmd**[/ eklemek](../profiling/attach.md) `ProcName` **:**{`PID`&#124;}  

     `PID`hedef uygulamanın işlem kimliğini belirtir. Windows Görev Yöneticisi'nde çalışan tüm işlemlerin işlem lerini görüntüleyebilirsiniz.

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hedef uygulama çalışırken, *VSPerfCmd.exe* seçeneklerini kullanarak dosyaya veri yazısını başlatıp durdurarak veri toplamayı denetleyebilirsiniz. Veri toplamayı denetleyerek, uygulamanın başlatılması veya kapatılması gibi program yürütmesinin belirli bir bölümü için veri toplayabilirsiniz.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki tablodaki seçenek çiftleri veri toplamayı başlatın ve durdurun. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Tüm işlemler için **(/globalon)** başlatır veya durur (**/globaloff**) veri toplama.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|İşlem Kimliğinin (`PID`) belirttiği işlem için **(/processon)** başlatır veya (**/processoff)** veri toplamayı durdurur.|
    |[/ekle](../profiling/attach.md) **:**:`PID` `ProcName`{&#124;} [/ayırma](../profiling/detach.md) `ProcName`[**:**{`PID`&#124;}]|**/ekle** işlem kimliği (`PID`) veya işlem adı *(ProcName)* belirttiği işlem için veri toplamaya başlar. **/detach,** belirtilen işlem için veya işlem belirtilmemişse tüm işlemler için veri toplamayı durdurur.|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sonlandırma
 Profil oluşturma oturumunu sona erdirmek için profil oluşturucunun veri toplamaması gerekir. Uygulamayı kapatarak veya **VSPerfCmd /detach** seçeneğini çağırarak örnekleme yöntemiyle profillenmiş bir uygulamadan veri toplamayı durdurabilirsiniz. Daha sonra profil oluşturma veri dosyasını kapatmak ve kapatmak için **VSPerfCmd /shutdown** seçeneğini çağırırsınız.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdirmek için

1. Profilciyi kapatarak veya aşağıdaki komutu yazarak hedef uygulamadan ayırın:

     **VSPerfCmd /ayırma**

2. Aşağıdaki komutu yazarak profiloluşturucuyu kapatın:

     **VSPerfCmd**  [/kapatma](../profiling/shutdown.md)
