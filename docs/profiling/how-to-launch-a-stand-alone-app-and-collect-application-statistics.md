---
title: Profil oluşturma komut satırı - Tek başına uygulamayı başlatma, uygulama istatistiklerini al
description: Tek başına bir uygulama başlatmak Visual Studio Profil Oluşturma Araçları ve örnekleme yöntemini kullanarak performans verilerini toplamak için komut satırı araçlarını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 52dcee2b-f178-4a76-bddc-e36c50bfcb78
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 6d8626bd4742e14f14b32fe47e3e61412020f5dd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122107621"
---
# <a name="how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line"></a>Nasıl yapılır: Profil oluşturucu ile bağımsız bir uygulama başlatma ve komut satırını kullanarak uygulama istatistikleri toplama
Bu konu başlığı altında, tek Profil Oluşturma Araçları (istemci) uygulaması başlatmak ve örnekleme yöntemini kullanarak performans istatistikleri toplamak için komut satırı araçlarını kullanma [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] açıklanmıştır.

> [!NOTE]
> Windows 8 ve Windows Server 2012 profil oluşturma Visual Studio bu platformlarda veri toplama şeklinde önemli değişiklikler gerektirmektedir. UWP uygulamaları için yeni koleksiyon teknikleri de gerekir. Uygulama [ve uygulama Windows 8 performans Windows Server 2012 bakın.](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)
>
> Profil oluşturma çalıştırması için katman etkileşim verileri eklemek için komut satırı profil oluşturma araçlarıyla belirli yordamlar gerekir. Bkz. [Katman etkileşim verilerini toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md)

 Profil oluşturma komut satırı araçlarını kullanmak için, Komut İstemi penceresinin PATH ortam değişkenine yolu eklemeniz veya komutun kendisine eklemeniz gerekir. Profil oluşturma araçlarını bir komut penceresinden Visual Studio makinede Visual Studio çalıştırabilirsiniz.

1. Profil oluşturma araçlarını Visual Studio yüklü bir makinede Visual Studio doğru yolları ayarlar. Araçlar **menüsünde** VS komut **istemini seçin**

> [!NOTE]
> Profil oluşturma araçlarının yolunu almak için [bkz. Komut satırı araçlarının yolunu belirtme.](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md) 64 bit bilgisayarlarda, araçların hem 64 bit hem de 32 bit sürümleri kullanılabilir. Profil oluşturma komut satırı araçlarını kullanmak için, araç yolunu Komut İstemi penceresinin PATH ortam değişkenine eklemeniz veya komutun kendisine eklemeniz gerekir.

## <a name="start-the-application-with-the-profiler"></a>Uygulamayı profil oluşturma ile başlatma
 Profilleyiciyi kullanarak hedef uygulamayı başlatmak için VSPerfCmd **/start** ve **/launch** seçeneklerini kullanarak profilleyiciyi başlatarak uygulamayı başlatabilirsiniz. **/start** ve **/launch seçeneklerini tek** bir komut satırı üzerinde belirtebilirsiniz.

 Hedef uygulamanın başında veri toplamayı duraklatmak için **/globaloff** seçeneğini de ekebilirsiniz. Ardından veri **toplamaya başlamak için /globalon** kullanırsanız.

#### <a name="to-start-an-application-by-using-the-profiler"></a>Profilleyiciyi kullanarak bir uygulamayı başlatmak için

1. Bir komut istemi penceresi açın.

2. Profilleyiciyi başlatma. Şunu yazın:

    **VSPerfCmd /start:sample /output:** `OutputFile` [`Options`]

   - [/start](../profiling/start.md)**:sample** seçeneği profilleyiciyi başlatıyor.

   - [/output](../profiling/output.md)**: seçeneği** / start ile `OutputFile` **gereklidir.** `OutputFile` profil oluşturma verileri (.vsp) dosyasının adını ve konumunu belirtir.

     **/start:sample** seçeneğiyle aşağıdaki seçeneklerden herhangi birini kullanabilirsiniz.

   | Seçenek | Açıklama |
   | - | - |
   | [/wincounter:](../profiling/wincounter.md) `WinCounterPath` | Profil oluşturma Windows toplanacak bir performans sayacı belirtir. |
   | [/automark:](../profiling/automark.md) `Interval` | Yalnızca **/wincounter ile** kullanın. Performans sayacı toplama olayları arasındaki milisaniye Windows sayısını belirtir. Varsayılan değer 500 ms'tir. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Profil oluşturma sırasında toplanacak Windows (ETW) olayı için bir Olay İzleme belirtir. ETW olayları ayrı bir () içinde toplanır.*etl*) dosyasını seçin. |

