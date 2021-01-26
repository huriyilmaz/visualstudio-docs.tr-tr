---
title: Eşzamanlılık verisi toplamak için .NET 'e profil oluşturucu iliştirme-komut satırı
titleSuffix: ''
description: Profil oluşturucuyu bir .NET Framework hizmetine eklemek ve örnekleme yöntemini kullanarak işlem ve iş parçacığı eşzamanlılık verileri almak için Visual Studio Profil Oluşturma Araçları kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ffbdfe37-8325-44be-bd36-2c8aab2dec7b
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: c3b7a8e255094cb03cac8708dbaa4cb4a938db24
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98800382"
---
# <a name="how-to-attach-the-profiler-to-a-net-service-to-collect-concurrency-data-by-using-the-command-line"></a>Nasıl yapılır: komut satırını kullanarak eşzamanlılık verileri toplamak için bir .NET hizmetine profil oluşturucu Iliştirme
Bu makalede [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , bir .NET Framework hizmetine profil oluşturucuyu iliştirmek ve örnekleme yöntemini kullanarak işlem ve iş parçacığı eşzamanlılık verilerini toplamak için profil oluşturma araçları komut satırı araçlarının nasıl kullanılacağı açıklanır.

> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. UWP uygulamaları için de yeni koleksiyon teknikleri gerekir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

> [!NOTE]
> Profil oluşturma araçlarının yolunu almak için, bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). 64 bit bilgisayarlarda, araçların her ikisi de 64-bit ve 32 bit sürümleri mevcuttur. Profil oluşturucu komut satırı araçlarını kullanmak için araçlar yolunu komut Istemi penceresinin PATH ortam değişkenine eklemeniz ya da komutun kendisine eklemeniz gerekir.

 Eşzamanlılık verilerini toplamak için, profil oluşturucuyu hizmet işlemine iliştirin. Profil Oluşturucu hizmete iliştirirken, veri toplamayı duraklatabilir ve devam ettirebilirsiniz. Profil oluşturma oturumunu sonlandırmak için, profil oluşturucunun artık hizmete bağlı olmaması ve profil oluşturucunun açıkça kapatılması gerekir. Çoğu durumda, bir oturumun sonunda profil oluşturma ortam değişkenlerini temizlemeniz önerilir.

## <a name="attach-the-profiler"></a>Profil oluşturucuyu iliştirme

#### <a name="to-attach-the-profiler-to-a-net-framework-service"></a>Profil oluşturucuyu bir .NET Framework hizmetine eklemek için

1. Hizmeti yükler.

2. Komut penceresi açın.

3. Profil oluşturma ortamı değişkenlerini başlatın. Şunu yazın:

     [VSPerfCLREnv](../profiling/vsperfclrenv.md) **/globalsampleon** [**/samplelineoff**]

    - **/globalsampleon** , örneklemesi sunar.

    - **/samplelineoff** toplanan verilerin belirli kaynak kodu satırlarına atanmasını devre dışı bırakır. Bu seçenek belirtildiğinde, veriler yalnızca işlevlere atanır.

4. Bilgisayarı yeniden başlatın.

