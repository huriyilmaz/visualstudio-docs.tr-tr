---
title: Eşzamanlı veri toplamak için profiler'ı .NET hizmetine ekleme
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ffbdfe37-8325-44be-bd36-2c8aab2dec7b
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: a95e907379db19d88fd7204e8410038ddb881d3b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779122"
---
# <a name="how-to-attach-the-profiler-to-a-net-service-to-collect-concurrency-data-by-using-the-command-line"></a>Nasıl kullanılır: Komut satırını kullanarak eşzamanlı veri toplamak için profiloluşturcuğu bir .NET hizmetine iliştirin
Bu makalede, profil [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oluşturucuyu bir .NET Framework hizmetine eklemek ve örnekleme yöntemini kullanarak işlem ve iş parçacığı eşzamanlılık verilerini toplamak için Profil Oluşturma Araçları komut satırı araçlarının nasıl kullanılacağı açıklanmaktadır.

> [!NOTE]
> Windows 8 ve Windows Server 2012'deki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturucusu bu platformlarda veri toplama şeklinde önemli değişiklikler gerektiriyordu. UWP uygulamaları da yeni toplama teknikleri gerektirir. [Windows 8 ve Windows Server 2012 uygulamalarında Performans Araçları'na](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)bakın.

> [!NOTE]
> Profil oluşturma araçlarına giden yolu almak [için](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)bkz. 64 bit bilgisayarlarda, araçların hem 64 bit hem de 32 bit sürümleri kullanılabilir. Profil oluşturucu komut satırı araçlarını kullanmak için, komut istemi penceresinin PATH ortamı değişkenine araçlar yolunu eklemeniz veya komutun kendisine eklemeniz gerekir.

 Eşzamanlı veri toplamak için profil oluşturucuyu hizmet işlemine bağlarsınız. Profil oluşturucu hizmete bağlıyken, veri toplamayı duraklatabilir ve devam ettirebilirsiniz. Profil oluşturma oturumunu sona erdirmek için profil oluşturucuartık hizmete eklenmemeli ve profil oluşturucu açıkça kapatılmalıdır. Çoğu durumda, oturumun sonunda profil oluşturma ortamı değişkenlerini temizlemenizi öneririz.

## <a name="attach-the-profiler"></a>Profil oluşturucuyu takın

#### <a name="to-attach-the-profiler-to-a-net-framework-service"></a>ProfiloluşturcIyi bir .NET Framework hizmetine eklemek için

1. Hizmeti yükleyin.

2. Komut penceresi açın.

3. Profil oluşturma ortamı değişkenlerini başlangıç olarak önleştirin. Şunu yazın:

     [VSPerfClrEnv](../profiling/vsperfclrenv.md) **/globalsampleon** [**/samplelineoff**]

    - **/globalsampleon** örneklemeyi sağlar.

    - **/samplelineoff,** toplanan verilerin belirli kaynak kod satırlarına atamasını devre dışı kılabilir. Bu seçenek belirtildiğinde, veriler yalnızca işlevlere atanır.

4. Bilgisayarı yeniden başlatın.

5. Profilciyi çalıştırın. Şunu yazın:

     [VSPerfCmd](../profiling/vsperfcmd.md) **/start:eşzamanlılık /çıktı:** `OutputFile` [`Options`]

     [/output](../profiling/output.md)**:** `OutputFile` seçeneği **/start**ile gereklidir. `OutputFile`profil oluşturma verileri (.vsp) dosyasının adını ve konumunu belirtir.

     **/başlat** seçeneği ile aşağıdaki seçeneklerden herhangi birini kullanabilirsiniz.

    > [!NOTE]
    > Hizmetler için **genellikle /kullanıcı** ve **/çapraz oturum** seçenekleri gereklidir.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/kullanıcı](../profiling/user-vsperfcmd.md) **:**[ ]`Domain`**\\**`UserName`|Profilli işlemin sahibi hesabın etki alanını ve kullanıcı adını belirtir. Bu seçenek, yalnızca işlem kullanıcı da oturum açmış kullanıcı dışında bir kullanıcı olarak çalışıyorsa gereklidir. İşlem sahibi, Windows Görev Yöneticisi'nin **İşlemler** sekmesinde **Kullanıcı Adı** sütununda listelenir.|
    |[/çapraz oturum](../profiling/crosssession.md)|Diğer oturumlarda işlemlerin profilini çıkarma sağlar. Hizmet farklı bir oturumda çalışıyorsa bu seçenek gereklidir. Oturum kimliği, Windows Görev Yöneticisi'nin **İşlemler** sekmesindeki **Oturum Kimliği** sütununda listelenir. **/CS** **/ crosssession**için bir kısaltma olarak belirtilebilir.|
    |[/wincounter](../profiling/wincounter.md) **:**`WinCounterPath`|Profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir.|
    |[/automark](../profiling/automark.md) **:**`Interval`|Yalnızca **/wincounter** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 ms'dir.|
    |[/olaylar](../profiling/events-vsperfcmd.md) **:**`Config`|Profil oluşturma sırasında toplanacak windows için olay izleme (ETW) olayı belirtir. ETW olayları ayrı bir şekilde toplanır (.* etl*) dosyası.|

