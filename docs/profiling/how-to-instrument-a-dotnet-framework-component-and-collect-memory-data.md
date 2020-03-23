---
title: 'Profiler komut satırı: Enstrüman istemcisi .NET bileşeni, bellek verilerini almak'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d09cc46a-70f5-48f9-aa24-89913e67b359
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 76d216c4f112f88001b0314a23f22e689f729106
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74775907"
---
# <a name="how-to-instrument-a-stand-alone-net-framework-component-and-collect-memory-data-with-the-profiler-by-using-the-command-line"></a>Nasıl yapılır: Tek başına bir .NET Framework bileşenini izleme ve komut satırını kullanarak profil oluşturucu ile bellek verileri toplama
Bu makalede, .exe veya .dll dosyası gibi bağımsız bir uygulamanın .NET Framework bileşenini kullanmak ve profil oluşturucuyu kullanarak bellek bilgilerini toplamak için Profil Oluşturma Araçları komut satırı araçlarının nasıl kullanılacağı [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] açıklanmaktadır.

> [!NOTE]
> Profil oluşturma araçlarına giden yolu almak [için](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)bkz. 64 bit bilgisayarlarda, araçların hem 64 bit hem de 32 bit sürümleri kullanılabilir. Profil oluşturucu komut satırı araçlarını kullanmak için, komut istemi penceresinin PATH ortamı değişkenine araçlar yolunu eklemeniz veya komutun kendisine eklemeniz gerekir.

 Bir .NET Framework bileşeninden enstrümantasyon yöntemini kullanarak bellek verileri toplamak için, bileşenin enstrümantize edilmiş bir sürümünü ve profil oluşturma ortamı değişkenlerini başlatmayı sağlamak için [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) aracını oluşturmak için [VSInstr.exe](../profiling/vsinstr.md) aracını kullanırsınız. Daha sonra *VSPerfCmd.exe* aracını kullanarak profil oluşturucuyu başlatın.

 Enstrümantif bileşen yürütüldüğünde, bellek verileri otomatik olarak bir veri dosyasına toplanır. Profil oluşturma oturumu sırasında veri toplamayı duraklatabilir ve devam ettirebilirsiniz.

 Profil oluşturma oturumunu sona erdirmek için hedef uygulamayı kapatır ve profil oluşturucuyu açıkça kapatırsınız. Çoğu durumda, oturumun sonunda profil oluşturma ortamı değişkenlerini temizlemenizi öneririz.

## <a name="start-the-application-with-the-profiler"></a>Uygulamayı profil oluşturucuyla başlatın

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Çalışan bir .NET Framework uygulamasına profil oluşturucu eklemek için

1. Bir komut istemi penceresi açın.

2. Hedef uygulamanın enstrümanted sürümünü oluşturmak için **VSInstr** aracını kullanın.

