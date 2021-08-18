---
title: Profil oluşturma komut satırı - İstemci .NET uygulamasını açın, eşzamanlılık verilerini al
description: Tek başına bir .NET Visual Studio Profil Oluşturma Araçları başlatmak ve işlem ve iş parçacığı eşzamanlılık verileri toplamak için komut satırı araçlarını kullanmayı öğrenin.
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
ms.openlocfilehash: 2d0bc0d26c6d7232f0264455c9e4a2db987aef47
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122033479"
---
# <a name="how-to-launch-a-stand-alone-net-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line"></a>Nasılürüm: Komut .NET Framework eşzamanlılık verileri toplamak için tek başına bir .NET Framework uygulaması başlatma
Bu konuda tek başına (istemci) bir Profil Oluşturma Araçları başlatmak ve işlem ve iş parçacığı eşzamanlılık verileri toplamak için .NET Framework komut satırı araçlarının [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nasıl kullanımı açıklanmıştır

> [!NOTE]
> Profil oluşturma araçlarının yolunu almak için [bkz. Komut satırı araçlarının yolunu belirtme.](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md) 64 bit bilgisayarlarda, araçların hem 64 bit hem de 32 bit sürümleri kullanılabilir. Profil oluşturma komut satırı araçlarını kullanmak için, araç yolunu Komut İstemi penceresinin PATH ortam değişkenine eklemeniz veya komutun kendisine eklemeniz gerekir.

 Profiler uygulamaya bağlıyken veri toplamayı duraklatabilir ve sürdürebilirsiniz. Profil oluşturma oturumunu sona erdirmak için, Profiler'ın artık uygulamaya bağlı olması ve Profil Oluşturma'nın açıkça kapatılamaması gerekir.

## <a name="start-the-application-with-the-profiler"></a>Uygulamayı profil oluşturma ile başlatma
 Profil Oluşturma .NET Framework bir hedef uygulama başlatmak için profil *oluşturma değişkenleriniVSPerfClrEnv.exe* için .NET Framework kullanın. Ardından VSPerfCmd **/start** ve **/launch** seçeneklerini kullanarak Profiler'ı başlatarak uygulamayı başlatabilirsiniz. **/start** ve **/launch seçeneklerini tek** bir komut satırı üzerinde belirtebilirsiniz. Hedef uygulama başlatıldığında veri **toplamayı duraklatmak** için komut satırına /globaloff seçeneğini de ekebilirsiniz. Ardından veri toplamaya başlamak için ayrı bir komut satırı üzerinde **/globalon** kullanırsanız.

#### <a name="to-start-an-application-with-the-profiler"></a>Bir uygulamayı profil oluşturma ile başlatmak için

1. Bir komut istemi penceresi açın.

2. Profilleyiciyi başlatma. Şunu yazın:

    [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency**[**,**{**ResourceOnly**&#124;**ThreadOnly**}] **/output:** `OutputFile` [ `Options` ]

   - [/start seçeneği](../profiling/start.md) profilleyiciyi başlatıyor.

     | Komut | Açıklama |
     |-------------------------------------| - |
     | **/start:concurrency** | Hem kaynak hem de iş parçacığı yürütme verilerini toplamaya olanak sağlar. |
     | **/start:concurrency,resourceonly** | Yalnızca kaynak musiki verilerini toplamaya olanak sağlar. |
     | **/start:concurrency,threadonly** | Yalnızca iş parçacığı yürütme verilerini toplamayı sağlar. |

   - [/output](../profiling/output.md)**: seçeneği** / start ile `OutputFile` **gereklidir.** `OutputFile` profil oluşturma verileri (.vsp) dosyasının adını ve konumunu belirtir.

     **/start:concurrency** seçeneğiyle aşağıdaki seçeneklerden herhangi birini kullanabilirsiniz.

   | Seçenek | Açıklama |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:**[ `domain\` ]`username` | Profil oluşturma için erişim izni verilen hesabın isteğe bağlı etki alanını ve kullanıcı adını belirtir. |
   | [/crosssession](../profiling/crosssession.md) | Diğer oturum açma oturumlarında işlemlerin profil oluşturmasını sağlar. |
   | [/wincounter:](../profiling/wincounter.md) `WinCounterPath` | Profil oluşturma Windows toplanacak bir performans sayacı belirtir. |
   | [/automark:](../profiling/automark.md) `Interval` | Yalnızca **/wincounter ile** kullanın. Performans sayacı toplama olayları arasındaki milisaniye Windows sayısını belirtir. Varsayılan değer 500 ms'tir. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Profil oluşturma sırasında toplanacak Windows (ETW) olayı için bir Olay İzleme belirtir. ETW olayları ayrı bir () içinde toplanır.*etl*) dosyasını seçin. |

3. Hedef uygulamayı başlatma. Şunu yazın:

    **VSPerfCmd**[/launch:](../profiling/launch.md)  [ ] `AppName` [ `Options` `Sample Event` ]  

    **/launch** seçeneğiyle aşağıdaki seçeneklerden herhangi birini kullanabilirsiniz.

   |Seçenek|Açıklama|
   |------------|-----------------|
   |[/args:](../profiling/args.md) `Arguments`|Hedef uygulamaya geçirilen komut satırı bağımsız değişkenlerini içeren bir dize belirtir.|
   |[/console](../profiling/console.md)|Hedef komut satırı uygulamasını ayrı bir pencerede başlatır.|
   |[/targetclr](../profiling/targetclr.md) **:**`Version`|Bir uygulamada birden fazla çalışma zamanı sürümü yüklendiğinde profili oluşturmak için ortak dil çalışma zamanının (CLR) sürümünü belirtir.|

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hedef uygulama çalışırken veri toplamayı, veri toplama seçeneklerini kullanarak dosyada veri yazmayı başlatarak *ve durdurarakVSPerfCmd.exe* yapabilirsiniz. Veri toplamayı denetlemek, uygulamanın başlat veya kapatılması gibi program yürütmenin belirli bir bölümü için veri toplamaya olanak sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

1. Aşağıdaki iki seçenek *VSPerfCmd.exe* toplamayı başlat ve durdur. Her seçeneği ayrı bir komut satırı üzerinde belirtin. Veri toplamayı birden çok kez açabilirsiniz ve kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Tüm işlemler **için veri toplamayı** başlatır ( /globalon ) veya durdurur (**/globaloff).**|
    |[/processon:](../profiling/processon-and-processoff.md)  `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|İşlem kimliği ( ) tarafından belirtilen işlem için veri toplamayı (**/processon**) veya durdurur ( `PID` ).|
    |[/attach:](../profiling/attach.md) { `PID`&#124;`ProcName` } [/detach](../profiling/detach.md)[**:**{ `PID`&#124;`ProcName` }]|**/attach,** işlem kimliği ( ) veya işlem adı `PID` (ProcName) tarafından belirtilen işlem için veri toplamaya başlar. **/detach,** belirtilen işlem için veya belirli bir işlem belirtilmezse tüm işlemler için veri toplamayı durdurur.|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sona er
 Profil oluşturma oturumunu sona erdirecek şekilde profil oluşturma, veri toplamama gerekir. Profili yapılan uygulamayı kapatarak veya **VSPerfCmd /detach** seçeneğini kullanarak eşzamanlılık verilerini toplamayı durdurabilirsiniz. Ardından **VSPerfCmd /shutdown** seçeneğini çağırarak profil oluşturma verilerini kapatabilirsiniz. **VSPerfClrEnv /off** komutu profil oluşturma ortam değişkenlerini temizler.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdir

1. Profilleyiciyi hedef uygulamadan ayırmak için aşağıdakilerden birini yapın.

    - Hedef uygulamayı kapatın.

         -veya-

    - **VSPerfCmd /detach yazın**

2. Profilleyiciyi kapatma

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)