5. Profil oluşturucuyu başlatın. Şunu yazın:

     [VSPerfCmd](../profiling/vsperfcmd.md) **/Start: eşzamanlılık/çıkış:** `OutputFile` [ `Options` ]

     /Start ile [/output](../profiling/output.md)**:** `OutputFile` seçeneği gereklidir.  `OutputFile` profil oluşturma verileri (. vsp) dosyasının adını ve konumunu belirtir.

     Aşağıdaki seçeneklerden herhangi birini, **/Start** seçeneğiyle kullanabilirsiniz.

    > [!NOTE]
    > **/User** ve **/CrossSession** seçenekleri genellikle hizmetler için gereklidir.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName`|Profili oluşturulan işlemin sahibi olan hesabın etki alanını ve Kullanıcı adını belirtir. Bu seçenek yalnızca, işlem oturum açmış kullanıcı dışında bir kullanıcı olarak çalışıyorsa gereklidir. İşlem sahibi, Windows Görev Yöneticisi 'nin **işlemler** sekmesinde **Kullanıcı adı** sütununda listelenir.|
    |[/CrossSession](../profiling/crosssession.md)|Diğer oturumlardaki işlemlerin profilini oluşturmaya izin vermez. Hizmet farklı bir oturumda çalışıyorsa, bu seçenek gereklidir. Oturum KIMLIĞI, Windows Görev Yöneticisi 'nin **süreçler** SEKMESINDEKI **oturum kimliği** sütununda listelenir. **/CS** , **/CrossSession** için bir kısaltma olarak belirtilebilir.|
    |[/WINCOUNTER](../profiling/wincounter.md) **:**`WinCounterPath`|Profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir.|
    |[/AutoMark](../profiling/automark.md) **:**`Interval`|Yalnızca **/WINCOUNTER** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 MS 'dir.|
    |[/Events](../profiling/events-vsperfcmd.md) **:**`Config`|Profil oluşturma sırasında toplanacak bir Windows için olay Izleme (ETW) olayı belirtir. ETW olayları ayrı bir (.*ETL*) dosyası.|

6. Gerekirse, hizmeti başlatın.

7. Profil oluşturucuyu hizmete ekleyin. Şunu yazın:

     **VSPerfCmd/Attach:** `PID` [[/targetclr](../profiling/targetclr.md)**:** `Version` ]

    - `PID` Hizmetin işlem KIMLIĞINI veya işlem adını belirtir. Windows Görev Yöneticisi 'nde çalışan tüm işlemlerin işlem kimliklerini görüntüleyebilirsiniz.

    - **targetclr:** `Version` bir uygulamaya çalışma zamanının birden fazla sürümü yüklendiğinde profil için ortak dil çalışma zamanının (CLR) sürümünü belirtir. İsteğe bağlı.

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hizmet çalışırken, *VSPerfCmd.exe* seçeneklerini kullanarak verileri dosyaya yazmayı başlatıp durdurarak veri toplamayı kontrol edebilirsiniz. Veri toplamayı denetlemek, program yürütmenin, uygulamanın başlatılması veya kapatılmasını gibi belirli bir bölümü için veri toplamanızı sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki **VSPerfCmd** seçenek çiftleri veri toplamayı başlatır ve durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Tüm süreçler için veri toplamayı başlatır (**/GlobalOn**) veya Durdur (**/globaloff**).|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|İşlem KIMLIĞI () tarafından belirtilen işlem için (**/ProcessOn**) veya duraklar (**/ProcessOff**) veri toplamayı başlatır `PID` .|
    |**/Attach:**{ `PID`&#124;`ProcName` } [/detach](../profiling/detach.md)[: { `PID`&#124;`ProcName` }]|**/Attach** işlem kimliği veya işlem adı tarafından belirtilen işlem için veri toplamaya başlar. **/Detach** belirtilen işlem veya belirli bir işlem belirtilmemişse tüm işlemler için veri toplamayı durduruyor.|

- Veri dosyasına bir profil oluşturma işareti eklemek için **VSPerfCmd.exe** [/Mark](../profiling/mark.md) seçeneğini de kullanabilirsiniz. **/Mark** komutu bir tanımlayıcı, bir zaman damgası ve Kullanıcı tanımlı isteğe bağlı bir metin dizesi ekler. İşaretler, profil oluşturucu raporlarında ve veri görünümlerinde verileri filtrelemek için kullanılabilir. Aşağıdaki VSPerfCmd seçenek çiftleri veri toplamayı başlatır ve durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu Sonlandır
 Profil oluşturma oturumunu sonlandırmak için, profil oluşturucunun veri toplamamalıdır. Hizmeti durdurarak veya **VSPerfCmd/detach** seçeneğini çağırarak eşzamanlılık yöntemiyle profili oluşturulmuş bir uygulamadan veri toplamayı durdurabilirsiniz. Ardından, profil oluşturucuyu kapatmak ve profil oluşturma veri dosyasını kapatmak için **VSPerfCmd/shutdown** seçeneğini çağırın. **VSPerfCLREnv/globaloff** komutu profil oluşturma ortam değişkenlerini temizler, ancak bilgisayar yeniden başlatılana kadar sistem yapılandırması sıfırlanmaz.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sonlandırmak için

1. Profil oluşturucuyu hedef uygulamadan ayırmak için aşağıdakilerden birini yapın.

    - Hizmeti durdurun.

         -veya-

    - **VSPerfCmd/çıkarılabilir yazın.**

2. Profil oluşturucuyu kapatın. Şunu yazın:

     **VSPerfCmd**  [kapatması](../profiling/shutdown.md)