3. .NET Framework profil oluşturma ortamı değişkenlerini başlangıç olarak karşılayın. Şunu yazın:

    **VSPerfClrEnv** {**/tracegc** &#124; **/tracegclife**}

   - **/tracegc** ve **/tracegclife** seçenekleri, yalnızca bellek ayırma verilerini toplamak veya hem bellek ayırma hem de nesne yaşam boyu verilerini toplamak için ortam değişkenlerini başlangıç olarak sunar.

       |Seçenek|Açıklama|
       |------------|-----------------|
       |**/tracegc**|Yalnızca bellek ayırma verilerinin toplanmasını sağlar.|
       |**/tracegclife**|Hem bellek ayırma hem de nesne yaşam boyu verilerinin toplanmasını sağlar.|

4. Profilciyi çalıştırın. Şunu yazın:

    **VSPerfCmd /start:trace /output:** `OutputFile` [`Options`]

   - [/start](../profiling/start.md)**:trace** seçeneği profil oluşturucuyu başlatir.

   - [/output](../profiling/output.md)**:** `OutputFile` seçeneği **/start**ile gereklidir. `OutputFile`profil oluşturma verilerinin adını ve konumunu belirtir (.* vsp*) dosyası.

     **/start:trace** seçeneği ile aşağıdaki seçeneklerden herhangi birini kullanabilirsiniz.

   | Seçenek | Açıklama |
   | - | - |
   | [/kullanıcı](../profiling/user-vsperfcmd.md) **:**[ ]`Domain`**\\**`UserName` | Profilli işlemin sahibi hesabın etki alanını ve kullanıcı adını belirtir. Bu seçenek yalnızca işlem oturum açmış kullanıcı dışında bir kullanıcı olarak çalışıyorsa gereklidir. İşlem sahibi, Windows Görev Yöneticisi'nin **İşlemler** sekmesinde Kullanıcı Adı sütununda listelenir. |
   | [/çapraz oturum](../profiling/crosssession.md) | Diğer oturumlarda işlemlerin profilini çıkarma sağlar. Uygulama farklı bir oturumda çalışıyorsa bu seçenek gereklidir. Oturum tanımlayıcısı, Windows Görev Yöneticisi'nin **İşlemler** sekmesindeki **Oturum Kimliği** sütununda listelenir. **/CS** **/ crosssession**için bir kısaltma olarak belirtilebilir. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Veri toplama duraklatılmış profil oluşturucuyu başlatmak için **/globaloff** seçeneğini **/start** komut satırına ekleyin. Profil oluşturmayı sürdürmek için **/globalon'u** kullanın. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Yalnızca **/wincounter** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 ms'dir. |
   | [/sayaç](../profiling/counter.md) **:**`Config` | Config'de belirtilen işlemci performans sayacından bilgi toplar. Sayaç bilgileri, her profil oluşturma etkinliğinde toplanan verilere eklenir. |
   | [olaylar](../profiling/events-vsperfcmd.md) **:**`Config` | Profil oluşturma sırasında toplanacak windows için olay izleme (ETW) olayı belirtir. ETW olayları ayrı bir şekilde toplanır (.* etl*) dosyası. |

5. Komut İstemi penceresinden hedef uygulamayı başlatın.

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hedef uygulama çalışırken, *VSPerfCmd.exe* seçeneklerini kullanarak dosyaya veri yazısını başlatıp durdurarak veri toplamayı denetleyebilirsiniz. Veri toplamayı denetlemek, uygulamayı başlatma veya kapatma gibi program yürütmesinin belirli bir bölümü için veri toplamanızı sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki **VSPerfCmd** seçenekleri, veri toplamayı başlayıp durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/globalon](../profiling/globalon-and-globaloff.md) [/globaloff](../profiling/globalon-and-globaloff.md)|Tüm işlemler için **(/globalon)** başlatır veya durur (**/globaloff**) veri toplama.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|İşlem Kimliği () tarafından belirtilen işlem için **(/processon)** başlatır veya`PID`(**/processoff**) veri toplamayı durdurur .|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:**`TID`|İş parçacığı kimliği ( ) tarafından belirtilen iş parçacığı için **(/threadon)**`TID`başlatır veya (**/threadoff**) veri toplamayı durdurur.|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sonlandırma
 Profil oluşturma oturumunu sona erdirmek için, enstrümantasyonlu bileşeni çalıştıran uygulamayı kapatın ve profil oluşturma veri dosyasını kapatmak için **VSPerfCmd** [/shutdown](../profiling/shutdown.md) seçeneğini arayın. **VSPerfClrEnv /off** komutu profil oluşturma ortamı değişkenlerini temizler.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdirmek için

1. Hedef uygulamayı kapatın.

2. Profilciyi kapat. Şunu yazın:

     **VSPerfCmd /kapatma**

3. (İsteğe bağlı) Profil oluşturma ortamı değişkenlerini temizleyin. Şunu yazın:

     **VSPerfCmd /kapalı**

## <a name="see-also"></a>Ayrıca bkz.
- [Profil tek başına uygulamalar](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [.NET bellek veri görünümleri](../profiling/dotnet-memory-data-views.md)
