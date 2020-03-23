---
title: Profil oluşturucuyu yerel bir uygulamaya takın ve uygulama istatistiklerini toplayın
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: df44fe42-281b-4398-b3fc-277b62ae41f1
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: 96d4a812fd98dbd0f58a8012a61cdaef96db3a8b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779109"
---
# <a name="how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-application-statistics-by-using-the-command-line"></a>Nasıl yapılır: Profil oluşturucu komut satırını kullanarak yerel bir tek başına uygulamaya profil oluşturucu ekleme ve uygulama istatistikleri toplama
Bu makalede, profil [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oluşturucuyu çalışan bir yerel bağımsız (istemci) uygulamaya eklemek ve örnekleme yöntemini kullanarak performans istatistikleri toplamak için Profil Oluşturma Araçları komut satırı araçlarının nasıl kullanılacağı açıklanmaktadır.

> [!NOTE]
> Windows 8 ve Windows Server 2012'deki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturucusu bu platformlarda veri toplama şeklinde önemli değişiklikler gerektiriyordu. UWP uygulamaları da yeni toplama teknikleri gerektirir. [Windows 8 ve Windows Server 2012 uygulamalarında Performans Araçları'na](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)bakın.
>
> Profil oluşturma araçlarına giden yolu almak [için](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)bkz. 64 bit bilgisayarlarda, araçların hem 64 bit hem de 32 bit sürümleri kullanılabilir. Profil oluşturucu komut satırı araçlarını kullanmak için, komut istemi penceresinin PATH ortamı değişkenine araçlar yolunu eklemeniz veya komutun kendisine eklemeniz gerekir.

 Profil oluşturucu uygulamaya iliştirildiğinde, veri toplamayı duraklatabilir ve devam ettirebilirsiniz. Profil oluşturma oturumunu sona erdirmek için profil oluşturucuartık uygulamaya eklenmemeli ve profil oluşturucu açıkça kapatılmalıdır.

## <a name="attach-the-profiler"></a>Profil oluşturucuyu takın
 Profiloluşturciyi kullanarak bir hedef uygulamaya profil oluşturucu eklemek için, profiloluşturcuyumu başlatmak ve hedef uygulamaya eklemek için **VSPerfCmd/start** **ve/attach** seçeneklerini kullanırsınız. Tek bir komut satırında **/başlat** ve **/ekle** ve ilgili seçeneklerini belirtebilirsiniz. Hedef uygulamanın başında veri toplamayı duraklatmak için **/globaloff** seçeneğini de ekleyebilirsiniz. Daha sonra veri toplamaya başlamak için **/globalon'u** kullanırsınız.

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Çalışan bir .NET Framework uygulamasına profil oluşturucu eklemek için

1. Bir komut istemi penceresi açın.

2. Profilciyi çalıştırın. Şunu yazın:

    **VSPerfCmd /start:örnek /çıktı:** `OutputFile` [`Options`]

   - [/start](../profiling/start.md)**:örnek** seçeneği profil oluşturucuyu başlatir.

   - [/output](../profiling/output.md)**:** `OutputFile` seçeneği **/start**ile gereklidir. `OutputFile`profil oluşturma verileri (.vsp) dosyasının adını ve konumunu belirtir.

     **/start:sample** seçeneği ile aşağıdaki seçeneklerden herhangi birini kullanabilirsiniz.

   | Seçenek | Açıklama |
   | - | - |
   | [/kullanıcı](../profiling/user-vsperfcmd.md) **:**[ ]`Domain`**\\**`UserName` | Profilli işlemin sahibi hesabın etki alanını ve kullanıcı adını belirtir. Bu seçenek yalnızca işlem oturum açmış kullanıcı dışında bir kullanıcı olarak çalışıyorsa gereklidir. İşlem sahibi, Windows Görev Yöneticisi'nin İşlemler sekmesinde Kullanıcı Adı sütununda listelenir. |
   | [/çapraz oturum](../profiling/crosssession.md) | Diğer oturumlarda işlemlerin profilini çıkarma sağlar. ASP.NET uygulaması farklı bir oturumda çalışıyorsa bu seçenek gereklidir. Oturum tanımlayıcısı, Windows Görev Yöneticisi'nin İşlemler sekmesindeki Oturum Kimliği sütununda listelenir. **/CS** **/ crosssession**için bir kısaltma olarak belirtilebilir. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Yalnızca **/wincounter** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 ms'dir. |
   | [/olaylar](../profiling/events-vsperfcmd.md) **:**`Config` | Profil oluşturma sırasında toplanacak windows için olay izleme (ETW) olayı belirtir. ETW olayları ayrı bir şekilde toplanır (.* etl*) dosyası. |

