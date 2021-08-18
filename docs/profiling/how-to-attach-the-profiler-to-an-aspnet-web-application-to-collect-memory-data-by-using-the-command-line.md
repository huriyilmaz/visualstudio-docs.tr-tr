---
title: Bellek verilerini toplamak ASP.NET profil oluşturma
description: Profil Visual Studio Profil Oluşturma Araçları web uygulamasına eklemek ve ASP.NET ayırmalarının sayısı ve boyutu hakkında veri almak için .NET Framework kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d608f85a-41ae-4ca7-85e6-b96624dbc83c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 7a28943bbca2ace833b1381a7316ca672715eabc25587fe3ed0bbcc198399e4b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121355236"
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line"></a>Nasıl kullanılır: Komut satırı kullanarak ASP.NET verileri toplamak için profil oluşturma web uygulamasına profil oluşturma
Bu makalede, profil Profil Oluşturma Araçları web uygulamasına eklemek ve veri kaynağı bellek ayırmalarının sayısı ve boyutu hakkında veri toplamak için .NET Framework [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] açıklanmıştır. Ayrıca, bellek nesnelerinin kullanım ömrü hakkında .NET Framework toplayabilirsiniz.

> [!NOTE]
> Profil oluşturma araçlarının yolunu almak için [bkz. Komut satırı araçlarının yolunu belirtme.](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md) 64 bit bilgisayarlarda, araçların hem 64 bit hem de 32 bit sürümleri kullanılabilir. Profil oluşturma komut satırı araçlarını kullanmak için, araç yolunu Komut İstemi penceresinin PATH ortam değişkenine eklemeniz veya komutun kendisine eklemeniz gerekir.

 Bir Web uygulamasından performans verileri toplamak için [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) aracını kullanarak Web uygulamasını barındıran bilgisayarda uygun ortam değişkenlerini [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] başlatmanız gerekir. Ardından, Web sunucusunu profil oluşturma için yapılandırmak üzere bilgisayarı yeniden başlatmanız gerekir.

 Daha sonra, [VSPerfCmd.exe](../profiling/vsperfcmd.md) web sitesini barındıran çalışan sürecine eklemek [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] içinVSPerfCmd.exearacını kullanın. Profiler uygulamaya ekli olduğunda veri toplamayı duraklatabilir ve sürdürebilirsiniz.

 Profil oluşturma oturumunu sona ertmak için, profil oluşturmanın artık uygulamaya bağlı olması ve profilleyicinin açıkça kapatılamaması gerekir. Çoğu durumda, bir oturumun sonunda profil oluşturma ortam değişkenlerini temizlemenizi öneririz.

## <a name="attach-the-profiler"></a>Profilleyiciyi ekleme

#### <a name="to-attach-the-profiler-to-an-aspnet-web-application"></a>Profilleyiciyi bir web uygulamasına ASP.NET için

1. Bir komut istemi penceresi açın.

2. Profil oluşturma ortam değişkenlerini başlatma. Şunu yazın:

    **VSPerfClrEnv** {**/globalsamplegc** &#124; **/globalsamplegclife**} [**/samplelineoff**]

   - **/globalsamplegc ve** **/globalsamplegclife** seçenekleri top için bellek verisi türünü belirtir.

        Aşağıdaki seçeneklerden bir ve yalnızca bir tanesini belirtin.

       |Seçenek|Açıklama|
       |------------|-----------------|
       |**/globalsamplegc**|Bellek ayırma verilerinin toplanmasını etkinleştirir.|
       |**/globalsamplegclife**|Bellek ayırma verilerinin ve nesne yaşam süresi verilerinin toplanmasını etkinleştirir.|

   - **/samplelineoff seçeneği,** toplanan verilerin belirli kaynak kod satırlarına atamasını devre dışı bırakıyor. Bu seçenek belirtilirse veriler işlev düzeyinde atanır.

3. Yeni ortam yapılandırmasını ayarlamak için bilgisayarı yeniden başlatın.

4. Bir komut istemi penceresi açın. Gerekirse profil oluşturma yolu ortam değişkenlerini ayarlayın.

5. Profilleyiciyi başlatma. Şunu yazın:

    **VSPerfCmd**  [/start](../profiling/start.md) **:sample**  [/output](../profiling/output.md) **:** [ `OutputFile` `Options` ]

   - **/start:sample** seçeneği profilleyiciyi başlatıyor.

   - **/output:** `OutputFile` seçeneği / **start ile gereklidir.** `OutputFile` profil oluşturma verileri (.vsp) dosyasının adını ve konumunu belirtir.

     **/start:sample** seçeneğiyle aşağıdaki seçeneklerden herhangi birini kullanabilirsiniz.

   > [!NOTE]
   > /user **ve** **/crosssession** seçenekleri genellikle uygulama ASP.NET gereklidir.

   | Seçenek | Açıklama |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Çalışan işleminin sahibi olan hesabın etki alanını ve kullanıcı ASP.NET belirtir. İşlem oturum açmış kullanıcıdan farklı bir kullanıcı olarak çalışıyorsa bu seçenek gereklidir. İşlem sahibi, Görev Yöneticisi'nin İşlemler sekmesindeki Kullanıcı Adı Windows listelenir. |
   | [/crosssession](../profiling/crosssession.md) | Diğer oturum açma oturumlarında işlemlerin profil oluşturmasını sağlar. Uygulama farklı bir oturumda ASP.NET bu seçenek gereklidir. Oturum idenitifier, Görev Yöneticisi'nin İşlemler sekmesinde oturum Windows listelenir. **/CS,** **/crosssession için bir kısaltma olarak belirtilebilir.** |
   | [/waitstart](../profiling/waitstart.md) [**:** `Interval` ] | Profil oluşturmanın hata döndürmeden önce başlatılmasını bekleyeceği saniye sayısını belirtir. `Interval`Belirtilmezse, profil oluşturma süresiz olarak bekler. Varsayılan **olarak, /start hemen** döndürür. |
   | [/wincounter:](../profiling/wincounter.md) `WinCounterPath` | Profil oluşturma Windows bir performans sayacı belirtir. |
   | [/automark:](../profiling/automark.md) `Interval` | Yalnızca **/wincounter ile** kullanın. Performans sayacı toplama olayları arasındaki milisaniye Windows sayısını belirtir. Varsayılan değer 500 ms'tir. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Profil oluşturma sırasında toplanacak Windows (ETW) olayı için bir Olay İzleme belirtir. ETW olayları ayrı bir (.etl) dosyasında toplanır. |

6. Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] uygulamasını normal şekilde başlatabilirsiniz.

