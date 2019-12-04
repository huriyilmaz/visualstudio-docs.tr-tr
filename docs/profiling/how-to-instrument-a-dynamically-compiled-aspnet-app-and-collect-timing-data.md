---
title: 'Profil oluşturucu komut satırı: dinamik ASP.NET uygulamasını gereç, zamanlama verilerini al'
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: d8270c9948efe5f9c972f2e4f0eccb035c793953
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74775463"
---
# <a name="how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line"></a>Nasıl yapılır: dinamik olarak derlenen bir ASP.NET Web uygulamasını izleme ve komut satırını kullanarak profil Oluşturucu ile ayrıntılı zamanlama verileri toplama

Bu makalede, izleme profili oluşturma yöntemi kullanılarak dinamik olarak derlenen bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] uygulaması için ayrıntılı zamanlama verileri toplamak üzere Visual Studio Profil Oluşturma Araçları komut satırı araçlarının nasıl kullanılacağı açıklanır.

> [!NOTE]
> Profil oluşturma araçlarının yolunu almak için, bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). 64 bit bilgisayarlarda, araçların her ikisi de 64-bit ve 32 bit sürümleri mevcuttur. Profil oluşturucu komut satırı araçlarını kullanmak için araçlar yolunu komut Istemi penceresinin PATH ortam değişkenine eklemeniz ya da komutun kendisine eklemeniz gerekir.

