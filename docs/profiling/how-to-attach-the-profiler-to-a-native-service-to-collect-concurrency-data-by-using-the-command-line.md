---
title: Eşzamanlılık verilerini almak için yerel hizmete profil oluşturma ekleme
description: Yerel Visual Studio Profil Oluşturma Araçları (C/C++) hizmetten işlem ve iş parçacığı eşzamanlılık verileri toplamak için komut satırına ait verileri kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 283a1ee1-b43e-4daf-95ae-1311925a42a8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: dbc3cc968bc1814802fe64638ee3096b34404ff85320560b11c1cd31e74934c9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121396569"
---
# <a name="how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line-vsperfcmd"></a>Nasıl kullanılır: Komut satırı (VSPerfCmd) kullanarak eşzamanlılık verileri toplamak için yerel bir hizmete profil oluşturma ekleme
Bu makalede, Profil Oluşturma Araçları komut satırı araçlarını kullanarak profilleyiciyi yerel (C/C++) hizmetine ekleme ve örnekleme yöntemini kullanarak işlem ve iş parçacığı eşzamanlılık verileri toplama işlemleri [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] açıklanmıştır.

> [!NOTE]
> Windows 8 ve Windows Server 2012'daki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturmanın bu platformlarda veri toplaması sırasında önemli değişiklikler gerektirmektedir. UWP uygulamaları için yeni koleksiyon teknikleri de gerekir. Uygulama [ve uygulama Windows 8 performans Windows Server 2012 bakın.](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)

> [!NOTE]
> Profil oluşturma araçlarının yolunu almak için [bkz. Komut satırı araçlarının yolunu belirtme.](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md) 64 bit bilgisayarlarda, araçların hem 64 bit hem de 32 bit sürümleri kullanılabilir. Profil oluşturma komut satırı araçlarını kullanmak için, araç yolunu Komut İstemi penceresinin PATH ortam değişkenine eklemeniz veya komutun kendisine eklemeniz gerekir.

 Profil oluşturma hizmetine bağlıyken veri toplamayı duraklatabilir ve sürdürebilirsiniz. Profil oluşturma oturumunu sona erdirmak için, profil oluşturmanın artık hizmete bağlı olması ve Profiler'ın açıkça kapatılamaması gerekir.

## <a name="attach-the-profiler"></a>Profilleyiciyi ekleme
 Profilleyiciyi yerel bir hizmete eklemek için **VSPerfCmd/start** ve **/attach** seçeneklerini kullanarak profilleyiciyi başlatarak hedef uygulamaya iliştirebilirsiniz. **/start ve /attach** seçeneklerini **tek** bir komut satırı üzerinde belirtebilirsiniz. Hedef uygulamanın başında veri toplamayı duraklatmak için **/globaloff** seçeneğini de ekebilirsiniz. Ardından veri **toplamaya başlamak için /globalon** kullanırsanız.

#### <a name="to-attach-the-profiler-to-a-native-service"></a>Profilleyiciyi yerel bir hizmete eklemek için

1. Hizmet çalışmıyorsa, hizmeti başlatabilirsiniz.

2. Bir komut istemine aşağıdakini yazarak profil oluşturma başlatabilirsiniz:

    [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency /output:** `OutputFile` [ `Options` ]

   - [/output](../profiling/output.md)**: seçeneği** / start ile `OutputFile` **gereklidir.** `OutputFile` profil oluşturma verileri (.vsp) dosyasının adını ve konumunu belirtir.

     Aşağıdaki tabloda **/start** seçeneğiyle herhangi bir seçeneği kullanabilirsiniz.

   > [!NOTE]
   > Hizmetlerin çoğu **/user ve** **/crosssession seçeneğini** gerektirir.

   | Seçenek | Açıklama |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:**[ `Domain\` ]`UserName` | Profil oluşturma için erişim izni verilen hesabın isteğe bağlı etki alanını ve kullanıcı adını belirtir. |
   | [/crosssession](../profiling/crosssession.md) | Diğer oturum açma oturumlarında işlemlerin profil oluşturmasını sağlar. |
   | [/wincounter:](../profiling/wincounter.md) `WinCounterPath` | Profil oluşturma Windows toplanacak bir performans sayacı belirtir. |
   | [/automark:](../profiling/automark.md) `Interval` | Yalnızca **/wincounter ile** kullanın. Performans sayacı toplama olayları arasındaki milisaniye Windows sayısını belirtir. Varsayılan değer 500'dür. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Profil oluşturma sırasında toplanacak Windows (ETW) olayı için bir Olay İzleme belirtir. ETW olayları ayrı bir (.etl) dosyasında toplanır. |

3. Komut istemine aşağıdaki komutu yazarak profiler'i hizmete iliştirin:

    **VSPerfCmd /attach:**`PID`

    `PID` hedef uygulamanın işlem kimliğini veya işlem adını belirtir. Görev Yöneticisi'nde çalışan tüm işlemlerin işlem kimliklerini Windows görüntüebilirsiniz.

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hedef uygulama çalışırken, veri toplamayı denetleme seçenekleriyle dosyada veri yazmayı başlatarak *ve durdurarakVSPerfCmd.exe* yapabilirsiniz. Veri toplamayı denetleyerek, uygulamanın başlatılıyor veya kapatılıyor gibi program yürütmenin belirli bir bölümü için veri toplayabilirsiniz.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki tabloda yer alan seçenek çiftleri veri toplamayı başlatacak ve durduracak. Her seçeneği ayrı bir komut satırı üzerinde belirtin. Veri toplamayı birden çok kez açabilirsiniz ve kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Tüm işlemler **için veri toplamayı** başlatır ( /globalon ) veya durdurur (**/globaloff).**|
    |[/processon:](../profiling/processon-and-processoff.md)  `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|İşlem kimliğinin ( ) tarafından belirtilen işlem için veri koleksiyonunu (**/processon**) veya durdurur (**/processoff).** `PID`|
    |[/attach:](../profiling/attach.md) { `PID`&#124;`ProcName` } [/detach](../profiling/detach.md)[**:**{ `PID`&#124;`ProcName` }]|**/attach,** işlem kimliği ( ) veya işlem adı ( `PID` *ProcName*) tarafından belirtilen işlem için veri toplamaya başlar. **/detach,** belirtilen işlem için veya herhangi bir işlem belirtilmezse tüm işlemler için veri toplamayı durdurur.|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sona er
 Profil oluşturma oturumunu sona erdirecek şekilde, profil oluşturmanın veri toplaması gerekir. Hizmeti durdurarak veya **VSPerfCmd /detach** seçeneğini kullanarak eşzamanlılık yöntemiyle profili yapılan yerel bir hizmetten veri toplamayı durdurabilirsiniz. Ardından **VSPerfCmd /shutdown** seçeneğini çağırarak profil oluşturma verilerini kapatabilirsiniz.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdir

1. Hizmeti durdurarak veya bir komut istemine aşağıdaki komutu yazarak profilleyiciyi hedef uygulamadan ayırabilirsiniz:

     **VSPerfCmd /detach yazın**

2. Komut istemine aşağıdaki komutu yazarak profil oluşturmayı kapatın:

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)
