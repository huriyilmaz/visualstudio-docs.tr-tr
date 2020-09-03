---
title: Profil oluşturucu komut satırı-aracı istemci .NET bileşeni, zaman verilerini al
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: b7dcc27b-45c6-4302-9552-6fa5b1e94b56
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 64c69a8f38e7b0e4705fb8cca187936b96264f55
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85328023"
---
# <a name="how-to-instrument-a-stand-alone-net-framework-component-and-collect-timing-data-with-the-profiler-from-the-command-line"></a>Nasıl yapılır: Tek başına bir .NET Framework bileşenini izleme ve komut satırından profil oluşturucu ile zamanlama verileri toplama
Bu konu, gibi bir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .NET Framework bileşenini işaretlemek için profil oluşturma araçları komut satırı araçlarının nasıl kullanılacağını açıklar.* exe* veya. *DLL* dosyası ve ayrıntılı zamanlama verilerini toplamak.

> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. UWP uygulamaları için de yeni koleksiyon teknikleri gerekir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> Profil oluşturma araçlarının yolunu almak için, bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). 64 bit bilgisayarlarda, araçların her ikisi de 64-bit ve 32 bit sürümleri mevcuttur. Profil oluşturucu komut satırı araçlarını kullanmak için araçlar yolunu komut Istemi penceresinin PATH ortam değişkenine eklemeniz ya da komutun kendisine eklemeniz gerekir.
>
> Bir profil oluşturma çalıştırmasına katman etkileşim verileri eklemek, komut satırı profil oluşturma araçlarıyla belirli yordamlar gerektirir. Bkz. [Katman etkileşimi verilerini toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md).

 İzleme yöntemini kullanarak bir .NET Framework bileşeninden ayrıntılı zamanlama verileri toplamak için, profil oluşturma ortamı değişkenlerini başlatmak üzere bileşenin belgelenmiş bir sürümünü ve [VSPerfCLREnv. cmd](../profiling/vsperfclrenv.md) aracını oluşturmak için [VSInstr.exe](../profiling/vsinstr.md) aracını kullanın. Ardından profil oluşturucuyu başlatın.

 Belgelenmiş bileşen yürütüldüğünde, zamanlama verileri bir veri dosyasına otomatik olarak toplanır. Profil oluşturma oturumu sırasında veri toplamayı duraklatabilir ve devam ettirebilirsiniz.

 Profil oluşturma oturumunu sonlandırmak için hedef uygulamayı kapatır ve profil oluşturucuyu açıkça kapatın. Çoğu durumda, bir oturumun sonunda profil oluşturma ortam değişkenlerini temizlemeniz önerilir.

## <a name="start-the-profiling-session"></a>Profil oluşturma oturumunu Başlat

#### <a name="to-start-profiling-by-using-the-instrumentation-method"></a>İzleme yöntemini kullanarak profil oluşturmayı başlatmak için

1. Bir komut istemi penceresi açın. Gerekirse, profil oluşturucu Araçları dizinini PATH ortam değişkenine ekleyin. Yol, yükleme sırasında eklenmez.

2. Hedef uygulamanın belgelenmiş bir sürümünü oluşturmak için **vsinstr** aracını kullanın.

3. .NET Framework profil oluşturma ortamı değişkenlerini başlatın. Şunu yazın:

    **VSPerfClrEnv/TRACEON**

