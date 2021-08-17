---
title: Profil oluşturucu komut satırı-açık istemci .NET uygulaması, eşzamanlılık verileri al
description: .net tek başına uygulamasını başlatmak ve işlem ve iş parçacığı eşzamanlılık verilerini toplamak için Visual Studio Profil Oluşturma Araçları komut satırı araçlarının nasıl kullanılacağını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 17a48848-bd3e-44ef-9971-e39836ff1df2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: f9ed0972f96ef3d9ef8a5692943ca31548e3667f4ade64812990ba20ab5186cf
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121396519"
---
# <a name="how-to-launch-a-stand-alone-net-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line"></a>nasıl yapılır: komut satırını kullanarak eşzamanlılık verileri toplamak için profil oluşturucu ile tek başına .NET Framework uygulaması başlatma
bu konu, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bir .NET Framework tek başına (istemci) uygulaması başlatmak ve işlem ve iş parçacığı eşzamanlılık verilerini toplamak için Profil Oluşturma Araçları komut satırı araçlarının nasıl kullanılacağını açıklar

> [!NOTE]
> Profil oluşturma araçlarının yolunu almak için, bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). 64 bit bilgisayarlarda, araçların her ikisi de 64-bit ve 32 bit sürümleri mevcuttur. Profil oluşturucu komut satırı araçlarını kullanmak için araçlar yolunu komut Istemi penceresinin PATH ortam değişkenine eklemeniz ya da komutun kendisine eklemeniz gerekir.

 Profil Oluşturucu uygulamaya iliştirirken, veri toplamayı duraklatabilir ve devam ettirebilirsiniz. Profil oluşturma oturumunu sonlandırmak için, profil oluşturucunun artık uygulamaya bağlı olmaması ve profil oluşturucunun açıkça kapatılması gerekir.

## <a name="start-the-application-with-the-profiler"></a>Uygulamayı Profil Oluşturucu ile başlatma
 profil oluşturucu ile .NET Framework hedef uygulamayı başlatmak için *VSPerfClrEnv.exe* kullanarak .NET Framework profil oluşturma değişkenlerini ayarlayabilirsiniz. Ardından VSPerfCmd **/Start** ve **/Launch** seçeneklerini kullanarak profil oluşturucuyu başlatabilir ve uygulamayı başlatabilirsiniz. **/Start** ve **/Launch** seçeneklerini ve ilgili seçeneklerini tek bir komut satırında belirtebilirsiniz. Ayrıca, hedef uygulama başladığında veri toplamayı duraklatmak için komut satırına **/globaloff** seçeneğini ekleyebilirsiniz. Ardından, veri toplamaya başlamak için ayrı bir komut satırında **/GlobalOn** komutunu kullanın.

#### <a name="to-start-an-application-with-the-profiler"></a>Profil Oluşturucu ile bir uygulamayı başlatmak için

1. Bir komut istemi penceresi açın.

