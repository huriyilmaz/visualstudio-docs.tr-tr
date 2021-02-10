---
title: Profil oluşturucu komut satırı gereci tek başına .NET bileşeni, bellek verilerini al
description: Tek başına bir uygulamanın .NET Framework bileşeni için bellek verileri toplamak üzere Visual Studio Profil Oluşturma Araçları komut satırı araçlarının nasıl kullanılacağını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d09cc46a-70f5-48f9-aa24-89913e67b359
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 40d9476b1a96e212709528aa4b8f572cd665fcbc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942756"
---
# <a name="how-to-instrument-a-stand-alone-net-framework-component-and-collect-memory-data-with-the-profiler-by-using-the-command-line"></a>Nasıl yapılır: Tek başına bir .NET Framework bileşenini izleme ve komut satırını kullanarak profil oluşturucu ile bellek verileri toplama
Bu makalede [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ,. exe veya. dll dosyası gibi tek başına bir uygulamanın .NET Framework bileşenini işaretlemek için profil oluşturma araçları komut satırı araçlarının nasıl kullanılacağı ve profil oluşturucuyu kullanarak bellek bilgilerinin toplanması açıklanmaktadır.

> [!NOTE]
> Profil oluşturma araçlarının yolunu almak için, bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). 64 bit bilgisayarlarda, araçların her ikisi de 64-bit ve 32 bit sürümleri mevcuttur. Profil oluşturucu komut satırı araçlarını kullanmak için araçlar yolunu komut Istemi penceresinin PATH ortam değişkenine eklemeniz ya da komutun kendisine eklemeniz gerekir.

 İzleme yöntemini kullanarak bir .NET Framework bileşeninden bellek verileri toplamak için, profil oluşturma ortamı değişkenlerini başlatmak üzere bileşenin belgelenmiş bir sürümünü ve [VSPerfCLREnv. cmd](../profiling/vsperfclrenv.md) aracını oluşturmak için [VSInstr.exe](../profiling/vsinstr.md) aracını kullanın. Ardından *VSPerfCmd.exe* aracını kullanarak profil oluşturucuyu başlatabilirsiniz.

 Araçlı bileşen yürütüldüğünde, bellek verileri otomatik olarak bir veri dosyasına toplanır. Profil oluşturma oturumu sırasında veri toplamayı duraklatabilir ve devam ettirebilirsiniz.

 Profil oluşturma oturumunu sonlandırmak için hedef uygulamayı kapatır ve profil oluşturucuyu açıkça kapatın. Çoğu durumda, bir oturumun sonunda profil oluşturma ortam değişkenlerini temizlemeniz önerilir.

## <a name="start-the-application-with-the-profiler"></a>Uygulamayı Profil Oluşturucu ile başlatma

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Profil oluşturucuyu çalışan bir .NET Framework uygulamasına eklemek için

1. Bir komut istemi penceresi açın.

2. Hedef uygulamanın belgelenmiş bir sürümünü oluşturmak için **vsinstr** aracını kullanın.

