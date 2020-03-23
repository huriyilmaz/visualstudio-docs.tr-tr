---
title: 'Profiler komut satırı: Enstrüman statik ASP.NET uygulaması, zamanlama verileri almak'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b260ce68-76e6-4c3b-8062-3c00bd5cf7b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 7d743dd854bd11449161c47cc896d0735849e1dd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778862"
---
# <a name="how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line"></a>Nasıl yapılır: Web uygulamasına statik olarak derlenmiş bir ASP.NET ve komut satırını kullanarak profiloluşturucu ile ayrıntılı zamanlama verileri toplamak
Bu makalede, önceden [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] derlenmiş bir web bileşenini veya [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] web sitesini enstrümanlamak ve ayrıntılı zamanlama verileri toplamak için Profil Oluşturma Araçları komut satırı araçlarının nasıl kullanılacağı açıklanmaktadır.

> [!NOTE]
> Profil oluşturma araçlarına giden yolu almak [için](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)bkz. 64 bit bilgisayarlarda, araçların hem 64 bit hem de 32 bit sürümleri kullanılabilir. Profil oluşturucu komut satırı araçlarını kullanmak için, komut istemi penceresinin PATH ortamı değişkenine araçlar yolunu eklemeniz veya komutun kendisine eklemeniz gerekir.
>
> Profil oluşturma çalışmasına katman etkileşim verileri eklemek, komut satırı profil oluşturma araçlarıyla belirli yordamlar gerektirir. Bkz. [Katman etkileşim verilerini toplama.](../profiling/adding-tier-interaction-data-from-the-command-line.md)

 Enstrümantasyon yöntemini [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] kullanarak bir Web bileşeninden ayrıntılı zamanlama verileri toplamak için, bileşenin enstrümantasyonlu bir sürümünü oluşturmak için [VSInstr.exe](../profiling/vsinstr.md) aracını kullanırsınız. Bileşeni barındıran bilgisayarda, bileşenin enstrümantine olmayan sürümünü enstrümantedilmiş sürümle değiştirirsiniz. Ardından, küresel profil oluşturma ortamı değişkenlerini başlatmak ve ana bilgisayarı yeniden başlatmak için [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) aracını kullanırsınız. Daha sonra profilci başlatın.

 Enstrümantif bileşen yürütüldüğünde, zamanlama verileri otomatik olarak bir veri dosyasına toplanır. Profil oluşturma oturumu sırasında veri toplamayı duraklatabilir ve devam ettirebilirsiniz.

 Profil oluşturma oturumunu sona erdirmek [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] için, bileşeni barındıran alt işlemi kapatır ve ardından profil oluşturucuyu açıkça kapatırsınız. Çoğu durumda, oturumun sonunda profil oluşturma ortamı değişkenlerini temizlemenizi öneririz.

## <a name="start-to-profile"></a>Profil başlatma

#### <a name="to-instrument-an-aspnet-web-component-and-start-profiling"></a>ASP.NET bir web bileşenini enstrüman ve profil oluşturma başlatmak için

1. Bir komut istemi penceresi açın.

2. Hedef uygulamanın enstrümanted sürümünü oluşturmak için **VSInstr** aracını kullanın. Gerekirse, ASP.NET ana bilgisayardaki uygulama ikililerini enstrümantifleştirilmiş ikililerle değiştirin.

3. .NET profil oluşturma ortamı değişkenlerini başlangıç olarak gün,. Komut İstemi penceresinde, yazın:

    **VSPerfClrEnv /globaltraceon**

4. Bilgisayarı yeniden başlatın.

5. Bir komut istemi penceresi açın. Gerekirse, profil oluşturma araçları yolunu ayarlayın.

