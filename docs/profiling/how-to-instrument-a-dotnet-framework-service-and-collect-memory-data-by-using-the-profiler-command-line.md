---
title: 'Profiler komut satırı: Instrument .NET hizmeti, bellek verilerini alma'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2fa072fc-05fe-4420-99c0-51d2ea3ac4ce
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 8697f1451e3d528ff27beb2467ff7758e04267cc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74775502"
---
# <a name="how-to-instrument-a-net-framework-service-and-collect-memory-data-by-using-the-profiler-command-line"></a>Nasıl yapılır: Bir .NET Framework hizmetini enstrümanlayın ve profil oluşturucu komut satırını kullanarak bellek verilerini toplayın
Bu makalede, bir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .NET Framework hizmeti ne zaman bir .NET Framework hizmeti araç ve bellek kullanım verileri toplamak için Profil Oluşturma Araçları komut satırı araçları nasıl kullanılacağı açıklanmaktadır. Bellek ayırma verilerini toplayabilir veya hem bellek ayırma hem de nesne yaşam boyu verilerini toplayabilirsiniz.

> [!NOTE]
> Windows 8 ve Windows Server 2012'deki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturucusu bu platformlarda veri toplama şeklinde önemli değişiklikler gerektiriyordu. UWP uygulamaları da yeni toplama teknikleri gerektirir. [Windows 8 ve Windows Server 2012 uygulamalarında Performans Araçları'na](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)bakın.
>
> [!NOTE]
> Bilgisayar başladıktan sonra hizmet yeniden başlatılamıyorsa, işletim sistemi başlatıldığında başlayan böyle bir hizmet, bir hizmetin enstrümantasyon yöntemiyle profilini alamazsınız.
>
> Profil oluşturma araçlarına giden yolu almak [için](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)bkz. 64 bit bilgisayarlarda, araçların hem 64 bit hem de 32 bit sürümleri kullanılabilir. Profil oluşturucu komut satırı araçlarını kullanmak için, komut istemi penceresinin PATH ortamı değişkenine araçlar yolunu eklemeniz veya komutun kendisine eklemeniz gerekir.

## <a name="start-the-profiling-session"></a>Profil oluşturma oturumunu başlatma
 Bir .NET Framework hizmetinden performans verileri toplamak için, uygun ortam değişkenlerini ve [VSInstr.exe](../profiling/vsinstr.md) aracını başlatmayı ve hizmet ikili dosyasının enstrümantize edilmiş bir kopyasını oluşturmak için [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) aracını kullanırsınız.

 Hizmeti barındıran bilgisayarın profil oluşturma için yapılandırmak için yeniden başlatılması gerekir. Hizmeti, Servis Denetim Yöneticisi'nden de el ile başlatmanız gerekir. Daha sonra profil oluşturucuyu ve sonra .NET Framework hizmetini başlatın.

 Enstrümantif bileşen yürütüldüğünde, bellek verileri otomatik olarak bir veri dosyasına toplanır. Profil oluşturma oturumu sırasında veri toplamayı duraklatabilir ve devam ettirebilirsiniz.

 Profil oluşturma oturumunu sona erdirmek için hizmeti kapatır ve profil oluşturucuyu açıkça kapatırsınız. Çoğu durumda, oturumun sonunda profil oluşturma ortamı değişkenlerini temizlemenizi öneririz.

#### <a name="to-begin-profiling-a-net-framework-service"></a>Bir .NET Framework hizmetinin profilini çıkarmaya başlamak için

1. Bir komut istemi penceresi açın.

2. Hizmet ikilisinin enstrümantedilmiş bir sürümünü oluşturmak için **VSInstr** aracını kullanın.

3. Orijinal ikiliyi enstrümantedilmiş sürümle değiştirmek için Servis Denetim Yöneticisi'ni kullanın. Hizmet Başlangıç Türü'nün El Kitabı olarak ayarlandıklarına emin olun.

