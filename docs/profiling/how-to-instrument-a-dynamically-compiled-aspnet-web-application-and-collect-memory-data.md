---
title: Profil oluşturma komut satırı - Dinamik ASP.NET, bellek verilerini al
description: Dinamik olarak derlenmiş bir Visual Studio Profil Oluşturma Araçları için ayrıntılı bellek etkinliği verileri toplamak üzere komut satırı araçlarının nasıl ASP.NET öğrenin.
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
ms.openlocfilehash: 879b77bdc782c17f3969797890c1e0ce24d0d470
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122033544"
---
# <a name="how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line"></a>Nasıl kullanılır: Profil oluşturma komut ASP.NET kullanarak dinamik olarak derlenmiş bir web uygulamasını ve bellek verilerini toplama
Bu konu başlığı altında, Profil Oluşturma Araçları profil oluşturma yöntemini kullanarak dinamik olarak derlenmiş bir web uygulaması için ayrıntılı .NET bellek ayırma ve nesne yaşam süresi verilerini toplamak üzere Profil Oluşturma Araçları komut satırı araçlarının [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] nasıl kullanımı açıklanmıştır.

> [!NOTE]
> Profil oluşturma araçlarının yolunu almak için [bkz. Komut satırı araçlarının yolunu belirtme.](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md) 64 bit bilgisayarlarda, araçların hem 64 bit hem de 32 bit sürümleri kullanılabilir. Profil oluşturma komut satırı araçlarını kullanmak için, araç yolunu Komut İstemi penceresinin PATH ortam değişkenine eklemeniz veya komutun kendisine eklemeniz gerekir.

 Bir web uygulamasından performans verileri toplamak için,web.configaracının dinamik olarak derlenmiş uygulama dosyalarını takipVSInstr.exeiçin hedef uygulamanınVSInstr.exe[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] dosyasını değiştirirsiniz.  [](../profiling/vsinstr.md) Ardından [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) aracını kullanarak Web uygulamasını barındıran sunucuyu yapılandıracak ve uygun ortam değişkenlerini ayarlayacak .NET bellek profili oluşturmayı etkinleştirdikten sonra [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] bilgisayarı yeniden başlatabilirsiniz.

 Veri toplamak için profilleyiciyi çalıştırın ve ardından hedef uygulamayı çalıştırın. Profiler uygulamaya bağlıyken veri toplamayı duraklatabilir ve sürdürebilirsiniz. Uygun verileri topsanız, uygulamayı kapatın, Internet Information Services (IIS) çalışan işlemini kapatın ve ardından profilleyiciyi kapatın.

 Profil oluşturma çalışmanızı tamamlandıktan sonra,web.config *ve* web sunucusunu özgün durumuna geri yükleyebilirsiniz.

## <a name="configure-the-aspnet-web-application-and-the-web-server"></a>Web ASP.NET web sunucusunu yapılandırma

#### <a name="to-configure-the-aspnet-web-application-and-the-web-server"></a>Web uygulamasını ASP.NET web sunucusunu yapılandırmak için

1. Hedef *web.config* dosyanın adını değiştirme. Bkz. Nasıl web.config web uygulamaları için dinamik olarak derlenmiş dosyaları [ASP.NET dosyaları değiştirme.](../profiling/how-to-modify-web-config-files-to-instrument-dynamically-compiled-aspnet-apps.md)

2. Web uygulamasını barındıran bilgisayarda bir komut istemi penceresi açın.

3. Profil oluşturma ortam değişkenlerini başlatma. Şunu yazın:

     **VSPerfClrEnv /globaltracegc**

     -veya-

     **VSPerfClrEnv /globaltracegclife**

    - **/globaltracegc,** bellek ayırma verilerini toplamayı sağlar.

    - **/globaltracegclife,** bellek ayırma verileri ve nesne yaşam süresi verilerini toplamaya olanak sağlar.

4. Bilgisayarı yeniden başlatın.

## <a name="run-the-profiling-session"></a>Profil oluşturma oturumunu çalıştırma

#### <a name="to-profile-the-aspnet-web-application"></a>Web uygulamasının ASP.NET için

