---
title: 'Profiler komut satırı: Enstrüman dinamik ASP.NET uygulaması, bellek verileri almak'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2cdd9903-39db-47e8-93dd-5e6a21bc3435
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 3378a45ebace942bb8696f2f67962365b5f57796
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778888"
---
# <a name="how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line"></a>Nasıl yapılır: Dinamik olarak derlenmiş bir web uygulaması ASP.NET ve profiler komut satırını kullanarak bellek verilerini toplamak
Bu konu, enstrümantasyon profilleme yöntemini kullanarak dinamik olarak derlenmiş [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] bir web uygulaması için ayrıntılı .NET bellek ayırma ve nesne yaşam boyu verilerini toplamak için Profil Oluşturma Araçları komut satırı araçlarının nasıl kullanılacağını açıklar.

> [!NOTE]
> Profil oluşturma araçlarına giden yolu almak [için](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)bkz. 64 bit bilgisayarlarda, araçların hem 64 bit hem de 32 bit sürümleri kullanılabilir. Profil oluşturucu komut satırı araçlarını kullanmak için, komut istemi penceresinin PATH ortamı değişkenine araçlar yolunu eklemeniz veya komutun kendisine eklemeniz gerekir.

 Bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] web uygulamasından performans verileri toplamak için, [vsinstr.exe](../profiling/vsinstr.md) aracının dinamik olarak derlenen uygulama dosyalarını enstrümanla masını sağlamak için hedef uygulamanın *web.config* dosyasını değiştirirsiniz. Daha [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] sonra, Web uygulamasını barındıran sunucuyu yapılandırmak ve uygun ortam değişkenlerini ayarlayarak .NET bellek profilini etkinleştirmek ve bilgisayarı yeniden başlatmak için [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) aracını kullanırsınız.

 Veri toplamak için profil oluşturcayı başlatın ve hedef uygulamayı çalıştırın. Profil oluşturucu uygulamaya bağlı yken, veri toplamayı duraklatabilir ve devam ettirebilirsiniz. Uygun verileri topladığınızda, uygulamayı kapatın, Internet Information Services (IIS) alt işlemini kapatın ve profil oluşturucuyu kapatın.

 Profil oluşturma çalışmanızı tamamladığınızda, *web.config* dosyasını ve web sunucusunu özgün durumlarına geri yükleyin.

## <a name="configure-the-aspnet-web-application-and-the-web-server"></a>ASP.NET web uygulamasını ve web sunucusunu yapılandırma

#### <a name="to-configure-the-aspnet-web-application-and-the-web-server"></a>ASP.NET web uygulamasını ve web sunucusunu yapılandırmak için

1. Hedef uygulamanın *web.config* dosyasını değiştirin. [Bkz. Nasıl Yapılır: web.config dosyalarını enstrüman ve web uygulamaları ASP.NET dinamik olarak derlenmiş profille değiştirin.](../profiling/how-to-modify-web-config-files-to-instrument-dynamically-compiled-aspnet-apps.md)

2. Web uygulamasını barındıran bilgisayarda bir komut istemi penceresi açın.

3. Profil oluşturma ortamı değişkenlerini başlangıç olarak önleştirin. Şunu yazın:

     **VSPerfClrEnv /globaltracegc**

     -veya-

     **VSPerfClrEnv /globaltracegclife**

    - **/globaltracegc** bellek ayırma verilerinin toplanmasını sağlar.

    - **/globaltracegclife** bellek ayırma verilerinin ve nesne yaşam boyu verilerinin toplanmasını sağlar.

4. Bilgisayarı yeniden başlatın.

## <a name="run-the-profiling-session"></a>Profil oluşturma oturumunu çalıştırma

#### <a name="to-profile-the-aspnet-web-application"></a>ASP.NET web uygulamasının profilini çıkarmak için

