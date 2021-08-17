---
title: profil oluşturucu komut satırı-araç dinamik ASP.NET uygulaması, bellek verilerini al
description: dinamik olarak derlenen ASP.NET uygulaması için ayrıntılı bellek etkinliği verileri toplamak üzere Visual Studio Profil Oluşturma Araçları komut satırı araçlarının nasıl kullanılacağını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 2cdd9903-39db-47e8-93dd-5e6a21bc3435
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 711f30b9dd93af7da03319a837e7990c437da6e5fd9efd5c0506cab1be247a3c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121355106"
---
# <a name="how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line"></a>nasıl yapılır: profil oluşturucu komut satırını kullanarak dinamik olarak derlenmiş bir ASP.NET web uygulamasını izleme ve bellek verileri toplama
Bu konu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] , izleme profili oluşturma yöntemi kullanılarak dinamik olarak derlenen bir Web uygulaması için ayrıntılı .net bellek ayırma ve nesne yaşam süresi verilerini toplamak üzere profil oluşturma araçları komut satırı araçlarının nasıl kullanılacağını açıklar.

> [!NOTE]
> Profil oluşturma araçlarının yolunu almak için, bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). 64 bit bilgisayarlarda, araçların her ikisi de 64-bit ve 32 bit sürümleri mevcuttur. Profil oluşturucu komut satırı araçlarını kullanmak için araçlar yolunu komut Istemi penceresinin PATH ortam değişkenine eklemeniz ya da komutun kendisine eklemeniz gerekir.

 Bir Web uygulamasından performans verilerini toplamak için [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] , [VSInstr.exe](../profiling/vsinstr.md) aracının dinamik olarak derlenen uygulama dosyalarını işaretlemesini sağlamak üzere hedef uygulamanın *web.config* dosyasını değiştirirsiniz. Daha sonra, [VSPerfCLREnv. cmd](../profiling/vsperfclrenv.md) aracını kullanarak Web uygulamasını barındıran sunucuyu yapılandırabilir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ve uygun ortam değişkenlerini ayarlayarak ve ardından bilgisayarı yeniden başlatarak .net bellek profili oluşturmayı etkinleştirebilirsiniz.

 Veri toplamak için profil oluşturucuyu başlatın ve hedef uygulamayı çalıştırın. Profil Oluşturucu uygulamaya iliştirirken, veri toplamayı duraklatabilir ve devam ettirebilirsiniz. uygun verileri topladığınızda, uygulamayı kapatın, Internet Information Services (ııs) çalışan işlemini kapatın ve sonra profil oluşturucuyu kapatın.

 Profil oluşturma işinizi tamamladıktan sonra, *web.config* dosyasını ve Web sunucusunu özgün durumlarına geri yükleyin.

## <a name="configure-the-aspnet-web-application-and-the-web-server"></a>ASP.NET web uygulamasını ve web sunucusunu yapılandırma

#### <a name="to-configure-the-aspnet-web-application-and-the-web-server"></a>ASP.NET web uygulamasını ve web sunucusunu yapılandırmak için

1. Hedef uygulamanın *web.config* dosyasını değiştirin. bkz. [nasıl yapılır: web.config dosyalarını değiştirme ve profili dinamik olarak derlenmiş ASP.NET web uygulamaları](../profiling/how-to-modify-web-config-files-to-instrument-dynamically-compiled-aspnet-apps.md).

2. Web uygulamasını barındıran bilgisayarda bir komut istemi penceresi açın.

3. Profil oluşturma ortamı değişkenlerini başlatın. Şunu yazın:

     **VSPerfClrEnv/globaltracegc**

     -veya-

     **VSPerfClrEnv/globaltracegclife**

    - **/globaltracegc** bellek ayırma verilerinin toplanmasını mümkün.

    - **/globaltracegclife** , bellek ayırma verilerinin ve nesne yaşam süresi verilerinin toplanmasını mümkün.

4. Bilgisayarı yeniden başlatın.

## <a name="run-the-profiling-session"></a>Profil oluşturma oturumunu çalıştırma

#### <a name="to-profile-the-aspnet-web-application"></a>ASP.NET web uygulaması profilini almak için

