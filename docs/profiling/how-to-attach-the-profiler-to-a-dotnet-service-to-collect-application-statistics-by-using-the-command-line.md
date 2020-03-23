---
title: Uygulama istatistiklerini toplamak için profiler'ı .NET hizmetine takın
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a0046c47-26c8-4bec-96a0-81da05e5104a
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 9294e9bf9ab35d75e0b06c620699c6e39babe1a3
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779148"
---
# <a name="how-to-attach-the-profiler-to-a-net-service-to-collect-application-statistics-by-using-the-command-line"></a>Nasıl yapilir: Komut satırını kullanarak uygulama istatistiklerini toplamak için profiloluşturcuğu bir .NET hizmetine iliştirin
Bu makalede, profil [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oluşturucuyu bir .NET Framework hizmetine eklemek ve örnekleme yöntemini kullanarak performans istatistikleri toplamak için Profil Oluşturma Araçları komut satırı araçlarının nasıl kullanılacağı açıklanmaktadır.

> [!NOTE]
> Windows 8 ve Windows Server 2012'deki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturucusu bu platformlarda veri toplama şeklinde önemli değişiklikler gerektiriyordu. UWP uygulamaları da yeni toplama teknikleri gerektirir. [Windows 8 ve Windows Server 2012 uygulamalarında Performans Araçları'na](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)bakın.
>
> Profil oluşturma araçlarına giden yolu almak [için](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)bkz. 64 bit bilgisayarlarda, araçların hem 64 bit hem de 32 bit sürümleri kullanılabilir. Profil oluşturucu komut satırı araçlarını kullanmak için, komut istemi penceresinin PATH ortamı değişkenine araçlar yolunu eklemeniz veya komutun kendisine eklemeniz gerekir.
>
> Profil oluşturma çalışmasına katman etkileşim verileri eklemek, komut satırı profil oluşturma araçlarıyla belirli yordamlar gerektirir. Bkz. [Katman etkileşim verilerini topla.](../profiling/adding-tier-interaction-data-from-the-command-line.md)

 Bir .NET Framework hizmetinden performans verileri toplamak için, uygun ortam değişkenlerini başlatmak için [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) aracını kullanmanız gerekir. Daha sonra hizmeti barındıran bilgisayarı yeniden başlatmanız ve bu bilgisayarı profil oluşturma için yapılandırmanız gerekir. Daha sonra profil oluşturucuyu hizmet işlemine bağlarsınız. Profil oluşturucu hizmete eklendiğinde, veri toplamayı duraklatabilir ve devam ettirebilirsiniz.

 Profil oluşturma oturumunu sonlandırmak için, profil oluşturucunun hizmetten ayrılması ve ve açıkça kapatılması gerekir. Çoğu durumda, oturumun sonunda profil oluşturma ortamı değişkenlerini temizlemenizi öneririz.

## <a name="attach-the-profiler"></a>Profil oluşturucuyu takın

#### <a name="to-attach-the-profiler-to-a-net-framework-service"></a>ProfiloluşturcIyi bir .NET Framework hizmetine eklemek için

1. Hizmeti yükleyin.

2. Bir komut istemi penceresi açın.

3. Profil oluşturma ortamı değişkenlerini başlangıç olarak önleştirin. Şunu yazın:

    **VSPerfClrEnv /globalsampleon** [**/samplelineoff**]

   - **/globalsampleon** örneklemeyi sağlar.

   - **/samplelineoff,** toplanan verilerin belirli kaynak kod satırlarına atamasını devre dışı kılabilir. Bu seçenek belirtildiğinde, veriler yalnızca işlevlere atanır.

4. Bilgisayarı yeniden başlatın.

5. Bir komut istemi penceresi açın.

6. Profilciyi çalıştırın. Şunu yazın:

    **VSPerfCmd**  [/start](../profiling/start.md) **:örnek**  [/çıktı](../profiling/output.md) **:** `OutputFile` [`Options`]

   - **/start:örnek** seçeneği profil oluşturucuyu başlatir.

   - **/output:** `OutputFile` seçeneği **/start**ile gereklidir. `OutputFile`profil oluşturma verileri (.vsp) dosyasının adını ve konumunu belirtir.

     **/start:sample** seçeneği ile aşağıdaki seçeneklerden herhangi birini kullanabilirsiniz.

   > [!NOTE]
   > Hizmetler için **genellikle /kullanıcı** ve **/çapraz oturum** seçenekleri gereklidir.

   | Seçenek | Açıklama |
   | - | - |
   | [/kullanıcı](../profiling/user-vsperfcmd.md) **:**[ ]`Domain`**\\**`UserName` | Profilli işlemin sahibi hesabın etki alanını ve kullanıcı adını belirtir. Bu seçenek, yalnızca işlem kullanıcı da oturum açmış kullanıcı dışında bir kullanıcı olarak çalışıyorsa gereklidir. İşlem sahibi, Windows Görev Yöneticisi'nin İşlemler sekmesinde Kullanıcı Adı sütununda listelenir. |
   | [/çapraz oturum](../profiling/crosssession.md) | Diğer oturumlarda işlemlerin profilini çıkarma sağlar. Hizmet farklı bir oturumda çalışıyorsa bu seçenek gereklidir. Oturum kimliği, Windows Görev Yöneticisi'nin İşlemler sekmesinde Oturum Kimliği sütununda listelenir. **/CS** **/ crosssession**için bir kısaltma olarak belirtilebilir. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Yalnızca **/wincounter** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 ms'dir. |
   | [/olaylar](../profiling/events-vsperfcmd.md) **:**`Config` | Profil oluşturma sırasında toplanacak windows için olay izleme (ETW) olayı belirtir. ETW olayları ayrı bir (.etl) dosyada toplanır. |