3. Profil oluşturucuyu hedef uygulamaya takın. Şunu yazın:

    **VSPerfCmd**[/ eklemek](../profiling/attach.md) `ProcName` **:**`Sample Event`{`PID`&#124;} [ ]  

    `PID`hedef uygulamanın işlem kimliğini belirtir. `ProcessName`işlemin adını belirtir. Aynı ada `ProcessName` sahip birden çok işlem belirtirseniz ve birden çok işlem çalışıyorsa, sonuçların öngörülemez olduğunu unutmayın. Windows Görev Yöneticisi'nde çalışan tüm işlemlerin işlem lerini görüntüleyebilirsiniz.

    Varsayılan olarak, performans verileri her 10.000.000 durdurulmayan işlemci saat döngüsünde örneklenir. Bu, 1GH işlemcide saniyede yaklaşık 100 kez dir. Saat döngüsü aralığını değiştirmek veya farklı bir örnekleme olayı belirtmek için aşağıdaki seçeneklerden birini belirtebilirsiniz.

   |Örnek olay|Açıklama|
   |------------------|-----------------|
   |[/zamanlayıcı](../profiling/timer.md) **:**`Interval`|Örnekleme aralığını, `Interval`'tarafından belirtilen durdurulmayan saat devir lerinin sayısıyla değiştirir.|
   |[/pf](../profiling/pf.md)[**:**`Interval`]|Örnekleme olayını sayfa hatalarıyla değiştirir. `Interval` Belirtilirse, örnekler arasındaki sayfa hatalarının sayısını ayarlar. Varsayılan değer 10'dur.|
   |[/sys](../profiling/sys-vsperfcmd.md) [**:**`Interval`]|Örnekleme olayını, işlemden işletim sistemi çekirdeğine (syscalls) sistem çağrılarına değiştirir. `Interval` Belirtilirse, örnekler arasındaki çağrı sayısını ayarlar. Varsayılan değer 10'dur.|
   |[/sayaç](../profiling/counter.md) **:**`Config`|Örnekleme olayını ve aralığıişlemci performans sayacına ve 'de belirtilen aralıkta `Config`değiştirir.|

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hedef uygulama çalışırken, profil oluşturucu veri dosyasına veri yazısını başlatmak ve durdurmak için *VSPerfCmd.exe* seçeneklerini kullanabilirsiniz. Veri toplamayı denetlemek, uygulamanın başlatılması veya kapatılması gibi program yürütmesinin belirli bir bölümü için veri toplamanızı sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki **VSPerfCmd** seçenekleri, veri toplamayı başlayıp durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Tüm işlemler için **(/globalon)** başlatır veya durur (**/globaloff**) veri toplama.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Tarafından belirtilen `PID`işlem için (**/processon)** başlatır veya durur (**/processoff**) veri toplama.|
    |[/ekle](../profiling/attach.md) **:** `PID` [/detach](../profiling/detach.md)|**/attach** tarafından `PID`belirtilen işlem için veri toplamaya başlar. **/detach** tüm işlemler için veri toplamayı durdurur.|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sonlandırma
 Profil oluşturma oturumunu sona erdirmek için profil oluşturucunun tüm profil işlemlerinden ayrılması ve profil oluşturucunun açıkça kapatılması gerekir. Uygulamayı kapatarak veya **VSPerfCmd /detach** seçeneğini arayarak profil oluşturma yöntemini kullanarak profillenmiş bir uygulamadan profillendirebilirsiniz. Daha sonra profil oluşturma veri dosyasını kapatmak ve kapatmak için **VSPerfCmd /shutdown** seçeneğini arayın. **VSPerfClrEnv /off** komutu profil oluşturma ortamı değişkenlerini temizler.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdirmek için

1. Profiloluşturucuyu hedef uygulamadan ayırmak için aşağıdaki adımlardan birini gerçekleştirin.

    - **VsPerfCmd /detach** yazın

         -veya-

    - Hedef uygulamayı kapatın.

2. Profilciyi kapat. Şunu yazın:

     **VSPerfCmd**  [/kapatma](../profiling/shutdown.md)

3. (İsteğe bağlı) Profil oluşturma ortamı değişkenlerini temizleyin. Şunu yazın:

     **VSPerfClrEnv /kapalı**

## <a name="see-also"></a>Ayrıca bkz.
- [Profil tek başına uygulamalar](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Örnekleme yöntemi veri görünümleri](../profiling/profiler-sampling-method-data-views.md)
