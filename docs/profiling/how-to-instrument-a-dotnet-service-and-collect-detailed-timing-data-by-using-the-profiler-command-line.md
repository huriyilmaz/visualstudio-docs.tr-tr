---
title: Profil oluşturma komut satırı - .NET hizmetini takip, zamanlama ayrıntısı al
description: Visual Studio Profil Oluşturma Araçları hizmeti için ayrıntılı zamanlama verileri toplamak üzere komut satırı araçlarını .NET Framework öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 8781170e8f934f457ae16d6193636819f12179ad
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122038831"
---
# <a name="how-to-instrument-a-net-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line"></a>Nasıl yapılır: Profil oluşturucu komut satırını kullanarak bir .NET hizmetini izleme ve ayrıntılı zamanlama verileri toplama

Bu makalede, bir hizmette Visual Studio Profil Oluşturma Araçları ve ayrıntılı zamanlama verileri toplamak için .NET Framework komut satırı araçlarının nasıl kullanımı açıklanmıştır.

> [!NOTE]
> Bilgisayar başlatıldıktan sonra hizmet yeniden başlatılamazsa, yalnızca işletim sistemi başlatıldığında başlayan bir hizmet gibi, bir hizmetin profilini, ölçümleme yöntemiyle profillerini oluşturmazsınız.
>
> Profil oluşturma araçlarının yolunu almak için [bkz. Komut satırı araçlarının yolunu belirtme.](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md) 64 bit bilgisayarlarda, araçların hem 64 bit hem de 32 bit sürümleri kullanılabilir. Profil oluşturma komut satırı araçlarını kullanmak için, araç yolunu Komut İstemi penceresinin PATH ortam değişkenine eklemeniz veya komutun kendisine eklemeniz gerekir.
>
> Profil oluşturma çalıştırması için katman etkileşim verileri eklemek için komut satırı profil oluşturma araçlarıyla belirli yordamlar gerekir. Bkz. [Katman etkileşim verilerini toplama.](../profiling/adding-tier-interaction-data-from-the-command-line.md)

Ölçüm aracını kullanarak bir .NET Framework hizmetten ayrıntılı zamanlama verileri toplamak [](../profiling/vsinstr.md) içinVSInstr.exearacını kullanarak bileşenin bir instrumented sürümünü oluşturabilirsiniz. Ardından, hizmetin araçsız sürümünü, hizmetin el ile başlayacak şekilde yapılandırıldığından emin olarak, araçlı sürümle değiştirirsiniz. [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) aracını kullanarak genel profil oluşturma ortam değişkenlerini başlatacak ve ardından konak bilgisayarı yeniden başlatabilirsiniz. Ardından profilleyiciyi başlatabilirsiniz.

Hizmet başlatılırken zamanlama verileri otomatik olarak bir veri dosyasına toplanır. Profil oluşturma oturumu sırasında veri toplamayı duraklatabilir ve sürdürebilirsiniz.

Profil oluşturma oturumunu sona erdirmak için hizmeti devre dışı bırakarak profil oluşturma profilini kapatabilirsiniz. Çoğu durumda, bir oturumun sonunda profil oluşturma ortam değişkenlerini temizlemenizi öneririz.

## <a name="start-the-application-with-the-profiler"></a>Uygulamayı profil oluşturma ile başlatma

1. Bir komut istemi penceresi açın.

2. Hizmet ikili sürümünün bir araçlı sürümünü oluşturmak için **VSInstr** aracını kullanın.

3. Özgün ikili dosyanın yerini, araçlı sürümle değiştirin. Hizmet Windows Yöneticisi'nde, hizmetin Başlangıç Türü'nin El ile olarak ayarlanmış olduğundan emin olun.

4. Profil oluşturma .NET Framework değişkenlerini başlatma. Şunu yazın:

     **VSPerfClrEnv /globaltraceon**

5. Bilgisayarı yeniden başlatın.

6. Bir komut istemi penceresi açın.

