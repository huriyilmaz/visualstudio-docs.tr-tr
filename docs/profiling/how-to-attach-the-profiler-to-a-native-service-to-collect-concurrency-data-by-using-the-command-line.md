---
title: 'VSPerfCmd: Eşzamanlılık verileri elde etmek için profil oluşturucuyu yerel hizmete takın'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 283a1ee1-b43e-4daf-95ae-1311925a42a8
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: 705e55363f4f8657da20fe66cd4369188f133cdb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74776614"
---
# <a name="how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line"></a>Nasıl yapılır: Komut satırını kullanarak eşzamanlılık verileri toplamak için yerel bir hizmete profil oluşturucu ekleme
Bu makalede, profil [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oluşturucu (C/C++) bir hizmete profil oluşturucu eklemek ve örnekleme yöntemini kullanarak işlem ve iş parçacığı eşzamanlılık verilerini toplamak için Profil Oluşturma Araçları komut satırı araçlarının nasıl kullanılacağı açıklanmaktadır.

> [!NOTE]
> Windows 8 ve Windows Server 2012'deki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturucusu bu platformlarda veri toplama şeklinde önemli değişiklikler gerektiriyordu. UWP uygulamaları da yeni toplama teknikleri gerektirir. [Windows 8 ve Windows Server 2012 uygulamalarında Performans Araçları'na](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)bakın.

> [!NOTE]
> Profil oluşturma araçlarına giden yolu almak [için](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)bkz. 64 bit bilgisayarlarda, araçların hem 64 bit hem de 32 bit sürümleri kullanılabilir. Profil oluşturucu komut satırı araçlarını kullanmak için, komut istemi penceresinin PATH ortamı değişkenine araçlar yolunu eklemeniz veya komutun kendisine eklemeniz gerekir.

 Profil oluşturucu hizmete bağlıyken, veri toplamayı duraklatabilir ve devam ettirebilirsiniz. Profil oluşturma oturumunu sona erdirmek için profil oluşturucunun hizmete artık eklenmemesi ve Profil Oluşturucu'nun açıkça kapatılması gerekir.

## <a name="attach-the-profiler"></a>Profil oluşturucuyu takın
 Profiloluşturciyi yerel bir hizmete eklemek için, profiloluşturcuyumu başlatmak ve hedef uygulamaya takmak için **VSPerfCmd/start** **ve/attach** seçeneklerini kullanırsınız. Tek bir komut satırında **/başlat** ve **/ekle** ve ilgili seçeneklerini belirtebilirsiniz. Hedef uygulamanın başında veri toplamayı duraklatmak için **/globaloff** seçeneğini de ekleyebilirsiniz. Daha sonra veri toplamaya başlamak için **/globalon'u** kullanırsınız.

#### <a name="to-attach-the-profiler-to-a-native-service"></a>ProfiloluşturcIyi yerel bir hizmete eklemek için

1. Hizmet çalışmıyorsa, hizmeti başlatın.

2. Bir komut istemi aşağıdaki yazarak profil oluşturucu başlatın:

    [VSPerfCmd](../profiling/vsperfcmd.md) **/start:eşzamanlılık /çıktı:** `OutputFile` [`Options`]

   - [/output](../profiling/output.md)**:** `OutputFile` seçeneği **/start**ile gereklidir. `OutputFile`profil oluşturma verileri (.vsp) dosyasının adını ve konumunu belirtir.

     Sonraki tabloda **/başlat** seçeneği ile herhangi bir seçeneği kullanabilirsiniz.

   > [!NOTE]
   > Çoğu hizmet **/kullanıcı** ve **/çapraz oturum** seçeneği gerektirir.

   | Seçenek | Açıklama |
   | - | - |
   | [/kullanıcı](../profiling/user-vsperfcmd.md) **:**[ ]`Domain\``UserName` | Profiloluşturucuya erişim hakkı verilecek isteğe bağlı etki alanını ve hesabın kullanıcı adını belirtir. |
   | [/çapraz oturum](../profiling/crosssession.md) | Diğer oturum oturumlarında işlemlerin profilini çıkarmasağlar. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Yalnızca **/wincounter** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500'dür. |
   | [/olaylar](../profiling/events-vsperfcmd.md) **:**`Config` | Profil oluşturma sırasında toplanacak windows için olay izleme (ETW) olayı belirtir. ETW olayları ayrı bir (.etl) dosyada toplanır. |

3. Bir komut isteminde aşağıdaki komutu yazarak profiloluşturcunu hizmete takın:

    **VSPerfCmd / eklemek:**`PID`

    `PID`hedef uygulamanın işlem kimliğini veya işlem adını belirtir. Windows Görev Yöneticisi'nde çalışan tüm işlemlerin işlem lerini görüntüleyebilirsiniz.

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hedef uygulama çalışırken, *VSPerfCmd.exe* seçenekleri ile dosyaya veri yazısını başlatıp durdurarak veri toplamayı denetleyebilirsiniz. Veri toplamayı denetleyerek, uygulamanın başlatılması veya kapatılması gibi program yürütmesinin belirli bir bölümü için veri toplayabilirsiniz.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki tablodaki seçenek çiftleri veri toplamayı başlatın ve durdurun. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Tüm işlemler için **(/globalon)** başlatır veya durur (**/globaloff**) veri toplama.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|İşlem Kimliğinin (`PID`) belirttiği işlem için **(/processon)** başlatır veya (**/processoff)** veri toplamayı durdurur.|
    |[/ekle](../profiling/attach.md) **:**:`PID` `ProcName`{&#124;} [/ayırma](../profiling/detach.md) `ProcName`[**:**{`PID`&#124;}]|**/ekle** işlem kimliği (`PID`) veya işlem adı *(ProcName)* belirttiği işlem için veri toplamaya başlar. **/detach,** belirtilen işlem için veya işlem belirtilmemişse tüm işlemler için veri toplamayı durdurur.|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sonlandırma
 Profil oluşturma oturumunu sona erdirmek için profil oluşturucunun veri toplamaması gerekir. Hizmeti durdurarak veya **VSPerfCmd /detach** seçeneğini çağırarak eşzamanlılık yöntemiyle profillenmiş olan yerel bir hizmetten veri toplamayı durdurabilirsiniz. Daha sonra profil oluşturucuyu kapatmak ve profil oluşturma veri dosyasını kapatmak için **VSPerfCmd /shutdown** seçeneğini çağırırsınız.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdirmek için

1. Profilciyi hizmeti durdurarak veya komut isteminde aşağıdaki komutu yazarak hedef uygulamadan ayırın:

     **VsPerfCmd /detach** yazın

2. Bir komut isteminde aşağıdaki komutu yazarak profiloluşturucuyu kapatın:

     **VSPerfCmd**  [/kapatma](../profiling/shutdown.md)
