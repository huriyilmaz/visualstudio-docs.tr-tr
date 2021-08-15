---
title: Uygulama istatistiklerini almak için yerel hizmete profil oluşturma ekleme
description: Yerel Visual Studio Profil Oluşturma Araçları performans istatistikleri toplamak için komutunu komut satırına kadar kullanın.
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
ms.openlocfilehash: c773aa6870e92ffbc0f7ef8712c2ed65e6f37e6eeb89906a1c29dd55644becb1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121355249"
---
# <a name="how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line-vsperfcmd"></a>Nasıl yapılanlar: Komut satırı (VSPerfCmd) kullanarak uygulama istatistikleri toplamak için yerel bir hizmete profil oluşturma ekleme
Bu makalede, profil oluşturma Profil Oluşturma Araçları bir yerel hizmete eklemek ve örnekleme yöntemini kullanarak performans istatistikleri toplamak için Profil Oluşturma Araçları komut satırı araçlarının [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nasıl kullanımı açıklanmıştır.

> [!NOTE]
> Windows 8 ve Windows Server 2012'daki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturmanın bu platformlarda veri toplaması sırasında önemli değişiklikler gerektirmektedir. UWP uygulamaları için yeni koleksiyon teknikleri de gerekir. Uygulama [ve uygulama Windows 8 performans Windows Server 2012 bakın.](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)
>
> Profil oluşturma araçlarının yolunu almak için [bkz. Komut satırı araçlarının yolunu belirtme.](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md) 64 bit bilgisayarlarda, araçların hem 64 bit hem de 32 bit sürümleri kullanılabilir. Profil oluşturma komut satırı araçlarını kullanmak için, araç yolunu Komut İstemi penceresinin PATH ortam değişkenine eklemeniz veya komutun kendisine eklemeniz gerekir.

 Profil oluşturma hizmetine bağlıyken veri toplamayı duraklatabilir ve sürdürebilirsiniz.

 Profil oluşturma oturumunu sonlandırmak için, profil oluşturucunun hizmetten ayrılması ve ve açıkça kapatılması gerekir.

## <a name="start-the-application-with-the-profiler"></a>Uygulamayı profil oluşturma ile başlatma
 Profilleyiciyi yerel bir hizmete eklemek için **** [VSPerfCmd.exe/start](../profiling/start.md) ve [/attach](../profiling/attach.md) seçeneklerini kullanarak profilleyiciyi başlatarak hedef uygulamaya iliştirebilirsiniz. **/start ve /attach** seçeneklerini **tek** bir komut satırı üzerinde belirtebilirsiniz. Hedef uygulamanın başında veri toplamayı duraklatmak için [/globaloff](../profiling/globalon-and-globaloff.md) seçeneğini de ekebilirsiniz. Daha sonra veri [toplamaya başlamak için /globalon](../profiling/globalon-and-globaloff.md) kullanabilirsiniz.

#### <a name="to-attach-the-profiler-to-a-native-service"></a>Profilleyiciyi yerel bir hizmete eklemek için

1. Gerekirse hizmeti başlatabilirsiniz.

2. Bir komut istemi penceresi açın.

3. Profilleyiciyi başlatma. Şunu yazın:

    **VSPerfCmd /start:sample**  [/output](../profiling/output.md) **:** [ `OutputFile` `Options` ]

   - **/start:sample** seçeneği profilleyiciyi başlatıyor.

   - **/output:** `OutputFile` seçeneği / **start ile gereklidir.** `OutputFile` profil oluşturma verisi adını ve konumunu () belirtir.*vsp*) dosyasını seçin.

     **/start:sample** seçeneğiyle aşağıdaki seçeneklerden herhangi birini kullanabilirsiniz.

   > [!NOTE]
   > **/user ve** **/crosssession** seçenekleri genellikle hizmetler için gereklidir.

   | Seçenek | Açıklama |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Profili yapılan işleme sahip olan hesabın etki alanını ve kullanıcı adını belirtir. Bu seçenek yalnızca işlem oturum açmış kullanıcıdan farklı bir kullanıcı olarak çalışıyorsa gereklidir. İşlem sahibi, Görev Yöneticisi'nin İşlemler sekmesindeki Kullanıcı Adı Windows listelenir. |
   | [/crosssession](../profiling/crosssession.md) | Diğer oturumlarda işlemlerin profilini oluşturmayı sağlar. Uygulama farklı bir oturumda çalışıyorsa bu seçenek gereklidir. Oturum kimliği, Görev Yöneticisi'nin İşlemler sekmesindeki Oturum Windows listelenir. **/CS,** **/crosssession için bir kısaltma olarak belirtilebilir.** |
   | [/wincounter:](../profiling/wincounter.md) `WinCounterPath` | Profil oluşturma Windows bir performans sayacı belirtir. |
   | [/automark:](../profiling/automark.md) `Interval` | Yalnızca **/wincounter ile** kullanın. Performans sayacı toplama olayları arasındaki milisaniye Windows sayısını belirtir. Varsayılan değer 500 ms'tir. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Profil oluşturma sırasında toplanacak Windows (ETW) olayı için bir Olay İzleme belirtir. ETW olayları ayrı bir (.etl) dosyasında toplanır. |