7. Profilleyiciyi başlatma. Şunu yazın:

     **VSPerfCmd /start:trace /output:** `OutputFile` [`Options`]

   - [/start](../profiling/start.md)**:trace** seçeneği profilleyiciyi başlatıyor.

   - [/output](../profiling/output.md)**: seçeneği** / start ile `OutputFile` **gereklidir.** `OutputFile` profil oluşturma verisi adını ve konumunu () belirtir.*vsp*) dosyasını seçin.

     **/start:trace** seçeneğiyle aşağıdaki seçeneklerden herhangi birini kullanabilirsiniz.

     > [!NOTE]
     > Profil oluşturma hizmetleri için genellikle **/user** ve **/crosssession** seçenekleri gereklidir.

     | Seçenek | Açıklama |
     | - | - |
     | [/user](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Profili yapılan işleme sahip olan hesabın etki alanını ve kullanıcı adını belirtir. Bu seçenek yalnızca işlem oturum açmış kullanıcıdan farklı bir kullanıcı olarak çalışıyorsa gereklidir. İşlem sahibi, Görev **Yöneticisi'nin** İşlemler **sekmesindeki** Kullanıcı Adı Windows listelenir. |
     | [/crosssession](../profiling/crosssession.md) | Diğer oturumlarda işlemlerin profilini oluşturmayı sağlar. Uygulama farklı bir oturumda çalışıyorsa bu seçenek gereklidir. Oturum kimliği, Görev **Yöneticisi'nin** İşlemler **sekmesindeki** Oturum Windows listelenir. **/CS,** **/crosssession için bir kısaltma olarak belirtilebilir.** |
     | [/waitstart](../profiling/waitstart.md)[**:** `Interval` ] | Profil oluşturmanın hata döndürmeden önce başlatılmasını bekleyeceği saniye sayısını belirtir. `Interval`Belirtilmezse, profil oluşturma süresiz olarak bekler. Varsayılan **olarak, /start hemen** döndürür. |
     | [/globaloff](../profiling/globalon-and-globaloff.md) | Profilleyiciyi veri koleksiyonu duraklatılmış olarak başlatmak için **/start komut** satırına **/globaloff** seçeneğini ekleyin. Profil **oluşturmayı devam ettiren /globalon** kullanın. |
     | [/counter](../profiling/counter.md) **:**`Config` | Yapılandırma'da belirtilen işlemci performans sayacından bilgi toplar. Sayaç bilgileri her profil oluşturma olayında toplanan verilere eklenir. |
     | [/wincounter:](../profiling/wincounter.md) `WinCounterPath` | Profil oluşturma Windows toplanacak bir performans sayacı belirtir. |
     | [/automark:](../profiling/automark.md) `Interval` | Yalnızca **/wincounter ile** kullanın. Performans sayacı toplama olayları arasındaki milisaniye Windows sayısını belirtir. Varsayılan değer 500 ms'tir. |
     | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Profil oluşturma sırasında toplanacak Windows (ETW) olayı için bir Olay İzleme belirtir. ETW olayları ayrı bir () içinde toplanır.*etl*) dosyasını seçin. |

8. Hizmeti Service Control Manager Windows dan başlatabilirsiniz.

## <a name="control-data-collection"></a>Veri toplamayı denetleme

Hizmet çalışmaya devam ediyorsa, profil *VSPerfCmd.exe* veri dosyasına veri yazmayı başlatmak ve durdurmak için bu seçenekleri kullanabilirsiniz. Veri toplamayı denetlemek, programı yürütmenin belirli bir bölümü için hizmeti başlatma veya kapatma gibi verileri toplamaya olanak sağlar.

- Aşağıdaki **VSPerfCmd seçenekleri çiftleri** veri toplamayı başlatacak ve durduracak. Her seçeneği ayrı bir komut satırı üzerinde belirtin. Veri toplamayı birden çok kez açabilirsiniz ve kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Tüm işlemler **için veri toplamayı** başlatır ( /globalon ) veya durdurur (**/globaloff).**|
    |[/processon:](../profiling/processon-and-processoff.md)  `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|İşlem kimliği ( ) tarafından belirtilen işlem için veri toplamayı (**/processon**) veya durdurur ( `PID` ).|
    |[/threadon:](../profiling/threadon-and-threadoff.md)  `TID` [/threadoff:](../profiling/threadon-and-threadoff.md) `TID`|İş parçacığı kimliği ( ) tarafından belirtilen iş parçacığı için veri toplamayı (**/threadon**) veya durdurur ( `TID` ).|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sona er

Profil oluşturma oturumunu sona erdirecek şekilde, izlenilen bileşeni çalıştıran hizmeti durdurun ve **ardından VSPerfCmd** [/shutdown](../profiling/shutdown.md) seçeneğini çağırarak profil oluşturma veri dosyasını kapatın. **VSPerfClrEnv /globaloff** komutu profil oluşturma ortam değişkenlerini temizler.

Yeni ortam ayarlarının uygulanması için bilgisayarı yeniden başlatmanız gerekir.

1. Hizmeti Service Control Manager'dan durdurun.

2. Profilleyiciyi kapatın. Şunu yazın:

     **VSPerfCmd /shutdown**

3. Tüm profil oluşturmayı tamamlandıktan sonra profil oluşturma ortam değişkenlerini temizleyebilirsiniz. Şunu yazın:

     **VSPerfClrEnv /globaloff**

4. Instrumented modülünü özgün modülle değiştirin. Gerekirse, hizmetin Başlangıç Türünü yeniden yapılandırabilirsiniz.

5. Bilgisayarı yeniden başlatın.

## <a name="see-also"></a>Ayrıca bkz.

[Profil hizmetleri](../profiling/command-line-profiling-of-services.md) 
 [Ölçüm izleme yöntemi veri görünümleri](../profiling/instrumentation-method-data-views.md)
