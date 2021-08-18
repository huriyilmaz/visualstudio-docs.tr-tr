---
title: Profil oluşturma komut satırı - Statik uygulama ASP.NET, zamanlama verilerini al
description: Önceden derlenmiş bir web Visual Studio Profil Oluşturma Araçları web sitesi için ayrıntılı zamanlama verileri toplamak üzere ASP.NET komut satırı araçlarını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: b260ce68-76e6-4c3b-8062-3c00bd5cf7b8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: dbdd37622a4895e1ab1884663426a6ceec5eef95526b42556294ede289c141b4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121426917"
---
# <a name="how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line"></a>Nasıl kullanılır: Web uygulamasında statik olarak derlenmiş ASP.NET ve komut satırı kullanarak profil oluşturma ile ayrıntılı zamanlama verileri toplama
Bu makalede, önceden Profil Oluşturma Araçları bir web bileşenini veya web sitesini takip etmek ve ayrıntılı zamanlama verileri toplamak için komut satırı araçlarının nasıl [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] kullanımı açıklanmıştır.

> [!NOTE]
> Profil oluşturma araçlarının yolunu almak için [bkz. Komut satırı araçlarının yolunu belirtme.](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md) 64 bit bilgisayarlarda, araçların hem 64 bit hem de 32 bit sürümleri kullanılabilir. Profil oluşturma komut satırı araçlarını kullanmak için, araç yolunu Komut İstemi penceresinin PATH ortam değişkenine eklemeniz veya komutun kendisine eklemeniz gerekir.
>
> Profil oluşturma çalıştırması için katman etkileşim verileri eklemek için komut satırı profil oluşturma araçlarıyla belirli yordamlar gerekir. Bkz. [Katman etkileşim verilerini toplama.](../profiling/adding-tier-interaction-data-from-the-command-line.md)

 Bir Web bileşeninden ölçümleme yöntemini kullanarak ayrıntılı zamanlama verileri toplamak içinVSInstr.exearacını kullanarak bileşenin [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] bir instrumented sürümünü oluşturabilirsiniz. [](../profiling/vsinstr.md) Bileşeni barındıran bilgisayarda, bileşenin noninstrumented sürümünü, araçlı sürümle değiştirirsiniz. Ardından [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) aracını kullanarak genel profil oluşturma ortam değişkenlerini başlatacak ve konak bilgisayarı yeniden başlatabilirsiniz. Ardından profilleyiciyi başlatabilirsiniz.

 Ölçüme alınan bileşen yürütülürken zamanlama verileri otomatik olarak bir veri dosyasına toplanır. Profil oluşturma oturumu sırasında veri toplamayı duraklatabilir ve sürdürebilirsiniz.

 Profil oluşturma oturumunu sona erersiniz, bileşeni barındıran çalışan işlemini kapatır ve ardından [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] profilleyiciyi açıkça kapatır. Çoğu durumda, bir oturumun sonunda profil oluşturma ortam değişkenlerini temizlemenizi öneririz.

## <a name="start-to-profile"></a>Profil oluşturmaya başlama

#### <a name="to-instrument-an-aspnet-web-component-and-start-profiling"></a>Bir web bileşenini ASP.NET ve profil oluşturmayı başlatmak için

1. Bir komut istemi penceresi açın.

2. Hedef **uygulamanın izlenilen** bir sürümünü oluşturmak için VSInstr aracını kullanın. Gerekirse, konak bilgisayarda uygulama ikililerini ASP.NET ikili dosyalar ile değiştirin.

3. .NET profil oluşturma ortam değişkenlerini başlatma. Komut İstemi penceresine şunları yazın:

    **VSPerfClrEnv /globaltraceon**

4. Bilgisayarı yeniden başlatın.

5. Bir komut istemi penceresi açın. Gerekirse profil oluşturma araçları yolunu ayarlayın.

