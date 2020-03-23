---
title: 'Profiler komut satırı: Enstrüman dinamik ASP.NET uygulaması, zamanlama verileri almak'
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: d8270c9948efe5f9c972f2e4f0eccb035c793953
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74775463"
---
# <a name="how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line"></a>Nasıl yapılır: Dinamik olarak derlenmiş bir web uygulaması ASP.NET ve komut satırını kullanarak profiloluşturucu ile ayrıntılı zamanlama verileri toplamak

Bu makalede, enstrümantasyon profilleme yöntemini kullanarak dinamik olarak derlenmiş bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] uygulama için ayrıntılı zamanlama verileri toplamak için Visual Studio Profil Oluşturma Araçları komut satırı araçlarının nasıl kullanılacağı açıklanmaktadır.

> [!NOTE]
> Profil oluşturma araçlarına giden yolu almak [için](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)bkz. 64 bit bilgisayarlarda, araçların hem 64 bit hem de 32 bit sürümleri kullanılabilir. Profil oluşturucu komut satırı araçlarını kullanmak için, komut istemi penceresinin PATH ortamı değişkenine araçlar yolunu eklemeniz veya komutun kendisine eklemeniz gerekir.

Bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] web uygulamasından performans verileri toplamak için, [vsinstr.exe](../profiling/vsinstr.md) aracının dinamik olarak derlenen uygulama dosyalarını enstrümanla masını sağlamak için hedef uygulamanın *web.config* dosyasını değiştirirsiniz. Daha sonra profil oluşturmayı etkinleştirmek ve bilgisayarı yeniden başlatmak için web sunucusundaki uygun ortam değişkenlerini ayarlamak için [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) aracını kullanırsınız.

Profil oluşturucuyu çalıştırın ve hedef uygulamayı çalıştırın. Profil oluşturucu uygulamaya bağlı yken, veri toplamayı duraklatabilir ve devam ettirebilirsiniz. Profil oluşturmayı bitirdiğinizde, uygulamayı kapatın, Internet Information Services (IIS) alt işlemini kapatın ve profil oluşturucuyu kapatın. Profil oluşturma çalışmanızı tamamladığınızda, *web.config* dosyasını ve Web sunucusunu özgün durumlarına geri yükleyin.

## <a name="configure-the-aspnet-web-application-and-the-web-server"></a>ASP.NET web uygulamasını ve web sunucusunu yapılandırma

1. Hedef uygulamanın *web.config* dosyasını değiştirin. [Bkz. Nasıl Yapılır: web.config dosyalarını enstrüman ve web uygulamaları ASP.NET dinamik olarak derlenmiş profille değiştirin.](../profiling/how-to-modify-web-config-files-to-instrument-dynamically-compiled-aspnet-apps.md)

2. Bir komut istemi penceresi açın.

3. Profil oluşturma ortamı değişkenlerini başlangıç olarak önleştirin. Şunu yazın:

     **VSPerfClrEnv /globaltraceon**

    - **/globaltraceon** enstrümantasyon yöntemini kullanarak profil oluşturmayı sağlar.

4. Bilgisayarı yeniden başlatın.

## <a name="run-the-profiling-session"></a>Profil oluşturma oturumunu çalıştırma

1. Bir komut istemi penceresi açın.

