---
title: Profil oluşturma komut satırı - .NET hizmetini takip, bellek verilerini al
description: Visual Studio Profil Oluşturma Araçları hizmeti için bellek ayırma ve nesne yaşam süresi verilerini toplamak üzere .NET Framework öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 2fa072fc-05fe-4420-99c0-51d2ea3ac4ce
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 60ad31c91123f3226227920e08c5194136cfe09ff774a045e1721b2091c527a1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121231190"
---
# <a name="how-to-instrument-a-net-framework-service-and-collect-memory-data-by-using-the-profiler-command-line"></a>Nasıl kullanılır: Profil .NET Framework komut satırı kullanarak bir hizmette veri toplamayı ve bellek verilerini toplama

Bu makalede, bir Profil Oluşturma Araçları hizmetini Profil Oluşturma Araçları bellek kullanım verilerini toplamak için .NET Framework komut satırı [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] araçlarının nasıl kullanımı açıklanmıştır. Bellek ayırma verilerini toplayabilirsiniz veya hem bellek ayırma hem de nesne yaşam süresi verilerini toplayabilirsiniz.

> [!NOTE]
> Windows 8 ve Windows Server 2012 profil oluşturma Visual Studio bu platformlarda veri toplama şeklinde önemli değişiklikler gerektirmektedir. UWP uygulamaları için yeni koleksiyon teknikleri de gerekir. Uygulama [ve uygulama Windows 8 performans Windows Server 2012 bakın.](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)
>
> [!NOTE]
> Bilgisayar başlatıldıktan sonra hizmet yeniden başlatılamazsa, işletim sistemi başlatıldığında başlayan bir hizmet gibi, bir hizmetin profilini, ölçümleme yöntemiyle profillerini oluşturmazsınız.
>
> Profil oluşturma araçlarının yolunu almak için [bkz. Komut satırı araçlarının yolunu belirtme.](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md) 64 bit bilgisayarlarda, araçların hem 64 bit hem de 32 bit sürümleri kullanılabilir. Profil oluşturma komut satırı araçlarını kullanmak için, araç yolunu Komut İstemi penceresinin PATH ortam değişkenine eklemeniz veya komutun kendisine eklemeniz gerekir.

## <a name="start-the-profiling-session"></a>Profil oluşturma oturumunu başlatma
 .NET Framework hizmetlerinden performans verileri toplamak için [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) aracını kullanarak uygun ortam değişkenlerini ve [VSInstr.exe](../profiling/vsinstr.md) aracını başlatarak hizmet ikili dosyasının bir araç kopyasını oluşturursınız.

 Hizmeti barındıran bilgisayarın profil oluşturma için yapılandırılması için yeniden başlatılması gerekir. Ayrıca hizmeti Service Control Manager'dan el ile de başlatmanız gerekir. Ardından profil oluşturma hizmetini ve ardından .NET Framework başlatabilirsiniz.

 Ölçüme alınan bileşen yürütülürken, bellek verileri otomatik olarak bir veri dosyasına toplanır. Profil oluşturma oturumu sırasında veri toplamayı duraklatabilir ve sürdürebilirsiniz.

 Profil oluşturma oturumunu sona ererken hizmeti kapatır ve profilleyiciyi açıkça kapatırsiniz. Çoğu durumda, bir oturumun sonunda profil oluşturma ortam değişkenlerini temizlemenizi öneririz.

#### <a name="to-begin-profiling-a-net-framework-service"></a>Bir hizmet profili .NET Framework için

1. Bir komut istemi penceresi açın.

2. Hizmet ikili sürümünün bir araçlı sürümünü oluşturmak için **VSInstr** aracını kullanın.

3. Özgün ikili dosyanın yerini araçlı sürümle değiştirmek için Hizmet Denetimi Yöneticisi'ni kullanın. Hizmetin Başlangıç Türü'nin El ile olarak ayar olduğundan emin olun.

