---
title: Profil oluşturucu komut satırı-aracı yerel bileşeni, zamanlama verilerini al
description: C++ .exe veya .dll dosyası gibi bir yerel bileşen için ayrıntılı zamanlama verileri toplamak üzere Visual Studio Profil Oluşturma Araçları komut satırı araçlarının nasıl kullanılacağını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 36883074-9be8-4e90-a66f-7e87f21fcd30
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: d000addcf2e0e0ee324dd587b0dfb4096ed0b624
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122076650"
---
# <a name="how-to-instrument-a-native-stand-alone-component-and-collect-timing-data-with-the-profiler-from-the-command-line"></a>Nasıl yapılır: Yerel bir tek başına bileşeni izleme ve komut satırından profil oluşturucu ile zamanlama verileri toplama
Bu konu, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] C++ gibi bir yerel bileşeni işaretlemek için profil oluşturma araçları komut satırı araçlarının nasıl kullanılacağını açıklar.*exe* veya. *DLL* dosyası ve ayrıntılı zamanlama verilerini toplamak.

> [!NOTE]
> Profil oluşturma araçlarının yolunu almak için, bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). 64 bit bilgisayarlarda, araçların her ikisi de 64-bit ve 32 bit sürümleri mevcuttur. Profil oluşturucu komut satırı araçlarını kullanmak için araçlar yolunu komut Istemi penceresinin PATH ortam değişkenine eklemeniz ya da komutun kendisine eklemeniz gerekir.

İzleme yöntemini kullanarak bir bileşenden ayrıntılı zamanlama verileri toplamak için, bileşenin belgelenmiş bir sürümünü oluşturmak için [VSInstr.exe](../profiling/vsinstr.md) aracını kullanın. Ardından profil oluşturucuyu başlatın. Belgelenmiş bileşen yürütüldüğünde, zamanlama verileri bir veri dosyasına otomatik olarak toplanır. Profil oluşturma oturumu sırasında veri toplamayı duraklatabilir ve devam ettirebilirsiniz.

 Profil oluşturma oturumunu sonlandırmak için hedef uygulamayı kapatır ve sonra profil oluşturucuyu açıkça kapatın.

## <a name="start-the-profiling-session"></a>Profil oluşturma oturumunu Başlat

#### <a name="to-start-profiling-by-using-the-instrumentation-method"></a>İzleme yöntemini kullanarak profil oluşturmayı başlatmak için

1. Bir komut istemi penceresi açın.

2. Hedef uygulamanın belgelenmiş bir sürümünü oluşturmak için **vsinstr** aracını kullanın.

3. Profil oluşturucuyu başlatın. Şunu yazın:

    **VSPerfCmd/start: Trace/output:** `OutputFile` [`Options`]

   - [/Start](../profiling/start.md)**: Trace** seçeneği profil oluşturucuyu başlatır.

   - /Start ile [/output](../profiling/output.md)**:** `OutputFile` seçeneği gereklidir.  `OutputFile` profil oluşturma verileri (. vsp) dosyasının adını ve konumunu belirtir.

     Aşağıdaki seçeneklerden birini veya daha fazlasını **/Start: Trace** seçeneği ile kullanabilirsiniz.

   | Seçenek | Açıklama |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Profili oluşturulan işlemin sahibi olan hesabın etki alanını ve Kullanıcı adını belirtir. Bu seçenek yalnızca, işlem oturum açan kullanıcıdan farklı bir kullanıcı olarak çalışıyorsa gereklidir. işlem sahibi, Windows görev yöneticisi 'nin **işlemler** sekmesinde **kullanıcı adı** sütununda listelenir. |
   | [/CrossSession](../profiling/crosssession.md) | Diğer oturumlardaki işlemlerin profilini oluşturmaya izin vermez. Uygulama farklı bir oturumda çalışıyorsa, bu seçenek gereklidir. oturum tanımlayıcısı, Windows görev yöneticisi 'nin süreçler sekmesindeki **oturum kimliği** sütununda listelenir. **/CS** , **/CrossSession** için bir kısaltma olarak belirtilebilir. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Profil Oluşturucu veri koleksiyonu duraklatılmış şekilde başlatılır. Profil oluşturmayı sürdürmeye yönelik [/GlobalOn](../profiling/globalon-and-globaloff.md) kullanın. |
   | [/Counter](../profiling/counter.md) **:**`Config` | ' De belirtilen işlemci performans sayacından bilgi toplar `Config` . Her profil oluşturma olayında toplanan verilere sayaç bilgileri eklenir. |
   | [/WINCOUNTER](../profiling/wincounter.md) **:**`WinCounterPath` | profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir. |
   | [/AutoMark](../profiling/automark.md) **:**`Interval` | Yalnızca **/WINCOUNTER** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 MS 'dir. |
   | [/Events](../profiling/events-vsperfcmd.md) **:**`Config` | profil oluşturma sırasında toplanacak Windows (ETW) olayı için bir olay izleme olayı belirtir. ETW olayları ayrı bir (.*ETL*) dosyası. |

4. Hedef uygulamayı normal şekilde başlatın.

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hedef uygulama çalışırken, *VSPerfCmd.exe* seçeneklerini kullanarak verileri dosyaya yazmayı başlatıp durdurarak veri toplamayı kontrol edebilirsiniz. Veri toplamayı denetlemek, program yürütmesinin, uygulamayı başlatma veya kapatma gibi belirli bir bölümü için veri toplamanızı sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki seçenek çiftleri veri toplamayı başlatır ve durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Tüm süreçler için veri toplamayı başlatır (**/GlobalOn**) veya Durdur (**/globaloff**).|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|İşlem KIMLIĞI () tarafından belirtilen işlem için (**/ProcessOn**) veya duraklar (**/ProcessOff**) veri toplamayı başlatır `PID` .|
    |[/ThreadOn](../profiling/threadon-and-threadoff.md) **:** `TID` [/ThreadOff](../profiling/threadon-and-threadoff.md) **:**`TID`|İş parçacığı KIMLIĞI () tarafından belirtilen iş parçacığı için (**/ThreadOn**) veya Durdur (**/ThreadOff**) veri toplamayı başlatır `TID` .|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu Sonlandır
 Profil oluşturma oturumunu sonlandırmak için, Araçlı bileşeni çalıştıran uygulamayı kapatın ve ardından **VSPerfCmd** [/Shutdown](../profiling/shutdown.md) seçeneğini çağırıp profil oluşturucuyu kapatın ve profil oluşturma veri dosyasını kapatın.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sonlandırmak için

1. Hedef uygulamayı kapatın.

2. Profil oluşturucuyu kapatın. Şunu yazın:

     **VSPerfCmd/shutdown**

## <a name="see-also"></a>Ayrıca bkz.
- [Tek başına uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [İzleme yöntemi veri görünümleri](../profiling/instrumentation-method-data-views.md)
