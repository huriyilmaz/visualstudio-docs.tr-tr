---
title: Uygulama istatistiklerini almak için ASP.NET web uygulamasına profil oluşturun
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3725ddbe-ce91-4469-991e-8c5ed048c618
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 549e43f403b19d8832e00277f826cdc7b276b747
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779083"
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line"></a>Nasıl yapılı: Komut satırını kullanarak uygulama istatistiklerini toplamak için profiloluşturcuğu ASP.NET bir web uygulamasına takın
Bu makalede, profil [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oluşturucuyu ASP.NET bir Web uygulamasına eklemek ve örnekleme yöntemini kullanarak performans istatistikleri toplamak için Profil Oluşturma Araçları komut satırı araçlarının nasıl kullanılacağı açıklanmaktadır.

> [!NOTE]
> Windows 8 ve Windows Server 2012'deki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturucusu bu platformlarda veri toplama şeklinde önemli değişiklikler gerektiriyordu. UWP uygulamaları da yeni toplama teknikleri gerektirir. [Windows 8 ve Windows Server 2012 uygulamalarında Performans Araçları'na](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)bakın.
>
> Profil oluşturma çalışmasına katman etkileşim verileri eklemek, komut satırı profil oluşturma araçlarıyla belirli yordamlar gerektirir. Bkz. [Katman etkileşim verilerini topla.](../profiling/adding-tier-interaction-data-from-the-command-line.md)
>
> Profil oluşturma araçlarına giden yolu almak [için](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)bkz. 64 bit bilgisayarlarda, araçların hem 64 bit hem de 32 bit sürümleri kullanılabilir. Profil oluşturucu komut satırı araçlarını kullanmak için, komut istemi penceresinin PATH ortamı değişkenine araçlar yolunu eklemeniz veya komutun kendisine eklemeniz gerekir.

 ASP.NET bir Web uygulamasından performans verileri toplamak için, uygun ortam değişkenlerinin başlatılması ve ASP.NET Web uygulamasını barındıran bilgisayarın profil oluşturma için Web sunucusunu yapılandırmak üzere yeniden başlatılması gerekir.

 Daha sonra profil oluşturucuyu Web sitenizi barındıran ASP.NET çalışanı işlemine bağlarsınız. Profil oluşturucu uygulamaya iliştirildiğinde, veri toplamayı duraklatabilir ve devam ettirebilirsiniz.

 Profil oluşturma oturumunu sona erdirmek için profil oluşturucunun profil uygulamasından ayrılması ve profil oluşturucunun açıkça kapatılması gerekir. Çoğu durumda, oturumun sonunda profil oluşturma ortamı değişkenlerini temizlemenizi öneririz.

## <a name="start-the-profiler-and-attach-to-an-aspnet-web-application"></a>Profil oluşturucuyu başlatın ve ASP.NET bir web uygulamasına iliştirin

#### <a name="to-attach-the-profiler-to-an-aspnet-web-application"></a>Profil oluşturucuyu bir ASP.NET Web uygulamasına eklemek için

1. Bir komut istemi penceresi açın.

2. Profil oluşturma ortamı değişkenlerini başlangıç olarak önleştirin. Şunu yazın:

    **VSPerfClrEnv /globalsampleon** [**/samplelineoff**]

   - **/globalsampleon** örneklemeyi sağlar.

   - **/samplelineoff,** toplanan verilerin belirli kaynak kod satırlarına atamasını devre dışı kılabilir. Bu seçenek belirtildiğinde, veriler yalnızca işlevlere atanır.

3. Bilgisayarı yeniden başlatın.

4. Profilciyi çalıştırın. Tür:**VSPerfCmd** [/start](../profiling/start.md)**:örnek** `Options` [/çıktı](../profiling/output.md)**:**`OutputFile`[ ]

   - **/start:örnek** seçeneği profil oluşturucuyu başlatir.

   - **/output:** `OutputFile` seçeneği **/start**ile gereklidir. `OutputFile`profil oluşturma verileri (.vsp) dosyasının adını ve konumunu belirtir.

     **/start:sample** seçeneği ile aşağıdaki seçeneklerden herhangi birini kullanabilirsiniz.

   > [!NOTE]
   > **/kullanıcı** ve **/crosssession** seçenekleri genellikle ASP.NET uygulamalar için gereklidir.

   | Seçenek | Açıklama |
   | - | - |
   | [/kullanıcı](../profiling/user-vsperfcmd.md) **:**[ ]`Domain`**\\**`UserName` | ASP.NET alt işleminin sahibi hesabın etki alanını ve kullanıcı adını belirtir. İşlem, oturum açmış kullanıcı dışında bir kullanıcı olarak çalışıyorsa, bu seçenek gereklidir. İşlem sahibi, Windows Görev Yöneticisi'nin **İşlemler** sekmesinde **Kullanıcı Adı** sütununda listelenir. |
   | [/çapraz oturum](../profiling/crosssession.md) | Diğer oturum oturumlarında işlemlerin profilini çıkarmasağlar. ASP.NET uygulaması farklı bir oturumda çalışıyorsa bu seçenek gereklidir. Oturum tanımlayıcısı, Windows Görev Yöneticisi'nin İşlemler sekmesindeki Oturum Kimliği sütununda listelenir. **/CS** **/ crosssession**için bir kısaltma olarak belirtilebilir. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Yalnızca **/wincounter** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 ms'dir. |
   | [/olaylar](../profiling/events-vsperfcmd.md) **:**`Config` | Profil oluşturma sırasında toplanacak windows için olay izleme (ETW) olayı belirtir. ETW olayları ayrı bir (.etl) dosyada toplanır. |

