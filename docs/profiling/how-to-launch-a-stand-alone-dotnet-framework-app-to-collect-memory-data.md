---
title: Profil oluşturma komut satırı - İstemci uygulamasını .NET Framework, bellek verilerini al
description: Tek başına bir uygulama başlatmak Visual Studio Profil Oluşturma Araçları ve bellek etkinliği verilerini toplamak için .NET Framework komut satırı araçlarını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 3bc53041-91b7-4ad0-8413-f8bf2c4b3f5e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: ae577364987be7fa4ed9a6be633b4fa0efd7c0ba301f434055730bdf15432248
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121410677"
---
# <a name="how-to-launch-a-stand-alone-net-framework-application-with-the-profiler-to-collect-memory-data-by-using-the-command-line"></a>Nasıl kullanılır: Komut satırı kullanarak .NET Framework veri toplamak için profil oluşturma ile tek başına bir uygulama başlatma
Bu konuda, tek başına (Profil Oluşturma Araçları) bir uygulama başlatmak ve bellek verileri .NET Framework komut satırı araçlarının [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nasıl kullanımı açıklanmıştır.

 Profil oluşturma oturumunun üç parçası vardır:

- Profilleyiciyi kullanarak uygulamayı başlatma.

- Profil oluşturma verilerini toplama.

- Profil oluşturma oturumunu sonlandırma.

> [!NOTE]
> Profil oluşturma araçlarının yolunu almak için [bkz. Komut satırı araçlarının yolunu belirtme.](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md) 64 bit bilgisayarlarda, araçların hem 64 bit hem de 32 bit sürümleri kullanılabilir. Profil oluşturma komut satırı araçlarını kullanmak için, araç yolunu Komut İstemi penceresinin PATH ortam değişkenine eklemeniz veya komutun kendisine eklemeniz gerekir.

## <a name="start-the-application-with-the-profiler"></a>Uygulamayı profil oluşturma ile başlatma
 Profilleyiciyi kullanarak bir hedef uygulamayı başlatmak için profilVSPerfCmd.exebaşlatmak ve uygulamayı başlatmak için **/start** ve **/launch** seçeneklerini kullanın. **/start** ve **/launch seçeneklerini tek** bir komut satırı üzerinde belirtebilirsiniz.

 Hedef uygulamanın başında veri toplamayı duraklatmak için **/globaloff** seçeneklerini de ekebilirsiniz. Ardından veri **toplamaya başlamak için /globalon** kullanırsanız.

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

3. Hedef uygulamayı başlatma. Şunu yazın:

    **VSPerfCmd**[/launch:](../profiling/launch.md)  `appName` **/gc:**{**ayırma**&#124;**yaşam süresi**}[ `Options` ]  

   - Bellek verilerini **toplamak** için [/gc](../profiling/gc-vsperfcmd.md) `Keyword` : .NET Framework gereklidir. anahtar sözcüğü parametresi, bellek ayırma verilerini mi topla, yoksa hem bellek ayırma hem de nesne yaşam süresi verilerini toplamayı belirtir.

     |Anahtar kelime|Açıklama|
     |-------------|-----------------|
     |**Ayırma**|Yalnızca bellek ayırma verilerini toplayın.|
     |**Ömür boyu**|Hem bellek ayırma hem de nesne yaşam süresi verilerini toplayın.|

     **/launch** seçeneğiyle aşağıdaki seçeneklerden herhangi birini kullanabilirsiniz.

   |Seçenek|Açıklama|
   |------------|-----------------|
   |[/args:](../profiling/args.md) `Arguments`|Hedef uygulamaya geçirilen komut satırı bağımsız değişkenlerini içeren bir dize belirtir.|
   |[/console](../profiling/console.md)|Hedef komut satırı uygulamasını ayrı bir pencerede başlatır.|
   |[/events](../profiling/events-vsperfcmd.md) **:**`Config`|Profil oluşturma sırasında toplanacak Windows (ETW) olayı için bir Olay İzleme belirtir. ETW olayları ayrı bir (.etl) dosyasında toplanır.|
   |[/targetclr](../profiling/targetclr.md) **:**`Version`|Bir uygulamada birden fazla çalışma zamanı sürümü yüklendiğinde profili oluşturmak için ortak dil çalışma zamanının (CLR) sürümünü belirtir.|

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hedef uygulama çalıştıryken, veri toplama seçeneklerini kullanarak dosyada veri yazmayı başlatarak ve *durdurarak veriVSPerfCmd.exeyapabilirsiniz.* Veri toplamayı denetlemek, uygulamayı başlatma veya kapatma gibi program yürütmenin belirli bir bölümü için veri toplamaya olanak sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki seçenek çiftleri veri toplamayı başlat ve durdur. Her seçeneği ayrı bir komut satırı üzerinde belirtin. Veri toplamayı birden çok kez açabilirsiniz ve kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Tüm işlemler **için veri toplamayı** başlatır ( /globalon ) veya durdurur (**/globaloff).**|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [processoff:](../profiling/processon-and-processoff.md) `PID`|İşlem kimliği ( ) tarafından belirtilen işlem için veri toplamayı (**/processon**) veya durdurur ( `PID` ).|
    |[/attach](../profiling/attach.md) **:** `PID` [/detach](../profiling/detach.md)|**/attach,** tarafından belirtilen işlem (işlem kimliği) için `PID` veri toplamaya başlar. **/detach tüm** işlemler için veri toplamayı durdurur.|

- Veri dosyasına profil **VSPerfCmd.exe** [/mark](../profiling/mark.md) seçeneğini de kullanabilirsiniz. **/mark komutu** bir tanımlayıcı, zaman damgası ve isteğe bağlı bir kullanıcı tanımlı metin dizesi ekler. İşaretler verileri filtrelemek için kullanılabilir.

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sona er
 Profil oluşturma oturumunu sona erdirmak için profil oluşturma işleminin tüm profili yapılan işlemlerden ayrılmaları ve profil oluşturma işleminin açıkça kapatılmış olması gerekir. Uygulamayı kapatarak veya **VSPerfCmd /detach** seçeneğini çağırarak, örnekleme yöntemini kullanarak profil profili yapılan bir uygulamanın profillerini ayırabilirsiniz. Ardından **VSPerfCmd /shutdown** seçeneğini çağırarak profil oluşturma veri dosyasını kapatın. **VSPerfClrEnv /off** komutu profil oluşturma ortam değişkenlerini temizler.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdir

1. Profilleyiciyi hedef uygulamadan ayırmak için aşağıdaki adımlardan birini gerçekleştirin:

    - Hedef uygulamayı kapatın.

         -veya-

    - **VSPerfCmd /detach yazın**

2. Profilleyiciyi kapatın. Şunu yazın:

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [.NET bellek veri görünümleri](../profiling/dotnet-memory-data-views.md)
