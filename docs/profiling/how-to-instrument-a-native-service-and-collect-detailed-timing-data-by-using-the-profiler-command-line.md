---
title: Profil oluşturma komut satırı - Yerel hizmeti ölçümle, zamanlama verilerini al
description: Yerel bir C/C++ Visual Studio Profil Oluşturma Araçları ayrıntılı zamanlama verileri toplamak için komut satırı araçlarını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: dfe58b39-63f8-4a87-ab3a-2b5b14faa8d0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: d3849137067d58d5fc641cbd26bcadc765fae747
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122033531"
---
# <a name="how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line"></a>Nasıl yapılır: Profil oluşturucu komut satırını kullanarak yerel bir hizmeti izleme ve ayrıntılı zamanlama verileri toplama
Bu makalede yerel (C/C++) Profil Oluşturma Araçları ve ayrıntılı zamanlama verileri toplamak için komut satırı araçlarının nasıl [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] kullanımı açıklanmıştır.

> [!NOTE]
> Bilgisayar başlatıldıktan sonra hizmet yeniden başlatılamazsa, yalnızca işletim sistemi başlatıldığında başlayan bir hizmet gibi, bir hizmetin profilini, ölçümleme yöntemiyle profillerini oluşturmazsınız.
>
> Profil oluşturma araçlarının yolunu almak için [bkz. Komut satırı araçlarının yolunu belirtme.](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md) 64 bit bilgisayarlarda, araçların hem 64 bit hem de 32 bit sürümleri kullanılabilir. Profil oluşturma komut satırı araçlarını kullanmak için, araç yolunu Komut İstemi penceresinin PATH ortam değişkenine eklemeniz veya komutun kendisine eklemeniz gerekir.

 Bir yerel hizmetten ölçümleme yöntemini kullanarak ayrıntılı zamanlama verileri [](../profiling/vsinstr.md) toplamak içinVSInstr.exearacını kullanarak bileşenin bir araç sürümünü oluşturabilirsiniz. Ardından, hizmetin araçsız sürümünü, hizmetin el ile başlayacak şekilde yapılandırıldığından emin olarak, araçlı sürümle değiştirirsiniz. Ardından profilleyiciyi başlatabilirsiniz.

 Hizmet başlatılırken zamanlama verileri otomatik olarak bir veri dosyasına toplanır. Profil oluşturma oturumu sırasında veri toplamayı duraklatabilir ve sürdürebilirsiniz.

 Profil oluşturma oturumunu sona erdirmak için hizmeti devre dışı bırakarak profil oluşturma profilini kapatabilirsiniz.

## <a name="start-the-application-with-the-profiler"></a>Uygulamayı profil oluşturma ile başlatma

#### <a name="to-start-profiling-a-native-service"></a>Yerel bir hizmetin profilini oluşturmayı başlatmak için

1. Bir komut istemi penceresi açın.

2. Hizmet ikili sürümünün bir araçlı sürümünü oluşturmak için **VSInstr** aracını kullanın.

3. Özgün ikili dosyanın yerini, araçlı sürümle değiştirin. Hizmet Windows Yöneticisi'nde, hizmetin Başlangıç Türü'nin El ile olarak ayarlanmış olduğundan emin olun.