7. Gerekirse hizmeti başlatın.

8. ProfiloluşturcIyi servise takın. Şunu yazın:

    **VSPerfCmd**[/ ekle](../profiling/attach.md) `ProcName` **:** `Sample Event`{`PID`&#124;} [ [[/ targetclr](../profiling/targetclr.md)**:**`Version`]  

   - Hizmetin işlem`PID`kimliğini ( ) veya işlem adını (ProcName) belirtin. Windows Görev Yöneticisi'nde tüm çalışan işlemlerin işlem adlarını ve adlarını görüntüleyebilirsiniz.

     Varsayılan olarak, performans verileri her 10.000.000 durdurulmayan işlemci saat döngüsünde örneklenir. Bu, 1GH işlemcide saniyede yaklaşık 100 örnektir. Saat döngüsü aralığını değiştirmek veya farklı bir örnekleme olayı belirtmek için aşağıdaki seçeneklerden birini belirtebilirsiniz.

   |Örnek Olay|Açıklama|
   |------------------|-----------------|
   |[/zamanlayıcı](../profiling/timer.md) **:**`Interval`|Örnekleme aralığını, `Interval`'tarafından belirtilen durdurulmayan saat döngülerinin sayısıyla değiştirir.|
   |[/pf](../profiling/pf.md)[**:**`Interval`]|Örnekleme olayını sayfa hatalarıyla değiştirir. `Interval` Belirtilirse, örnekler arasındaki sayfa hatalarının sayısını ayarlar. Varsayılan değer 10'dur.|
   |[/sys](../profiling/sys-vsperfcmd.md)`:``Interval`[ ]|Örnekleme olayını, işlemden işletim sistemi çekirdeğine (syscalls) sistem çağrılarına değiştirir. `Interval` Belirtilirse, örnekler arasındaki çağrı sayısını ayarlar. Varsayılan değer 10'dur.|
   |[/sayaç](../profiling/counter.md) **:**`Config`|Örnekleme olayını ve aralığını işlemci performans sayacına ve 'de belirtilen aralıkta `Config`değiştirir.|

   - **targetclr:** `Version` bir uygulamada çalışma süresinin birden fazla sürümü yüklendiğinde, ortak dil çalışma zamanının (CLR) profilinin sürümünü belirtir. İsteğe bağlı.

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hizmet çalışırken, profil oluşturucu veri dosyasına veri yazısını başlatmak ve durdurmak için *VSPerfCmd.exe* seçeneklerini kullanabilirsiniz. Veri toplamayı denetlemek, uygulamayı başlatma veya kapatma gibi program yürütmesinin belirli bir bölümü için veri toplamanızı sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki **VSPerfCmd** seçenekleri, veri toplamayı başlayıp durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Tüm işlemler için **(/globalon)** başlatır veya durur (**/globaloff**) veri toplama.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|İşlem Kimliği tarafından belirtilen işlem için **(/processon)** başlatır veya **(/processoff)** veri toplamayı durdurur (`PID`).|
    |**/ekle:**`PID` { `ProcName`&#124;} [/detach](../profiling/detach.md)[:{`PID`&#124;`ProcName`}]|**/ekle** işlem kimliği veya işlem adı tarafından belirtilen işlem için veri toplamaya başlar. **/detach,** belirli bir işlem belirtilmemişse, belirtilen işlem veya tüm işlemler için veri toplamayı durdurur.|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sonlandırma
 Profil oluşturma oturumunu sona erdirmek için profil oluşturucunun tüm profil işlemlerinden ayrılması ve profil oluşturucunun açıkça kapatılması gerekir. Uygulamayı kapatarak veya **VSPerfCmd /detach** seçeneğini arayarak örnekleme yöntemiyle profilli bir uygulamadan ayırabilirsiniz. Daha sonra profil oluşturma veri dosyasını kapatmak ve kapatmak için **VSPerfCmd /shutdown** seçeneğini arayın.

 **VSPerfClrEnv /globaloff** komutu profil oluşturma ortamı değişkenlerini temizler, ancak bilgisayar yeniden başlatılıncaya kadar sistem yapılandırması sıfırlanmaz.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdirmek için

1. Profiloluşturciyi hedef uygulamadan ayırmak için aşağıdakilerden birini yapın:

    - Servisi durdurun.

         -veya-

    - **VsPerfCmd /detach** yazın

2. Profilciyi kapat. Şunu yazın:

     **VSPerfCmd /kapatma**

3. (İsteğe bağlı) Profil oluşturma ortamı değişkenlerini temizleyin. Şunu yazın:

     **VSPerfClrEnv /globaloff**

4. Bilgisayarı yeniden başlatın.

## <a name="see-also"></a>Ayrıca bkz.
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
- [Örnekleme yöntemi veri görünümleri](../profiling/profiler-sampling-method-data-views.md)