1. Profilciyi çalıştırın. Şunu yazın:

    **VSPerfCmd** [/start](../profiling/start.md) **:trace** [/output](../profiling/output.md) **:** `OutputFile` [`Options`]

   - **/start:trace** seçeneği profil oluşturucuyu başlatir.

   - **/output:** `OutputFile` seçeneği **/start**ile gereklidir. `OutputFile`profil oluşturma verilerinin adını ve konumunu belirtir (.* vsp*) dosyası.

     **/start:trace** seçeneği ile aşağıdaki seçeneklerden herhangi birini kullanabilirsiniz.

   > [!NOTE]
   > **/kullanıcı** ve **/crosssession** seçenekleri genellikle ASP.NET uygulamalar için gereklidir.

   | Seçenek | Açıklama |
   | - | - |
   | [/kullanıcı](../profiling/user-vsperfcmd.md) **:**[ ]`Domain`**\\**`UserName` | [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] İşçi işleminin sahibi hesabın isteğe bağlı etki alanını ve kullanıcı adını belirtir. İşlem, oturum açmış kullanıcı dışında bir kullanıcı olarak çalışıyorsa, bu seçenek gereklidir. Ad, Windows Görev Yöneticisi'nin **İşlemler** sekmesinde **Kullanıcı Adı** sütununda listelenir. |
   | [/çapraz oturum](../profiling/crosssession.md) | Diğer oturumlarda işlemlerin profilini çıkarma sağlar. Uygulama farklı bir oturumda çalışıyorsa bu seçenek gereklidir. Oturum kimliği, Windows Görev Yöneticisi'nin **İşlemler** sekmesindeki **Oturum Kimliği** sütununda listelenir. **/CS** **/ crosssession**için bir kısaltma olarak belirtilebilir. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Veri toplama duraklatılmış profil oluşturucuyu başlatır. Profil oluşturmayı sürdürmek için [/globalon'u](../profiling/globalon-and-globaloff.md) kullanın. |
   | [/sayaç](../profiling/counter.md) **:**`Config` | 'de `Config`belirtilen işlemci performans sayacından bilgi toplar. Sayaç bilgileri, her profil oluşturma etkinliğinde toplanan verilere eklenir. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Yalnızca **/wincounter** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 ms'dir. |
   | [/olaylar](../profiling/events-vsperfcmd.md) **:**`Config` | Profil oluşturma sırasında toplanacak windows için olay izleme (ETW) olayı belirtir. ETW olayları ayrı bir şekilde toplanır (.* etl*) dosyası. |

2. Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] uygulamasını tipik bir şekilde başlatın.

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hedef uygulama çalışırken, *VSPerfCmd.exe* seçeneklerini kullanarak profil oluşturucu veri dosyasına veri yazısını başlatıp durdurarak veri toplamayı denetleyebilirsiniz. Veri toplamayı denetlemek, uygulamayı başlatma veya kapatma gibi program yürütmesinin belirli bir bölümü için veri toplamanızı sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki seçenek çiftleri veri toplamayı başlayıp durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Tüm işlemler için **(/globalon)** başlatır veya durur (**/globaloff**) veri toplama.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|İşlem Kimliği tarafından belirtilen işlem için **(/processon)** başlatır veya **(/processoff)** veri toplamayı durdurur (`PID`).|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:**`TID`|İş parçacığı kimliği ( ))'nin belirttiği iş parçacığı için (**/threadon)** veya durur (**/threadoff**) veri toplamayı başlatır (`TID`).|

- Veri dosyasına profil işareti eklemek için **VSPerfCmd.exe**[/mark](../profiling/mark.md) seçeneğini de kullanabilirsiniz. **/işareti** komutu bir tanımlayıcı, bir zaman damgası ve isteğe bağlı kullanıcı tanımlı metin dizesi ekler. Markalar, profil oluşturucu raporlarında ve veri görünümlerinde verileri filtrelemek için kullanılabilir.

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sonlandırma
 Profil oluşturma oturumunu sona erdirmek [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] için hedef web uygulamasını kapatın, profilli işlemi durdurmak için Internet Information Services'ı (IIS) durdurun ve profil oluşturucuyu kapatın. Sonra IIS'yi yeniden başlatın.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdirmek için

1. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulamasını kapatın.

2. Internet [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Bilgi Hizmetlerini (IIS) sıfırlayarak alt işlemi kapatın. Şunu yazın:

    **IISReset /stop**

3. Profilciyi kapat. Şunu yazın:

    **VSPerfCmd** [/kapatma](../profiling/shutdown.md)

4. IIS’yi yeniden başlatın. Şunu yazın:

    **IISReset /başlangıç**

## <a name="restore-the-application-and-computer-configuration"></a>Uygulama ve bilgisayar yapılandırmasını geri yükleme
 Tüm profil oluşturmayı tamamladığınızda, *web.config* dosyasını değiştirin, profil oluşturma ortamı değişkenlerini temizleyin [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ve sunucuyu ve uygulamayı özgün durumlarına geri yüklemek için bilgisayarı yeniden başlatın.

#### <a name="to-restore-the-application-and-computer-configuration"></a>Uygulama ve bilgisayar yapılandırmasını geri yüklemek için

1. *web.config* dosyasını özgün dosyanın bir kopyasıyla değiştirin.

2. (İsteğe bağlı). Profil oluşturma ortamı değişkenlerini temizleyin. Şunu yazın:

     **VSPerfCmd /globaloff**

3. Bilgisayarı yeniden başlatın.

## <a name="see-also"></a>Ayrıca bkz.
- [Web uygulamaları ASP.NET profil](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [.NET bellek veri görünümleri](../profiling/dotnet-memory-data-views.md)