3. .NET Framework profil oluşturma ortamı değişkenlerini başlatın. Şunu yazın:

    **VSPerfCLREnv** {**/tracegc** &#124; **/tracegclife**}

   - **/Tracegc** ve **/tracegclife** seçenekleri, yalnızca bellek ayırma verilerini toplamak için ortam değişkenlerini başlatır veya hem bellek ayırma hem de nesne yaşam süresi verilerini toplar.

       |Seçenek|Açıklama|
       |------------|-----------------|
       |**/tracegc**|Yalnızca bellek ayırma verilerinin toplanmasını mümkün.|
       |**/tracegclife**|Hem bellek ayırma hem de nesne yaşam süresi verilerinin toplanmasını mümkün.|

4. Profil oluşturucuyu başlatın. Şunu yazın:

    **VSPerfCmd/start: Trace/output:** `OutputFile` [`Options`]

   - [/Start](../profiling/start.md)**: Trace** seçeneği profil oluşturucuyu başlatır.

   - /Start ile [/output](../profiling/output.md)**:** `OutputFile` seçeneği gereklidir.  `OutputFile` profil oluşturma verilerinin adını ve konumunu belirtir (.*VSP*) dosyası.

     Aşağıdaki seçeneklerden herhangi birini, **/Start: Trace** seçeneği ile kullanabilirsiniz.

   | Seçenek | Açıklama |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Profili oluşturulan işlemin sahibi olan hesabın etki alanını ve Kullanıcı adını belirtir. Bu seçenek yalnızca, işlem oturum açan kullanıcıdan farklı bir kullanıcı olarak çalışıyorsa gereklidir. İşlem sahibi, Windows Görev Yöneticisi 'nin **işlemler** sekmesinde Kullanıcı adı sütununda listelenir. |
   | [/CrossSession](../profiling/crosssession.md) | Diğer oturumlardaki işlemlerin profilini oluşturmaya izin vermez. Uygulama farklı bir oturumda çalışıyorsa, bu seçenek gereklidir. Oturum tanımlayıcısı, Windows Görev Yöneticisi 'nin **süreçler** SEKMESINDEKI **oturum kimliği** sütununda listelenir. **/CS** , **/CrossSession** için bir kısaltma olarak belirtilebilir. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Veri toplama duraklatılmış şekilde profil oluşturucuyu başlatmak için, **/Start** komut satırına **/globaloff** seçeneğini ekleyin. Profil oluşturmayı sürdürmeye yönelik **/GlobalOn** kullanın. |
   | [/WINCOUNTER](../profiling/wincounter.md) **:**`WinCounterPath` | Profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir. |
   | [/AutoMark](../profiling/automark.md) **:**`Interval` | Yalnızca **/WINCOUNTER** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 MS 'dir. |
   | [/Counter](../profiling/counter.md) **:**`Config` | Yapılandırma içinde belirtilen işlemci performans sayacından bilgi toplar. Her profil oluşturma olayında toplanan verilere sayaç bilgileri eklenir. |
   | [Olaylar](../profiling/events-vsperfcmd.md) **:**`Config` | Profil oluşturma sırasında toplanacak bir Windows için olay Izleme (ETW) olayı belirtir. ETW olayları ayrı bir (.*ETL*) dosyası. |

5. Hedef uygulamayı komut Istemi penceresinden başlatın.

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hedef uygulama çalışırken, *VSPerfCmd.exe* seçeneklerini kullanarak verileri dosyaya yazmayı başlatıp durdurarak veri toplamayı kontrol edebilirsiniz. Veri toplamayı denetlemek, program yürütmesinin, uygulamayı başlatma veya kapatma gibi belirli bir bölümü için veri toplamanızı sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki **VSPerfCmd** seçenek çiftleri veri toplamayı başlatır ve durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/GlobalOn](../profiling/globalon-and-globaloff.md) [/globaloff](../profiling/globalon-and-globaloff.md)|Tüm süreçler için veri toplamayı başlatır (**/GlobalOn**) veya Durdur (**/globaloff**).|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|İşlem KIMLIĞI () tarafından belirtilen işlem için (**/ProcessOn**) veya duraklar (**/ProcessOff**) veri toplamayı başlatır `PID` .|
    |[/ThreadOn](../profiling/threadon-and-threadoff.md) **:** `TID` [/ThreadOff](../profiling/threadon-and-threadoff.md) **:**`TID`|İş parçacığı KIMLIĞI () tarafından belirtilen iş parçacığı için (**/ThreadOn**) veya Durdur (**/ThreadOff**) veri toplamayı başlatır `TID` .|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu Sonlandır
 Profil oluşturma oturumunu sonlandırmak için, Araçlı bileşeni çalıştıran uygulamayı kapatın ve ardından **VSPerfCmd** [/Shutdown](../profiling/shutdown.md) seçeneğini çağırıp profil oluşturucuyu kapatın ve profil oluşturma veri dosyasını kapatın. **VSPerfCLREnv/off** komutu profil oluşturma ortam değişkenlerini temizler.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sonlandırmak için

1. Hedef uygulamayı kapatın.

2. Profil oluşturucuyu kapatın. Şunu yazın:

     **VSPerfCmd/shutdown**

3. Seçim Profil oluşturma ortamı değişkenlerini temizleyin. Şunu yazın:

     **VSPerfCmd/off**

## <a name="see-also"></a>Ayrıca bkz.
- [Tek başına uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [.NET bellek verileri görünümleri](../profiling/dotnet-memory-data-views.md)