4. Profiler'i hizmete ekleme. Şunu yazın:

    **VSPerfCmd /attach:** `PID` [`Sample Event`]

    `PID` hedef uygulamanın işlem kimliğini belirtir. Görev Yöneticisi'nde çalışan tüm işlemlerin işlem kimliklerini Windows görüntüebilirsiniz.

    Varsayılan olarak, her 10.000.000 durdurulan işlemci saat döngüsü için performans verileri örnek alır. Bu, 1GH işlemcide 10 saniyede bir yaklaşık bir kez olur. Saat döngüsü aralığını değiştirmek veya farklı bir örnekleme olayı belirtmek için aşağıdaki seçeneklerden birini belirtebilirsiniz.

   |Örnek Olay|Açıklama|
   |------------------|-----------------|
   |[/timer](../profiling/timer.md) **:**`Interval`|Örnekleme aralığını tarafından belirtilen durdurulmamış saat döngülerinin sayısına `Interval` değiştirir.|
   |[/pf](../profiling/pf.md)[**:** `Interval` ]|Örnekleme olayında sayfa hatalarını değiştirir. `Interval`belirtilirse, örnekler arasındaki sayfa hatalarının sayısını ayarlar. Varsayılan değer 10'dır.|
   |[/sys](../profiling/sys-vsperfcmd.md) [**:** `Interval` ]|Örnekleme olayı, işlemden işletim sistemi çekirdeğine (syscalls) yapılan sistem çağrılarını değiştirir. `Interval`belirtilirse, örnekler arasındaki çağrı sayısını ayarlar. Varsayılan değer 10'dır.|
   |[/counter](../profiling/counter.md) **:**`Config`|Örnekleme olayı ve aralığını, içinde belirtilen işlemci performans sayacı ve aralığı olarak `Config` değiştirir.|

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hedef uygulama çalışırken, profil oluşturma *VSPerfCmd.exe* profil oluşturma veri dosyasına veri yazmayı başlatmak ve durdurmak için bu seçenekleri kullanabilirsiniz. Veri toplamayı denetlemek, uygulamayı başlatma veya kapatma gibi program yürütmenin belirli bir bölümü için veri toplamaya olanak sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki **VSPerfCmd seçenekleri çiftleri** veri toplamayı başlatacak ve durduracak. Her seçeneği ayrı bir komut satırı üzerinde belirtin. Veri toplamayı birden çok kez açabilirsiniz ve kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Tüm işlemler **için veri toplamayı** başlatır ( /globalon ) veya durdurur (**/globaloff).**|
    |[/processon:](../profiling/processon-and-processoff.md)  `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|İşlem kimliği ( ) tarafından belirtilen işlem için veri toplamayı (**/processon**) veya durdurur ( `PID` ).|
    |**/attach:** { `PID`&#124;`ProcName` } [/detach](../profiling/detach.md)[:{ `PID`&#124;`ProcName` }]|**/attach,** işlem kimliği veya işlem adı tarafından belirtilen işlem için veri toplamaya başlar. **/detach,** belirtilen işlem için veya bir işlem belirtilmezse tüm işlemler için veri toplamayı durdurur.|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sona er
 Profil oluşturma oturumunu sona erdirmak için profil oluşturmanın hizmetten ayrılması ve ardından açıkça kapanması gerekir. Hizmeti durdurarak veya **VSPerfCmd /detach** seçeneğini çağırarak örnekleme yöntemiyle profili oluşturmakta olan yerel hizmeti ayırabilirsiniz. Ardından, profil oluşturma veri dosyasını kapatmak ve profil oluşturma verilerini kapatmak için **VSPerfCmd** [/shutdown](../profiling/shutdown.md) seçeneğini çağırabilirsiniz.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdir

1. Profilleyiciyi hedef uygulamadan ayırmak için aşağıdakilerden birini yapın:

    - Hizmeti durdurun.

         -veya-

    - **VSPerfCmd /detach yazın**

2. Profilleyiciyi kapatın. Şunu yazın:

     **VSPerfCmd /shutdown**

## <a name="see-also"></a>Ayrıca bkz.
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
- [Örnekleme yöntemi veri görünümleri](../profiling/profiler-sampling-method-data-views.md)