2. Profilciyi çalıştırın. Şunu yazın:

     **VSPerfCmd**  [/start](../profiling/start.md) **:trace**  [/output](../profiling/output.md) **:** `OutputFile` [`Options`]

   - **/start:trace** seçeneği profil oluşturucuyu başlatir.

   - **/output:** `OutputFile` seçeneği **/start**ile gereklidir. `OutputFile`profil oluşturma verilerinin adını ve konumunu belirtir (.* vsp*) dosyası.

     **/start:trace** seçeneği ile aşağıdaki seçeneklerden herhangi birini kullanabilirsiniz.

     > [!NOTE]
     > **/kullanıcı** ve **/crosssession** seçenekleri genellikle ASP.NET uygulamalar için gereklidir.

     | Seçenek | Açıklama |
     | - | - |
     | [/kullanıcı](../profiling/user-vsperfcmd.md) **:**[ ]`Domain`**\\**`UserName` | ASP.NET alt işleminin sahibi hesabın etki alanını ve kullanıcı adını belirtir. İşlem, oturum açmış kullanıcı dışında bir kullanıcı olarak çalışıyorsa, bu seçenek gereklidir. İşlem sahibi, Windows Görev Yöneticisi'nin **İşlemler** sekmesinde **Kullanıcı Adı** sütununda listelenir. |
     | [/çapraz oturum](../profiling/crosssession.md) | Diğer oturum oturumlarında işlemlerin profilini çıkarmasağlar. ASP.NET uygulaması farklı bir oturumda çalışıyorsa bu seçenek gereklidir. Oturum tanımlayıcısı, Windows Görev Yöneticisi'nin **İşlemler** sekmesindeki **Oturum Kimliği** sütununda listelenir. **/CS** **/ crosssession**için bir kısaltma olarak belirtilebilir. |
     | [/globaloff](../profiling/globalon-and-globaloff.md) | Veri toplama duraklatılmış profil oluşturucuyu başlatır. Profil oluşturmayı sürdürmek için [/globalon'u](../profiling/globalon-and-globaloff.md) kullanın. |
     | [/sayaç](../profiling/counter.md) **:**`Config` | 'de `Config`belirtilen işlemci performans sayacından bilgi toplar. Sayaç bilgileri, her profil oluşturma etkinliğinde toplanan verilere eklenir. |
     | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir. |
     | [/automark](../profiling/automark.md) **:**`Interval` | Yalnızca **/wincounter** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 ms'dir. |
     | [/olaylar](../profiling/events-vsperfcmd.md) **:**`Config` | Profil oluşturma sırasında toplanacak windows için olay izleme (ETW) olayı belirtir. ETW olayları ayrı bir şekilde toplanır (.* etl*) dosyası. |

3. Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] uygulamasını tipik bir şekilde başlatın.

## <a name="control-data-collection"></a>Veri toplamayı denetleme

Hedef uygulama çalışırken, *VSPerfCmd.exe* seçeneklerini kullanarak profil oluşturucu veri dosyasına veri yazısını başlatıp durdurarak veri toplamayı denetleyebilirsiniz. Veri toplamayı denetlemek, uygulamayı başlatma veya kapatma gibi program yürütmesinin belirli bir bölümü için veri toplamanızı sağlar.

- Aşağıdaki seçenek çiftleri veri toplamayı başlayıp durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Tüm işlemler için **(/globalon)** başlatır veya durur (**/globaloff**) veri toplama.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|İşlem Kimliği tarafından belirtilen işlem için **(/processon)** başlatır veya **(/processoff)** veri toplamayı durdurur (`PID`).|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:**`TID`|İş parçacığı kimliği ( ))'nin belirttiği iş parçacığı için (**/threadon)** veya durur (**/threadoff**) veri toplamayı başlatır (`TID`).|

- Veri dosyasına profil işareti eklemek için **VSPerfCmd.exe**[/mark](../profiling/mark.md) seçeneğini de kullanabilirsiniz. **/işareti** komutu bir tanımlayıcı, bir zaman damgası ve isteğe bağlı kullanıcı tanımlı metin dizesi ekler. Markalar, profil oluşturucu raporlarında ve veri görünümlerinde verileri filtrelemek için kullanılabilir.

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sonlandırma

Profil oluşturma oturumunu sona erdirmek [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] için hedef web uygulamasını kapatın, profilli işlemi durdurmak için IIS'yi sıfırlayın ve profil oluşturucuyu kapatın.

1. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulamasını kapatın.

2. Internet [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Bilgi Hizmetlerini (IIS) sıfırlayarak alt işlemi kapatın. Şunu yazın:

     **IISReset /stop**

3. Profilciyi kapat. Şunu yazın:

     **VSPerfCmd**  [/kapatma](../profiling/shutdown.md)

4. IIS’yi yeniden başlatın. Şunu yazın:

     **IISReset /başlangıç**

## <a name="restore-the-application-and-computer-configuration"></a>Uygulama ve bilgisayar yapılandırmasını geri yükleme

Tüm profil oluşturmayı tamamladığınızda, *web.config* dosyasını değiştirin, profil oluşturma ortamı değişkenlerini temizleyin ve uygulamayı ve sunucuyu profil oluşturmadan önce içinde oldukları durumlara geri yüklemek için bilgisayarı yeniden başlatın.

1. *web.config* dosyasını özgün dosyanın bir kopyasıyla değiştirin.

2. Profil oluşturma ortamı değişkenlerini temizleyin. Şunu yazın:

     **VSPerfCmd /globaloff**

3. Bilgisayarı yeniden başlatın.

## <a name="see-also"></a>Ayrıca bkz.

[Profil ASP.NET web uygulamaları](../profiling/command-line-profiling-of-aspnet-web-applications.md)
[Enstrümantasyon yöntemi veri görünümleri](../profiling/instrumentation-method-data-views.md)
