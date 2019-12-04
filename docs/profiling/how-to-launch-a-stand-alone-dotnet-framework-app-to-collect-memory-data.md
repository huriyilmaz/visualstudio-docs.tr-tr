---
title: 'Profil oluşturucu komut satırı: istemci .NET Framework uygulamasını açın, bellek verilerini alın'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3bc53041-91b7-4ad0-8413-f8bf2c4b3f5e
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: c9ee0ae59fd32394e31acc75184d0e55aaae872d
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74775366"
---
# <a name="how-to-launch-a-stand-alone-net-framework-application-with-the-profiler-to-collect-memory-data-by-using-the-command-line"></a>Nasıl yapılır: komut satırını kullanarak bellek verileri toplamak için Profil Oluşturucu ile tek başına .NET Framework uygulaması başlatma
Bu konu, bir .NET Framework tek başına (istemci) uygulaması başlatmak ve bellek verileri toplamak için [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Oluşturma Araçları komut satırı araçlarının nasıl kullanılacağını açıklar.

 Profil oluşturma oturumunun üç bölümü vardır:

- Profil oluşturucuyu kullanarak uygulamayı başlatma.

- Profil oluşturma verileri toplanıyor.

- Profil oluşturma oturumu sonlandırılıyor.

> [!NOTE]
> Profil oluşturma araçlarının yolunu almak için, bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). 64 bit bilgisayarlarda, araçların her ikisi de 64-bit ve 32 bit sürümleri mevcuttur. Profil oluşturucu komut satırı araçlarını kullanmak için araçlar yolunu komut Istemi penceresinin PATH ortam değişkenine eklemeniz ya da komutun kendisine eklemeniz gerekir.

## <a name="start-the-application-with-the-profiler"></a>Uygulamayı Profil Oluşturucu ile başlatma
 Profil oluşturucuyu kullanarak bir hedef uygulamayı başlatmak için **VSPerfCmd. exe/start** ve **/Launch** seçeneklerini kullanarak profil oluşturucuyu başlatabilir ve uygulamayı başlatabilirsiniz. **/Start** ve **/Launch** seçeneklerini ve ilgili seçeneklerini tek bir komut satırında belirtebilirsiniz.

 Ayrıca, hedef uygulamanın başlangıcında veri toplamayı duraklatmak için **/globaloff** seçeneklerini de ekleyebilirsiniz. Ardından, veri toplamaya başlamak için **/GlobalOn** kullanın.

#### <a name="to-start-an-application-by-using-the-profiler"></a>Profil oluşturucuyu kullanarak bir uygulamayı başlatmak için

1. Bir Komut İstemi penceresi açın.

2. Profil oluşturucuyu başlatın. Tür:

    **VSPerfCmd/start: örnek/output:** `OutputFile` [`Options`]

   - [/Start](../profiling/start.md) **: örnek** seçeneği, profil oluşturucuyu başlatır.

   - [/Output](../profiling/output.md) **:** `OutputFile` seçeneği, **/Start**ile gereklidir. `OutputFile` profil oluşturma verileri (. vsp) dosyasının adını ve konumunu belirtir.

     Aşağıdaki seçeneklerden herhangi birini, **/Start: Sample** seçeneğiyle kullanabilirsiniz.

   | Seçenek | Açıklama |
   | - | - |
   | [/WINCOUNTER](../profiling/wincounter.md) **:** `WinCounterPath` | Profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir. |
   | [/AutoMark](../profiling/automark.md) **:** `Interval` | Yalnızca **/WINCOUNTER** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 MS 'dir. |

