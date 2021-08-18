---
title: Uygulama istatistiklerini almak için yerel hizmete profil oluşturucu iliştirme
description: yerel bir hizmetten performans istatistikleri toplamak için komut satırından Visual Studio Profil Oluşturma Araçları kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: f783817f-77a0-4eb8-985b-ec3b77eadc42
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: 4b2de7a03dae8bcd0fcbebd4dcd2aaba7aba6f09
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122131475"
---
# <a name="how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line-vsperfcmd"></a>Nasıl yapılır: komut satırını kullanarak uygulama istatistikleri toplamak için bir yerel hizmete profil oluşturucu Iliştirme (VSPerfCmd)
Bu makalede, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bir yerel hizmete profil oluşturucu eklemek ve örnekleme yöntemini kullanarak performans istatistikleri toplamak için profil oluşturma araçları komut satırı araçlarının nasıl kullanılacağı açıklanır.

> [!NOTE]
> Windows 8 ve Windows Server 2012 gelişmiş güvenlik özellikleri Visual Studio profiler 'ın bu platformlarda verileri topladıkları şekilde gerekli önemli değişikliklere sahiptir. UWP uygulamaları için de yeni koleksiyon teknikleri gerekir. bkz. [Windows 8 ve Windows Server 2012 uygulamalarda performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> Profil oluşturma araçlarının yolunu almak için, bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). 64 bit bilgisayarlarda, araçların her ikisi de 64-bit ve 32 bit sürümleri mevcuttur. Profil oluşturucu komut satırı araçlarını kullanmak için araçlar yolunu komut Istemi penceresinin PATH ortam değişkenine eklemeniz ya da komutun kendisine eklemeniz gerekir.

 Profil Oluşturucu hizmete iliştirirken, veri toplamayı duraklatabilir ve devam ettirebilirsiniz.

 Profil oluşturma oturumunu sonlandırmak için, profil oluşturucunun hizmetten ayrılması ve ve açıkça kapatılması gerekir.

## <a name="start-the-application-with-the-profiler"></a>Uygulamayı Profil Oluşturucu ile başlatma
 Profil oluşturucuyu yerel bir hizmete iliştirmek için, **VSPerfCmd.exe** [/Start](../profiling/start.md) ve [/Attach](../profiling/attach.md) seçeneklerini kullanarak profil oluşturucuyu başlatabilir ve hedef uygulamaya iliştirebilirsiniz. **/Start** ve **/Attach** ve ilgili seçeneklerini tek bir komut satırında belirtebilirsiniz. Ayrıca, hedef uygulamanın başlangıcında veri toplamayı duraklatmak için [/globaloff](../profiling/globalon-and-globaloff.md) seçeneğini de ekleyebilirsiniz. Daha sonra, veri toplamaya başlamak için [/GlobalOn](../profiling/globalon-and-globaloff.md) kullanabilirsiniz.

#### <a name="to-attach-the-profiler-to-a-native-service"></a>Profil oluşturucuyu yerel bir hizmete eklemek için

1. Gerekirse, hizmeti başlatın.

2. Bir komut istemi penceresi açın.

3. Profil oluşturucuyu başlatın. Şunu yazın:

    **VSPerfCmd/start: örnek**  [/output](../profiling/output.md) **:** `OutputFile` [ `Options` ]

   - **/Start: örnek** seçeneği, profil oluşturucuyu başlatır.

   - /Start ile **/output:** `OutputFile` seçeneği gereklidir.  `OutputFile` profil oluşturma verilerinin adını ve konumunu belirtir (.*VSP*) dosyası.

     Aşağıdaki seçeneklerden herhangi birini, **/Start: Sample** seçeneğiyle kullanabilirsiniz.

   > [!NOTE]
   > **/User** ve **/CrossSession** seçenekleri genellikle hizmetler için gereklidir.

   | Seçenek | Açıklama |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Profili oluşturulan işlemin sahibi olan hesabın etki alanını ve Kullanıcı adını belirtir. Bu seçenek yalnızca, işlem oturum açmış kullanıcı dışında bir kullanıcı olarak çalışıyorsa gereklidir. işlem sahibi, Windows görev yöneticisi 'nin işlemler sekmesinde kullanıcı adı sütununda listelenir. |
   | [/CrossSession](../profiling/crosssession.md) | Diğer oturumlardaki işlemlerin profilini oluşturmaya izin vermez. Uygulama farklı bir oturumda çalışıyorsa, bu seçenek gereklidir. oturum kimliği, Windows görev yöneticisi 'nin süreçler sekmesindeki oturum kimliği sütununda listelenir. **/CS** , **/CrossSession** için bir kısaltma olarak belirtilebilir. |
   | [/WINCOUNTER](../profiling/wincounter.md) **:**`WinCounterPath` | profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir. |
   | [/AutoMark](../profiling/automark.md) **:**`Interval` | Yalnızca **/WINCOUNTER** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 MS 'dir. |
   | [/Events](../profiling/events-vsperfcmd.md) **:**`Config` | profil oluşturma sırasında toplanacak Windows (ETW) olayı için bir olay izleme olayı belirtir. ETW olayları ayrı bir (. etl) dosyasında toplanır. |

