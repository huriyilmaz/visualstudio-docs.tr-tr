---
title: Eşzamanlılık verilerini ASP.NET profil oluşturma
description: Profil Visual Studio Profil Oluşturma Araçları bir uygulamaya eklemek ve işlem ve iş parçacığı eşzamanlılık verilerini ASP.NET komut satırı araçlarını kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 0e215fdd-55f8-43ef-9534-06542eefe223
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 97bb80ed996ce523d01d9228293f419ba011d8e4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122033635"
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line"></a>Nasıl kullanılır: Komut ASP.NET eşzamanlılık verileri toplamak için bir web uygulamasına profil oluşturma ekleme

Bu makalede, profil Profil Oluşturma Araçları bir ASP.NET eklemek ve işlem ve iş parçacığı eşzamanlılık verilerini toplamak için ASP.NET komut [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] satırı araçlarının nasıl kullanımı açıklanmıştır.

Profil oluşturma araçlarının yolunu almak için [bkz. Komut satırı araçlarının yolunu belirtme.](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md) 64 bit bilgisayarlarda, araçların hem 64 bit hem de 32 bit sürümleri kullanılabilir. Profil oluşturma komut satırı araçlarını kullanmak için, araç yolunu Komut İstemi penceresinin PATH ortam değişkenine eklemeniz veya komutun kendisine eklemeniz gerekir.

 Eşzamanlılık verileri toplamak için, profilleyiciyi Web sitenizi barındıran ASP.NET çalışma sürecine iliştirebilirsiniz. Profiler uygulamaya bağlıyken veri toplamayı duraklatabilir ve sürdürebilirsiniz. Profil oluşturma oturumunu sona erdirmak için, profil oluşturmanın artık uygulamaya bağlı olması ve Profiler'ın açıkça kapatılamaması gerekir. Çoğu durumda, bir oturumun sonunda profil oluşturma ortam değişkenlerini temizlemelisiniz.

## <a name="attach-the-profiler"></a>Profilleyiciyi ekleme

#### <a name="to-attach-the-profiler-to-a-aspnet-application"></a>Profilleyiciyi bir ASP.NET eklemek için

1. Aşağıdaki komutu yazarak profil oluşturmayı başlatabilirsiniz:

    [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency /output:** `OutputFile` [ `Options` ]

   - [/start seçeneği,](../profiling/start.md) kaynakla ilgili veri toplamak için profilleyiciyi başlatıyor.

   - [/output](../profiling/output.md)**: seçeneği** / start ile `OutputFile` **gereklidir.** `OutputFile` profil oluşturma verileri (.vsp) dosyasının adını ve konumunu belirtir.

     Aşağıdaki tabloda **/start** seçeneğiyle herhangi bir seçeneği kullanabilirsiniz.

   | Seçenek | Açıklama |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:**[ `Domain\` ]`UserName` | Profil oluşturma için erişim izni verilen hesabın isteğe bağlı etki alanını ve kullanıcı adını belirtir. |
   | [/crosssession](../profiling/crosssession.md) | Diğer oturum açma oturumlarında işlemlerin profil oluşturmasını sağlar. |
   | [/wincounter:](../profiling/wincounter.md) `WinCounterPath` | Profil oluşturma Windows toplanacak bir performans sayacı belirtir. |
   | [/automark:](../profiling/automark.md) `Interval` | Yalnızca **/wincounter ile** kullanın. Performans sayacı toplama olayları arasındaki milisaniye Windows sayısını belirtir. Varsayılan değer 500'dür. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Profil oluşturma sırasında toplanacak Windows (ETW) olayı için bir Olay İzleme belirtir. ETW olayları ayrı bir () içinde toplanır.*etl*) dosyasını seçin. |

2. Uygulama ASP.NET normal şekilde başlatabilirsiniz.

3. Profil oluşturma işleyicisini ASP.NET komutu yazarak işleyiciye iliştirin:**VSPerfCmd /attach:** `PID` [**/targetclr:** `Version` ]

   - `PID`çalışan işleminin kimliğini veya ASP.NET belirtir. Görev Yöneticisi'nde çalışan tüm işlemlerin işlem kimliklerini Windows görüntüebilirsiniz.

   - [/targetclr:](../profiling/targetclr.md)  bir uygulamada birden fazla çalışma zamanı sürümü yüklendiğinde profili oluşturmak için ortak dil çalışma `Version` zamanının (CLR) sürümünü belirtir. Bu parametre isteğe bağlıdır.

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Uygulama çalışırken, veri toplama seçeneklerini kullanarak veri yazmayı başlatarak ve durdurarak veri *toplamayıVSPerfCmd.exe* yapabilirsiniz. Veri toplamayı denetleyerek, uygulamanın başlatılıyor veya kapatılıyor gibi program yürütmenin belirli bir bölümü için veri toplayabilirsiniz.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki tabloda yer alan VSPerfCmd seçenekleri çiftleri veri toplamayı başlat ve durdur. Her seçeneği ayrı bir komut satırı üzerinde belirtin. Veri toplamayı birden çok kez açabilirsiniz ve kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Tüm işlemler **için veri toplamayı** başlatır ( /globalon ) veya durdurur (**/globaloff).**|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [processoff:](../profiling/processon-and-processoff.md)   `PID`|İşlem kimliğinin ( ) tarafından belirtilen işlem için veri koleksiyonunu (**/processon**) veya durdurur (**/processoff).** `PID`|
    |[/attach:](../profiling/attach.md) { `PID`&#124;`ProcName` } [/detach](../profiling/detach.md)[**:**{ `PID`&#124;`ProcName` }]|**/attach,** işlem kimliği ( ) veya işlem adı ( `PID` *ProcName*) tarafından belirtilen işlem için veri toplamaya başlar. **/detach,** belirtilen işlem için veya herhangi bir işlem belirtilmezse tüm işlemler için veri toplamayı durdurur.|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sona er
 Profil oluşturma oturumunu sona erdirecek şekilde profil oluşturma, veri toplamama gerekir. ASP.NET çalışan işlemini yeniden başlatarak veya **VSPerfCmd /detach** seçeneğini başlatarak eşzamanlılık yöntemiyle profili profili yapılan bir uygulamadan veri toplamayı durdurabilirsiniz. Ardından **VSPerfCmd /shutdown** seçeneğini çağırarak profil oluşturma verilerini kapatabilirsiniz. **VSPerfClrEnv /globaloff** komutu profil oluşturma ortam değişkenlerini temizler, ancak bilgisayar yeniden başlatana kadar sistem yapılandırması sıfırlanmaz.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdir

1. Profilleyiciyi kapatarak veya komut istemine aşağıdakini yazarak hedef uygulamadan ayırabilirsiniz:

     **VSPerfCmd /detach**

2. Komut istemine aşağıdaki komutu yazarak profil oluşturma profilini kapatın:

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Web ASP.NET profil oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [VSPerfASPNETCmd ile hızlı web sitesi profili oluşturma](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)
