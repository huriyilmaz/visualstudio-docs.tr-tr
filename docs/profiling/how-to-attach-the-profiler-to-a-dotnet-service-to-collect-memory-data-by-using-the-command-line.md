---
title: Bellek verilerini toplamak için profiloluşturcağı bir .NET hizmetine takın
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: aeac39af-ad99-479f-aa36-4104356ca512
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 94ea4f38ccebc1015419e2254b06033fa17a09a8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777037"
---
# <a name="how-to-attach-the-profiler-to-a-net-service-to-collect-memory-data-by-using-the-command-line"></a>Nasıl yapılır: Komut satırını kullanarak bellek verileri toplamak için bir .NET hizmetine profil oluşturucu ekleme
Bu makalede, profil [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oluşturucuyu bir .NET Framework hizmetine eklemek ve bellek verilerini toplamak için Profil Oluşturma Araçları komut satırı araçlarının nasıl kullanılacağı açıklanmaktadır. Bellek ayırmalarının sayısı ve boyutu hakkında veri toplayabilir ve ayrıca, bellek nesnelerinin yaşam süresi hakkında veri toplayabilirsiniz.

> [!NOTE]
> Windows 8 ve Windows Server 2012'deki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturucusu bu platformlarda veri toplama şeklinde önemli değişiklikler gerektiriyordu. UWP uygulamaları da yeni toplama teknikleri gerektirir. [Windows 8 ve Windows Server 2012 uygulamalarında Performans Araçları'na](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)bakın.
>
> [!NOTE]
> Profil oluşturma araçlarına giden yolu almak [için](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)bkz. 64 bit bilgisayarlarda, araçların hem 64 bit hem de 32 bit sürümleri kullanılabilir. Profil oluşturucu komut satırı araçlarını kullanmak için, komut istemi penceresinin PATH ortamı değişkenine araçlar yolunu eklemeniz veya komutun kendisine eklemeniz gerekir.

 Bir .NET Framework hizmetinden bellek verileri toplamak için, hizmeti barındıran bilgisayardaki uygun ortam değişkenlerini başlatmak için [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) aracını kullanırsınız. Bilgisayarın, profil oluşturma için yapılandırılmak üzere yeniden başlatılması gerekir.

 Daha sonra profiloluşturcIyi servis işlemine eklemek için [VSPerfCmd](../profiling/vsperfcmd.md) aracını kullanırsınız. Profil oluşturucu hizmete bağlıyken, veri toplamayı duraklatabilir ve devam ettirebilirsiniz.

 Profil oluşturma oturumunu sonlandırmak için, profil oluşturucunun hizmetten ayrılması ve ve açıkça kapatılması gerekir. Çoğu durumda, oturumun sonunda profil oluşturma ortamı değişkenlerini temizlemenizi öneririz.

## <a name="attach-the-profiler"></a>Profil oluşturucuyu takın

#### <a name="to-attach-the-profiler-to-a-net-framework-service"></a>ProfiloluşturcIyi bir .NET Framework hizmetine eklemek için

1. Gerekirse hizmeti yükleyin.

2. Bir komut istemi penceresi açın.

3. Profil oluşturma ortamı değişkenlerini başlangıç olarak önleştirin. Şunu yazın:

    **VSPerfClrEnv** {**/globalsamplegc /globalsamplegclife**}[**/samplelineoff**]

   - **/globalsamplegclife** ve **/globalsamplegclife** seçenekleri toplanacak bellek veritürünü belirtir. Aşağıdaki seçeneklerden bir ve yalnızca bir tanesini belirtin.

     **/globalsamplegc** Bellek ayırma verilerinin toplanmasını sağlar.

     **/globalsamplegclife** Hem bellek ayırma verilerinin hem de nesne yaşam alanı verilerinin toplanmasını sağlar.

   - **/samplelineoff** seçeneği kaynak kodu satırı numarası verilerinin toplanmasını devre dışı kılabilir.

4. Yeni ortam yapılandırmasını ayarlamak için bilgisayarı yeniden başlatın.

5. Gerekirse hizmeti başlatın.

6. Bir komut istemi penceresi açın. Gerekirse, profil oluşturucu yolunu PATH ortam değişkenine ekleyin.

