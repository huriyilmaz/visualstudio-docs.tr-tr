---
title: 'Profil oluşturucu komut satırı: static ASP.NET uygulamasını gereç, bellek verilerini edinme'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ea1dcb7c-1dc3-49ff-9418-8795b5b3d3bc
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 98fac9f01219cd398f1d5ec462e3f5165f4638d7
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74775437"
---
# <a name="how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line"></a>Nasıl yapılır: profil oluşturucu komut satırını kullanarak statik olarak derlenen bir ASP.NET Web uygulamasını izleme ve bellek verileri toplama
Bu makalede, önceden derlenmiş bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web bileşenini veya Web sitesini işaretlemek ve .NET bellek ayırmayı, nesne ömrünü ve ayrıntılı zamanlama verilerini toplamak için [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Oluşturma Araçları komut satırı araçlarının nasıl kullanılacağı açıklanır.

> [!NOTE]
> Profil oluşturma araçlarının yolunu almak için, bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). 64 bit bilgisayarlarda, araçların her ikisi de 64-bit ve 32 bit sürümleri mevcuttur. Profil oluşturucu komut satırı araçlarını kullanmak için araçlar yolunu komut Istemi penceresinin PATH ortam değişkenine eklemeniz ya da komutun kendisine eklemeniz gerekir.

 İzleme yöntemini kullanarak bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web bileşeninden veri toplamak için, bir bileşenin belgelenmiş bir sürümünü oluşturmak için [vsinstr. exe](../profiling/vsinstr.md) aracını kullanın. Bileşeni barındıran bilgisayarda, bileşenin belgelenmiş olmayan sürümünü belgelenmiş sürümle değiştirirsiniz. Daha sonra, genel profil oluşturma ortamı değişkenlerini başlatmak için [VSPerfCLREnv. cmd](../profiling/vsperfclrenv.md) aracını kullanın ve ana bilgisayarı yeniden başlatın. Ardından profil oluşturucuyu başlatın.

 Belgelenmiş bileşen yürütüldüğünde, zamanlama verileri bir veri dosyasına otomatik olarak toplanır. Profil oluşturma oturumu sırasında veri toplamayı duraklatabilir ve devam ettirebilirsiniz.

 Profil oluşturma oturumunu sonlandırmak için, bileşeni barındıran [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] çalışan işlemini kapatır ve sonra profil oluşturucuyu açıkça kapatın. Çoğu durumda, bir oturumun sonunda profil oluşturma ortam değişkenlerini temizlemeniz önerilir.

## <a name="start-to-profile"></a>Profile başla

#### <a name="to-instrument-an-aspnet-web-component-and-start-profiling"></a>Bir ASP.NET Web bileşenini işaretlemek ve profil oluşturmayı başlatmak için

1. Hedef uygulamanın belgelenmiş bir sürümünü oluşturmak için **vsinstr** aracını kullanın. Gerekirse, ASP.NET ana bilgisayarındaki uygulama ikililerini belgelenmiş ikili dosyalarla değiştirin.

2. Bir komut istemi penceresi açın

3. .NET profil oluşturma ortamı değişkenlerini başlatın. Komut istemi penceresinde şunu yazın:

    **VSPerfClrEnv/globaltracegc**

    veya

    **VSPerfClrEnv/globaltracegclife**

   - **/globaltracegc** .net bellek ayırmayı ve zamanlama verilerini toplar.

   - **/globaltracegclife** .net bellek ayırmayı, nesne ömrünü ve ayrıntılı zamanlama verilerini toplar.

4. Bilgisayarı yeniden başlatın.

5. Bir komut istemi penceresi açın.