4. Profilleyiciyi başlatma. Şunu yazın:

    **VSPerfCmd** [/start](../profiling/start.md) **:trace**  [/output](../profiling/output.md) **:** [ `OutputFile` `Options` ]

   - **/start:trace** seçeneği profilleyiciyi başlatıyor.

   - **/output:** `OutputFile` seçeneği / **start ile gereklidir.** `OutputFile` profil oluşturma verisi adını ve konumunu () belirtir.*vsp*) dosyasını seçin.

     **/start:trace** seçeneğiyle aşağıdaki seçeneklerden herhangi birini kullanabilirsiniz.

   > [!NOTE]
   > /user **ve** **/crosssession** seçenekleri genellikle uygulama ASP.NET gereklidir.

   | Seçenek | Açıklama |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Çalışan işleminin sahibi olan hesabın etki alanını ve kullanıcı ASP.NET belirtir. İşlem oturum açmış kullanıcıdan farklı bir kullanıcı olarak çalışıyorsa bu seçenek gereklidir. İşlem sahibi, Görev **Yöneticisi'nin** İşlemler **sekmesindeki** Kullanıcı Adı Windows listelenir. |
   | [/crosssession](../profiling/crosssession.md) | Diğer oturum açma oturumlarında işlemlerin profil oluşturmasını sağlar. Bu seçenek, ASP.NET farklı bir oturumda çalışıyorsa gereklidir. Oturum kimliği, Görev Yöneticisi'nin İşlemler sekmesindeki Oturum Windows listelenir. **/CS,** **/crosssession için bir kısaltma olarak belirtilebilir.** |
   | [/waitstart](../profiling/waitstart.md)[**:** `Interval` ] | Profil oluşturmanın hata döndürmeden önce başlatılmasını bekleyeceği saniye sayısını belirtir. `Interval`Belirtilmezse, profil oluşturma süresiz olarak bekler. Varsayılan **olarak, /start hemen** döndürür. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Profilleyiciyi veri koleksiyonu duraklatılmış olarak başlatmak için **/start komut** satırına **/globaloff** seçeneğini ekleyin. Profil **oluşturmayı devam ettiren /globalon** kullanın. |
   | [/counter](../profiling/counter.md) **:**`Config` | Yapılandırma'da belirtilen işlemci performans sayacından bilgi toplar. Sayaç bilgileri her profil oluşturma olayında toplanan verilere eklenir. |
   | [/wincounter:](../profiling/wincounter.md) `WinCounterPath` | Profil oluşturma Windows toplanacak bir performans sayacı belirtir. |
   | [/automark:](../profiling/automark.md) `Interval` | Yalnızca **/wincounter ile** kullanın. Performans sayacı toplama olayları arasındaki milisaniye Windows sayısını belirtir. Varsayılan değer 500 ms'tir. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Profil oluşturma sırasında toplanacak Windows (ETW) olayı için bir Olay İzleme belirtir. ETW olayları ayrı bir () içinde toplanır.*etl*) dosyasını seçin. |

5. Hizmeti Service Control Manager'dan başlatabilirsiniz.

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hizmet çalışmaya devam ediyorsa, profil *VSPerfCmd.exe* veri dosyasına veri yazmayı başlatmak ve durdurmak için bu seçenekleri kullanabilirsiniz. Veri toplamayı denetlemek, programı yürütmenin belirli bir bölümü için hizmeti başlatma veya kapatma gibi verileri toplamaya olanak sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki **VSPerfCmd seçenekleri çiftleri** veri toplamayı başlatacak ve durduracak. Her seçeneği ayrı bir komut satırı üzerinde belirtin. Veri toplamayı birden çok kez açabilirsiniz ve kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Tüm işlemler **için veri toplamayı** başlatır ( /globalon ) veya durdurur (**/globaloff).**|
    |[/processon:](../profiling/processon-and-processoff.md)  `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|İşlem kimliği ( ) tarafından belirtilen işlem için veri toplamayı (**/processon**) veya durdurur ( `PID` ).|
    |[/threadon:](../profiling/threadon-and-threadoff.md)  `TID` [/threadoff:](../profiling/threadon-and-threadoff.md) `TID`|İş parçacığı kimliği ( ) tarafından belirtilen iş parçacığı için veri toplamayı (**/threadon**) veya durdurur ( `TID` ).|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sona er
 Profil oluşturma oturumunu sona erdirecek şekilde, izlenilen bileşeni çalıştıran hizmeti durdurun ve **ardından VSPerfCmd**[/shutdown](../profiling/shutdown.md) seçeneğini çağırarak profil oluşturma veri dosyasını kapatın.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdir

1. Hizmeti Service Control Manager'dan durdurun.

2. Profilleyiciyi kapatın. Şunu yazın:

     **VSPerfCmd /shutdown**

3. Instrumented modülünü özgün modülle değiştirin. Gerekirse, hizmetin Başlangıç Türünü yeniden yapılandırabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
- [Ölçüm izleme yöntemi veri görünümleri](../profiling/instrumentation-method-data-views.md)