4. Profil oluşturma ortam değişkenlerini başlatma. Şunu yazın:

    **VSPerfClrEnv** {**/globaltracegc** &#124; **/globaltracegclife**}

   - **/globaltracegc** ve **/globaltracegclife,** bellek ayırma ve nesne yaşam süresi verilerini toplamayı etkinleştirir.

       |Seçenek|Açıklama|
       |------------|-----------------|
       |**/globaltracegc**|Yalnızca bellek ayırma verilerini toplar.|
       |**/globaltracegclife**|Bellek ayırma ve nesne yaşam süresi verilerini toplar.|

5. Bilgisayarı yeniden başlatın.

6. Bir komut istemi penceresi açın.

7. Profilleyiciyi başlatma. Şunu yazın:

    **VSPerfCmd**  [/start](../profiling/start.md) **:trace**  [/output](../profiling/output.md) **:** [ `OutputFile` `Options` ]

   - **/start: contention seçeneği** profilleyiciyi başlatıyor.

   - **/output:** `OutputFile` seçeneği / **start ile gereklidir.** `OutputFile` profil oluşturma verileri (.vsp) dosyasının adını ve konumunu belirtir.

     **/start:sample** seçeneğiyle aşağıdaki seçeneklerden herhangi birini kullanabilirsiniz.

   > [!NOTE]
   > **/user ve** **/crosssession** seçenekleri genellikle hizmetler için gereklidir.

   | Seçenek | Açıklama |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Çalışan işleminin sahibi olan hesabın etki alanını ve kullanıcı ASP.NET belirtir. İşlem oturum açmış kullanıcıdan farklı bir kullanıcı olarak çalışıyorsa bu seçenek gereklidir. İşlem sahibi, Görev Yöneticisi'nin İşlemler sekmesindeki Kullanıcı Adı Windows listelenir. |
   | [/crosssession](../profiling/crosssession.md) | Diğer oturum açma oturumlarında işlemlerin profil oluşturmasını sağlar. Uygulama farklı bir oturumda ASP.NET bu seçenek gereklidir. Oturum kimliği, Görev **Yöneticisi'nin** İşlemler **sekmesindeki** Oturum Windows listelenir. **/CS,** **/crosssession için bir kısaltma olarak belirtilebilir.** |
   | [/waitstart](../profiling/waitstart.md)[**:** `Interval` ] | Profil oluşturmanın hata döndürmeden önce başlatılmasını bekleyeceği saniye sayısını belirtir. `Interval`Belirtilmezse, profil oluşturma süresiz olarak bekler. Varsayılan **olarak, /start hemen** döndürür. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Profilleyiciyi veri koleksiyonu duraklatılmış olarak başlatmak için **/start komut** satırına **/globaloff** seçeneğini ekleyin. Profil **oluşturmayı devam ettiren /globalon** kullanın. |
   | [/counter](../profiling/counter.md) **:**`Config` | Yapılandırma'da belirtilen işlemci performans sayacından bilgi toplar. Sayaç bilgileri her profil oluşturma olayında toplanan verilere eklenir. |
   | [/wincounter:](../profiling/wincounter.md) `WinCounterPath` | Profil oluşturma Windows toplanacak bir performans sayacı belirtir. |
   | [/automark:](../profiling/automark.md) `Interval` | Yalnızca **/wincounter ile** kullanın. Performans sayacı toplama olayları arasındaki milisaniye Windows sayısını belirtir. Varsayılan değer 500 ms'tir. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Profil oluşturma sırasında toplanacak Windows (ETW) olayı için bir Olay İzleme belirtir. ETW olayları ayrı bir () içinde toplanır.*etl*) dosyasını seçin. |

8. Gerekirse hizmeti başlatabilirsiniz.

9. Profiler'i hizmete ekleme. Şunu yazın:

     **VSPerfCmd /attach:** `PID`&#124;`ProcessName`

    - Hizmetin işlem kimliğini veya işlem adını belirtin. Görev Yöneticisi'nde çalışan tüm işlemlerin işlem kimliklerini ve Windows görüntüebilirsiniz.

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hizmet çalışırken veri toplamayı, veri toplama seçenekleriyle dosyada veri yazmayı başlatarak *ve durdurarakVSPerfCmd.exe* yapabilirsiniz. Veri toplamayı denetlemek, uygulamayı başlatma veya kapatma gibi program yürütmenin belirli bir bölümü için veri toplamaya olanak sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki **VSPerfCmd seçenekleri çiftleri** veri toplamayı başlatacak ve durduracak. Her seçeneği ayrı bir komut satırı üzerinde belirtin. Veri toplamayı birden çok kez açabilirsiniz ve kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Tüm işlemler **için veri toplamayı** başlatır ( /globalon ) veya durdurur (**/globaloff).**|
    |[/processon:](../profiling/processon-and-processoff.md)  `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|İşlem kimliği ( ) tarafından belirtilen işlem için veri toplamayı (**/processon**) veya durdurur ( `PID` ).|
    |[/threadon:](../profiling/threadon-and-threadoff.md)  `TID` [/threadoff:](../profiling/threadon-and-threadoff.md) `TID`|İş parçacığı kimliği ( ) tarafından belirtilen iş parçacığı için veri toplamayı (**/threadon**) veya durdurur ( `TID` ).|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sona er
 Profil oluşturma oturumunu sona çevirmek için, izlenilen bileşeni çalıştıran uygulamayı kapatın, ardından **VSPerfCmd** [/shutdown](../profiling/shutdown.md) seçeneğini başlatarak profil oluşturma veri dosyasını kapatın ve profil oluşturma verilerini kapatın. **VSPerfClrEnv /globaloff** komutu profil oluşturma ortam değişkenlerini temizler.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdir

1. Hizmeti Service Control Manager'dan durdurun.

2. Profilleyiciyi kapatın. Şunu yazın:

     **VSPerfCmd /shutdown**

3. Tüm profil oluşturmayı tamamlandıktan sonra profil oluşturma ortam değişkenlerini temizleyebilirsiniz. Şunu yazın:

     **VSPerfClrEnv /globaloff**

     Instrumented modülünü özgün modülle değiştirin. Gerekirse, hizmetin Başlangıç Türünü yeniden yapılandırabilirsiniz.

4. Bilgisayarı yeniden başlatın.

## <a name="see-also"></a>Ayrıca bkz.
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
- [.NET bellek veri görünümleri](../profiling/dotnet-memory-data-views.md)