5. web uygulamasını ASP.NET normal şekilde başlatın.

6. Profil oluşturucuyu ASP.NET çalışma işlemine takın. Tür:**VSPerfCmd** [/ ekle](../profiling/attach.md)**:**`PID` {&#124;`ProcName`} [`Sample Event`] [ /[targetclr](../profiling/targetclr.md)**:**`Version`]

   - `PID`ASP.NET işçi sürecinin işlem kimliğini belirtir; `ProcName` işçi işleminin adını belirtir. Windows Görev Yöneticisi'nde tüm çalışan işlemlerin işlem adlarını ve adlarını görüntüleyebilirsiniz.

   - Varsayılan olarak, performans verileri her 10.000.000 durdurulmayan işlemci saat döngüsünde örneklenir. Bu, 1GH işlemcide saniyede yaklaşık 100 kez dir. Saat döngüsü aralığını değiştirmek veya farklı bir örnekleme olayı belirtmek için aşağıdaki **VSPerfCmd** seçeneklerinden birini belirtebilirsiniz.

   |Örnek olay|Açıklama|
   |------------------|-----------------|
   |[/zamanlayıcı](../profiling/timer.md) **:**`Interval`|Örnekleme aralığını, `Interval`'tarafından belirtilen durdurulmayan saat devir lerinin sayısıyla değiştirir.|
   |[/pf](../profiling/pf.md)[**:**`Interval`]|Örnekleme olayını sayfa hatalarıyla değiştirir. `Interval` Belirtilirse, örnekler arasındaki sayfa hatalarının sayısını ayarlar. Varsayılan değer 10'dur.|
   |[/sys](../profiling/sys-vsperfcmd.md)`:``Interval`[ ]|Örnekleme olayını, işlemden işletim sistemi çekirdeğine (syscalls) sistem çağrılarına değiştirir. `Interval` Belirtilirse, örnekler arasındaki çağrı sayısını ayarlar. Varsayılan değer 10'dur.|
   |[/sayaç](../profiling/counter.md) **:**`Config`|Örnekleme olayını ve aralığını işlemci performans sayacına `Config`ve 'de belirtilen aralıkta değiştirir.|
   |[/targetclr](../profiling/targetclr.md) **:**`Version`|Bir uygulamada çalışma zamanının birden fazla sürümü yüklendiğinde, ortak dil çalışma zamanının (CLR) profilinin sürümünü belirtir.|

   - **targetclr:** `Version` bir uygulamada çalışma süresinin birden fazla sürümü yüklendiğinde CLR'nin profilini yükselten sürümünü belirtir. İsteğe bağlı.

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Uygulama çalışırken, *VSPerfCmd.exe* seçeneklerini kullanarak dosyaya veri yazısını başlatıp durdurarak veri toplamayı denetleyebilirsiniz. Veri toplamayı denetlemek, uygulamayı başlatma veya kapatma gibi program yürütmesinin belirli bir bölümü için veri toplamanızı sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki **VSPerfCmd** seçenekleri, veri toplamayı başlayıp durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Tüm işlemler için **(/globalon)** başlatır veya durur (**/globaloff**) veri toplama.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` **/processoff:**`PID`|Tarafından belirtilen `PID`işlem için (**/processon)** başlatır veya durur (**/processoff**) veri toplama.|
    |[/ekle](../profiling/attach.md) **:**:`PID` `ProcName`{&#124;} [/ayırma](../profiling/detach.md) `ProcName`[**:**{`PID`&#124;}]|**/ekle** `PID` veya işlem adı (ProcName) tarafından belirtilen işlem için veri toplamaya başlar. **/detach,** belirli bir işlem belirtilmemişse, belirtilen işlem veya tüm işlemler için veri toplamayı durdurur.|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sonlandırma
 Profil oluşturma oturumunu sona [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] erdirmek için Web uygulamasını kapatın ve ardından alt işlemi kapatmak için [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Internet Information Services **(IIS) IISReset** komutunu kullanın. Profil oluşturucuyu kapatmak ve profil oluşturma veri dosyasını kapatmak için **VSPerfCmd** [/shutdown](../profiling/shutdown.md) seçeneğini arayın.

 **VSPerfClrEnv /globaloff** komutu profil oluşturma ortamı değişkenlerini temizler. Uygulanacak yeni ortam ayarları için bilgisayarı yeniden başlatmanız gerekir.

 **VSPerfClrEnv /globaloff** komutu profil oluşturma ortamı değişkenlerini temizler, ancak bilgisayar yeniden başlatılıncaya kadar sistem yapılandırması sıfırlanmaz.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdirmek için

1. Profiloluşturciyi hedef uygulamadan ayırmak için aşağıdakilerden birini yapın:

   - **VsPerfCmd /detach** yazın

      -veya-

   - İşçi [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] işlemini kapatın.

2. Profilciyi kapat. Türü:**VSPerfCmd** [/shutdown](../profiling/shutdown.md)

3. (İsteğe bağlı) Profil oluşturma ortamı değişkenlerini temizleyin. Şunu yazın:

    **VSPerfCmd /globaloff**

4. Bilgisayarı yeniden başlatın.

## <a name="see-also"></a>Ayrıca bkz.
- [Web uygulamaları ASP.NET profil](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Örnekleme yöntemi veri görünümleri](../profiling/profiler-sampling-method-data-views.md)