6. Gerekirse hizmeti başlatın.

7. ProfiloluşturcIyi servise takın. Şunu yazın:

     **VSPerfCmd /ekle:** `PID` [[/targetclr](../profiling/targetclr.md)**:**`Version`]

    - `PID`hizmetin işlem kimliğini veya işlem adını belirtir. Windows Görev Yöneticisi'nde çalışan tüm işlemlerin işlem lerini görüntüleyebilirsiniz.

    - **targetclr:** `Version` bir uygulamada çalışma süresinin birden fazla sürümü yüklendiğinde, ortak dil çalışma zamanının (CLR) profilinin sürümünü belirtir. İsteğe bağlı.

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hizmet çalışırken, *VSPerfCmd.exe* seçeneklerini kullanarak dosyaya veri yazısını başlatıp durdurarak veri toplamayı denetleyebilirsiniz. Veri toplamayı denetlemek, uygulamanın başlatılması veya kapatılması gibi program yürütmesinin belirli bir bölümü için veri toplamanızı sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki **VSPerfCmd** seçenekleri, veri toplamayı başlayıp durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Tüm işlemler için **(/globalon)** başlatır veya durur (**/globaloff**) veri toplama.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|İşlem Kimliği tarafından belirtilen işlem için **(/processon)** başlatır veya **(/processoff)** veri toplamayı durdurur (`PID`).|
    |**/ekle:**`PID` { `ProcName`&#124;} [/detach](../profiling/detach.md)[:{`PID`&#124;`ProcName`}]|**/ekle** işlem kimliği veya işlem adı tarafından belirtilen işlem için veri toplamaya başlar. **/detach,** belirli bir işlem belirtilmemişse, belirtilen işlem veya tüm işlemler için veri toplamayı durdurur.|

- Veri dosyasına profil işareti eklemek için **VSPerfCmd.exe**[/mark](../profiling/mark.md) seçeneğini de kullanabilirsiniz. **/işareti** komutu bir tanımlayıcı, bir zaman damgası ve isteğe bağlı kullanıcı tanımlı metin dizesi ekler. Markalar, profil oluşturucu raporlarında ve veri görünümlerinde verileri filtrelemek için kullanılabilir. Aşağıdaki VSPerfCmd seçenekleri, veri toplamayı başlayıp durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sonlandırma
 Profil oluşturma oturumunu sona erdirmek için profil oluşturucunun veri toplamaması gerekir. Hizmeti durdurarak veya **VSPerfCmd /detach** seçeneğini çağırarak eşzamanlılık yöntemiyle profillenmiş bir uygulamadan veri toplamayı durdurabilirsiniz. Daha sonra profil oluşturma veri dosyasını kapatmak ve kapatmak için **VSPerfCmd /shutdown** seçeneğini çağırırsınız. **VSPerfClrEnv /globaloff** komutu profil oluşturma ortamı değişkenlerini temizler, ancak bilgisayar yeniden başlatılıncaya kadar sistem yapılandırması sıfırlanmaz.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdirmek için

1. Profiloluşturciyi hedef uygulamadan ayırmak için aşağıdakilerden birini yapın.

    - Servisi durdurun.

         -veya-

    - **VSPerfCmd /detach yazın.**

2. Profilciyi kapat. Şunu yazın:

     **VSPerfCmd**  [Kapatma](../profiling/shutdown.md)
