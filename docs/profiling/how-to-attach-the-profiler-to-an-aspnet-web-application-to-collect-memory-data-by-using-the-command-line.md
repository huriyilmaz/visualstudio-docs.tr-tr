---
title: Bellek verileri toplamak için profiloluşturciyi ASP.NET uygulamasına takın
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d608f85a-41ae-4ca7-85e6-b96624dbc83c
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: f2b9ea7799656b0dd7dacd35bde62dc84aea08dd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779070"
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line"></a>Nasıl kullanılır: Komut satırını kullanarak bellek verileri toplamak için profil oluşturucuyu ASP.NET bir web uygulamasına takın
Bu makalede, profil [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oluşturucuyu bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulamasına eklemek ve .NET Framework bellek ayırmalarının sayısı ve boyutu hakkında veri toplamak için Profil Oluşturma Araçları komut satırı araçlarının nasıl kullanılacağı açıklanmaktadır. .NET Framework bellek nesnelerinin ömrü hakkında da veri toplayabilirsiniz.

> [!NOTE]
> Profil oluşturma araçlarına giden yolu almak [için](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)bkz. 64 bit bilgisayarlarda, araçların hem 64 bit hem de 32 bit sürümleri kullanılabilir. Profil oluşturucu komut satırı araçlarını kullanmak için, komut istemi penceresinin PATH ortamı değişkenine araçlar yolunu eklemeniz veya komutun kendisine eklemeniz gerekir.

 Bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulamasından performans verileri toplamak için, Web uygulamasını barındıran bilgisayardaki uygun ortam değişkenlerini başlatmak için [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) aracını kullanmanız gerekir. Daha sonra profil oluşturma için Web sunucusu yapılandırmak için bilgisayarı yeniden başlatmanız gerekir.

 Daha sonra, profil oluşturucuyu Web sitenizi barındıran [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] alt işleme eklemek için [VSPerfCmd.exe](../profiling/vsperfcmd.md) aracını kullanırsınız. Profil oluşturucu uygulamaya iliştirildiğinde, veri toplamayı duraklatabilir ve devam ettirebilirsiniz.

 Profil oluşturma oturumunu sona erdirmek için profil oluşturucuartık uygulamaya eklenmemeli ve profil oluşturucu açıkça kapatılmalıdır. Çoğu durumda, oturumun sonunda profil oluşturma ortamı değişkenlerini temizlemenizi öneririz.

## <a name="attach-the-profiler"></a>Profil oluşturucuyu takın

#### <a name="to-attach-the-profiler-to-an-aspnet-web-application"></a>ProfiloluşturcIyi ASP.NET bir web uygulamasına eklemek için

1. Bir komut istemi penceresi açın.

2. Profil oluşturma ortamı değişkenlerini başlangıç olarak önleştirin. Şunu yazın:

    **VSPerfClrEnv** {**/globalsamplegc** &#124; **/globalsamplegclife**} [**/samplelineoff**]

   - **/globalsamplegc** ve **/globalsamplegclife** seçenekleri toplanacak bellek veritürünü belirtir.

        Aşağıdaki seçeneklerden bir ve yalnızca bir tanesini belirtin.

       |Seçenek|Açıklama|
       |------------|-----------------|
       |**/globalsamplegc**|Bellek ayırma verilerinin toplanmasını etkinleştirir.|
       |**/globalsamplegclife**|Bellek ayırma verilerinin ve nesne yaşam süresi verilerinin toplanmasını etkinleştirir.|

   - Seçenek **/samplelineoff,** toplanan verilerin belirli kaynak kod satırlarına atamasını devre dışı kılabilir. Bu seçenek belirtilirse, veri işlev düzeyinde atanır.

3. Yeni ortam yapılandırmasını ayarlamak için bilgisayarı yeniden başlatın.

4. Bir komut istemi penceresi açın. Gerekirse, profilci yolu çevre değişkenini ayarlayın.

5. Profilciyi çalıştırın. Şunu yazın:

    **VSPerfCmd**  [/start](../profiling/start.md) **:örnek**  [/çıktı](../profiling/output.md) **:** `OutputFile` [`Options`]

   - **/start:örnek** seçeneği profil oluşturucuyu başlatir.

   - **/output:** `OutputFile` seçeneği **/start**ile gereklidir. `OutputFile`profil oluşturma verileri (.vsp) dosyasının adını ve konumunu belirtir.

     **/start:sample** seçeneği ile aşağıdaki seçeneklerden herhangi birini kullanabilirsiniz.

   > [!NOTE]
   > **/kullanıcı** ve **/crosssession** seçenekleri genellikle ASP.NET uygulamalar için gereklidir.

   | Seçenek | Açıklama |
   | - | - |
   | [/kullanıcı](../profiling/user-vsperfcmd.md) **:**[ ]`Domain`**\\**`UserName` | ASP.NET alt işleminin sahibi hesabın etki alanını ve kullanıcı adını belirtir. İşlem, oturum açmış kullanıcı dışında bir kullanıcı olarak çalışıyorsa, bu seçenek gereklidir. İşlem sahibi, Windows Görev Yöneticisi'nin İşlemler sekmesinde Kullanıcı Adı sütununda listelenir. |
   | [/çapraz oturum](../profiling/crosssession.md) | Diğer oturum oturumlarında işlemlerin profilini çıkarmasağlar. ASP.NET uygulaması farklı bir oturumda çalışıyorsa bu seçenek gereklidir. Oturum tanımlayıcısı, Windows Görev Yöneticisi'nin İşlemler sekmesindeki Oturum Kimliği sütununda listelenir. **/CS** **/ crosssession**için bir kısaltma olarak belirtilebilir. |
   | [/waitstart](../profiling/waitstart.md) [**:**`Interval`] | Profilcinin bir hata döndürmeden önce başlatılmasını beklemek için saniye sayısını belirtir. `Interval` Belirtilmemişse, profil oluşturucu süresiz olarak bekler. Varsayılan olarak, **/start** hemen döner. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Yalnızca **/wincounter** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 ms'dir. |
   | [/olaylar](../profiling/events-vsperfcmd.md) **:**`Config` | Profil oluşturma sırasında toplanacak windows için olay izleme (ETW) olayı belirtir. ETW olayları ayrı bir (.etl) dosyada toplanır. |

6. Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] uygulamasını tipik bir şekilde başlatın.

7. Profil oluşturucuyu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] alt işleme takın. Şunu yazın:

    **VSPerfCmd**[/ eklemek](../profiling/attach.md) `ProcName` **:**{`PID`&#124;} [ /[targetclr](../profiling/targetclr.md)**:**`Version`]  

   - İşlem kimliği, `(PID)` işlem kimliğini veya [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] iştirak işleminin işlem adını belirtir. Windows Görev Yöneticisi'nde çalışan tüm işlemlerin işlem lerini görüntüleyebilirsiniz.

   - **/targetclr:** `Version` bir uygulamada çalışma süresinin birden fazla sürümü yüklendiğinde, ortak dil çalışma zamanının (CLR) profilinin sürümünü belirtir.

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Uygulama çalışırken, **VSPerfCmd.exe** seçeneklerini kullanarak profil oluşturucu veri dosyasına veri yazısını başlatıp durdurarak veri toplamayı denetleyebilirsiniz. Veri toplamayı denetlemek, uygulamayı başlatma veya kapatma gibi program yürütmesinin belirli bir bölümü için veri toplamanızı sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki **VSPerfCmd** seçenekleri, veri toplamayı başlayıp durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Tüm işlemler için **(/globalon)** başlatır veya durur (**/globaloff**) veri toplama.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Tarafından belirtilen `PID`işlem için (**/processon)** başlatır veya durur (**/processoff**) veri toplama.|
    |**/attach:**`PID` { `ProcName`&#124;} [/detach](../profiling/detach.md)`ProcName`[**:**{`PID`&#124;: }]|**/ekle** işlem kimliği veya işlem adı tarafından belirtilen işlem için veri toplamaya başlar. **/detach,** belirli bir işlem belirtilmemişse, belirtilen işlem veya tüm işlemler için veri toplamayı durdurur.|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sonlandırma
 Profil oluşturma oturumunu sona erdirmek için profil oluşturucunun Web uygulamasından ayrılması gerekir. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Alt işlemi yeniden başlatarak veya **VSPerfCmd /detach** seçeneğini arayarak örnekleme yöntemiyle profillenmiş bir uygulamadan veri toplamayı durdurabilirsiniz. Daha sonra profil oluşturucuyu kapatmak ve profil oluşturma veri dosyasını kapatmak için **VSPerfCmd** [/shutdown](../profiling/shutdown.md) seçeneğini arayın. **VSPerfClrEnv /globaloff** komutu profil oluşturma ortamı değişkenlerini temizler, ancak bilgisayar yeniden başlatılıncaya kadar sistem yapılandırması sıfırlanmaz.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdirmek için

1. Profiloluşturucuyu hedef uygulamadan ayırmak için aşağıdaki adımlardan birini gerçekleştirin:

   - **VsPerfCmd** [/detach](../profiling/detach.md) yazın

      -veya-

   - İşçi [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] işlemini kapatın. Şunu yazın:

     **IISReset /stop**

2. Profilciyi kapat. Şunu yazın:

    **VSPerfCmd /kapatma**

3. (İsteğe bağlı) Profil oluşturma ortamı değişkenlerini temizleyin. Şunu yazın:

    **VSPerfCmd /globaloff**

4. Bilgisayarı yeniden başlatın. Gerekirse, Internet Bilgi Hizmetlerini (IIS) yeniden başlatın. Şunu yazın:

    **IISReset /başlangıç**

## <a name="see-also"></a>Ayrıca bkz.
- [Web uygulamaları ASP.NET profil](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [.NET bellek veri görünümleri](../profiling/dotnet-memory-data-views.md)
