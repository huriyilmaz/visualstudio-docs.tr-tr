---
title: 'Profil oluşturucu komut satırı: dinamik ASP.NET uygulamasını gereç, bellek verilerini edinme'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2cdd9903-39db-47e8-93dd-5e6a21bc3435
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 3378a45ebace942bb8696f2f67962365b5f57796
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778888"
---
# <a name="how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line"></a>Nasıl yapılır: profil oluşturucu komut satırını kullanarak dinamik olarak derlenmiş bir ASP.NET Web uygulamasını izleme ve bellek verileri toplama
Bu konuda, izleme profili oluşturma yöntemi kullanılarak dinamik olarak derlenmiş bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulaması için ayrıntılı .NET bellek ayırma ve nesne yaşam süresi verilerini toplamak üzere [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Oluşturma Araçları komut satırı araçlarının nasıl kullanılacağı açıklanmaktadır.

> [!NOTE]
> Profil oluşturma araçlarının yolunu almak için, bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). 64 bit bilgisayarlarda, araçların her ikisi de 64-bit ve 32 bit sürümleri mevcuttur. Profil oluşturucu komut satırı araçlarını kullanmak için araçlar yolunu komut Istemi penceresinin PATH ortam değişkenine eklemeniz ya da komutun kendisine eklemeniz gerekir.

 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulamasından performans verilerini toplamak için, [vsinstr. exe](../profiling/vsinstr.md) aracını dinamik olarak derlenen uygulama dosyalarını işaretlemek üzere hedef uygulamanın *Web. config* dosyasını değiştirirsiniz. Daha sonra, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulamasını barındıran sunucuyu yapılandırmak için [VSPerfCLREnv. cmd](../profiling/vsperfclrenv.md) aracını kullanın ve uygun ortam değişkenlerini ayarlayarak .net bellek profili oluşturmayı etkinleştirin ve ardından bilgisayarı yeniden başlatın.

 Veri toplamak için profil oluşturucuyu başlatın ve hedef uygulamayı çalıştırın. Profil Oluşturucu uygulamaya iliştirirken, veri toplamayı duraklatabilir ve devam ettirebilirsiniz. Uygun verileri topladığınızda, uygulamayı kapatın, Internet Information Services (IIS) çalışan işlemini kapatın ve sonra profil oluşturucuyu kapatın.

 Profil oluşturma işinizi tamamladıktan sonra, *Web. config* dosyasını ve Web sunucusunu özgün durumlarına geri yükleyin.

## <a name="configure-the-aspnet-web-application-and-the-web-server"></a>ASP.NET Web uygulamasını ve Web sunucusunu yapılandırma

#### <a name="to-configure-the-aspnet-web-application-and-the-web-server"></a>ASP.NET Web uygulamasını ve Web sunucusunu yapılandırmak için

1. Hedef uygulamanın *Web. config* dosyasını değiştirin. Bkz. [nasıl yapılır: Web. config dosyalarını dinamik olarak derlenen ASP.NET Web uygulamalarını işaretlemek ve profil haline getirmek Için değiştirme](../profiling/how-to-modify-web-config-files-to-instrument-dynamically-compiled-aspnet-apps.md).

2. Web uygulamasını barındıran bilgisayarda bir komut istemi penceresi açın.

3. Profil oluşturma ortamı değişkenlerini başlatın. Tür:

     **VSPerfClrEnv/globaltracegc**

     veya

     **VSPerfClrEnv/globaltracegclife**

    - **/globaltracegc** bellek ayırma verilerinin toplanmasını mümkün.

    - **/globaltracegclife** , bellek ayırma verilerinin ve nesne yaşam süresi verilerinin toplanmasını mümkün.

4. Bilgisayarı yeniden başlatın.

## <a name="run-the-profiling-session"></a>Profil oluşturma oturumunu çalıştırma

#### <a name="to-profile-the-aspnet-web-application"></a>ASP.NET Web uygulamasını profili eklemek için