7. Profilciyi çalıştırın. Şunu yazın:

    **VSPerfCmd**  [/start](../profiling/start.md) **:örnek**  [/çıktı](../profiling/output.md) **:** `OutputFile` [`Options`]

   - **/start:örnek** seçeneği profil oluşturucuyu başlatir.

   - **/output:** `OutputFile` seçeneği **/start**ile gereklidir. `OutputFile`profil oluşturma verileri (.vsp) dosyasının adını ve konumunu belirtir.

     **/start:sample** seçeneği ile aşağıdaki seçeneklerden birini veya birkaçını kullanabilirsiniz.

   > [!NOTE]
   > Hizmetler için **genellikle /kullanıcı** ve **/çapraz oturum** seçenekleri gereklidir.

   | Seçenek | Açıklama |
   | - | - |
   | [/kullanıcı](../profiling/user-vsperfcmd.md) **:**[ ]`Domain`**\\**`UserName` | İşlemin sahibi olan hesabının etki alanını ve kullanıcı adını belirtir. İşlem, oturum açmış kullanıcı dışında bir kullanıcı olarak çalışıyorsa, bu seçenek gereklidir. İşlem sahibi, Windows Görev Yöneticisi'nin İşlemler sekmesinde Kullanıcı Adı sütununda listelenir. |
   | [/çapraz oturum](../profiling/crosssession.md) | Diğer oturum oturumlarında işlemlerin profilini çıkarmasağlar. ASP.NET uygulaması farklı bir oturumda çalışıyorsa bu seçenek gereklidir. Oturum kimliği, Windows Görev Yöneticisi'nin İşlemler sekmesinde Oturum Kimliği sütununda listelenir. **/CS** **/ crosssession**için bir kısaltma olarak belirtilebilir. |
   | [/kullanıcı](../profiling/user-vsperfcmd.md) **:**[ ]`Domain`**\\**`UserName` | Hizmetin altında çalıştığı oturum açma hesabının kullanıcı adını ve isteğe bağlı etki alanını belirtir. Oturum açma hesabın, Windows Hizmet Denetimi Yöneticisi'nde hizmetin Farklı Oturum Aç sütununda listelenir. |
   | [/crosssession&#124;cs](../profiling/crosssession.md) | Diğer oturum oturumlarında işlemlerin profilini çıkarmasağlar. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Yalnızca **/wincounter** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 ms'dir. |
   | [/olaylar](../profiling/events-vsperfcmd.md) **:**`Config` | Profil oluşturma sırasında toplanacak windows için olay izleme (ETW) olayı belirtir. ETW olayları ayrı bir (.etl) dosyada toplanır. |

8. ProfiloluşturcIyi servise takın. Şunu yazın:

    **VSPerfCmd**[/ eklemek](../profiling/attach.md) `ProcName` **:**{`PID`&#124;} [ /[targetclr](../profiling/targetclr.md)**:**`Version`]  

   - İşlem kimliğini veya hizmetin işlem adını belirtin. Windows Görev Yöneticisi'nde tüm çalışan işlemlerin işlem adlarını ve adlarını görüntüleyebilirsiniz.

   - **targetclr:** `Version` bir uygulamada çalışma süresinin birden fazla sürümü yüklendiğinde, ortak dil çalışma zamanının (CLR) profilinin sürümünü belirtir. İsteğe bağlı.

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hizmet çalışırken, profil oluşturucu veri dosyasına veri yazmayı durdurmak ve başlatmak için *VSPerfCmd.exe* seçeneklerini kullanabilirsiniz. Veri toplamanın denetlenmesi, program yürütmenin, uygulamanın başlatılması veya kapatılması gibi özel bir bölümü için veri toplamanızı sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki **VSPerfCmd** seçenekleri, veri toplamayı başlayıp durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Tüm işlemler için **(/globalon)** başlatır veya durur (**/globaloff**) veri toplama.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|İşlem Kimliği tarafından belirtilen işlem için **(/processon)** başlatır veya **(/processoff)** veri toplamayı durdurur (`PID`).|
    |**/ekle:**`PID` { `ProcName`&#124;} [/detach](../profiling/detach.md)[:{`PID`&#124;`ProcName`}]|**/ekle** işlem kimliği veya işlem adı tarafından belirtilen işlem için veri toplamaya başlar. **/detach** belirtilen işlem için veya belirli bir işlem belirtilmemişse tüm işlemler için veri toplamayı durdurur.|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sonlandırma
 Profil oluşturma oturumunu sona erdirmek için profil oluşturucunun veri toplamaması gerekir. Hizmeti durdurarak veya **VSPerfCmd /detach** seçeneğini arayarak, örnekleme yöntemiyle profillenmiş bir uygulamadan veri toplamayı durdurabilirsiniz. Daha sonra profil oluşturma veri dosyasını kapatmak ve kapatmak için **VSPerfCmd** [/shutdown](../profiling/shutdown.md) seçeneğini arayın. **VSPerfClrEnv /globaloff** komutu profil oluşturma ortamı değişkenlerini temizler, ancak bilgisayar yeniden başlatılıncaya kadar sistem yapılandırması sıfırlanmaz.

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
- [.NET bellek veri görünümleri](../profiling/dotnet-memory-data-views.md)