7. Profilleyiciyi çalışan sürecine [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ekleme. Şunu yazın:

    **VSPerfCmd**[/attach:](../profiling/attach.md) {&#124;} `PID` [ `ProcName` [/targetclr](../profiling/targetclr.md)**:** `Version` ]  

   - İşlem `(PID)` kimliği, çalışan işleminin işlem kimliğini veya işlem [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] adını belirtir. Görev Yöneticisi'nde çalışan tüm işlemlerin işlem kimliklerini Windows görüntüebilirsiniz.

   - **/targetclr:** `Version` bir uygulamada birden fazla çalışma zamanı sürümü yüklendiğinde profili oluşturmak için ortak dil çalışma zamanının (CLR) sürümünü belirtir.

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Uygulama çalışırken, profil oluşturma seçeneklerini kullanarak profil oluşturma veri dosyasına veri yazmayı başlatarak ve durdurarak veri **toplamayıVSPerfCmd.exe** yapabilirsiniz. Veri toplamayı denetlemek, uygulamayı başlatma veya kapatma gibi program yürütmenin belirli bir bölümü için veri toplamaya olanak sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki **VSPerfCmd seçenekleri çiftleri** veri toplamayı başlatacak ve durduracak. Her seçeneği ayrı bir komut satırı üzerinde belirtin. Veri toplamayı birden çok kez açabilirsiniz ve kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Tüm işlemler **için veri toplamayı** başlatır ( /globalon ) veya durdurur (**/globaloff).**|
    |[/processon:](../profiling/processon-and-processoff.md)  `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|tarafından belirtilen işlem için (**/processon**) veya durdurur (**/processoff**) veri toplamayı `PID` durdurur.|
    |**/attach:**{ `PID`&#124;`ProcName` } [/detach](../profiling/detach.md)[**:**{ `PID`&#124;: `ProcName` }]|**/attach,** işlem kimliği veya işlem adı tarafından belirtilen işlem için veri toplamaya başlar. **/detach,** belirtilen işlem için veya belirli bir işlem belirtilmezse tüm işlemler için veri toplamayı durdurur.|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sona er
 Profil oluşturma oturumunu sona erdirmak için, profil oluşturmanın Web uygulamasından ayrılmış olması gerekir. Çalışan işlemini yeniden başlatarak veya [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] **VSPerfCmd /detach** seçeneğini çağırarak örnekleme yöntemiyle profili yapılan bir uygulamadan veri toplamayı durdurabilirsiniz. Ardından **VSPerfCmd** [/shutdown](../profiling/shutdown.md) seçeneğini çağırarak profil oluşturma veri dosyasını kapatın. **VSPerfClrEnv /globaloff** komutu profil oluşturma ortam değişkenlerini temizler, ancak bilgisayar yeniden başlatana kadar sistem yapılandırması sıfırlanmaz.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdir

1. Profilleyiciyi hedef uygulamadan ayırmak için aşağıdaki adımlardan birini gerçekleştirin:

   - **VSPerfCmd** [/detach yazın](../profiling/detach.md)

      -veya-

   - Çalışan [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] işlemini kapatın. Şunu yazın:

     **IISReset /stop**

2. Profilleyiciyi kapatın. Şunu yazın:

    **VSPerfCmd /shutdown**

3. (İsteğe bağlı) Profil oluşturma ortam değişkenlerini temizleme. Şunu yazın:

    **VSPerfCmd /globaloff**

4. Bilgisayarı yeniden başlatın. Gerekirse, (IIS) Internet Information Services yeniden başlatın. Şunu yazın:

    **IISReset /start**

## <a name="see-also"></a>Ayrıca bkz.
- [Web ASP.NET profil oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [.NET bellek veri görünümleri](../profiling/dotnet-memory-data-views.md)