4. Profil oluşturma ortamı değişkenlerini başlangıç olarak önleştirin. Şunu yazın:

    **VSPerfClrEnv** {**/globaltracegc** &#124; **/globaltracegclife**}

   - **/globaltracegc** ve **/globaltracegclife** bellek ayırma ve nesne yaşam boyu verilerin toplanmasını sağlar.

       |Seçenek|Açıklama|
       |------------|-----------------|
       |**/globaltracegc**|Yalnızca bellek ayırma verilerini toplar.|
       |**/globaltracegclife**|Bellek ayırma ve nesne yaşam boyu verileri toplar.|

5. Bilgisayarı yeniden başlatın.

6. Bir komut istemi penceresi açın.

7. Profilciyi çalıştırın. Şunu yazın:

    **VSPerfCmd**  [/start](../profiling/start.md) **:trace**  [/output](../profiling/output.md) **:** `OutputFile` [`Options`]

   - **/start: çekişme** seçeneği profil oluşturucuyu başlatir.

   - **/output:** `OutputFile` seçeneği **/start**ile gereklidir. `OutputFile`profil oluşturma verileri (.vsp) dosyasının adını ve konumunu belirtir.

     **/start:sample** seçeneği ile aşağıdaki seçeneklerden herhangi birini kullanabilirsiniz.

   > [!NOTE]
   > Hizmetler için **genellikle /kullanıcı** ve **/çapraz oturum** seçenekleri gereklidir.

   | Seçenek | Açıklama |
   | - | - |
   | [/kullanıcı](../profiling/user-vsperfcmd.md) **:**[ ]`Domain`**\\**`UserName` | ASP.NET alt işleminin sahibi hesabın etki alanını ve kullanıcı adını belirtir. İşlem, oturum açmış kullanıcı dışında bir kullanıcı olarak çalışıyorsa, bu seçenek gereklidir. İşlem sahibi, Windows Görev Yöneticisi'nin İşlemler sekmesinde Kullanıcı Adı sütununda listelenir. |
   | [/çapraz oturum](../profiling/crosssession.md) | Diğer oturum oturumlarında işlemlerin profilini çıkarmasağlar. ASP.NET uygulaması farklı bir oturumda çalışıyorsa bu seçenek gereklidir. Oturum kimliği, Windows Görev Yöneticisi'nin **İşlemler** sekmesinde **Oturum Kimliği** sütununda listelenir. **/CS** **/ crosssession**için bir kısaltma olarak belirtilebilir. |
   | [/waitstart](../profiling/waitstart.md)[**:**`Interval`] | Profilcinin bir hata döndürmeden önce başlatılmasını beklemek için saniye sayısını belirtir. `Interval` Belirtilmemişse, profil oluşturucu süresiz olarak bekler. Varsayılan olarak, **/start** hemen döner. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Veri toplama duraklatılmış profil oluşturucuyu başlatmak için **/globaloff** seçeneğini **/start** komut satırına ekleyin. Profil oluşturmayı sürdürmek için **/globalon'u** kullanın. |
   | [/sayaç](../profiling/counter.md) **:**`Config` | Config'de belirtilen işlemci performans sayacından bilgi toplar. Sayaç bilgileri, her profil oluşturma etkinliğinde toplanan verilere eklenir. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Yalnızca **/wincounter** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 ms'dir. |
   | [/olaylar](../profiling/events-vsperfcmd.md) **:**`Config` | Profil oluşturma sırasında toplanacak windows için olay izleme (ETW) olayı belirtir. ETW olayları ayrı bir şekilde toplanır (.* etl*) dosyası. |

8. Gerekirse hizmeti başlatın.

9. ProfiloluşturcIyi servise takın. Şunu yazın:

     **VSPerfCmd /ekle:** `PID`&#124;`ProcessName`

    - Hizmetin işlem kimliğini veya işlem adını belirtin. Windows Görev Yöneticisi'nde tüm çalışan işlemlerin işlem adlarını ve adlarını görüntüleyebilirsiniz.

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hizmet çalışırken, *VSPerfCmd.exe* seçenekleriyle dosyaya veri yazısını başlatıp durdurarak veri toplamayı denetleyebilirsiniz. Veri toplamayı denetlemek, uygulamayı başlatma veya kapatma gibi program yürütmesinin belirli bir bölümü için veri toplamanızı sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki **VSPerfCmd** seçenekleri, veri toplamayı başlayıp durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Tüm işlemler için **(/globalon)** başlatır veya durur (**/globaloff**) veri toplama.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|İşlem Kimliği tarafından belirtilen işlem için **(/processon)** başlatır veya **(/processoff)** veri toplamayı durdurur (`PID`).|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:**`TID`|İş parçacığı kimliği ( ))'nin belirttiği iş parçacığı için (**/threadon)** veya durur (**/threadoff**) veri toplamayı başlatır (`TID`).|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sonlandırma
 Profil oluşturma oturumunu sona erdirmek için, enstrümantif bileşeni çalıştıran uygulamayı kapatın, ardından profil oluşturucuyu kapatmak ve profil oluşturma veri dosyasını kapatmak için **VSPerfCmd** [/shutdown](../profiling/shutdown.md) seçeneğini başlatın. **VSPerfClrEnv /globaloff** komutu profil oluşturma ortamı değişkenlerini temizler.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdirmek için

1. Hizmeti Servis Kontrol Yöneticisi'nden durdurun.

2. Profilciyi kapat. Şunu yazın:

     **VSPerfCmd /kapatma**

3. Tüm profil oluşturmayı tamamladığınızda, profil oluşturma ortamı değişkenlerini temizleyin. Şunu yazın:

     **VSPerfClrEnv /globaloff**

     Enstrümantedilen modülü orijinali ile değiştirin. Gerekirse, hizmetin Başlangıç Türünü yeniden yapılandırın.

4. Bilgisayarı yeniden başlatın.

## <a name="see-also"></a>Ayrıca bkz.
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
- [.NET bellek veri görünümleri](../profiling/dotnet-memory-data-views.md)
