---
title: Profil oluşturucu komut satırı-aracı .NET hizmeti, zamanlama ayrıntısı al
ms.date: 11/04/2016
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 62303ab2ea7296ca5093636efcf97ea7a3c540c1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85331478"
---
# <a name="how-to-instrument-a-net-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line"></a>Nasıl yapılır: Profil oluşturucu komut satırını kullanarak bir .NET hizmetini izleme ve ayrıntılı zamanlama verileri toplama

Bu makalede, bir .NET Framework hizmetini işaretlemek ve ayrıntılı zamanlama verilerini toplamak için Visual Studio Profil Oluşturma Araçları komut satırı araçlarının nasıl kullanılacağı açıklanır.

> [!NOTE]
> Hizmet, bilgisayar başladıktan sonra yalnızca işletim sistemi başladığında başlatılan bir hizmet gibi yeniden başlatılırsa, izleme yöntemiyle bir hizmetin profilini oluşturamazsınız.
>
> Profil oluşturma araçlarının yolunu almak için, bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). 64 bit bilgisayarlarda, araçların her ikisi de 64-bit ve 32 bit sürümleri mevcuttur. Profil oluşturucu komut satırı araçlarını kullanmak için araçlar yolunu komut Istemi penceresinin PATH ortam değişkenine eklemeniz ya da komutun kendisine eklemeniz gerekir.
>
> Bir profil oluşturma çalıştırmasına katman etkileşim verileri eklemek, komut satırı profil oluşturma araçlarıyla belirli yordamlar gerektirir. Bkz. [Katman etkileşimi verilerini toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md).

İzleme yöntemini kullanarak bir .NET Framework hizmetinden ayrıntılı zamanlama verileri toplamak için, bileşenin belgelenmiş bir sürümünü oluşturmak için [VSInstr.exe](../profiling/vsinstr.md) aracını kullanın. Sonra, hizmetin el ile başlatılacak şekilde yapılandırıldığından emin olmak için, Service 'in belgelenmiş olmayan sürümünü belgelenmiş sürümle değiştirirsiniz. Genel profil oluşturma ortamı değişkenlerini başlatmak için [VSPerfCLREnv. cmd](../profiling/vsperfclrenv.md) aracını kullanın ve ardından ana bilgisayarı yeniden başlatın. Ardından profil oluşturucuyu başlatın.

Hizmet başlatıldığında, zamanlama verileri bir veri dosyasına otomatik olarak toplanır. Profil oluşturma oturumu sırasında veri toplamayı duraklatabilir ve devam ettirebilirsiniz.

Profil oluşturma oturumunu sonlandırmak için, hizmeti devre dışı bırakın ve ardından profil oluşturucuyu açıkça kapatın. Çoğu durumda, bir oturumun sonunda profil oluşturma ortam değişkenlerini temizlemeniz önerilir.

## <a name="start-the-application-with-the-profiler"></a>Uygulamayı Profil Oluşturucu ile başlatma

1. Bir komut istemi penceresi açın.

2. Service binary 'ın belgelenmiş bir sürümünü oluşturmak için **vsinstr** aracını kullanın.

3. Özgün ikilisini belgelenmiş sürümle değiştirin. Windows hizmet denetimi Yöneticisi 'nde, hizmet başlatma türünün manuel olarak ayarlandığından emin olun.

4. .NET Framework profil oluşturma ortamı değişkenlerini başlatın. Şunu yazın:

     **VSPerfClrEnv/globaltraceon**

5. Bilgisayarı yeniden başlatın.

6. Bir komut istemi penceresi açın.

