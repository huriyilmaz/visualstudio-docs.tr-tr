---
title: 'VSPerfCmd: Uygulama istatistiklerini almak için profil oluşturucuya yerel hizmete takın'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f783817f-77a0-4eb8-985b-ec3b77eadc42
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: 00f0d3cedf2ef1875d93f7706f7cfa48a8b6b274
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779096"
---
# <a name="how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line"></a>Nasıl yapılır: Komut satırını kullanarak uygulama istatistikleri toplamak için bir yerel hizmete profil oluşturucu ekleme
Bu makalede, profil [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oluşturucuyu yerel bir hizmete eklemek ve örnekleme yöntemini kullanarak performans istatistikleri toplamak için Profil Oluşturma Araçları komut satırı araçlarının nasıl kullanılacağı açıklanmaktadır.

> [!NOTE]
> Windows 8 ve Windows Server 2012'deki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturucusu bu platformlarda veri toplama şeklinde önemli değişiklikler gerektiriyordu. UWP uygulamaları da yeni toplama teknikleri gerektirir. [Windows 8 ve Windows Server 2012 uygulamalarında Performans Araçları'na](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)bakın.
>
> Profil oluşturma araçlarına giden yolu almak [için](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)bkz. 64 bit bilgisayarlarda, araçların hem 64 bit hem de 32 bit sürümleri kullanılabilir. Profil oluşturucu komut satırı araçlarını kullanmak için, komut istemi penceresinin PATH ortamı değişkenine araçlar yolunu eklemeniz veya komutun kendisine eklemeniz gerekir.

 Profil oluşturucu hizmete bağlıyken, veri toplamayı duraklatabilir ve devam ettirebilirsiniz.

 Profil oluşturma oturumunu sonlandırmak için, profil oluşturucunun hizmetten ayrılması ve ve açıkça kapatılması gerekir.

