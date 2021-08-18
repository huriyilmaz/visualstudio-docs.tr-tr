---
title: Profil oluşturma komut satırı - İstemci .NET bileşenini takip, zaman verilerini al
description: Tek başına bir uygulamanın Visual Studio Profil Oluşturma Araçları için zamanlama verileri toplamak üzere .NET Framework komut satırı araçlarını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: b7dcc27b-45c6-4302-9552-6fa5b1e94b56
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 86421cef936a14b10f211c9660e9d920fa97bd3d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122107660"
---
# <a name="how-to-instrument-a-stand-alone-net-framework-component-and-collect-timing-data-with-the-profiler-from-the-command-line"></a>Nasıl yapılır: Tek başına bir .NET Framework bileşenini izleme ve komut satırından profil oluşturucu ile zamanlama verileri toplama
Bu konuda, gibi bir Profil Oluşturma Araçları için komut satırı araçlarının nasıl [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .NET Framework araçları açıklanmıştır.*exe veya* . *dll* dosyası ve ayrıntılı zamanlama verileri toplamak için.

> [!NOTE]
> Windows 8 ve Windows Server 2012'daki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturmanın bu platformlarda veri toplaması sırasında önemli değişiklikler gerektirmektedir. UWP uygulamaları için yeni koleksiyon teknikleri de gerekir. Uygulama [ve uygulama Windows 8 performans Windows Server 2012 bakın.](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)
>
> Profil oluşturma araçlarının yolunu almak için [bkz. Komut satırı araçlarının yolunu belirtme.](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md) 64 bit bilgisayarlarda, araçların hem 64 bit hem de 32 bit sürümleri kullanılabilir. Profil oluşturma komut satırı araçlarını kullanmak için, araç yolunu Komut İstemi penceresinin PATH ortam değişkenine eklemeniz veya komutun kendisine eklemeniz gerekir.
>
> Profil oluşturma çalıştırması için katman etkileşim verileri eklemek için komut satırı profil oluşturma araçlarıyla belirli yordamlar gerekir. Bkz. [Katman etkileşim verilerini toplama.](../profiling/adding-tier-interaction-data-from-the-command-line.md)

 Bir .NET Framework bileşeninden ayrıntılı zamanlama verilerini toplamak için, [VSInstr.exe](../profiling/vsinstr.md) aracını kullanarak bileşenin izlenilen bir sürümünü ve profil oluşturma ortam değişkenlerini başlatmak için [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) aracını kullanırsınız. Ardından profilleyiciyi başlatabilirsiniz.

 Ölçüme alınan bileşen yürütülürken zamanlama verileri otomatik olarak bir veri dosyasına toplanır. Profil oluşturma oturumu sırasında veri toplamayı duraklatabilir ve sürdürebilirsiniz.

 Profil oluşturma oturumunu sona erdirmak için hedef uygulamayı kapatın ve profil oluşturma profilini açıkça kapatın. Çoğu durumda, bir oturumun sonunda profil oluşturma ortam değişkenlerini temizlemenizi öneririz.

## <a name="start-the-profiling-session"></a>Profil oluşturma oturumunu başlatma

#### <a name="to-start-profiling-by-using-the-instrumentation-method"></a>Ölçüm ölçüm yöntemini kullanarak profil oluşturmayı başlatmak için

1. Bir komut istemi penceresi açın. Gerekirse, profil oluşturma araçları dizinini PATH ortam değişkeninize ekleyin. Yol yükleme sırasında eklenmez.

2. Hedef **uygulamanın izlenilen** bir sürümünü oluşturmak için VSInstr aracını kullanın.

3. Profil oluşturma .NET Framework değişkenlerini başlatma. Şunu yazın:

    **VSPerfClrEnv /traceon**

4. Profilleyiciyi başlatma. Şunu yazın:

    **VSPerfCmd /start:trace /output:** `OutputFile` [`Options`]

   - [/start](../profiling/start.md)**:trace** seçeneği profilleyiciyi başlatıyor.

   - [/output](../profiling/output.md)**: seçeneği** / start ile `OutputFile` **gereklidir.** `OutputFile` profil oluşturma verileri (.vsp) dosyasının adını ve konumunu belirtir.

     **/start:trace** seçeneğiyle aşağıdaki seçeneklerden herhangi birini kullanabilirsiniz.

   | Seçenek | Açıklama |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Profili yapılan işleme sahip olan hesabın etki alanını ve kullanıcı adını belirtir. Bu seçenek yalnızca işlem oturum açmış kullanıcıdan farklı bir kullanıcı olarak çalışıyorsa gereklidir. İşlem sahibi, Görev **Yöneticisi'nin** İşlemler **sekmesindeki** Kullanıcı Adı Windows listelenir. |
   | [/crosssession](../profiling/crosssession.md) | Diğer oturumlarda işlemlerin profilini oluşturmayı sağlar. Uygulama farklı bir oturumda ASP.NET bu seçenek gereklidir. Oturum tanımlayıcısı, Görev **Yöneticisi'nin** İşlemler **sekmesindeki** Oturum Kimliği Windows listelenir. **/CS,** **/crosssession için bir kısaltma olarak belirtilebilir.** |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Veri toplama duraklatılmış şekilde profilleyiciyi başlatır. Profil [oluşturmayı devam ettiren /globalon](../profiling/globalon-and-globaloff.md) kullanın. |
   | [/counter](../profiling/counter.md) **:**`Config` | içinde belirtilen işlemci performans sayacından bilgi `Config` toplar. Sayaç bilgileri, her profil oluşturma olayında toplanan verilere eklenir. |
   | [/wincounter:](../profiling/wincounter.md) `WinCounterPath` | Profil oluşturma Windows bir performans sayacı belirtir. |
   | [/automark:](../profiling/automark.md) `Interval` | Yalnızca **/wincounter ile** kullanın. Performans sayacı toplama olayları arasındaki milisaniye Windows sayısını belirtir. Varsayılan değer 500 ms'tir. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Profil oluşturma sırasında toplanacak Windows (ETW) olayı için bir Olay İzleme belirtir. ETW olayları ayrı bir () içinde toplanır.*etl*) dosyasını seçin. |

5. Komut İstemi penceresinden hedef uygulamayı çalıştırın.

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hedef uygulama çalıştıryken, profil oluşturma seçeneklerini kullanarak veri yazmayı başlatarak ve durdurarak veri *toplamayıVSPerfCmd.exe* yapabilirsiniz. Veri toplamayı denetlemek, uygulamayı başlatma veya kapatma gibi program yürütmenin belirli bir bölümü için veri toplamaya olanak sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki seçenek çiftleri veri toplamayı başlat ve durdur. Her seçeneği ayrı bir komut satırı üzerinde belirtin. Veri toplamayı birden çok kez açabilirsiniz ve kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Tüm işlemler **için veri toplamayı** başlatır ( /globalon ) veya durdurur (**/globaloff).**|
    |[/processon:](../profiling/processon-and-processoff.md)  `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|İşlem kimliği ( ) tarafından belirtilen işlem için veri toplamayı (**/processon**) veya durdurur ( `PID` ).|
    |[/threadon:](../profiling/threadon-and-threadoff.md)  `TID` [/threadoff:](../profiling/threadon-and-threadoff.md) `TID`|İş parçacığı kimliği ( ) tarafından belirtilen iş parçacığı için veri toplamayı (**/threadon**) veya durdurur ( `TID` ).|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sona er
 Profil oluşturma oturumunu sona ererken, araçlı bileşeni çalıştıran uygulamayı kapatın. Profilleyiciyi kapatmak ve profil oluşturma veri dosyasını kapatmak için **VSPerfCmd** [/shutdown](../profiling/shutdown.md) seçeneğini çağırma. **VSPerfClrEnv /off** komutu profil oluşturma ortam değişkenlerini temizler.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdir

1. Hedef uygulamayı kapatın.

2. Profilleyiciyi kapatın. Şunu yazın:

     **VSPerfCmd /shutdown**

3. (İsteğe bağlı) Profil oluşturma ortam değişkenlerini temizleme. Şunu yazın:

     **VSPerfClrEnv /off**

## <a name="see-also"></a>Ayrıca bkz.
- [Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Ölçüm izleme yöntemi veri görünümleri](../profiling/instrumentation-method-data-views.md)