7. Profil oluşturucuyu başlatın. Şunu yazın:

     **VSPerfCmd/start: Trace/output:** `OutputFile` [`Options`]

   - [/Start](../profiling/start.md)**: Trace** seçeneği profil oluşturucuyu başlatır.

   - /Start ile [/output](../profiling/output.md)**:** `OutputFile` seçeneği gereklidir. **/start** `OutputFile` profil oluşturma verilerinin adını ve konumunu belirtir (.* VSP*) dosyası.

     Aşağıdaki seçeneklerden herhangi birini, **/Start: Trace** seçeneği ile kullanabilirsiniz.

     > [!NOTE]
     > **/User** ve **/CrossSession** seçenekleri genellikle profil oluşturma hizmetleri için gereklidir.

     | Seçenek | Açıklama |
     | - | - |
     | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Profili oluşturulan işlemin sahibi olan hesabın etki alanını ve Kullanıcı adını belirtir. Bu seçenek yalnızca, işlem oturum açmış kullanıcı dışında bir kullanıcı olarak çalışıyorsa gereklidir. İşlem sahibi, Windows Görev Yöneticisi 'nin **işlemler** sekmesinde **Kullanıcı adı** sütununda listelenir. |
     | [/CrossSession](../profiling/crosssession.md) | Diğer oturumlardaki işlemlerin profilini oluşturmaya izin vermez. Uygulama farklı bir oturumda çalışıyorsa, bu seçenek gereklidir. Oturum KIMLIĞI, Windows Görev Yöneticisi 'nin **süreçler** SEKMESINDEKI **oturum kimliği** sütununda listelenir. **/CS** , **/CrossSession**için bir kısaltma olarak belirtilebilir. |
     | [/WaitStart](../profiling/waitstart.md)[**:** `Interval` ] | Profil oluşturucunun hata vermeden önce başlatılması için bekleyeceği saniye sayısını belirtir. `Interval`Belirtilmezse, profil oluşturucu süresiz olarak bekler. Varsayılan olarak, **/Start** hemen döndürür. |
     | [/globaloff](../profiling/globalon-and-globaloff.md) | Veri toplama duraklatılmış şekilde profil oluşturucuyu başlatmak için, **/Start** komut satırına **/globaloff** seçeneğini ekleyin. Profil oluşturmayı sürdürmeye yönelik **/GlobalOn** kullanın. |
     | [/Counter](../profiling/counter.md) **:**`Config` | Yapılandırma içinde belirtilen işlemci performans sayacından bilgi toplar. Her profil oluşturma olayında toplanan verilere sayaç bilgileri eklenir. |
     | [/WINCOUNTER](../profiling/wincounter.md) **:**`WinCounterPath` | Profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir. |
     | [/AutoMark](../profiling/automark.md) **:**`Interval` | Yalnızca **/WINCOUNTER** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 MS 'dir. |
     | [/Events](../profiling/events-vsperfcmd.md) **:**`Config` | Profil oluşturma sırasında toplanacak bir Windows için olay Izleme (ETW) olayı belirtir. ETW olayları ayrı bir (.* ETL*) dosyası. |

8. Hizmeti Windows hizmet denetimi Yöneticisi ' nden başlatın.

## <a name="control-data-collection"></a>Veri toplamayı denetleme

Hizmet çalışırken, verileri profil oluşturucu veri dosyasına yazmayı başlatmak ve durdurmak için *VSPerfCmd.exe* seçeneklerini kullanabilirsiniz. Veri toplamayı denetlemek, program yürütmenin belirli bir bölümü için, hizmeti başlatma veya kapatma gibi verileri toplamanızı sağlar.

- Aşağıdaki **VSPerfCmd** seçenek çiftleri veri toplamayı başlatır ve durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Tüm süreçler için veri toplamayı başlatır (**/GlobalOn**) veya Durdur (**/globaloff**).|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|İşlem KIMLIĞI () tarafından belirtilen işlem için (**/ProcessOn**) veya duraklar (**/ProcessOff**) veri toplamayı başlatır `PID` .|
    |[/ThreadOn](../profiling/threadon-and-threadoff.md) **:** `TID` [/ThreadOff](../profiling/threadon-and-threadoff.md) **:**`TID`|İş parçacığı KIMLIĞI () tarafından belirtilen iş parçacığı için (**/ThreadOn**) veya Durdur (**/ThreadOff**) veri toplamayı başlatır `TID` .|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu Sonlandır

Profil oluşturma oturumunu sonlandırmak için, Araçlı bileşeni çalıştıran hizmeti durdurun ve ardından **VSPerfCmd** [/Shutdown](../profiling/shutdown.md) seçeneğini çağırıp profil oluşturucuyu kapatın ve profil oluşturma veri dosyasını kapatın. **VSPerfCLREnv/globaloff** komutu profil oluşturma ortam değişkenlerini temizler.

Yeni ortam ayarlarının uygulanması için bilgisayarı yeniden başlatmanız gerekir.

1. Hizmeti hizmet denetimi Yöneticisi 'nden durdurun.

2. Profil oluşturucuyu kapatın. Şunu yazın:

     **VSPerfCmd/shutdown**

3. Tüm profil oluşturmayı tamamladığınızda, profil oluşturma ortam değişkenlerini temizleyin. Şunu yazın:

     **VSPerfClrEnv/globaloff**

4. Belgelenmiş modülün değerini özgün ile değiştirin. Gerekirse, hizmetin başlangıç türünü yeniden yapılandırın.

5. Bilgisayarı yeniden başlatın.

## <a name="see-also"></a>Ayrıca bkz.

[Profil hizmetleri](../profiling/command-line-profiling-of-services.md) 
 [İzleme yöntemi veri görünümleri](../profiling/instrumentation-method-data-views.md)