## <a name="start-the-application-with-the-profiler"></a>Uygulamayı profil oluşturucuyla başlatın
 Profiloluşturciyi yerel bir hizmete eklemek için, profiloluşturcuyumu başlatmak ve hedef uygulamaya eklemek için **VSPerfCmd.exe**[/start](../profiling/start.md) ve [/iliştirme](../profiling/attach.md) seçeneklerini kullanırsınız. Tek bir komut satırında **/başlat** ve **/ekle** ve ilgili seçeneklerini belirtebilirsiniz. Hedef uygulamanın başında veri toplamayı duraklatmak için [/globaloff](../profiling/globalon-and-globaloff.md) seçeneğini de ekleyebilirsiniz. Daha sonra veri toplamaya başlamak için [/globalon'u](../profiling/globalon-and-globaloff.md) kullanabilirsiniz.

#### <a name="to-attach-the-profiler-to-a-native-service"></a>ProfiloluşturcIyi yerel bir hizmete eklemek için

1. Gerekirse hizmeti başlatın.

2. Bir komut istemi penceresi açın.

3. Profilciyi çalıştırın. Şunu yazın:

    **VSPerfCmd /start:örnek**  [/çıktı](../profiling/output.md) **:** `OutputFile` [`Options`]

   - **/start:örnek** seçeneği profil oluşturucuyu başlatir.

   - **/output:** `OutputFile` seçeneği **/start**ile gereklidir. `OutputFile`profil oluşturma verilerinin adını ve konumunu belirtir (.* vsp*) dosyası.

     **/start:sample** seçeneği ile aşağıdaki seçeneklerden herhangi birini kullanabilirsiniz.

   > [!NOTE]
   > Hizmetler için **genellikle /kullanıcı** ve **/çapraz oturum** seçenekleri gereklidir.

   | Seçenek | Açıklama |
   | - | - |
   | [/kullanıcı](../profiling/user-vsperfcmd.md) **:**[ ]`Domain`**\\**`UserName` | Profilli işlemin sahibi hesabın etki alanını ve kullanıcı adını belirtir. Bu seçenek, yalnızca işlem kullanıcı da oturum açmış kullanıcı dışında bir kullanıcı olarak çalışıyorsa gereklidir. İşlem sahibi, Windows Görev Yöneticisi'nin İşlemler sekmesinde Kullanıcı Adı sütununda listelenir. |
   | [/çapraz oturum](../profiling/crosssession.md) | Diğer oturumlarda işlemlerin profilini çıkarma sağlar. Uygulama farklı bir oturumda çalışıyorsa bu seçenek gereklidir. Oturum kimliği, Windows Görev Yöneticisi'nin İşlemler sekmesinde Oturum Kimliği sütununda listelenir. **/CS** **/ crosssession**için bir kısaltma olarak belirtilebilir. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Yalnızca **/wincounter** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 ms'dir. |
   | [/olaylar](../profiling/events-vsperfcmd.md) **:**`Config` | Profil oluşturma sırasında toplanacak windows için olay izleme (ETW) olayı belirtir. ETW olayları ayrı bir (.etl) dosyada toplanır. |

4. ProfiloluşturcIyi servise takın. Şunu yazın:

    **VSPerfCmd /ekle:** `PID` [`Sample Event`]

    `PID`hedef uygulamanın işlem kimliğini belirtir. Windows Görev Yöneticisi'nde çalışan tüm işlemlerin işlem lerini görüntüleyebilirsiniz.

    Varsayılan olarak, performans verileri her 10.000.000 durdurulmayan işlemci saat döngüsünde örneklenir. Bu, 1GH işlemcide yaklaşık olarak her 10 saniyede bir dir. Saat döngüsü aralığını değiştirmek veya farklı bir örnekleme olayı belirtmek için aşağıdaki seçeneklerden birini belirtebilirsiniz.

   |Örnek Olay|Açıklama|
   |------------------|-----------------|
   |[/zamanlayıcı](../profiling/timer.md) **:**`Interval`|Örnekleme aralığını, `Interval`'tarafından belirtilen durdurulmayan saat döngülerinin sayısıyla değiştirir.|
   |[/pf](../profiling/pf.md)[**:**`Interval`]|Örnekleme olayını sayfa hatalarıyla değiştirir. `Interval` Belirtilirse, örnekler arasındaki sayfa hatalarının sayısını ayarlar. Varsayılan değer 10'dur.|
   |[/sys](../profiling/sys-vsperfcmd.md) [**:**`Interval`]|Örnekleme olayını, işlemden işletim sistemi çekirdeğine (syscalls) sistem çağrılarına değiştirir. `Interval` Belirtilirse, örnekler arasındaki çağrı sayısını ayarlar. Varsayılan değer 10'dur.|
   |[/sayaç](../profiling/counter.md) **:**`Config`|Örnekleme olayını ve aralığını işlemci performans sayacına ve 'de belirtilen aralıkta `Config`değiştirir.|

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hedef uygulama çalışırken, profil oluşturucu veri dosyasına veri yazısını başlatmak ve durdurmak için *VSPerfCmd.exe* seçeneklerini kullanabilirsiniz. Veri toplamayı denetlemek, uygulamayı başlatma veya kapatma gibi program yürütmesinin belirli bir bölümü için veri toplamanızı sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki **VSPerfCmd** seçenekleri, veri toplamayı başlayıp durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Tüm işlemler için **(/globalon)** başlatır veya durur (**/globaloff**) veri toplama.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|İşlem Kimliği tarafından belirtilen işlem için **(/processon)** başlatır veya **(/processoff)** veri toplamayı durdurur (`PID`).|
    |**/ekle:** `PID` { `ProcName`&#124;} [/detach](../profiling/detach.md)[:{`PID`&#124;`ProcName`}]|**/ekle** işlem kimliği veya işlem adı tarafından belirtilen işlem için veri toplamaya başlar. **/detach** belirtilen işlem için veya bir işlem belirtilmemişse tüm işlemler için veri toplamayı durdurur.|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sonlandırma
 Profil oluşturma oturumunu sona erdirmek için profil oluşturucunun hizmetten ayrılması ve ardından açıkça kapatılması gerekir. Hizmeti durdurarak veya **VSPerfCmd /detach** seçeneğini arayarak örnekleme yöntemiyle profillenmiş olan yerel hizmeti ayırabilirsiniz. Daha sonra profil oluşturma veri dosyasını kapatmak ve kapatmak için **VSPerfCmd** [/shutdown](../profiling/shutdown.md) seçeneğini arayın.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdirmek için

1. Profiloluşturciyi hedef uygulamadan ayırmak için aşağıdakilerden birini yapın:

    - Servisi durdurun.

         -veya-

    - **VsPerfCmd /detach** yazın

2. Profilciyi kapat. Şunu yazın:

     **VSPerfCmd /kapatma**

## <a name="see-also"></a>Ayrıca bkz.
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
- [Örnekleme yöntemi veri görünümleri](../profiling/profiler-sampling-method-data-views.md)