1. Profilleyiciyi başlatma. Şunu yazın:

    **VSPerfCmd** [/start](../profiling/start.md) **:trace** [/output](../profiling/output.md) **:** [ `OutputFile` `Options` ]

   - **/start:trace** seçeneği profilleyiciyi başlatıyor.

   - **/output:** `OutputFile` seçeneği / **start ile gereklidir.** `OutputFile` profil oluşturma verisi adını ve konumunu () belirtir.*vsp*) dosyasını seçin.

     **/start:trace** seçeneğiyle aşağıdaki seçeneklerden herhangi birini kullanabilirsiniz.

   > [!NOTE]
   > /user **ve** **/crosssession** seçenekleri genellikle uygulama ASP.NET gereklidir.

   | Seçenek | Açıklama |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Çalışan işleminin sahibi olan hesabın isteğe bağlı etki alanını ve kullanıcı [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] adını belirtir. İşlem oturum açmış kullanıcıdan farklı bir kullanıcı olarak çalışıyorsa bu seçenek gereklidir. Ad, Görev **Yöneticisi'nin** İşlemler **sekmesindeki** Kullanıcı Adı Windows listelenir. |
   | [/crosssession](../profiling/crosssession.md) | Diğer oturumlarda işlemlerin profilini oluşturmayı sağlar. Uygulama farklı bir oturumda çalışıyorsa bu seçenek gereklidir. Oturum kimliği, Görev **Yöneticisi'nin** İşlemler **sekmesindeki** Oturum Windows listelenir. **/CS,** **/crosssession için bir kısaltma olarak belirtilebilir.** |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Veri toplama duraklatılmış şekilde profilleyiciyi başlatır. Profil [oluşturmayı devam ettiren /globalon](../profiling/globalon-and-globaloff.md) kullanın. |
   | [/counter](../profiling/counter.md) **:**`Config` | içinde belirtilen işlemci performans sayacından bilgi `Config` toplar. Sayaç bilgileri her profil oluşturma olayında toplanan verilere eklenir. |
   | [/wincounter:](../profiling/wincounter.md) `WinCounterPath` | Profil oluşturma Windows toplanacak bir performans sayacı belirtir. |
   | [/automark:](../profiling/automark.md) `Interval` | Yalnızca **/wincounter ile** kullanın. Performans sayacı toplama olayları arasındaki milisaniye Windows sayısını belirtir. Varsayılan değer 500 ms'tir. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Profil oluşturma sırasında toplanacak Windows (ETW) olayı için bir Olay İzleme belirtir. ETW olayları ayrı bir () içinde toplanır.*etl*) dosyasını seçin. |

2. Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] uygulamasını normal şekilde başlatabilirsiniz.

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hedef uygulama çalışırken, profil oluşturma seçeneklerini kullanarak profil oluşturma veri dosyasına veri yazmayı başlatarak ve durdurarak veri *toplamayıVSPerfCmd.exe* yapabilirsiniz. Veri toplamayı denetlemek, uygulamayı başlatma veya kapatma gibi program yürütmenin belirli bir bölümü için veri toplamaya olanak sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki seçenek çiftleri veri toplamayı başlat ve durdur. Her seçeneği ayrı bir komut satırı üzerinde belirtin. Veri toplamayı birden çok kez açabilirsiniz ve kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Tüm işlemler **için veri toplamayı** başlatır ( /globalon ) veya durdurur (**/globaloff).**|
    |[/processon:](../profiling/processon-and-processoff.md)  `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|İşlem kimliği ( ) tarafından belirtilen işlem için veri toplamayı (**/processon**) veya durdurur ( `PID` ).|
    |[/threadon:](../profiling/threadon-and-threadoff.md)  `TID` [/threadoff:](../profiling/threadon-and-threadoff.md) `TID`|İş parçacığı kimliği ( ) tarafından belirtilen iş parçacığı için veri toplamayı (**/threadon**) veya durdurur ( `TID` ).|

- Veri dosyasına profil **VSPerfCmd.exe** [/mark](../profiling/mark.md) seçeneğini de kullanabilirsiniz. **/mark komutu** bir tanımlayıcı, bir zaman damgası ve isteğe bağlı bir kullanıcı tanımlı metin dizesi ekler. İşaretler, profil oluşturma raporlarında ve veri görünümlerde verileri filtrelemek için kullanılabilir.

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sona er
 Profil oluşturma oturumunu durdurmak için hedef web uygulamasını kapatın, profili Internet Information Services işlemini durdurmak için (IIS) uygulamayı durdurun ve ardından [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] profilleyiciyi kapatın. Ardından IIS'yi yeniden başlatın.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdir

1. Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] uygulamasını kapatın.

2. Çalışan işlemini [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] kapatmak için Internet Information Services (IIS). Şunu yazın:

    **IISReset /stop**

3. Profilleyiciyi kapatın. Şunu yazın:

    **VSPerfCmd** [/shutdown](../profiling/shutdown.md)

4. IIS’yi yeniden başlatın. Şunu yazın:

    **IISReset /start**

## <a name="restore-the-application-and-computer-configuration"></a>Uygulama ve bilgisayar yapılandırmasını geri yükleme
 Tüm profil oluşturmayı tamamlandıktan sonra, *web.config* dosyasını değiştirin, profil oluşturma ortam değişkenlerini temizin ve bilgisayarı yeniden başlatarak sunucuyu ve uygulamayı özgün [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] durumlarına geri yükleyin.

#### <a name="to-restore-the-application-and-computer-configuration"></a>Uygulama ve bilgisayar yapılandırmasını geri yüklemek için

1. web.config *dosyasını* özgün dosyanın bir kopyasıyla değiştirin.

2. (İsteğe bağlı). Profil oluşturma ortam değişkenlerini temizleme. Şunu yazın:

     **VSPerfCmd /globaloff**

3. Bilgisayarı yeniden başlatın.

## <a name="see-also"></a>Ayrıca bkz.
- [Web ASP.NET profil oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [.NET bellek veri görünümleri](../profiling/dotnet-memory-data-views.md)