6. Profil oluşturucuyu başlatın. Komut istemi penceresinde şunu yazın:

    **VSPerfCmd/start: Trace/output:** `OutputFile` [`Options`]

   - [/Start](../profiling/start.md) **: Trace** seçeneği profil oluşturucuyu başlatır.

   - [/Output](../profiling/output.md) **:** `OutputFile` seçeneği, **/Start**ile gereklidir. `OutputFile` profil oluşturma verileri (. vsp) dosyasının adını ve konumunu belirtir.

     Aşağıdaki seçeneklerden herhangi birini, **/Start: Trace** seçeneği ile kullanabilirsiniz.

   > [!NOTE]
   > **/User** ve **/CrossSession** seçenekleri genellikle ASP.NET uygulamaları için gereklidir.

   | Seçenek | Açıklama |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:** [`Domain` **\\** ]`UserName` | ASP.NET çalışan işleminin sahibi olan hesabın isteğe bağlı etki alanını ve Kullanıcı adını belirtir. İşlem, oturum açan kullanıcıdan farklı bir kullanıcı olarak çalışıyorsa, bu seçenek gereklidir. Ad, Windows Görev Yöneticisi 'nin **süreçler** sekmesinde **Kullanıcı adı** sütununda listelenir. |
   | [/CrossSession](../profiling/crosssession.md) | Diğer oturumlardaki işlemlerin profilini oluşturmaya izin vermez. Uygulama farklı bir oturumda çalışıyorsa, bu seçenek gereklidir. Oturum KIMLIĞI, Windows Görev Yöneticisi 'nin **süreçler** SEKMESINDEKI oturum kimliği sütununda listelenir. **/CS** , **/CrossSession**için bir kısaltma olarak belirtilebilir. |
   | [/WINCOUNTER](../profiling/wincounter.md) **:** `WinCounterPath` | Profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir. |
   | [/AutoMark](../profiling/automark.md) **:** `Interval` | Yalnızca **/WINCOUNTER** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 MS 'dir. |
   | [/Events](../profiling/events-vsperfcmd.md) **:** `Config` | Profil oluşturma sırasında toplanacak bir Windows için olay Izleme (ETW) olayı belirtir. ETW olayları ayrı bir (. etl) dosyasında toplanır. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Veri toplama duraklatılmış şekilde profil oluşturucuyu başlatmak için, **/Start** komut satırına **/globaloff** seçeneğini ekleyin. Profil oluşturmayı sürdürmeye yönelik **/GlobalOn** kullanın. |

7. Belgelenmiş bileşeni içeren Web sitesini açın.

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hedef uygulama çalışırken, *VSPerfCmd. exe* seçeneklerini kullanarak verileri dosyaya yazmayı başlatıp durdurarak veri toplamayı kontrol edebilirsiniz. Veri toplamayı denetlemek, program yürütmesinin, uygulamayı başlatma veya kapatma gibi belirli bir bölümü için veri toplamanızı sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki seçenek çiftleri veri toplamayı başlatır ve durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Tüm süreçler için veri toplamayı başlatır ( **/GlobalOn**) veya Durdur ( **/globaloff**).|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:** `PID`|İşlem KIMLIĞI (`PID`) tarafından belirtilen işlem için veri toplamayı başlatır ( **/ProcessOn**) veya Durdur ( **/ProcessOff**).|
    |[/ThreadOn](../profiling/threadon-and-threadoff.md) **:** `TID` [/ThreadOff](../profiling/threadon-and-threadoff.md) **:** `TID`|İş parçacığı KIMLIĞI (`TID`) tarafından belirtilen iş parçacığı için ( **/ThreadOn**) veya Durdur ( **/ThreadOff**) veri toplamayı başlatır.|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu Sonlandır
 Profil oluşturma oturumunu sonlandırmak için, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulamasını kapatın ve sonra [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] çalışan işlemini kapatmak için Internet Information Services (IIS) **IISReset** komutunu kullanın. Profiler 'ı devre dışı bırakmak ve profil oluşturma veri dosyasını kapatmak için **VSPerfCmd** [/Shutdown](../profiling/shutdown.md) seçeneğini çağırın. **VSPerfCLREnv/globaloff** komutu profil oluşturma ortam değişkenlerini temizler. Yeni ortam ayarlarının uygulanması için bilgisayarı yeniden başlatmanız gerekir.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sonlandırmak için

1. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulamasını kapatın.

2. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] çalışan işlemini kapatın. Tür:

    **IISReset/stop**

3. Profil oluşturucuyu kapatın. Tür:

    **VSPerfCmd/shutdown**

4. (İsteğe bağlı). Profil oluşturma ortamı değişkenlerini temizleyin. Tür:

    **VSPerfCmd/globaloff**

5. Bilgisayarı yeniden başlatın. Gerekirse, IIS 'yi yeniden başlatın. Tür:

    **IISReset/Start**

## <a name="see-also"></a>Ayrıca bkz.
- [ASP.NET Web uygulamaları profili](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [.NET bellek verileri görünümleri](../profiling/dotnet-memory-data-views.md)