6. Profilleyiciyi başlatma. Şunu yazın:

    **VSPerfCmd /start:trace /output:** `OutputFile` [`Options`]

   - [/start](../profiling/start.md)**:trace** seçeneği profilleyiciyi başlatıyor.

   - [/output](../profiling/output.md)**: seçeneği** / start ile `OutputFile` **gereklidir.** `OutputFile` profil oluşturma verileri (.vsp) dosyasının adını ve konumunu belirtir.

     **/start:trace** seçeneğiyle aşağıdaki seçeneklerden herhangi birini kullanabilirsiniz.

   > [!NOTE]
   > /user **ve** **/crosssession** seçenekleri genellikle uygulama ASP.NET gereklidir.

   | Seçenek | Açıklama |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Çalışan işleminin sahibi olan hesabın etki alanını ve kullanıcı ASP.NET belirtir. İşlem oturum açmış kullanıcıdan farklı bir kullanıcı olarak çalışıyorsa bu seçenek gereklidir. İşlem sahibi, Görev **Yöneticisi'nin** İşlemler **sekmesindeki** Kullanıcı Adı Windows listelenir. |
   | [/crosssession](../profiling/crosssession.md) | Diğer oturum açma oturumlarında işlemlerin profil oluşturmasını sağlar. Uygulama farklı bir oturumda ASP.NET bu seçenek gereklidir. Oturum tanımlayıcısı, Görev Yöneticisi'nin İşlemler **sekmesindeki** Oturum Kimliği Windows listelenir. **/CS,** **/crosssession için bir kısaltma olarak belirtilebilir.** |
   | [/wincounter:](../profiling/wincounter.md) `WinCounterPath` | Profil oluşturma Windows toplanacak bir performans sayacı belirtir. |
   | [/automark:](../profiling/automark.md) `Interval` | Yalnızca **/wincounter ile** kullanın. Performans sayacı toplama olayları arasındaki milisaniye Windows sayısını belirtir. Varsayılan değer 500 ms'tir. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Profil oluşturma sırasında toplanacak Windows (ETW) olayı için bir Olay İzleme belirtir. ETW olayları ayrı bir () içinde toplanır.*etl*) dosyasını seçin. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Profilleyiciyi veri koleksiyonu duraklatılmış olarak başlatmak için **/start komut** satırına **/globaloff** seçeneğini ekleyin. Profil **oluşturmayı devam ettiren /globalon** kullanın. |

7. Araçlı bileşeni içeren Web sitesini açın.

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hedef uygulama çalıştıryken, veri toplama seçeneklerini kullanarak dosyada veri yazmayı başlatarak ve *durdurarak veriVSPerfCmd.exeyapabilirsiniz.* Veri toplamayı denetlemek, uygulamayı başlatma veya kapatma gibi program yürütmenin belirli bir bölümü için veri toplamaya olanak sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki seçenek çiftleri veri toplamayı başlat ve durdur. Her seçeneği ayrı bir komut satırı üzerinde belirtin. Veri toplamayı birden çok kez açabilirsiniz ve kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Tüm işlemler **için veri toplamayı** başlatır ( /globalon ) veya durdurur (**/globaloff).**|
    |[/processon:](../profiling/processon-and-processoff.md)  `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|İşlem kimliği ( ) tarafından belirtilen işlem için veri toplamayı (**/processon**) veya durdurur ( `PID` ).|
    |[/threadon:](../profiling/threadon-and-threadoff.md)  `TID` [/threadoff:](../profiling/threadon-and-threadoff.md) `TID`|İş parçacığı kimliği ( ) tarafından belirtilen iş parçacığı için veri toplamayı (**/threadon**) veya durdurur ( `TID` ).|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sona er
 Profil oluşturma oturumunu sona ererken Web uygulamasını kapatın ve [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Internet Information Services **(IIS) IISReset** komutunu kullanarak [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] çalışan işlemini kapatın. Profilleyiciyi kapatmak ve profil oluşturma veri dosyasını kapatmak için **VSPerfCmd** [/shutdown](../profiling/shutdown.md) seçeneğini arayın.

 **VSPerfClrEnv /globaloff** komutu profil oluşturma ortam değişkenlerini temizler. Yeni ortam ayarlarının uygulanması için bilgisayarı yeniden başlatmanız gerekir.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdir

1. Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] uygulamasını kapatın.

2. Çalışan [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] işlemini kapatın. Şunu yazın:

    **IISReset /stop**

3. Profilleyiciyi kapatın. Şunu yazın:

    **VSPerfCmd /shutdown**

4. (İsteğe bağlı). Profil oluşturma ortam değişkenlerini temizleme. Şunu yazın:

    **VSPerfCmd /globaloff**

5. Bilgisayarı yeniden başlatın.

## <a name="see-also"></a>Ayrıca bkz.
- [Web ASP.NET profil oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Ölçüm izleme yöntemi veri görünümleri](../profiling/instrumentation-method-data-views.md)