4. Profil oluşturucuyu hizmete ekleyin. Şunu yazın:

    **VSPerfCmd/Attach:** `PID` [`Sample Event`]

    `PID` hedef uygulamanın işlem KIMLIĞINI belirtir. Windows görev yöneticisi 'nde çalışan tüm işlemlerin işlem kimliklerini görüntüleyebilirsiniz.

    Varsayılan olarak, performans verileri 10.000.000 her durdurulmayan işlemci saati döngüsünde örneklenir. Bu, yaklaşık olarak 1GH işlemcide her 10 saniyede bir. Saat çevrimi aralığını değiştirmek veya farklı bir örnekleme olayı belirtmek için aşağıdaki seçeneklerden birini belirtebilirsiniz.

   |Örnek olay|Açıklama|
   |------------------|-----------------|
   |[/Timer](../profiling/timer.md) **:**`Interval`|Örnekleme aralığını, tarafından belirtilen durdurulmayan saat döngüsü sayısına dönüştürür `Interval` .|
   |[/PF](../profiling/pf.md)[**:** `Interval` ]|Örnekleme olayını sayfa hatalarına dönüştürür. `Interval`Belirtilmişse, örnekler arasındaki sayfa hatalarının sayısını ayarlar. Varsayılan değer 10 ' dur.|
   |[/sys](../profiling/sys-vsperfcmd.md) [**:** `Interval` ]|Örnekleme olayını, işlemden işletim sistemi çekirdeğine (syscalls) sistem çağrıları olarak değiştirir. `Interval`Belirtilmişse, örnekler arasındaki çağrı sayısını ayarlar. Varsayılan değer 10 ' dur.|
   |[/Counter](../profiling/counter.md) **:**`Config`|Örnekleme olayını ve aralığını, ' de belirtilen işlemci performans sayacı ve aralığı olarak değiştirir `Config` .|

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hedef uygulama çalışırken, verileri profil oluşturucu veri dosyasına yazmayı başlatmak ve durdurmak için *VSPerfCmd.exe* seçeneklerini kullanabilirsiniz. Veri toplamayı denetlemek, program yürütmesinin, uygulamayı başlatma veya kapatma gibi belirli bir bölümü için veri toplamanızı sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki **VSPerfCmd** seçenek çiftleri veri toplamayı başlatır ve durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Tüm süreçler için veri toplamayı başlatır (**/GlobalOn**) veya Durdur (**/globaloff**).|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|İşlem KIMLIĞI () tarafından belirtilen işlem için (**/ProcessOn**) veya duraklar (**/ProcessOff**) veri toplamayı başlatır `PID` .|
    |**/Attach:** { `PID`&#124;`ProcName` } [/detach](../profiling/detach.md)[: { `PID`&#124;`ProcName` }]|**/Attach** işlem kimliği veya işlem adı tarafından belirtilen işlem için veri toplamaya başlar. **/Detach** belirtilen işlem için ya da bir işlem belirtilmemişse tüm işlemler için veri toplamayı durduruyor.|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu Sonlandır
 Profil oluşturma oturumunu sonlandırmak için, profil oluşturucunun hizmetten ayrılması ve açıkça kapatılması gerekir. Hizmeti durdurarak veya **VSPerfCmd/detach** seçeneğini çağırarak örnekleme yöntemiyle profili oluşturulan yerel hizmeti ayırabilirsiniz. Ardından, profil oluşturucuyu kapatmak ve profil oluşturma veri dosyasını kapatmak için **VSPerfCmd** [/Shutdown](../profiling/shutdown.md) seçeneğini çağırın.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sonlandırmak için

1. Profil oluşturucuyu hedef uygulamadan ayırmak için aşağıdakilerden birini yapın:

    - Hizmeti durdurun.

         -veya-

    - **VSPerfCmd/detach** yazın

2. Profil oluşturucuyu kapatın. Şunu yazın:

     **VSPerfCmd/shutdown**

## <a name="see-also"></a>Ayrıca bkz.
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
- [Örnekleme yöntemi veri görünümleri](../profiling/profiler-sampling-method-data-views.md)