1. Profil oluşturucuyu başlatın. Tür:

    **VSPerfCmd** [/Start](../profiling/start.md) **: Trace** [/output](../profiling/output.md) **:** `OutputFile` [`Options`]

   - **/Start: Trace** seçeneği profil oluşturucuyu başlatır.

   - **/Output:** `OutputFile` seçeneği, **/Start**ile gereklidir. `OutputFile` profil oluşturma verilerinin adını ve konumunu belirtir (. *VSP*) dosyası.

     Aşağıdaki seçeneklerden herhangi birini, **/Start: Trace** seçeneği ile kullanabilirsiniz.

   > [!NOTE]
   > **/User** ve **/CrossSession** seçenekleri genellikle ASP.NET uygulamaları için gereklidir.

   | Seçenek | Açıklama |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:** [`Domain` **\\** ]`UserName` | [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] çalışan işlemine sahip olan hesabın isteğe bağlı etki alanını ve Kullanıcı adını belirtir. İşlem, oturum açmış kullanıcı dışında bir kullanıcı olarak çalışıyorsa, bu seçenek gereklidir. Ad, Windows Görev Yöneticisi 'nin **süreçler** sekmesinde **Kullanıcı adı** sütununda listelenir. |
   | [/CrossSession](../profiling/crosssession.md) | Diğer oturumlardaki işlemlerin profilini oluşturmaya izin vermez. Uygulama farklı bir oturumda çalışıyorsa, bu seçenek gereklidir. Oturum KIMLIĞI, Windows Görev Yöneticisi 'nin **süreçler** SEKMESINDEKI **oturum kimliği** sütununda listelenir. **/CS** , **/CrossSession**için bir kısaltma olarak belirtilebilir. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Profil Oluşturucu veri koleksiyonu duraklatılmış şekilde başlatılır. Profil oluşturmayı sürdürmeye yönelik [/GlobalOn](../profiling/globalon-and-globaloff.md) kullanın. |
   | [/Counter](../profiling/counter.md) **:** `Config` | `Config`' de belirtilen işlemci performans sayacından bilgi toplar. Her profil oluşturma olayında toplanan verilere sayaç bilgileri eklenir. |
   | [/WINCOUNTER](../profiling/wincounter.md) **:** `WinCounterPath` | Profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir. |
   | [/AutoMark](../profiling/automark.md) **:** `Interval` | Yalnızca **/WINCOUNTER** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 MS 'dir. |
   | [/Events](../profiling/events-vsperfcmd.md) **:** `Config` | Profil oluşturma sırasında toplanacak bir Windows için olay Izleme (ETW) olayı belirtir. ETW olayları ayrı bir (. *ETL*) dosyası. |

2. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulamasını normal şekilde başlatın.

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hedef uygulama çalışırken, *VSPerfCmd. exe* seçeneklerini kullanarak profil oluşturucu veri dosyasına veri yazmayı başlatıp durdurarak veri toplamayı kontrol edebilirsiniz. Veri toplamayı denetlemek, program yürütmesinin, uygulamayı başlatma veya kapatma gibi belirli bir bölümü için veri toplamanızı sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki seçenek çiftleri veri toplamayı başlatır ve durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Tüm süreçler için veri toplamayı başlatır ( **/GlobalOn**) veya Durdur ( **/globaloff**).|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:** `PID`|İşlem KIMLIĞI (`PID`) tarafından belirtilen işlem için veri toplamayı başlatır ( **/ProcessOn**) veya Durdur ( **/ProcessOff**).|
    |[/ThreadOn](../profiling/threadon-and-threadoff.md) **:** `TID` [/ThreadOff](../profiling/threadon-and-threadoff.md) **:** `TID`|İş parçacığı KIMLIĞI (`TID`) tarafından belirtilen iş parçacığı için ( **/ThreadOn**) veya Durdur ( **/ThreadOff**) veri toplamayı başlatır.|

- Veri dosyasına bir profil oluşturma işareti eklemek için **VSPerfCmd. exe**[/Mark](../profiling/mark.md) seçeneğini de kullanabilirsiniz. **/Mark** komutu bir tanımlayıcı, bir zaman damgası ve Kullanıcı tanımlı isteğe bağlı bir metin dizesi ekler. İşaretler, profil oluşturucu raporlarında ve veri görünümlerinde verileri filtrelemek için kullanılabilir.

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu Sonlandır
 Profil oluşturma oturumunu sonlandırmak için, hedef [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulamasını kapatın, profili oluşturulmuş işlemi durdurmak için Internet Information Services (IIS) durdurun ve ardından Profiler 'ı kapatın. Ardından IIS 'yi yeniden başlatın.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sonlandırmak için

1. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulamasını kapatın.

2. Internet Information Services (IIS) ' i sıfırlayarak [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] çalışan işlemini kapatın. Tür:

    **IISReset/stop**

3. Profil oluşturucuyu kapatın. Tür:

    **VSPerfCmd** [/Shutdown](../profiling/shutdown.md)

4. IIS 'i yeniden başlatın. Tür:

    **IISReset/Start**

## <a name="restore-the-application-and-computer-configuration"></a>Uygulama ve bilgisayar yapılandırmasını geri yükleme
 Tüm profil oluşturmayı tamamladığınızda, *Web. config* dosyasını değiştirin, profil oluşturma ortamı değişkenlerini kaldırın ve sunucuyu ve [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] uygulamasını özgün durumlarına geri yüklemek için bilgisayarı yeniden başlatın.

#### <a name="to-restore-the-application-and-computer-configuration"></a>Uygulama ve bilgisayar yapılandırmasını geri yüklemek için

1. *Web. config* dosyasını özgün dosyanın bir kopyasıyla değiştirin.

2. (İsteğe bağlı). Profil oluşturma ortamı değişkenlerini temizleyin. Tür:

     **VSPerfCmd/globaloff**

3. Bilgisayarı yeniden başlatın.

## <a name="see-also"></a>Ayrıca bkz.
- [ASP.NET Web uygulamaları profili](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [.NET bellek verileri görünümleri](../profiling/dotnet-memory-data-views.md)
