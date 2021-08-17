---
title: Bellek verilerini toplamak için .NET hizmetine profil oluşturma ekleme
description: Profil Visual Studio Profil Oluşturma Araçları hizmetine eklemek ve bellek verilerini toplamak için .NET Framework komut satırı araçlarını kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: aeac39af-ad99-479f-aa36-4104356ca512
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: ad4a878d0c357a81fc6f8c62a08385df1741d2ad5591c7bf4aca6df7d05a73fc
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121368441"
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-service-to-collect-memory-data-by-using-the-command-line"></a>Nasıl kullanılır: Komut satırı kullanarak bellek .NET Framework için profil oluşturma hizmetinin profil oluşturma hizmetini ekleme
Bu makalede, bir Profil Oluşturma Araçları hizmetine profil oluşturma ve bellek verileri toplama için .NET Framework [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] komut satırı araçlarının nasıl kullanımı açıklanmıştır. Bellek ayırmalarının sayısı ve boyutu hakkında veri toplayabilir ve ayrıca, bellek nesnelerinin yaşam süresi hakkında veri toplayabilirsiniz.

> [!NOTE]
> Windows 8 ve Windows Server 2012'daki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturmanın bu platformlarda veri toplaması sırasında önemli değişiklikler gerektirmektedir. UWP uygulamaları için yeni koleksiyon teknikleri de gerekir. Uygulama [ve uygulama Windows 8 performans Windows Server 2012 bakın.](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)
>
> [!NOTE]
> Profil oluşturma araçlarının yolunu almak için [bkz. Komut satırı araçlarının yolunu belirtme.](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md) 64 bit bilgisayarlarda, araçların hem 64 bit hem de 32 bit sürümleri kullanılabilir. Profil oluşturma komut satırı araçlarını kullanmak için, araç yolunu Komut İstemi penceresinin PATH ortam değişkenine eklemeniz veya komutun kendisine eklemeniz gerekir.

 .NET Framework hizmetten bellek verileri toplamak için [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) aracını kullanarak hizmeti barındıran bilgisayarda uygun ortam değişkenlerini başlatabilirsiniz. Bilgisayarın, profil oluşturma için yapılandırılmak üzere yeniden başlatılması gerekir.

 Ardından [VSPerfCmd aracını](../profiling/vsperfcmd.md) kullanarak profilleyiciyi hizmet sürecine iliştirebilirsiniz. Profil oluşturma hizmetine bağlıyken veri toplamayı duraklatabilir ve sürdürebilirsiniz.

 Profil oluşturma oturumunu sonlandırmak için, profil oluşturucunun hizmetten ayrılması ve ve açıkça kapatılması gerekir. Çoğu durumda, bir oturumun sonunda profil oluşturma ortam değişkenlerini temizlemenizi öneririz.

## <a name="attach-the-profiler"></a>Profilleyiciyi ekleme

#### <a name="to-attach-the-profiler-to-a-net-framework-service"></a>Profilleyiciyi bir .NET Framework eklemek için

1. Gerekirse hizmeti yükleyin.

2. Bir komut istemi penceresi açın.

3. Profil oluşturma ortam değişkenlerini başlatma. Şunu yazın:

    **VSPerfClrEnv** {**/globalsamplegc /globalsamplegclife**}[**/samplelineoff**]

   - **/globalsamplegclife ve** **/globalsamplegclife** seçenekleri top için bellek verisi türünü belirtir. Aşağıdaki seçeneklerden bir ve yalnızca bir tanesini belirtin.

     **/globalsamplegc** Bellek ayırma verileri toplamayı sağlar.

     **/globalsamplegclife** Hem bellek ayırma verilerini hem de nesne yaşam süresi verilerini toplamayı sağlar.

   - **/samplelineoff seçeneği,** kaynak kod satırı numarası verilerini toplamayı devre dışı bırakıyor.

4. Yeni ortam yapılandırmasını ayarlamak için bilgisayarı yeniden başlatın.

5. Gerekirse hizmeti başlatabilirsiniz.

6. Bir komut istemi penceresi açın. Gerekirse, profil oluşturucu yolunu PATH ortam değişkenine ekleyin.

