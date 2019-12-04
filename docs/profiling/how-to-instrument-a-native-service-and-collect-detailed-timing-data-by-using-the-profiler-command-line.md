---
title: 'Profil oluşturucu komut satırı: yerel hizmeti gereç, zamanlama verilerini al'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: dfe58b39-63f8-4a87-ab3a-2b5b14faa8d0
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: c738a5183a7708c967192cf201e38a4f9384710e
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778875"
---
# <a name="how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line"></a>Nasıl yapılır: profil oluşturucu komut satırını kullanarak yerel bir hizmeti izleme ve ayrıntılı zamanlama verileri toplama
Bu makalede, yerel (C/C++) bir hizmeti işaretlemek ve ayrıntılı zamanlama verilerini toplamak için [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] profil oluşturma araçları komut satırı araçlarının nasıl kullanılacağı açıklanır.

> [!NOTE]
> Hizmet, bilgisayar başladıktan sonra yalnızca işletim sistemi başladığında başlatılan bir hizmet gibi yeniden başlatılamazsa, izleme yöntemiyle bir hizmetin profilini oluşturamazsınız.
>
> Profil oluşturma araçlarının yolunu almak için, bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). 64 bit bilgisayarlarda, araçların her ikisi de 64-bit ve 32 bit sürümleri mevcuttur. Profil oluşturucu komut satırı araçlarını kullanmak için araçlar yolunu komut Istemi penceresinin PATH ortam değişkenine eklemeniz ya da komutun kendisine eklemeniz gerekir.

 İzleme yöntemini kullanarak yerel bir hizmetten ayrıntılı zamanlama verileri toplamak için, bir bileşenin belgelenmiş bir sürümünü oluşturmak için [vsinstr. exe](../profiling/vsinstr.md) aracını kullanın. Sonra, hizmetin el ile başlatılacak şekilde yapılandırıldığından emin olmak için, Service 'in belgelenmiş olmayan sürümünü belgelenmiş sürümle değiştirirsiniz. Ardından profil oluşturucuyu başlatın.

 Hizmet başlatıldığında, zamanlama verileri bir veri dosyasına otomatik olarak toplanır. Profil oluşturma oturumu sırasında veri toplamayı duraklatabilir ve devam ettirebilirsiniz.

 Profil oluşturma oturumunu sonlandırmak için, hizmeti devre dışı bırakın ve ardından profil oluşturucuyu açıkça kapatın.

## <a name="start-the-application-with-the-profiler"></a>Uygulamayı Profil Oluşturucu ile başlatma

#### <a name="to-start-profiling-a-native-service"></a>Yerel bir hizmetin profilini oluşturmaya başlamak için

1. Bir komut istemi penceresi açın.

2. Service binary 'ın belgelenmiş bir sürümünü oluşturmak için **vsinstr** aracını kullanın.

3. Özgün ikilisini belgelenmiş sürümle değiştirin. Windows hizmet denetimi Yöneticisi 'nde, hizmet başlatma türünün manuel olarak ayarlandığından emin olun.