6. Profilciyi çalıştırın. Şunu yazın:

    **VSPerfCmd /start:trace /output:** `OutputFile` [`Options`]

   - [/start](../profiling/start.md)**:trace** seçeneği profil oluşturucuyu başlatir.

   - [/output](../profiling/output.md)**:** `OutputFile` seçeneği **/start**ile gereklidir. `OutputFile`profil oluşturma verileri (.vsp) dosyasının adını ve konumunu belirtir.

     **/start:trace** seçeneği ile aşağıdaki seçeneklerden herhangi birini kullanabilirsiniz.

   > [!NOTE]
   > **/kullanıcı** ve **/crosssession** seçenekleri genellikle ASP.NET uygulamalar için gereklidir.

   | Seçenek | Açıklama |
   | - | - |
   | [/kullanıcı](../profiling/user-vsperfcmd.md) **:**[ ]`Domain`**\\**`UserName` | ASP.NET alt işleminin sahibi hesabın etki alanını ve kullanıcı adını belirtir. İşlem, oturum açmış kullanıcı dışında bir kullanıcı olarak çalışıyorsa, bu seçenek gereklidir. İşlem sahibi, Windows Görev Yöneticisi'nin **İşlemler** sekmesinde **Kullanıcı Adı** sütununda listelenir. |
   | [/çapraz oturum](../profiling/crosssession.md) | Diğer oturum oturumlarında işlemlerin profilini çıkarmasağlar. ASP.NET uygulaması farklı bir oturumda çalışıyorsa bu seçenek gereklidir. Oturum tanımlayıcısı, Windows Görev Yöneticisi'nin **İşlemler** sekmesindeki Oturum Kimliği sütununda listelenir. **/CS** **/ crosssession**için bir kısaltma olarak belirtilebilir. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Yalnızca **/wincounter** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 ms'dir. |
   | [/olaylar](../profiling/events-vsperfcmd.md) **:**`Config` | Profil oluşturma sırasında toplanacak windows için olay izleme (ETW) olayı belirtir. ETW olayları ayrı bir şekilde toplanır (.* etl*) dosyası. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Veri toplama duraklatılmış profil oluşturucuyu başlatmak için **/globaloff** seçeneğini **/start** komut satırına ekleyin. Profil oluşturmayı sürdürmek için **/globalon'u** kullanın. |

7. Enstrümantinleştirilmiş bileşeni içeren Web sitesini açın.

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hedef uygulama çalışırken, *VSPerfCmd.exe* seçeneklerini kullanarak dosyaya veri yazısını başlatıp durdurarak veri toplamayı denetleyebilirsiniz. Veri toplamayı denetlemek, uygulamayı başlatma veya kapatma gibi program yürütmesinin belirli bir bölümü için veri toplamanızı sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki seçenek çiftleri veri toplamayı başlayıp durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Tüm işlemler için **(/globalon)** başlatır veya durur (**/globaloff**) veri toplama.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|İşlem Kimliği tarafından belirtilen işlem için **(/processon)** başlatır veya **(/processoff)** veri toplamayı durdurur (`PID`).|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:**`TID`|İş parçacığı kimliği ( ))'nin belirttiği iş parçacığı için (**/threadon)** veya durur (**/threadoff**) veri toplamayı başlatır (`TID`).|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sonlandırma
 Profil oluşturma oturumunu sona [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] erdirmek için Web uygulamasını kapatın ve ardından alt işlemi kapatmak için [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Internet Information Services **(IIS) IISReset** komutunu kullanın. Profil oluşturucuyu kapatmak ve profil oluşturma veri dosyasını kapatmak için **VSPerfCmd** [/shutdown](../profiling/shutdown.md) seçeneğini arayın.

 **VSPerfClrEnv /globaloff** komutu profil oluşturma ortamı değişkenlerini temizler. Uygulanacak yeni ortam ayarları için bilgisayarı yeniden başlatmanız gerekir.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdirmek için

1. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulamasını kapatın.

2. İşçi [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] işlemini kapatın. Şunu yazın:

    **IISReset /stop**

3. Profilciyi kapat. Şunu yazın:

    **VSPerfCmd /kapatma**

4. (İsteğe bağlı). Profil oluşturma ortamı değişkenlerini temizleyin. Şunu yazın:

    **VSPerfCmd /globaloff**

5. Bilgisayarı yeniden başlatın.

## <a name="see-also"></a>Ayrıca bkz.
- [Web uygulamaları ASP.NET profil](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Enstrümantasyon yöntemi veri görünümleri](../profiling/instrumentation-method-data-views.md)
