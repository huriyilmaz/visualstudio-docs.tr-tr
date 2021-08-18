---
title: Uygulama istatistikleri toplamak için yerel & profil oluşturma
description: Profil Visual Studio Profil Oluşturma Araçları çalışan bir yerel tek başına uygulamaya eklemek ve örnekleme yöntemini kullanarak performans istatistikleri almak için Visual Studio Profil Oluşturma Araçları'i kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: df44fe42-281b-4398-b3fc-277b62ae41f1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: 78f610802b6a9c3b9134f84c89adc783178985bc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122141915"
---
# <a name="how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-application-statistics-by-using-the-command-line"></a>Nasıl yapılır: Profil oluşturucu komut satırını kullanarak yerel bir tek başına uygulamaya profil oluşturucu ekleme ve uygulama istatistikleri toplama
Bu makalede, profilleyiciyi çalışan bir yerel tek başına (istemci) uygulamasına eklemek ve örnekleme yöntemini kullanarak performans istatistikleri toplamak için Profil Oluşturma Araçları komut satırı araçlarının nasıl [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] kullanımı açıklanmıştır.

> [!NOTE]
> Windows 8 ve Windows Server 2012 profil oluşturma Visual Studio bu platformlarda veri toplama şeklinde önemli değişiklikler gerektirmektedir. UWP uygulamaları için yeni koleksiyon teknikleri de gerekir. Uygulama [ve uygulama Windows 8 performans Windows Server 2012 bakın.](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)
>
> Profil oluşturma araçlarının yolunu almak için [bkz. Komut satırı araçlarının yolunu belirtme.](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md) 64 bit bilgisayarlarda, araçların hem 64 bit hem de 32 bit sürümleri kullanılabilir. Profil oluşturma komut satırı araçlarını kullanmak için, araç yolunu Komut İstemi penceresinin PATH ortam değişkenine eklemeniz veya komutun kendisine eklemeniz gerekir.

 Profiler uygulamaya ekli olduğunda veri toplamayı duraklatabilir ve sürdürebilirsiniz. Profil oluşturma oturumunu sona erdirmak için, profil oluşturmanın artık uygulamaya bağlı olması ve profilleyicinin açıkça kapatılamaması gerekir.

## <a name="attach-the-profiler"></a>Profilleyiciyi ekleme
 Profilleyiciyi profilleyiciyi kullanarak bir hedef uygulamaya eklemek için **VSPerfCmd/start** ve **/attach** seçeneklerini kullanarak profilleyiciyi başlatarak hedef uygulamaya iliştirebilirsiniz. **/start ve /attach** seçeneklerini **tek** bir komut satırı üzerinde belirtebilirsiniz. Hedef uygulamanın başında veri toplamayı duraklatmak için **/globaloff** seçeneğini de ekebilirsiniz. Ardından veri **toplamaya başlamak için /globalon** kullanırsanız.

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Profilleyiciyi çalışan bir uygulamanın .NET Framework için

1. Bir komut istemi penceresi açın.

2. Profilleyiciyi başlatma. Şunu yazın:

    **VSPerfCmd /start:sample /output:** `OutputFile` [`Options`]

   - [/start](../profiling/start.md)**:sample** seçeneği profilleyiciyi başlatıyor.

   - [/output](../profiling/output.md)**: seçeneği** / start ile `OutputFile` **gereklidir.** `OutputFile` profil oluşturma verileri (.vsp) dosyasının adını ve konumunu belirtir.

     **/start:sample** seçeneğiyle aşağıdaki seçeneklerden herhangi birini kullanabilirsiniz.

   | Seçenek | Açıklama |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Profili yapılan işleme sahip olan hesabın etki alanını ve kullanıcı adını belirtir. Bu seçenek yalnızca işlem oturum açmış kullanıcıdan farklı bir kullanıcı olarak çalışıyorsa gereklidir. İşlem sahibi, Görev Yöneticisi'nin İşlemler sekmesindeki Kullanıcı Adı Windows listelenir. |
   | [/crosssession](../profiling/crosssession.md) | Diğer oturumlarda işlemlerin profilini oluşturmayı sağlar. Uygulama farklı bir oturumda ASP.NET bu seçenek gereklidir. Oturum idenitifier, Görev Yöneticisi'nin İşlemler sekmesinde oturum Windows listelenir. **/CS,** **/crosssession için bir kısaltma olarak belirtilebilir.** |
   | [/wincounter:](../profiling/wincounter.md) `WinCounterPath` | Profil oluşturma Windows toplanacak bir performans sayacı belirtir. |
   | [/automark:](../profiling/automark.md) `Interval` | Yalnızca **/wincounter ile** kullanın. Performans sayacı toplama olayları arasındaki milisaniye Windows sayısını belirtir. Varsayılan değer 500 ms'tir. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Profil oluşturma sırasında toplanacak Windows (ETW) olayı için bir Olay İzleme belirtir. ETW olayları ayrı bir () içinde toplanır.*etl*) dosyasını seçin. |