3. Hedef uygulamayı başlatma. Tür:**VSPerfCmd /launch:** `appName` [ ] [ `Options` `Sample Event` ]

    **/launch** seçeneğiyle aşağıdaki seçeneklerden birini veya daha fazlasını kullanabilirsiniz.

   |Seçenek|Açıklama|
   |------------|-----------------|
   |[/args:](../profiling/args.md) `Arguments`|Hedef uygulamaya geçirilen komut satırı bağımsız değişkenlerini içeren bir dize belirtir.|
   |[/console](../profiling/console.md)|Hedef komut satırı uygulamasını ayrı bir pencerede başlatır.|

    Varsayılan olarak, her 10.000.000 durdurulan işlemci saat döngüsü için performans verileri örnek alır. Bu, 1 GHz işlemcide 10 saniyede bir yaklaşık bir kezdir. Saat döngüsü aralığını değiştirmek veya farklı bir örnekleme olayı belirtmek için aşağıdaki seçeneklerden birini belirtebilirsiniz.

   |Örnek olay|Açıklama|
   |------------------|-----------------|
   |[/timer](../profiling/timer.md) **:**`Interval`|Örnekleme aralığını tarafından belirtilen durdurulmamış saat döngülerinin sayısına `Interval` değiştirir.|
   |[/pf](../profiling/pf.md)[**:** `Interval` ]|Örnekleme olayında sayfa hatalarını değiştirir. `Interval`belirtilirse, örnekler arasındaki sayfa hatalarının sayısını ayarlar. Varsayılan değer 10'dır.|
   |[/sys](../profiling/sys-vsperfcmd.md)[**:** `Interval` ]|Örnekleme olayı, işlemden işletim sistemi çekirdeğine (syscalls) yapılan sistem çağrılarını değiştirir. `Interval`belirtilirse, örnekler arasındaki çağrı sayısını ayarlar. Varsayılan değer 10'dır.|
   |[/counter](../profiling/counter.md) **:**`Config`|Örnekleme olayı ve aralığını, içinde belirtilen işlemci performans sayacı ve aralığı olarak `Config` değiştirir.|

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hedef uygulamanın çalışma süresince, profil oluşturma seçeneklerini kullanarak profil oluşturma veri dosyasına veri yazmayı başlatarak ve durdurarak *veri toplamayıVSPerfCmd.exe* yapabilirsiniz. Veri toplamayı denetlemek, uygulamayı başlatma veya kapatma gibi program yürütmenin belirli bir bölümü için veri toplamaya olanak sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki seçenek çiftleri veri toplamayı başlat ve durdur. Her seçeneği ayrı bir komut satırı üzerinde belirtin. Veri toplamayı birden çok kez açabilirsiniz ve kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Tüm işlemler **için veri toplamayı** başlatır ( /globalon ) veya durdurur (**/globaloff).**|
    |[/processon:](../profiling/processon-and-processoff.md)  `PID` [/processoff](../profiling/processon-and-processoff.md) **:**  `PID`|İşlem kimliği ( ) tarafından belirtilen işlem için veri toplamayı (**/processon**) veya durdurur ( `PID` ).|
    |[/attach:](../profiling/attach.md) { `PID`&#124;`ProcName` } [/detach](../profiling/detach.md)[**:**{ `PID`&#124;`ProcName` }]|**/attach,** veya işlem adı `PID` (ProcName) tarafından belirtilen işlem için veri toplamaya başlar. **/detach,** belirtilen işlem için veya belirli bir işlem belirtilmezse tüm işlemler için veri toplamayı durdurur.|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sona er
 Profil oluşturma oturumunu sona ertmak için profil oluşturma işleminin profili yapılan hiçbir işleme bağlı olması ve profil oluşturma işleminin açıkça kapatılamaması gerekir. Uygulamayı kapatarak veya **VSPerfCmd /detach** seçeneğini çağırarak, örnekleme yöntemini kullanarak profil profili yapılan bir uygulamanın profillerini ayırabilirsiniz. Ardından, profil oluşturma veri dosyasını kapatmak ve profil oluşturma verilerini kapatmak için **VSPerfCmd /shutdown** seçeneğini çağırabilirsiniz. **VSPerfClrEnv /off** komutu profil oluşturma ortam değişkenlerini temizler.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdir

1. Profilleyiciyi hedef uygulamadan ayırmak için aşağıdaki adımlardan birini gerçekleştirin:

    - Hedef uygulamayı kapatın.

         -veya-

    - **VSPerfCmd /detach yazın**

2. Profilleyiciyi kapatın. Şunu yazın:

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Örnekleme yöntemi veri görünümleri](../profiling/profiler-sampling-method-data-views.md)