7. Profilleyiciyi başlatma. Şunu yazın:

    **VSPerfCmd**  [/start](../profiling/start.md) **:sample**  [/output](../profiling/output.md) **:** [ `OutputFile` `Options` ]

   - **/start:sample** seçeneği profilleyiciyi başlatıyor.

   - **/output:** `OutputFile` seçeneği / **start ile gereklidir.** `OutputFile` profil oluşturma verileri (.vsp) dosyasının adını ve konumunu belirtir.

     **/start:sample** seçeneğiyle aşağıdaki seçeneklerden birini veya daha fazlasını kullanabilirsiniz.

   > [!NOTE]
   > **/user ve** **/crosssession** seçenekleri genellikle hizmetler için gereklidir.

   | Seçenek | Açıklama |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | İşlemin sahibi olan hesabının etki alanını ve kullanıcı adını belirtir. İşlem oturum açmış kullanıcıdan farklı bir kullanıcı olarak çalışıyorsa bu seçenek gereklidir. İşlem sahibi, Görev Yöneticisi'nin İşlemler sekmesindeki Kullanıcı Adı Windows listelenir. |
   | [/crosssession](../profiling/crosssession.md) | Diğer oturum açma oturumlarında işlemlerin profil oluşturmasını sağlar. Uygulama farklı bir oturumda ASP.NET bu seçenek gereklidir. Oturum kimliği, Görev Yöneticisi'nin İşlemler sekmesindeki Oturum Kimliği Windows listelenir. **/CS,** **/crosssession için bir kısaltma olarak belirtilebilir.** |
   | [/user](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Hizmetin altında çalıştığı oturum açma hesabının kullanıcı adını ve isteğe bağlı etki alanını belirtir. Oturum açma hesabın, Windows Hizmet Denetimi Yöneticisi'nde hizmetin Farklı Oturum Aç sütununda listelenir. |
   | [/crosssession&#124;cs](../profiling/crosssession.md) | Diğer oturum açma oturumlarında işlemlerin profil oluşturmasını sağlar. |
   | [/wincounter:](../profiling/wincounter.md) `WinCounterPath` | Profil oluşturma Windows bir performans sayacı belirtir. |
   | [/automark:](../profiling/automark.md) `Interval` | Yalnızca **/wincounter ile** kullanın. Performans sayacı toplama olayları arasındaki milisaniye Windows sayısını belirtir. Varsayılan değer 500 ms'tir. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Profil oluşturma sırasında toplanacak Windows (ETW) olayı için bir Olay İzleme belirtir. ETW olayları ayrı bir (.etl) dosyasında toplanır. |

8. Profiler'i hizmete ekleme. Şunu yazın:

    **VSPerfCmd**[/attach:](../profiling/attach.md) {&#124;} `PID` [ `ProcName` [/targetclr](../profiling/targetclr.md)**:** `Version` ]  

   - İşlem kimliğini veya hizmetin işlem adını belirtin. Görev Yöneticisi'nde çalışan tüm işlemlerin işlem kimliklerini ve Windows görüntüebilirsiniz.

   - **targetclr:** `Version` bir uygulamada birden fazla çalışma zamanı sürümü yüklendiğinde profili oluşturmak için ortak dil çalışma zamanının (CLR) sürümünü belirtir. İsteğe bağlı.

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hizmet çalışırken, veriVSPerfCmd.exe *profil* oluşturma veri dosyasına veri yazmayı durdurmak ve başlatmak için bu seçenekleri kullanabilirsiniz. Veri toplamanın denetlenmesi, program yürütmenin, uygulamanın başlatılması veya kapatılması gibi özel bir bölümü için veri toplamanızı sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki **VSPerfCmd seçenekleri çiftleri** veri toplamayı başlatacak ve durduracak. Her seçeneği ayrı bir komut satırı üzerinde belirtin. Veri toplamayı birden çok kez açabilirsiniz ve kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Tüm işlemler **için veri toplamayı** başlatır ( /globalon ) veya durdurur (**/globaloff).**|
    |[/processon:](../profiling/processon-and-processoff.md)  `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|İşlem kimliği ( ) tarafından belirtilen işlem için veri toplamayı (**/processon**) veya durdurur ( `PID` ).|
    |**/attach:**{ `PID`&#124;`ProcName` } [/detach](../profiling/detach.md)[:{ `PID`&#124;`ProcName` }]|**/attach,** işlem kimliği veya işlem adı tarafından belirtilen işlem için veri toplamaya başlar. **/detach,** belirtilen işlem için veya belirli bir işlem belirtilmezse tüm işlemler için veri toplamayı durdurur.|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sona er
 Profil oluşturma oturumunu sona erdirecek şekilde profil oluşturma, veri toplamama gerekir. Hizmeti durdurarak veya **VSPerfCmd /detach** seçeneğini çağırarak örnekleme yöntemiyle profili yapılan bir uygulamanın veri toplamayı durdurabilirsiniz. Ardından, profil oluşturma veri dosyasını kapatmak ve profil oluşturma verilerini kapatmak için **VSPerfCmd** [/shutdown](../profiling/shutdown.md) seçeneğini çağırabilirsiniz. **VSPerfClrEnv /globaloff** komutu profil oluşturma ortam değişkenlerini temizler, ancak bilgisayar yeniden başlatana kadar sistem yapılandırması sıfırlanmaz.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdir

1. Profilleyiciyi hedef uygulamadan ayırmak için aşağıdakilerden birini yapın:

    - Hizmeti durdurun.

         -veya-

    - **VSPerfCmd /detach yazın**

2. Profilleyiciyi kapatın. Şunu yazın:

     **VSPerfCmd/shutdown**

3. Seçim Profil oluşturma ortamı değişkenlerini temizleyin. Şunu yazın:

     **VSPerfClrEnv/globaloff**

4. Bilgisayarı yeniden başlatın.

## <a name="see-also"></a>Ayrıca bkz.
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
- [.NET bellek verileri görünümleri](../profiling/dotnet-memory-data-views.md)
