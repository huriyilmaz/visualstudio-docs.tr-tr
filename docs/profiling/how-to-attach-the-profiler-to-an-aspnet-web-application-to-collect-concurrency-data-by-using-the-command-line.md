---
title: Eşzamanlı veri toplamak için ASP.NET uygulamaya profil oluşturucu ekleme
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0e215fdd-55f8-43ef-9534-06542eefe223
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 04745140c3f92b3d601a03ddbcd68259b3959364
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74776476"
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line"></a>Nasıl kullanılır: Komut satırını kullanarak eşzamanlılık verileri toplamak için profiloluşturcuğu ASP.NET bir web uygulamasına takın
Bu makalede, profil [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oluşturucuyu bir ASP.NET uygulamasına eklemek ve işlem ve iş parçacığı eşzamanlılık verilerini toplamak için Profil Oluşturma Araçları komut satırı araçlarının nasıl kullanılacağı açıklanmaktadır.

Profil oluşturma araçlarına giden yolu almak [için](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)bkz. 64 bit bilgisayarlarda, araçların hem 64 bit hem de 32 bit sürümleri kullanılabilir. Profil oluşturucu komut satırı araçlarını kullanmak için, komut istemi penceresinin PATH ortamı değişkenine araçlar yolunu eklemeniz veya komutun kendisine eklemeniz gerekir.

 Eşzamanlı veri toplamak için, profil oluşturucuyu Web sitenizi barındıran ASP.NET işleyici işlemine bağlarsınız. Profil oluşturucu uygulamaya bağlı yken, veri toplamayı duraklatabilir ve devam ettirebilirsiniz. Profil oluşturma oturumunu sona erdirmek için profil oluşturucuartık uygulamaya eklenmemeli ve Profil Oluşturucu açıkça kapatılmalıdır. Çoğu durumda, oturumun sonunda profil oluşturma ortamı değişkenlerini temizlemeniz gerekir.

## <a name="attach-the-profiler"></a>Profil oluşturucuyu takın

#### <a name="to-attach-the-profiler-to-a-aspnet-application"></a>ProfiloluşturcIyi bir ASP.NET uygulamasına eklemek için

1. Aşağıdaki komutu yazarak profiloluşturucuyu başlatın:

    [VSPerfCmd](../profiling/vsperfcmd.md) **/start:eşzamanlılık /çıktı:** `OutputFile` [`Options`]

   - [/başlat](../profiling/start.md) seçeneği, kaynak çekişme verileri toplamak için profil oluşturucuyu başlatır.

   - [/output](../profiling/output.md)**:** `OutputFile` seçeneği **/start**ile gereklidir. `OutputFile`profil oluşturma verileri (.vsp) dosyasının adını ve konumunu belirtir.

     Sonraki tabloda **/başlat** seçeneği ile herhangi bir seçeneği kullanabilirsiniz.

   | Seçenek | Açıklama |
   | - | - |
   | [/kullanıcı](../profiling/user-vsperfcmd.md) **:**[ ]`Domain\``UserName` | Profiloluşturucuya erişim hakkı verilecek isteğe bağlı etki alanını ve hesabın kullanıcı adını belirtir. |
   | [/çapraz oturum](../profiling/crosssession.md) | Diğer oturum oturumlarında işlemlerin profilini çıkarmasağlar. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Yalnızca **/wincounter** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500'dür. |
   | [/olaylar](../profiling/events-vsperfcmd.md) **:**`Config` | Profil oluşturma sırasında toplanacak windows için olay izleme (ETW) olayı belirtir. ETW olayları ayrı bir şekilde toplanır (.* etl*) dosyası. |

2. ASP.NET uygulamayı normal şekilde başlatın.

3. Profilleyiciyi aşağıdaki komutu yazarak ASP.NET alt işlemine takın:**VSPerfCmd /attach:** `PID` [**/targetclr:**`Version`]

   - `PID`ASP.NET işçi işleminin kimliğini veya adını belirtir. Windows Görev Yöneticisi'nde çalışan tüm işlemlerin işlem lerini görüntüleyebilirsiniz.

   - [/targetclr](../profiling/targetclr.md) **:** `Version` bir uygulamada çalışma süresinin birden fazla sürümü yüklendiğinde, ortak dil çalışma zamanının (CLR) profilinin sürümünü belirtir. Bu parametre isteğe bağlıdır.

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Uygulama çalışırken, *VSPerfCmd.exe* seçeneklerini kullanarak dosyaya veri yazısını başlatıp durdurarak veri toplamayı denetleyebilirsiniz. Veri toplamayı denetleyerek, uygulamanın başlatılması veya kapatılması gibi program yürütmesinin belirli bir bölümü için veri toplayabilirsiniz.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki tablodaki VSPerfCmd seçenekleri çiftleri veri toplamayı başlatın ve durdurun. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Tüm işlemler için **(/globalon)** başlatır veya durur (**/globaloff**) veri toplama.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [processoff](../profiling/processon-and-processoff.md) **:**  `PID`|İşlem Kimliğinin (`PID`) belirttiği işlem için **(/processon)** başlatır veya (**/processoff)** veri toplamayı durdurur.|
    |[/ekle](../profiling/attach.md) **:**:`PID` `ProcName`{&#124;} [/ayırma](../profiling/detach.md) `ProcName`[**:**{`PID`&#124;}]|**/ekle** işlem kimliği (`PID`) veya işlem adı *(ProcName)* belirttiği işlem için veri toplamaya başlar. **/detach,** belirtilen işlem için veya işlem belirtilmemişse tüm işlemler için veri toplamayı durdurur.|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sonlandırma
 Profil oluşturma oturumunu sona erdirmek için profil oluşturucunun veri toplamaması gerekir. ASP.NET alt işlemini yeniden başlatarak veya **VSPerfCmd /detach** seçeneğini çağırarak eşzamanlılık yöntemiyle profillenmiş bir uygulamadan veri toplamayı durdurabilirsiniz. Daha sonra profil oluşturucuyu kapatmak ve profil oluşturma veri dosyasını kapatmak için **VSPerfCmd /shutdown** seçeneğini çağırırsınız. **VSPerfClrEnv /globaloff** komutu profil oluşturma ortamı değişkenlerini temizler, ancak bilgisayar yeniden başlatılıncaya kadar sistem yapılandırması sıfırlanmaz.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdirmek için

1. Profiloluşturucuyu kapatarak veya komut istemine aşağıdakileri yazarak hedef uygulamadan ayırın:

     **VSPerfCmd /ayırma**

2. Bir komut isteminde aşağıdaki komutu yazarak profiloluşturucuyu kapatın:

     **VSPerfCmd**  [/kapatma](../profiling/shutdown.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Web uygulamaları ASP.NET profil](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [VSPerfASPNETCmd ile hızlı web sitesi profiloluşturma](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)