4. Profil oluşturucuyu başlatın. Şunu yazın:

    **VSPerfCmd/start: Trace/output:** `OutputFile` [`Options`]

   - [/Start](../profiling/start.md)**: Trace** seçeneği profil oluşturucuyu başlatır.

   - /Start ile [/output](../profiling/output.md)**:** `OutputFile` seçeneği gereklidir. **/start** `OutputFile` profil oluşturma verileri (. vsp) dosyasının adını ve konumunu belirtir.

     Aşağıdaki seçeneklerden herhangi birini, **/Start: Trace** seçeneği ile kullanabilirsiniz.

   | Seçenek | Açıklama |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Profili oluşturulan işlemin sahibi olan hesabın etki alanını ve Kullanıcı adını belirtir. Bu seçenek yalnızca, işlem oturum açan kullanıcıdan farklı bir kullanıcı olarak çalışıyorsa gereklidir. İşlem sahibi, Windows Görev Yöneticisi 'nin **işlemler** sekmesinde **Kullanıcı adı** sütununda listelenir. |
   | [/CrossSession](../profiling/crosssession.md) | Diğer oturumlardaki işlemlerin profilini oluşturmaya izin vermez. ASP.NET uygulaması farklı bir oturumda çalışıyorsa, bu seçenek gereklidir. Oturum tanımlayıcısı, Windows Görev Yöneticisi 'nin **süreçler** SEKMESINDEKI **oturum kimliği** sütununda listelenir. **/CS** , **/CrossSession**için bir kısaltma olarak belirtilebilir. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Profil Oluşturucu veri koleksiyonu duraklatılmış şekilde başlatılır. Profil oluşturmayı sürdürmeye yönelik [/GlobalOn](../profiling/globalon-and-globaloff.md) kullanın. |
   | [/Counter](../profiling/counter.md) **:**`Config` | ' De belirtilen işlemci performans sayacından bilgi toplar `Config` . Her profil oluşturma olayında toplanan verilere sayaç bilgileri eklenir. |
   | [/WINCOUNTER](../profiling/wincounter.md) **:**`WinCounterPath` | Profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir. |
   | [/AutoMark](../profiling/automark.md) **:**`Interval` | Yalnızca **/WINCOUNTER** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 MS 'dir. |
   | [/Events](../profiling/events-vsperfcmd.md) **:**`Config` | Profil oluşturma sırasında toplanacak bir Windows için olay Izleme (ETW) olayı belirtir. ETW olayları ayrı bir (.* ETL*) dosyası. |

5. Hedef uygulamayı komut Istemi penceresinden başlatın.

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hedef uygulama çalışırken, *VSPerfCmd.exe* seçeneklerini kullanarak profil oluşturucu veri dosyasına veri yazmayı başlatıp durdurarak veri toplamayı kontrol edebilirsiniz. Veri toplamayı denetlemek, program yürütmesinin, uygulamayı başlatma veya kapatma gibi belirli bir bölümü için veri toplamanızı sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki seçenek çiftleri veri toplamayı başlatır ve durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Tüm süreçler için veri toplamayı başlatır (**/GlobalOn**) veya Durdur (**/globaloff**).|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|İşlem KIMLIĞI () tarafından belirtilen işlem için (**/ProcessOn**) veya duraklar (**/ProcessOff**) veri toplamayı başlatır `PID` .|
    |[/ThreadOn](../profiling/threadon-and-threadoff.md) **:** `TID` [/ThreadOff](../profiling/threadon-and-threadoff.md) **:**`TID`|İş parçacığı KIMLIĞI () tarafından belirtilen iş parçacığı için (**/ThreadOn**) veya Durdur (**/ThreadOff**) veri toplamayı başlatır `TID` .|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu Sonlandır
 Profil oluşturma oturumunu sonlandırmak için, Araçlı bileşeni çalıştıran uygulamayı kapatın. Profiler 'ı devre dışı bırakmak ve profil oluşturma veri dosyasını kapatmak için **VSPerfCmd** [/Shutdown](../profiling/shutdown.md) seçeneğini çağırın. **VSPerfCLREnv/off** komutu profil oluşturma ortam değişkenlerini temizler.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sonlandırmak için

1. Hedef uygulamayı kapatın.

2. Profil oluşturucuyu kapatın. Şunu yazın:

     **VSPerfCmd/shutdown**

3. Seçim Profil oluşturma ortamı değişkenlerini temizleyin. Şunu yazın:

     **VSPerfClrEnv/off**

## <a name="see-also"></a>Ayrıca bkz.
- [Tek başına uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [İzleme yöntemi veri görünümleri](../profiling/instrumentation-method-data-views.md)
