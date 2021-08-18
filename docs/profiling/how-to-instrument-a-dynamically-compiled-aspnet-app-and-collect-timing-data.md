---
title: profil oluşturucu komut satırı-araç dinamik ASP.NET uygulaması, zamanlama verilerini al
description: dinamik olarak derlenen ASP.NET uygulaması için ayrıntılı zamanlama verileri toplamak üzere Visual Studio Profil Oluşturma Araçları komut satırı araçlarının nasıl kullanılacağını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 70217105ea5a35aec25b28121d794d941862bbaa9e21b02b276a95c2071e6c3a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121426891"
---
# <a name="how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line"></a>nasıl yapılır: komut satırını kullanarak dinamik olarak derlenmiş ASP.NET web uygulamasını izleme ve profil oluşturucu ile ayrıntılı zamanlama verileri toplama

bu makalede [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] , izleme profili oluşturma yöntemi kullanılarak dinamik olarak derlenen bir uygulama için ayrıntılı zamanlama verileri toplamak üzere Visual Studio Profil Oluşturma Araçları komut satırı araçlarının nasıl kullanılacağı açıklanır.

> [!NOTE]
> Profil oluşturma araçlarının yolunu almak için, bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). 64 bit bilgisayarlarda, araçların her ikisi de 64-bit ve 32 bit sürümleri mevcuttur. Profil oluşturucu komut satırı araçlarını kullanmak için araçlar yolunu komut Istemi penceresinin PATH ortam değişkenine eklemeniz ya da komutun kendisine eklemeniz gerekir.

Bir Web uygulamasından performans verilerini toplamak için [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] , [VSInstr.exe](../profiling/vsinstr.md) aracının dinamik olarak derlenen uygulama dosyalarını işaretlemesini sağlamak üzere hedef uygulamanın *web.config* dosyasını değiştirirsiniz. Daha sonra, profil oluşturmayı etkinleştirmek üzere Web sunucusunda uygun ortam değişkenlerini ayarlamak için [VSPerfCLREnv. cmd](../profiling/vsperfclrenv.md) aracını kullanın ve ardından bilgisayarı yeniden başlatın.

Profil oluşturucuyu başlatın ve hedef uygulamayı çalıştırın. Profil Oluşturucu uygulamaya iliştirirken, veri toplamayı duraklatabilir ve devam ettirebilirsiniz. profil oluşturmayı bitirdiğinizde uygulamayı kapatın, Internet Information Services (ııs) çalışan işlemini kapatın ve sonra profil oluşturucuyu kapatın. Profil oluşturma işinizi tamamladıktan sonra, *web.config* dosyasını ve Web sunucusunu özgün durumlarına geri yükleyin.

## <a name="configure-the-aspnet-web-application-and-the-web-server"></a>ASP.NET web uygulamasını ve web sunucusunu yapılandırma

1. Hedef uygulamanın *web.config* dosyasını değiştirin. bkz. [nasıl yapılır: web.config dosyalarını değiştirme ve profili dinamik olarak derlenmiş ASP.NET web uygulamaları](../profiling/how-to-modify-web-config-files-to-instrument-dynamically-compiled-aspnet-apps.md).

2. Bir komut istemi penceresi açın.

3. Profil oluşturma ortamı değişkenlerini başlatın. Şunu yazın:

     **VSPerfClrEnv/globaltraceon**

    - **/globaltraceon** , izleme yöntemini kullanarak profil oluşturmayı mümkün.

4. Bilgisayarı yeniden başlatın.

## <a name="run-the-profiling-session"></a>Profil oluşturma oturumunu çalıştırma

1. Bir komut istemi penceresi açın.