1. Profil oluşturucuyu başlatın. Şunu yazın:

    **VSPerfCmd** [/Start](../profiling/start.md) **: Trace** [/output](../profiling/output.md) **:** `OutputFile` [ `Options` ]

   - **/Start: Trace** seçeneği profil oluşturucuyu başlatır.

   - /Start ile **/output:** `OutputFile` seçeneği gereklidir.  `OutputFile` profil oluşturma verilerinin adını ve konumunu belirtir (.*VSP*) dosyası.

     Aşağıdaki seçeneklerden herhangi birini, **/Start: Trace** seçeneği ile kullanabilirsiniz.

   > [!NOTE]
   > **/user** ve **/crosssession** seçenekleri genellikle ASP.NET uygulamalar için gereklidir.

   | Seçenek | Açıklama |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Çalışan işlemin sahibi olan hesabın isteğe bağlı etki alanını ve Kullanıcı adını belirtir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] . İşlem, oturum açmış kullanıcı dışında bir kullanıcı olarak çalışıyorsa, bu seçenek gereklidir. ad, Windows görev yöneticisi 'nin **süreçler** sekmesinde **kullanıcı adı** sütununda listelenir. |
   | [/CrossSession](../profiling/crosssession.md) | Diğer oturumlardaki işlemlerin profilini oluşturmaya izin vermez. Uygulama farklı bir oturumda çalışıyorsa, bu seçenek gereklidir. oturum kimliği, Windows görev yöneticisi 'nin **süreçler** sekmesindeki **oturum kimliği** sütununda listelenir. **/CS** , **/CrossSession** için bir kısaltma olarak belirtilebilir. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Profil Oluşturucu veri koleksiyonu duraklatılmış şekilde başlatılır. Profil oluşturmayı sürdürmeye yönelik [/GlobalOn](../profiling/globalon-and-globaloff.md) kullanın. |
   | [/Counter](../profiling/counter.md) **:**`Config` | ' De belirtilen işlemci performans sayacından bilgi toplar `Config` . Her profil oluşturma olayında toplanan verilere sayaç bilgileri eklenir. |
   | [/WINCOUNTER](../profiling/wincounter.md) **:**`WinCounterPath` | profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir. |
   | [/AutoMark](../profiling/automark.md) **:**`Interval` | Yalnızca **/WINCOUNTER** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 MS 'dir. |
   | [/Events](../profiling/events-vsperfcmd.md) **:**`Config` | profil oluşturma sırasında toplanacak Windows (ETW) olayı için bir olay izleme olayı belirtir. ETW olayları ayrı bir (.*ETL*) dosyası. |

2. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]Web uygulamasını normal şekilde başlatın.

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hedef uygulama çalışırken, *VSPerfCmd.exe* seçeneklerini kullanarak profil oluşturucu veri dosyasına veri yazmayı başlatıp durdurarak veri toplamayı kontrol edebilirsiniz. Veri toplamayı denetlemek, program yürütmesinin, uygulamayı başlatma veya kapatma gibi belirli bir bölümü için veri toplamanızı sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki seçenek çiftleri veri toplamayı başlatır ve durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Tüm süreçler için veri toplamayı başlatır (**/GlobalOn**) veya Durdur (**/globaloff**).|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|İşlem KIMLIĞI () tarafından belirtilen işlem için (**/ProcessOn**) veya duraklar (**/ProcessOff**) veri toplamayı başlatır `PID` .|
    |[/ThreadOn](../profiling/threadon-and-threadoff.md) **:** `TID` [/ThreadOff](../profiling/threadon-and-threadoff.md) **:**`TID`|İş parçacığı KIMLIĞI () tarafından belirtilen iş parçacığı için (**/ThreadOn**) veya Durdur (**/ThreadOff**) veri toplamayı başlatır `TID` .|

- Veri dosyasına bir profil oluşturma işareti eklemek için **VSPerfCmd.exe** [/Mark](../profiling/mark.md) seçeneğini de kullanabilirsiniz. **/Mark** komutu bir tanımlayıcı, bir zaman damgası ve Kullanıcı tanımlı isteğe bağlı bir metin dizesi ekler. İşaretler, profil oluşturucu raporlarında ve veri görünümlerinde verileri filtrelemek için kullanılabilir.

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu Sonlandır
 profil oluşturma oturumunu sonlandırmak için, hedef [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] web uygulamasını kapatın, profili oluşturulmuş işlemi durdurmak için Internet Information Services (ııs) durdurun ve ardından profil oluşturucuyu kapatın. Ardından IIS 'yi yeniden başlatın.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sonlandırmak için

1. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]Web uygulamasını kapatın.

2. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]Internet Information Services (ııs) öğesini sıfırlayarak çalışan işlemini kapatın. Şunu yazın:

    **IISReset/stop**

3. Profil oluşturucuyu kapatın. Şunu yazın:

    **VSPerfCmd** [/Shutdown](../profiling/shutdown.md)

4. IIS’yi yeniden başlatın. Şunu yazın:

    **IISReset/Start**

## <a name="restore-the-application-and-computer-configuration"></a>Uygulama ve bilgisayar yapılandırmasını geri yükleme
 Tüm profil oluşturmayı tamamladıktan sonra *web.config* dosyasını değiştirin, profil oluşturma ortamı değişkenlerini temizleyin ve sunucuyu ve uygulamayı özgün durumlarına geri yüklemek için bilgisayarı yeniden başlatın [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] .

#### <a name="to-restore-the-application-and-computer-configuration"></a>Uygulama ve bilgisayar yapılandırmasını geri yüklemek için

1. *web.config* dosyasını özgün dosyanın kopyasıyla değiştirin.

2. (İsteğe bağlı). Profil oluşturma ortamı değişkenlerini temizleyin. Şunu yazın:

     **VSPerfCmd /globaloff**

3. Bilgisayarı yeniden başlatın.

## <a name="see-also"></a>Ayrıca bkz.
- [Web ASP.NET profil oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [.NET bellek veri görünümleri](../profiling/dotnet-memory-data-views.md)