4. Profil oluşturucuyu başlatın. Tür:

    **VSPerfCmd** [/Start](../profiling/start.md) **: Trace**  [/output](../profiling/output.md) **:** `OutputFile` [`Options`]

   - **/Start: Trace** seçeneği profil oluşturucuyu başlatır.

   - **/Output:** `OutputFile` seçeneği, **/Start**ile gereklidir. `OutputFile` profil oluşturma verilerinin adını ve konumunu belirtir (. *VSP*) dosyası.

     Aşağıdaki seçeneklerden herhangi birini, **/Start: Trace** seçeneği ile kullanabilirsiniz.

   > [!NOTE]
   > **/User** ve **/CrossSession** seçenekleri genellikle ASP.NET uygulamaları için gereklidir.

   | Seçenek | Açıklama |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:** [`Domain` **\\** ]`UserName` | ASP.NET çalışan işleminin sahibi olan hesabın etki alanını ve Kullanıcı adını belirtir. İşlem, oturum açmış kullanıcı dışında bir kullanıcı olarak çalışıyorsa, bu seçenek gereklidir. İşlem sahibi, Windows Görev Yöneticisi 'nin **işlemler** sekmesinde **Kullanıcı adı** sütununda listelenir. |
   | [/CrossSession](../profiling/crosssession.md) | Diğer oturum oturumlarda işlemlerin profilini oluşturmayı mümkün. ASP.NET uygulaması farklı bir oturumda çalışıyorsa, bu seçenek gereklidir. Oturum KIMLIĞI, Windows Görev Yöneticisi 'nin süreçler sekmesindeki oturum KIMLIĞI sütununda listelenir. **/CS** , **/CrossSession**için bir kısaltma olarak belirtilebilir. |
   | [/WaitStart](../profiling/waitstart.md)[ **:** `Interval`] | Profil oluşturucunun hata vermeden önce başlatılması için bekleyeceği saniye sayısını belirtir. `Interval` belirtilmemişse, profil oluşturucu süresiz olarak bekler. Varsayılan olarak, **/Start** hemen döndürür. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Veri toplama duraklatılmış şekilde profil oluşturucuyu başlatmak için, **/Start** komut satırına **/globaloff** seçeneğini ekleyin. Profil oluşturmayı sürdürmeye yönelik **/GlobalOn** kullanın. |
   | [/Counter](../profiling/counter.md) **:** `Config` | Yapılandırma içinde belirtilen işlemci performans sayacından bilgi toplar. Her profil oluşturma olayında toplanan verilere sayaç bilgileri eklenir. |
   | [/WINCOUNTER](../profiling/wincounter.md) **:** `WinCounterPath` | Profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir. |
   | [/AutoMark](../profiling/automark.md) **:** `Interval` | Yalnızca **/WINCOUNTER** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 MS 'dir. |
   | [/Events](../profiling/events-vsperfcmd.md) **:** `Config` | Profil oluşturma sırasında toplanacak bir Windows için olay Izleme (ETW) olayı belirtir. ETW olayları ayrı bir (. *ETL*) dosyası. |

5. Hizmeti Hizmet Denetim Yöneticisi 'nden başlatın.

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hizmet çalışırken, *VSPerfCmd. exe* seçeneklerini kullanarak verileri profil oluşturucu veri dosyasına yazmayı başlatabilir ve durdurabilirsiniz. Veri toplamayı denetlemek, program yürütmenin belirli bir bölümü için, hizmeti başlatma veya kapatma gibi verileri toplamanızı sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki **VSPerfCmd** seçenek çiftleri veri toplamayı başlatır ve durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Tüm süreçler için veri toplamayı başlatır ( **/GlobalOn**) veya Durdur ( **/globaloff**).|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:** `PID`|İşlem KIMLIĞI (`PID`) tarafından belirtilen işlem için veri toplamayı başlatır ( **/ProcessOn**) veya Durdur ( **/ProcessOff**).|
    |[/ThreadOn](../profiling/threadon-and-threadoff.md) **:** `TID` [/ThreadOff](../profiling/threadon-and-threadoff.md) **:** `TID`|İş parçacığı KIMLIĞI (`TID`) tarafından belirtilen iş parçacığı için ( **/ThreadOn**) veya Durdur ( **/ThreadOff**) veri toplamayı başlatır.|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu Sonlandır
 Profil oluşturma oturumunu sonlandırmak için, Araçlı bileşeni çalıştıran hizmeti durdurun ve ardından **VSPerfCmd**[/Shutdown](../profiling/shutdown.md) seçeneğini çağırıp profil oluşturucuyu kapatın ve profil oluşturma veri dosyasını kapatın.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sonlandırmak için

1. Hizmeti hizmet denetimi Yöneticisi 'nden durdurun.

2. Profil oluşturucuyu kapatın. Tür:

     **VSPerfCmd/shutdown**

3. Belgelenmiş modülün değerini özgün ile değiştirin. Gerekirse, hizmetin başlangıç türünü yeniden yapılandırın.

## <a name="see-also"></a>Ayrıca bkz.
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
- [İzleme yöntemi veri görünümleri](../profiling/instrumentation-method-data-views.md)