2. Profil oluşturucuyu başlatın. Şunu yazın:

     **VSPerfCmd**  [/Start](../profiling/start.md) **: Trace**  [/output](../profiling/output.md) **:** `OutputFile` [ `Options` ]

   - **/Start: Trace** seçeneği profil oluşturucuyu başlatır.

   - /Start ile **/output:** `OutputFile` seçeneği gereklidir.  `OutputFile` profil oluşturma verilerinin adını ve konumunu belirtir (.*VSP*) dosyası.

     Aşağıdaki seçeneklerden herhangi birini, **/Start: Trace** seçeneği ile kullanabilirsiniz.

     > [!NOTE]
     > **/user** ve **/crosssession** seçenekleri genellikle ASP.NET uygulamalar için gereklidir.

     | Seçenek | Açıklama |
     | - | - |
     | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | ASP.NET çalışan işleminin sahibi olan hesabın etki alanını ve kullanıcı adını belirtir. Bu seçenek, işlem oturum açan kullanıcıdan farklı bir kullanıcı olarak çalışıyorsa gereklidir. işlem sahibi, Windows görev yöneticisi 'nin **işlemler** sekmesinde **kullanıcı adı** sütununda listelenir. |
     | [/CrossSession](../profiling/crosssession.md) | Diğer oturum oturumlarda işlemlerin profilini oluşturmayı mümkün. ASP.NET uygulaması farklı bir oturumda çalışıyorsa, bu seçenek gereklidir. oturum tanımlayıcısı, Windows görev yöneticisi 'nin **süreçler** sekmesindeki **oturum kimliği** sütununda listelenir. **/CS** , **/CrossSession** için bir kısaltma olarak belirtilebilir. |
     | [/globaloff](../profiling/globalon-and-globaloff.md) | Profil Oluşturucu veri koleksiyonu duraklatılmış şekilde başlatılır. Profil oluşturmayı sürdürmeye yönelik [/GlobalOn](../profiling/globalon-and-globaloff.md) kullanın. |
     | [/Counter](../profiling/counter.md) **:**`Config` | ' De belirtilen işlemci performans sayacından bilgi toplar `Config` . Her profil oluşturma olayında toplanan verilere sayaç bilgileri eklenir. |
     | [/WINCOUNTER](../profiling/wincounter.md) **:**`WinCounterPath` | profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir. |
     | [/AutoMark](../profiling/automark.md) **:**`Interval` | Yalnızca **/WINCOUNTER** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 MS 'dir. |
     | [/Events](../profiling/events-vsperfcmd.md) **:**`Config` | profil oluşturma sırasında toplanacak Windows (ETW) olayı için bir olay izleme olayı belirtir. ETW olayları ayrı bir (.*ETL*) dosyası. |

3. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]Web uygulamasını normal şekilde başlatın.

## <a name="control-data-collection"></a>Veri toplamayı denetleme

Hedef uygulama çalışırken, *VSPerfCmd.exe* seçeneklerini kullanarak profil oluşturucu veri dosyasına veri yazmayı başlatıp durdurarak veri toplamayı kontrol edebilirsiniz. Veri toplamayı denetlemek, program yürütmesinin, uygulamayı başlatma veya kapatma gibi belirli bir bölümü için veri toplamanızı sağlar.

- Aşağıdaki seçenek çiftleri veri toplamayı başlatır ve durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Tüm süreçler için veri toplamayı başlatır (**/GlobalOn**) veya Durdur (**/globaloff**).|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|İşlem KIMLIĞI () tarafından belirtilen işlem için (**/ProcessOn**) veya duraklar (**/ProcessOff**) veri toplamayı başlatır `PID` .|
    |[/ThreadOn](../profiling/threadon-and-threadoff.md) **:** `TID` [/ThreadOff](../profiling/threadon-and-threadoff.md) **:**`TID`|İş parçacığı KIMLIĞI () tarafından belirtilen iş parçacığı için (**/ThreadOn**) veya Durdur (**/ThreadOff**) veri toplamayı başlatır `TID` .|

- Veri dosyasına bir profil oluşturma işareti eklemek için **VSPerfCmd.exe** [/Mark](../profiling/mark.md) seçeneğini de kullanabilirsiniz. **/Mark** komutu bir tanımlayıcı, bir zaman damgası ve Kullanıcı tanımlı isteğe bağlı bir metin dizesi ekler. İşaretler, profil oluşturucu raporlarında ve veri görünümlerinde verileri filtrelemek için kullanılabilir.

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu Sonlandır

Bir profil oluşturma oturumunu sonlandırmak için, hedef [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulamasını kapatın, profili oluşturulmuş işlemi durdurmak IÇIN IIS 'i sıfırlayın ve sonra profil oluşturucuyu kapatın.

1. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]Web uygulamasını kapatın.

2. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]Internet Information Services (ııs) öğesini sıfırlayarak çalışan işlemini kapatın. Şunu yazın:

     **IISReset/stop**

3. Profil oluşturucuyu kapatın. Şunu yazın:

     **VSPerfCmd**  [/Shutdown](../profiling/shutdown.md)

4. IIS’yi yeniden başlatın. Şunu yazın:

     **IISReset/Start**

## <a name="restore-the-application-and-computer-configuration"></a>Uygulama ve bilgisayar yapılandırmasını geri yükleme

Tüm profil oluşturmayı tamamladıktan sonra *web.config* dosyasını değiştirin, profil oluşturma ortamı değişkenlerini kaldırın ve uygulamayı ve sunucuyu profil oluşturmadan önce içinde oldukları durumlara geri yüklemek için bilgisayarı yeniden başlatın.

1. *web.config* dosyasını özgün dosyanın kopyasıyla değiştirin.

2. Profil oluşturma ortamı değişkenlerini temizleyin. Şunu yazın:

     **VSPerfCmd/globaloff**

3. Bilgisayarı yeniden başlatın.

## <a name="see-also"></a>Ayrıca bkz.

[web uygulamalarının](../profiling/command-line-profiling-of-aspnet-web-applications.md) 
 profilini ASP.NET [İzleme yöntemi veri görünümleri](../profiling/instrumentation-method-data-views.md)