2. Profil oluşturucuyu başlatın. Şunu yazın:

    [VSPerfCmd](../profiling/vsperfcmd.md) **/Start: eşzamanlılık**[**,**{**resourceonly**&#124;**threadonly**}] **/output:** `OutputFile` [ `Options` ]

   - [/Start](../profiling/start.md) seçeneği profil oluşturucuyu başlatır.

     | Komut | Açıklama |
     |-------------------------------------| - |
     | **/Start: eşzamanlılık** | Hem kaynak çekişmesinin hem de iş parçacığı yürütme verilerinin toplanmasını mümkün. |
     | **/Start: eşzamanlılık, yalnızca Resource** | Yalnızca kaynak çekişme verilerinin toplanmasını mümkün. |
     | **/Start: eşzamanlılık, threadonly** | Yalnızca iş parçacığı yürütme verilerinin toplanmasını mümkün. |

   - /Start ile [/output](../profiling/output.md)**:** `OutputFile` seçeneği gereklidir.  `OutputFile` profil oluşturma verileri (. vsp) dosyasının adını ve konumunu belirtir.

     Aşağıdaki seçeneklerden herhangi birini, **/Start: eşzamanlılık** seçeneğiyle kullanabilirsiniz.

   | Seçenek | Açıklama |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `domain\` ]`username` | Profil oluşturucuya erişim verilecek hesabın isteğe bağlı etki alanını ve Kullanıcı adını belirtir. |
   | [/CrossSession](../profiling/crosssession.md) | Diğer oturum oturumlarda işlemlerin profilini oluşturmayı mümkün. |
   | [/WINCOUNTER](../profiling/wincounter.md) **:**`WinCounterPath` | profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir. |
   | [/AutoMark](../profiling/automark.md) **:**`Interval` | Yalnızca **/WINCOUNTER** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 MS 'dir. |
   | [/Events](../profiling/events-vsperfcmd.md) **:**`Config` | profil oluşturma sırasında toplanacak Windows (ETW) olayı için bir olay izleme olayı belirtir. ETW olayları ayrı bir (.*ETL*) dosyası. |

3. Hedef uygulamayı başlatın. Şunu yazın:

    **VSPerfCmd**  [/Launch](../profiling/launch.md) **:** `AppName` [ `Options` ] [ `Sample Event` ]

    Aşağıdaki seçeneklerden herhangi birini **/Launch** seçeneği ile kullanabilirsiniz.

   |Seçenek|Açıklama|
   |------------|-----------------|
   |[/args](../profiling/args.md) **:**`Arguments`|Hedef Uygulamaya geçirilecek komut satırı bağımsız değişkenlerini içeren bir dize belirtir.|
   |[/Console](../profiling/console.md)|Hedef komut satırı uygulamasını ayrı bir pencerede başlatır.|
   |[/targetclr](../profiling/targetclr.md) **:**`Version`|Bir uygulamaya çalışma zamanının birden fazla sürümü yüklendiğinde profil için ortak dil çalışma zamanının (CLR) sürümünü belirtir.|

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hedef uygulama çalışırken, *VSPerfCmd.exe* seçeneklerini kullanarak verileri dosyaya yazmayı başlatıp durdurarak veri toplamayı kontrol edebilirsiniz. Veri toplamayı denetlemek, program yürütmenin, uygulamanın başlatılması veya kapatılmasını gibi belirli bir bölümü için veri toplamanızı sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

1. Aşağıdaki *VSPerfCmd.exe* seçenek çiftleri veri toplamayı başlatır ve durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Tüm süreçler için veri toplamayı başlatır (**/GlobalOn**) veya Durdur (**/globaloff**).|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|İşlem KIMLIĞI () tarafından belirtilen işlem için (**/ProcessOn**) veya duraklar (**/ProcessOff**) veri toplamayı başlatır `PID` .|
    |[/Attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` } [/Detach](../profiling/detach.md)[**:**{ `PID`&#124;`ProcName` }]|**/Attach** işlem kimliği ( `PID` ) veya Işlem adı (ProcName) tarafından belirtilen işlem için veri toplamaya başlar. **/Detach** belirtilen işlem veya belirli bir işlem belirtilmemişse tüm işlemler için veri toplamayı durduruyor.|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu Sonlandır
 Profil oluşturma oturumunu sonlandırmak için, profil oluşturucunun veri toplamamalıdır. Profili oluşturulmuş uygulamayı kapatarak veya **VSPerfCmd/detach** seçeneğini çağırarak eşzamanlılık verilerinin toplanmasını durdurabilirsiniz. Ardından, profil oluşturucuyu kapatmak ve profil oluşturma veri dosyasını kapatmak için **VSPerfCmd/shutdown** seçeneğini çağırın. **VSPerfCLREnv/off** komutu profil oluşturma ortam değişkenlerini temizler.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sonlandırmak için

1. Profil oluşturucuyu hedef uygulamadan ayırmak için aşağıdakilerden birini yapın.

    - Hedef uygulamayı kapatın.

         -veya-

    - **VSPerfCmd/detach** yazın

2. Profil oluşturucuyu kapatma

     **VSPerfCmd**  [/Shutdown](../profiling/shutdown.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)