[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulamasından performans verilerini toplamak için, [vsinstr. exe](../profiling/vsinstr.md) aracını dinamik olarak derlenen uygulama dosyalarını işaretlemek üzere hedef uygulamanın *Web. config* dosyasını değiştirirsiniz. Daha sonra, profil oluşturmayı etkinleştirmek üzere Web sunucusunda uygun ortam değişkenlerini ayarlamak için [VSPerfCLREnv. cmd](../profiling/vsperfclrenv.md) aracını kullanın ve ardından bilgisayarı yeniden başlatın.

Profil oluşturucuyu başlatın ve hedef uygulamayı çalıştırın. Profil Oluşturucu uygulamaya iliştirirken, veri toplamayı duraklatabilir ve devam ettirebilirsiniz. Profil oluşturmayı bitirdiğinizde uygulamayı kapatın, Internet Information Services (IIS) çalışan işlemini kapatın ve sonra profil oluşturucuyu kapatın. Profil oluşturma işinizi tamamladıktan sonra, *Web. config* dosyasını ve Web sunucusunu özgün durumlarına geri yükleyin.

## <a name="configure-the-aspnet-web-application-and-the-web-server"></a>ASP.NET Web uygulamasını ve Web sunucusunu yapılandırma

1. Hedef uygulamanın *Web. config* dosyasını değiştirin. Bkz. [nasıl yapılır: Web. config dosyalarını dinamik olarak derlenen ASP.NET Web uygulamalarını işaretlemek ve profil haline getirmek Için değiştirme](../profiling/how-to-modify-web-config-files-to-instrument-dynamically-compiled-aspnet-apps.md).

2. Bir Komut İstemi penceresi açın.

3. Profil oluşturma ortamı değişkenlerini başlatın. Tür:

     **VSPerfClrEnv/globaltraceon**

    - **/globaltraceon** , izleme yöntemini kullanarak profil oluşturmayı mümkün.

4. Bilgisayarı yeniden başlatın.

## <a name="run-the-profiling-session"></a>Profil oluşturma oturumunu çalıştırma

1. Bir Komut İstemi penceresi açın.

2. Profil oluşturucuyu başlatın. Tür:

     **VSPerfCmd**  [/Start](../profiling/start.md) **: Trace**  [/output](../profiling/output.md) **:** `OutputFile` [`Options`]

   - **/Start: Trace** seçeneği profil oluşturucuyu başlatır.

   - **/Output:** `OutputFile` seçeneği, **/Start**ile gereklidir. `OutputFile` profil oluşturma verilerinin adını ve konumunu belirtir (. *VSP*) dosyası.

     Aşağıdaki seçeneklerden herhangi birini, **/Start: Trace** seçeneği ile kullanabilirsiniz.

     > [!NOTE]
     > **/User** ve **/CrossSession** seçenekleri genellikle ASP.NET uygulamaları için gereklidir.

     | Seçenek | Açıklama |
     | - | - |
     | [/User](../profiling/user-vsperfcmd.md) **:** [`Domain` **\\** ]`UserName` | ASP.NET çalışan işleminin sahibi olan hesabın etki alanını ve Kullanıcı adını belirtir. Bu seçenek, işlem oturum açan kullanıcıdan farklı bir kullanıcı olarak çalışıyorsa gereklidir. İşlem sahibi, Windows Görev Yöneticisi 'nin **işlemler** sekmesinde **Kullanıcı adı** sütununda listelenir. |
     | [/CrossSession](../profiling/crosssession.md) | Diğer oturum oturumlarda işlemlerin profilini oluşturmayı mümkün. ASP.NET uygulaması farklı bir oturumda çalışıyorsa, bu seçenek gereklidir. Oturum tanımlayıcısı, Windows Görev Yöneticisi 'nin **süreçler** SEKMESINDEKI **oturum kimliği** sütununda listelenir. **/CS** , **/CrossSession**için bir kısaltma olarak belirtilebilir. |
     | [/globaloff](../profiling/globalon-and-globaloff.md) | Profil Oluşturucu veri koleksiyonu duraklatılmış şekilde başlatılır. Profil oluşturmayı sürdürmeye yönelik [/GlobalOn](../profiling/globalon-and-globaloff.md) kullanın. |
     | [/Counter](../profiling/counter.md) **:** `Config` | `Config`' de belirtilen işlemci performans sayacından bilgi toplar. Her profil oluşturma olayında toplanan verilere sayaç bilgileri eklenir. |
     | [/WINCOUNTER](../profiling/wincounter.md) **:** `WinCounterPath` | Profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir. |
     | [/AutoMark](../profiling/automark.md) **:** `Interval` | Yalnızca **/WINCOUNTER** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 MS 'dir. |
     | [/Events](../profiling/events-vsperfcmd.md) **:** `Config` | Profil oluşturma sırasında toplanacak bir Windows için olay Izleme (ETW) olayı belirtir. ETW olayları ayrı bir (. *ETL*) dosyası. |

3. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulamasını normal şekilde başlatın.

## <a name="control-data-collection"></a>Veri toplamayı denetleme

Hedef uygulama çalışırken, *VSPerfCmd. exe* seçeneklerini kullanarak profil oluşturucu veri dosyasına veri yazmayı başlatıp durdurarak veri toplamayı kontrol edebilirsiniz. Veri toplamayı denetlemek, program yürütmesinin, uygulamayı başlatma veya kapatma gibi belirli bir bölümü için veri toplamanızı sağlar.

- Aşağıdaki seçenek çiftleri veri toplamayı başlatır ve durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Tüm süreçler için veri toplamayı başlatır ( **/GlobalOn**) veya Durdur ( **/globaloff**).|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:** `PID`|İşlem KIMLIĞI (`PID`) tarafından belirtilen işlem için veri toplamayı başlatır ( **/ProcessOn**) veya Durdur ( **/ProcessOff**).|
    |[/ThreadOn](../profiling/threadon-and-threadoff.md) **:** `TID` [/ThreadOff](../profiling/threadon-and-threadoff.md) **:** `TID`|İş parçacığı KIMLIĞI (`TID`) tarafından belirtilen iş parçacığı için ( **/ThreadOn**) veya Durdur ( **/ThreadOff**) veri toplamayı başlatır.|

- Veri dosyasına bir profil oluşturma işareti eklemek için **VSPerfCmd. exe**[/Mark](../profiling/mark.md) seçeneğini de kullanabilirsiniz. **/Mark** komutu bir tanımlayıcı, bir zaman damgası ve Kullanıcı tanımlı isteğe bağlı bir metin dizesi ekler. İşaretler, profil oluşturucu raporlarında ve veri görünümlerinde verileri filtrelemek için kullanılabilir.

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu Sonlandır

Bir profil oluşturma oturumunu sonlandırmak için, hedef [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulamasını kapatın, profili oluşturulmuş işlemi durdurmak için IIS 'yi sıfırlayın ve sonra profil oluşturucuyu kapatın.

1. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulamasını kapatın.

2. Internet Information Services (IIS) ' i sıfırlayarak [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] çalışan işlemini kapatın. Tür:

     **IISReset/stop**

3. Profil oluşturucuyu kapatın. Tür:

     **VSPerfCmd**  [/Shutdown](../profiling/shutdown.md)

4. IIS 'i yeniden başlatın. Tür:

     **IISReset/Start**

## <a name="restore-the-application-and-computer-configuration"></a>Uygulama ve bilgisayar yapılandırmasını geri yükleme

Tüm profil oluşturmayı tamamladığınızda, *Web. config* dosyasını değiştirin, profil oluşturma ortamı değişkenlerini kaldırın ve uygulamayı ve sunucuyu profil oluşturmadan önce içinde oldukları durumlara geri yüklemek için bilgisayarı yeniden başlatın.

1. *Web. config* dosyasını özgün dosyanın bir kopyasıyla değiştirin.

2. Profil oluşturma ortamı değişkenlerini temizleyin. Tür:

     **VSPerfCmd/globaloff**

3. Bilgisayarı yeniden başlatın.

## <a name="see-also"></a>Ayrıca bkz.

[Profil ASP.NET Web uygulamaları](../profiling/command-line-profiling-of-aspnet-web-applications.md)
[izleme yöntemi veri görünümleri](../profiling/instrumentation-method-data-views.md)