3. Hedef uygulamayı başlatın. Tür:

    **VSPerfCmd**  [/Launch](../profiling/launch.md) **:** `appName` **/GC:** {**ayırma**&#124;**ömrü**} [`Options`]

   - .NET Framework bellek verileri toplamak için [/GC](../profiling/gc-vsperfcmd.md) **:** `Keyword` seçeneği gereklidir. Anahtar sözcüğü parametresi, bellek ayırma verilerinin mi toplanacağını yoksa hem bellek ayırma hem de nesne yaşam süresi verilerini mi toplayacağınızı belirtir.

     |sözcükle|Açıklama|
     |-------------|-----------------|
     |**ayırmasını**|Yalnızca bellek ayırma verilerini toplayın.|
     |**süre**|Hem bellek ayırma hem de nesne yaşam süresi verilerini toplayın.|

     Aşağıdaki seçeneklerden herhangi birini **/Launch** seçeneği ile kullanabilirsiniz.

   |Seçenek|Açıklama|
   |------------|-----------------|
   |[/args](../profiling/args.md) **:** `Arguments`|Hedef Uygulamaya geçirilecek komut satırı bağımsız değişkenlerini içeren bir dize belirtir.|
   |[/Console](../profiling/console.md)|Hedef komut satırı uygulamasını ayrı bir pencerede başlatır.|
   |[/Events](../profiling/events-vsperfcmd.md) **:** `Config`|Profil oluşturma sırasında toplanacak bir Windows için olay Izleme (ETW) olayı belirtir. ETW olayları ayrı bir (. etl) dosyasında toplanır.|
   |[/targetclr](../profiling/targetclr.md) **:** `Version`|Bir uygulamaya çalışma zamanının birden fazla sürümü yüklendiğinde profil için ortak dil çalışma zamanının (CLR) sürümünü belirtir.|

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hedef uygulama çalışırken, *VSPerfCmd. exe* seçeneklerini kullanarak verileri dosyaya yazmayı başlatıp durdurarak veri toplamayı kontrol edebilirsiniz. Veri toplamayı denetlemek, program yürütmesinin, uygulamayı başlatma veya kapatma gibi belirli bir bölümü için veri toplamanızı sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki seçenek çiftleri veri toplamayı başlatır ve durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Tüm süreçler için veri toplamayı başlatır ( **/GlobalOn**) veya Durdur ( **/globaloff**).|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [ProcessOff](../profiling/processon-and-processoff.md) **:** `PID`|İşlem KIMLIĞI (`PID`) tarafından belirtilen işlem için ( **/ProcessOn**) veya duraklar ( **/ProcessOff**) veri toplamayı başlatır.|
    |[/Attach](../profiling/attach.md) **:** `PID` [/Detach](../profiling/detach.md)|**/Attach** , `PID` (işlem kimliği) tarafından belirtilen işlem için veri toplamaya başlar. **/Detach** tüm süreçler için veri toplamayı durduruyor.|

- Veri dosyasına bir profil oluşturma işareti eklemek için **VSPerfCmd. exe**[/Mark](../profiling/mark.md) seçeneğini de kullanabilirsiniz. **/Mark** komutu bir tanımlayıcı, bir zaman damgası ve Kullanıcı tanımlı isteğe bağlı bir metin dizesi ekler. İşaretler, verileri filtrelemek için kullanılabilir.

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu Sonlandır
 Profil oluşturma oturumunu sonlandırmak için, profil oluşturucunun profili oluşturulmuş tüm işlemlerden ayrılması ve profil oluşturucunun açıkça kapatılması gerekir. Profil oluşturucuyu, uygulamayı kapatarak veya **VSPerfCmd/detach** seçeneğini çağırarak örnekleme yöntemini kullanarak profili oluşturulmuş bir uygulamadan ayırabilirsiniz. Ardından, profil oluşturucuyu kapatmak ve profil oluşturma veri dosyasını kapatmak için **VSPerfCmd/shutdown** seçeneğini çağırın. **VSPerfCLREnv/off** komutu profil oluşturma ortam değişkenlerini temizler.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sonlandırmak için

1. Profil oluşturucuyu hedef uygulamadan ayırmak için aşağıdaki adımlardan birini gerçekleştirin:

    - Hedef uygulamayı kapatın.

         veya

    - **VSPerfCmd/detach** yazın

2. Profil oluşturucuyu kapatın. Tür:

     **VSPerfCmd**  [/Shutdown](../profiling/shutdown.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Tek başına uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [.NET bellek verileri görünümleri](../profiling/dotnet-memory-data-views.md)
