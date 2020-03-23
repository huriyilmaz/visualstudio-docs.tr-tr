---
title: Eşzamanlı veri toplamak için profil oluşturucuyu bir .NET uygulamasına takın | Microsoft Dokümanlar
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fdd41576-797e-4312-8520-fee7bb767e4a
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: f44213bf7356d499f852b53335698c701bf03eb7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779161"
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-stand-alone-application-to-collect-concurrency-data-by-using-the-command-line"></a>Nasıl kullanılır: Komut satırını kullanarak eşzamanlılık verileri toplamak için profiloluşturucuyu .NET Framework tek başına uygulamasına takın
Bu makalede, profil [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oluşturucuyu çalışan bir .NET Framework tek başına (istemci) uygulamasına eklemek ve işlem ve iş parçacığı eşzamanlılık verilerini toplamak için Profil Oluşturma Araçları komut satırı araçlarının nasıl kullanılacağı açıklanmaktadır.

> [!NOTE]
> Profil oluşturma araçlarına giden yolu almak için [Bkz. Walkthrough: Profil oluşturucu API'lerini kullanma.](../profiling/walkthrough-using-profiler-apis.md) 64 bit bilgisayarlarda, araçların hem 64 bit hem de 32 bit sürümleri kullanılabilir. Profil oluşturucu komut satırı araçlarını kullanmak için, komut istemi penceresinin PATH ortamı değişkenine araçlar yolunu eklemeniz veya komutun kendisine eklemeniz gerekir. Daha fazla bilgi için [bkz.](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)

 Profil oluşturucu uygulamaya bağlı yken, veri toplamayı duraklatabilir ve devam ettirebilirsiniz. Profil oluşturma oturumunu sona erdirmek için profil oluşturucuartık uygulamaya eklenmemeli ve Profil Oluşturucu açıkça kapatılmalıdır.

## <a name="attach-the-profiler"></a>Profil oluşturucuyu takın

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Çalışan bir .NET Framework uygulamasına profil oluşturucu eklemek için

1. Bir komut istemi penceresi açın.

2. Profilciyi çalıştırın. Şunu yazın:

     [VSPerfCmd](../profiling/vsperfcmd.md) **/start:eşzamanlılık /çıktı:** `OutputFile` [`Options`]

     [/output](../profiling/output.md)**:** `OutputFile` seçeneği **/start**ile gereklidir. `OutputFile`profil oluşturma verileri (.vsp) dosyasının adını ve konumunu belirtir.

     **/start:eşzamanlılık** seçeneği ile aşağıdaki seçeneklerden herhangi birini kullanabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/wincounter](../profiling/wincounter.md) **:**`WinCounterPath`|Profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir.|
    |[/automark](../profiling/automark.md) **:**`Interval`|Yalnızca **/wincounter** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 ms'dir.|
    |[/olaylar](../profiling/events-vsperfcmd.md) **:**`Config`|Profil oluşturma sırasında toplanacak windows için olay izleme (ETW) olayı belirtir. ETW olayları ayrı bir (.etl) dosyada toplanır.|

3. Hedef uygulamayı tipik bir şekilde başlatın.

4. Profil oluşturucuyu hedef uygulamaya takın. Şunu yazın:

     **VSPerfCmd /ekle:** `PID` [**/lineoff**] [**/targetclr:**`Version`]

    - `PID`hedef uygulamanın işlem kimliğini belirtir. Windows Görev Yöneticisi'nde çalışan tüm işlemlerin işlem lerini görüntüleyebilirsiniz.

    - [/lineoff](../profiling/lineoff.md) satır numarası verilerinin toplanmasını devre dışı kılabilir.

    - [/targetclr](../profiling/targetclr.md) **:** `Version` bir uygulamada çalışma süresinin birden fazla sürümü yüklendiğinde, ortak dil çalışma zamanının (CLR) profilinin sürümünü belirtir. İsteğe bağlı.

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hedef uygulama çalışırken, *VSPerfCmd.exe* seçeneklerini kullanarak dosyaya veri yazısını başlatıp durdurarak veri toplamayı denetleyebilirsiniz. Veri toplamayı denetlemek, uygulamanın başlatılması veya kapatılması gibi program yürütmesinin belirli bir bölümü için veri toplamanızı sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki *VSPerfCmd.exe* seçenekleri çiftleri veri toplamayı başlayıp durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Tüm işlemler için **(/globalon)** başlatır veya durur (**/globaloff**) veri toplama.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|İşlem Kimliği tarafından belirtilen işlem için **(/processon)** başlatır veya **(/processoff)** veri toplamayı durdurur (`PID`).|
    |[/ekle](../profiling/attach.md) **:**:`PID` `ProcName`{&#124;} [/ayırma](../profiling/detach.md) `ProcName`[**:**{`PID`&#124;}]|**/ekle** işlem kimliği (`PID`) veya işlem adı (ProcName) tarafından belirtilen işlem için veri toplamaya başlar. **/detach,** belirli bir işlem belirtilmemişse, belirtilen işlem veya tüm işlemler için veri toplamayı durdurur.|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sonlandırma
 Profil oluşturma oturumunu sona erdirmek için profil oluşturucunun veri toplamaması gerekir. Uygulamayı kapatarak veya **VSPerfCmd /detach** seçeneğini çağırarak eşzamanlılık yöntemiyle profillenmiş bir uygulamadan veri toplamayı durdurabilirsiniz. Daha sonra profil oluşturma veri dosyasını kapatmak ve kapatmak için **VSPerfCmd /shutdown** seçeneğini çağırırsınız. **VSPerfClrEnv /off** komutu profil oluşturma ortamı değişkenlerini temizler.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdirmek için

1. Profiloluşturciyi hedef uygulamadan ayırmak için aşağıdakilerden birini yapın.

    - **VsPerfCmd /detach** yazın

         -veya-

    - Hedef uygulamayı kapatın.

2. Profilciyi kapat. Şunu yazın:

     VSPerfCmd[/kapatma](../profiling/shutdown.md)