3. Profilleyiciyi hedef uygulamaya ekleme. Şunu yazın:

    **VSPerfCmd**[/attach:](../profiling/attach.md) {&#124;} `PID` [ `ProcName` `Sample Event` ]  

    `PID` hedef uygulamanın işlem kimliğini belirtir. `ProcessName` , işlem adını belirtir. belirttiğinizde ve aynı `ProcessName` adı içeren birden çok işlem çalışıyorsa, sonuçların tahmin edilemez olduğunu unutmayın. Görev Yöneticisi'nde çalışan tüm işlemlerin işlem kimliklerini Windows görüntüebilirsiniz.

    Varsayılan olarak, her 10.000.000 durdurulan işlemci saat döngüsü için performans verileri örnek alır. Bu, 1GH işlemcide her saniye yaklaşık 100 kezdir. Saat döngüsü aralığını değiştirmek veya farklı bir örnekleme olayı belirtmek için aşağıdaki seçeneklerden birini belirtebilirsiniz.

   |Örnek olay|Açıklama|
   |------------------|-----------------|
   |[/timer](../profiling/timer.md) **:**`Interval`|Örnekleme aralığını tarafından belirtilen durdurulmamış saat döngülerinin sayısına `Interval` değiştirir.|
   |[/pf](../profiling/pf.md)[**:** `Interval` ]|Örnekleme olayında sayfa hatalarını değiştirir. `Interval`belirtilirse, örnekler arasındaki sayfa hatalarının sayısını ayarlar. Varsayılan değer 10'dır.|
   |[/sys](../profiling/sys-vsperfcmd.md) [**:** `Interval` ]|Örnekleme olayı, işlemden işletim sistemi çekirdeğine (syscalls) yapılan sistem çağrılarını değiştirir. `Interval`belirtilirse, örnekler arasındaki çağrı sayısını ayarlar. Varsayılan değer 10'dır.|
   |[/counter](../profiling/counter.md) **:**`Config`|Örnekleme olayı ve aralığını işlemci performans sayacıyla ve içinde belirtilen aralıkla `Config` değiştirir.|

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hedef uygulama çalışmaya devam ediyorsa, profil *VSPerfCmd.exe* veri dosyasına veri yazmayı başlatmak ve durdurmak için uygulama seçeneklerini kullanabilirsiniz. Veri toplamayı denetlemek, uygulamanın başlat veya kapatılması gibi program yürütmenin belirli bir bölümü için veri toplamaya olanak sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki **VSPerfCmd seçenekleri çiftleri** veri toplamayı başlatacak ve durduracak. Her seçeneği ayrı bir komut satırı üzerinde belirtin. Veri toplamayı birden çok kez açabilirsiniz ve kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Tüm işlemler **için veri toplamayı** başlatır ( /globalon ) veya durdurur (**/globaloff).**|
    |[/processon:](../profiling/processon-and-processoff.md)  `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|tarafından belirtilen işlem için (**/processon**) veya durdurur (**/processoff**) veri toplamayı `PID` durdurur.|
    |[/attach](../profiling/attach.md) **:** `PID` [/detach](../profiling/detach.md)|**/attach** tarafından belirtilen işlem için veri toplamaya `PID` başlar. **/detach tüm** işlemler için veri toplamayı durdurur.|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sona er
 Profil oluşturma oturumunu sona erdirmak için profil oluşturma işleminin tüm profili yapılan işlemlerden ayrılmaları ve profil oluşturma işleminin açıkça kapatılmış olması gerekir. Uygulamayı kapatarak veya **VSPerfCmd /detach** seçeneğini çağırarak, örnekleme yöntemini kullanarak profil profili yapılan bir uygulamanın profillerini ayırabilirsiniz. Ardından, profil oluşturma veri dosyasını kapatmak ve profil oluşturma verilerini kapatmak için **VSPerfCmd /shutdown** seçeneğini çağırabilirsiniz. **VSPerfClrEnv /off** komutu profil oluşturma ortam değişkenlerini temizler.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdir

1. Profilleyiciyi hedef uygulamadan ayırmak için aşağıdaki adımlardan birini gerçekleştirin.

    - **VSPerfCmd /detach yazın**

         -veya-

    - Hedef uygulamayı kapatın.

2. Profilleyiciyi kapatın. Şunu yazın:

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)

3. (İsteğe bağlı) Profil oluşturma ortam değişkenlerini temizleme. Şunu yazın:

     **VSPerfClrEnv/off**

## <a name="see-also"></a>Ayrıca bkz.
- [Tek başına uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Örnekleme yöntemi veri görünümleri](../profiling/profiler-sampling-method-data-views.md)
