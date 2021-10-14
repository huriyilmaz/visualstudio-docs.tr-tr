---
title: Uygulama istatistiklerini toplamak için .NET hizmetine profil oluşturucu iliştirme
description: profil oluşturucuyu bir .NET Framework hizmetine eklemek ve örnekleme yöntemini kullanarak performans istatistikleri almak için Visual Studio Profil Oluşturma Araçları komut satırı araçlarını kullanın.
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: a0046c47-26c8-4bec-96a0-81da05e5104a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 81c86caa96a7d2780c6cce2c2292c375b62a4a55
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129968076"
---
# <a name="how-to-attach-the-profiler-to-a-net-service-to-collect-application-statistics-by-using-the-command-line"></a>Nasıl yapılır: komut satırını kullanarak uygulama istatistikleri toplamak için bir .NET hizmetine profil oluşturucu Iliştirme
bu makalede [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , profil oluşturucuyu bir .NET Framework hizmetine eklemek ve örnekleme yöntemini kullanarak performans istatistikleri toplamak için Profil Oluşturma Araçları komut satırı araçlarının nasıl kullanılacağı açıklanır.

> [!NOTE]
> Windows 8 ve Windows Server 2012 gelişmiş güvenlik özellikleri Visual Studio profiler 'ın bu platformlarda verileri topladıkları şekilde gerekli önemli değişikliklere sahiptir. UWP uygulamaları için de yeni koleksiyon teknikleri gerekir. bkz. [Windows 8 ve Windows Server 2012 uygulamalarda performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> Profil oluşturma araçlarının yolunu almak için, bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). 64 bit bilgisayarlarda, araçların her ikisi de 64-bit ve 32 bit sürümleri mevcuttur. Profil oluşturucu komut satırı araçlarını kullanmak için araçlar yolunu komut Istemi penceresinin PATH ortam değişkenine eklemeniz ya da komutun kendisine eklemeniz gerekir.
>
> Bir profil oluşturma çalıştırmasına katman etkileşim verileri eklemek, komut satırı profil oluşturma araçlarıyla belirli yordamlar gerektirir. Bkz. [Katman etkileşimi verilerini toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md).

 .NET Framework bir hizmetten performans verilerini toplamak için, uygun ortam değişkenlerini başlatmak üzere [vsperfclrenv. cmd](../profiling/vsperfclrenv.md) aracını kullanmanız gerekir. Ardından, hizmeti barındıran bilgisayarı yeniden başlatmanız ve bu bilgisayarı profil oluşturma için yapılandırmanız gerekir. Ardından profil oluşturucuyu hizmet işlemine iliştirebilirsiniz. Profil Oluşturucu hizmete eklendiğinde, veri toplamayı duraklatabilir ve devam ettirebilirsiniz.

 Profil oluşturma oturumunu sonlandırmak için, profil oluşturucunun hizmetten ayrılması ve ve açıkça kapatılması gerekir. Çoğu durumda, bir oturumun sonunda profil oluşturma ortam değişkenlerini temizlemeniz önerilir.

## <a name="attach-the-profiler"></a>Profil oluşturucuyu iliştirme

#### <a name="to-attach-the-profiler-to-a-net-framework-service"></a>profil oluşturucuyu bir .NET Framework hizmetine eklemek için

1. Hizmeti yükler.

2. Bir komut istemi penceresi açın.

3. Profil oluşturma ortamı değişkenlerini başlatın. Şunu yazın:

    **VSPerfCLREnv/globalsampleon** [**/samplelineoff**]

   - **/globalsampleon** , örneklemesi sunar.

   - **/samplelineoff** toplanan verilerin belirli kaynak kodu satırlarına atanmasını devre dışı bırakır. Bu seçenek belirtildiğinde, veriler yalnızca işlevlere atanır.

4. Bilgisayarı yeniden başlatın.

5. Bir komut istemi penceresi açın.

6. Profil oluşturucuyu başlatın. Şunu yazın:

    **VSPerfCmd**  [/Start](../profiling/start.md) **: örnek**  [/output](../profiling/output.md) **:** `OutputFile` [ `Options` ]

   - **/Start: örnek** seçeneği, profil oluşturucuyu başlatır.

   - /Start ile **/output:** `OutputFile` seçeneği gereklidir.  `OutputFile` profil oluşturma verileri (. vsp) dosyasının adını ve konumunu belirtir.

     Aşağıdaki seçeneklerden herhangi birini, **/Start: Sample** seçeneğiyle kullanabilirsiniz.

   > [!NOTE]
   > **/User** ve **/CrossSession** seçenekleri genellikle hizmetler için gereklidir.

   | Seçenek | Açıklama |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Profili oluşturulan işlemin sahibi olan hesabın etki alanını ve Kullanıcı adını belirtir. Bu seçenek yalnızca, işlem oturum açmış kullanıcı dışında bir kullanıcı olarak çalışıyorsa gereklidir. işlem sahibi, Windows görev yöneticisi 'nin işlemler sekmesinde kullanıcı adı sütununda listelenir. |
   | [/CrossSession](../profiling/crosssession.md) | Diğer oturumlardaki işlemlerin profilini oluşturmaya izin vermez. Hizmet farklı bir oturumda çalışıyorsa, bu seçenek gereklidir. oturum kimliği, Windows görev yöneticisi 'nin süreçler sekmesindeki oturum kimliği sütununda listelenir. **/CS** , **/CrossSession** için bir kısaltma olarak belirtilebilir. |
   | [/WINCOUNTER](../profiling/wincounter.md) **:** `WinCounterPath` | profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir. |
   | [/AutoMark](../profiling/automark.md) **:** `Interval` | Yalnızca **/WINCOUNTER** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 MS 'dir. |
   | [/Events](../profiling/events-vsperfcmd.md) **:** `Config` | profil oluşturma sırasında toplanacak Windows (ETW) olayı için bir olay izleme olayı belirtir. ETW olayları ayrı bir (. etl) dosyasında toplanır. |

7. Gerekirse, hizmeti başlatın.

8. Profil oluşturucuyu hizmete ekleyin. Şunu yazın:

    **VSPerfCmd**[/Attach](../profiling/attach.md) **:** { `PID`&#124;`ProcName` } [ `Sample Event` ] [[/targetclr](../profiling/targetclr.md)**:** `Version` ]  

   - Hizmetin işlem KIMLIĞI ( `PID` ) veya işlem adı (ProcName) belirtin. Windows görev yöneticisi 'nde çalışan tüm işlemlerin işlem kimliklerini ve adlarını görüntüleyebilirsiniz.

     Varsayılan olarak, performans verileri 10.000.000 her durdurulmayan işlemci saati döngüsünde örneklenir. Bu, 1 GH işlemcide saniyede yaklaşık 100 örnek olur. Saat çevrimi aralığını değiştirmek veya farklı bir örnekleme olayı belirtmek için aşağıdaki seçeneklerden birini belirtebilirsiniz.

   |Örnek olay|Description|
   |------------------|-----------------|
   |[/Timer](../profiling/timer.md) **:** `Interval`|Örnekleme aralığını, tarafından belirtilen durdurulmayan saat döngüsü sayısına dönüştürür `Interval` .|
   |[/PF](../profiling/pf.md)[**:** `Interval` ]|Örnekleme olayını sayfa hatalarına dönüştürür. `Interval`Belirtilmişse, örnekler arasındaki sayfa hatalarının sayısını ayarlar. Varsayılan değer 10 ' dur.|
   |[/sys](../profiling/sys-vsperfcmd.md)[ `:``Interval` ]|Örnekleme olayını, işlemden işletim sistemi çekirdeğine (syscalls) sistem çağrıları olarak değiştirir. `Interval`Belirtilmişse, örnekler arasındaki çağrı sayısını ayarlar. Varsayılan değer 10 ' dur.|
   |[/Counter](../profiling/counter.md) **:** `Config`|Örnekleme olayını ve aralığını, ' de belirtilen işlemci performans sayacı ve aralığı olarak değiştirir `Config` .|

   - **targetclr:** `Version` bir uygulamaya çalışma zamanının birden fazla sürümü yüklendiğinde profil için ortak dil çalışma zamanının (CLR) sürümünü belirtir. İsteğe bağlı.

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hizmet çalışırken, verileri profil oluşturucu veri dosyasına yazmayı başlatmak ve durdurmak için *VSPerfCmd.exe* seçeneklerini kullanabilirsiniz. Veri toplamayı denetlemek, program yürütmesinin, uygulamayı başlatma veya kapatma gibi belirli bir bölümü için veri toplamanızı sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki **VSPerfCmd** seçenek çiftleri veri toplamayı başlatır ve durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Tüm süreçler için veri toplamayı başlatır (**/GlobalOn**) veya Durdur (**/globaloff**).|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:** `PID`|İşlem KIMLIĞI () tarafından belirtilen işlem için (**/ProcessOn**) veya duraklar (**/ProcessOff**) veri toplamayı başlatır `PID` .|
    |**/Attach:**{ `PID`&#124;`ProcName` } [/detach](../profiling/detach.md)[: { `PID`&#124;`ProcName` }]|**/Attach** işlem kimliği veya işlem adı tarafından belirtilen işlem için veri toplamaya başlar. **/Detach** belirtilen işlem veya belirli bir işlem belirtilmemişse tüm işlemler için veri toplamayı durduruyor.|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu Sonlandır
 Profil oluşturma oturumunu sona erdirmak için profil oluşturma işleminin tüm profil oluşturma işlemlerinden ayrılması ve profil oluşturmanın açıkça kapatılmış olması gerekir. Uygulamayı kapatarak veya **VSPerfCmd /detach** seçeneğini çağırarak örnekleme yöntemiyle profili profili yapılan bir uygulamadan ayırabilirsiniz. Ardından, profil oluşturma veri dosyasını kapatıp kapatmak için **VSPerfCmd /shutdown** seçeneğini çağırabilirsiniz.

 **VSPerfClrEnv /globaloff** komutu profil oluşturma ortam değişkenlerini temizler, ancak bilgisayar yeniden başlatana kadar sistem yapılandırması sıfırlanmaz.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdirecek

1. Profilleyiciyi hedef uygulamadan ayırmak için aşağıdakilerden birini yapın:

    - Hizmeti durdurun.

         -veya-

    - **VSPerfCmd /detach yazın**

2. Profilleyiciyi kapatın. Şunu yazın:

     **VSPerfCmd /shutdown**

3. (İsteğe bağlı) Profil oluşturma ortam değişkenlerini temizleme. Şunu yazın:

     **VSPerfClrEnv /globaloff**

4. Bilgisayarı yeniden başlatın.

## <a name="see-also"></a>Ayrıca bkz.
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
- [Örnekleme yöntemi veri görünümleri](../profiling/profiler-sampling-method-data-views.md)
