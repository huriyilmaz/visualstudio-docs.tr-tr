---
title: 'Profiler komut satırı: İstemci .NET uygulamasını açın, eşzamanlılık verilerini alın'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 17a48848-bd3e-44ef-9971-e39836ff1df2
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 4a52c65f8a53d62edde42c26fafef9940046ba5d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74775405"
---
# <a name="how-to-launch-a-stand-alone-net-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line"></a>Nasıl kullanılır: Komut satırını kullanarak eşzamanlılık verileri toplamak için profiloluşturucu ile tek başına bir .NET Framework uygulaması başlatın
Bu konu, bir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .NET Framework tek başına (istemci) uygulaması başlatmak ve işlem ve iş parçacığı eşzamanlılık verilerini toplamak için Profil Oluşturma Araçları komut satırı araçlarının nasıl kullanılacağını açıklar

> [!NOTE]
> Profil oluşturma araçlarına giden yolu almak [için](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)bkz. 64 bit bilgisayarlarda, araçların hem 64 bit hem de 32 bit sürümleri kullanılabilir. Profil oluşturucu komut satırı araçlarını kullanmak için, komut istemi penceresinin PATH ortamı değişkenine araçlar yolunu eklemeniz veya komutun kendisine eklemeniz gerekir.

 Profil oluşturucu uygulamaya bağlı yken, veri toplamayı duraklatabilir ve devam ettirebilirsiniz. Profil oluşturma oturumunu sona erdirmek için Profiler'ın uygulamaya artık eklenmemesi ve Profiler'ın açıkça kapatılması gerekir.

## <a name="start-the-application-with-the-profiler"></a>Uygulamayı profil oluşturucuyla başlatın
 Profiler ile bir .NET Framework hedef uygulaması başlatmak için,.NET Framework profil oluşturma değişkenlerini ayarlamak için *VSPerfClrEnv.exe* kullanırsınız. Daha sonra Profiler'ı başlatmak ve uygulamayı başlatmak için VSPerfCmd **/start** ve **/başlat** seçeneklerini kullanırsınız. Tek bir komut satırında **/başlat** ve **/başlat** ve ilgili seçeneklerini belirtebilirsiniz. Hedef uygulama başladığında veri toplamayı duraklatmak için komut satırına **/globaloff** seçeneğini de ekleyebilirsiniz. Daha sonra veri toplamaya başlamak için ayrı bir komut satırında **/globalon** kullanırsınız.

#### <a name="to-start-an-application-with-the-profiler"></a>Profil oluşturucuyla bir uygulama başlatmak için

1. Bir komut istemi penceresi açın.

2. Profilciyi çalıştırın. Şunu yazın:

    [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency**[**,**{**ResourceOnly**&#124;**ThreadOnly**}] **/output:** `OutputFile` [ ]`Options`

   - [/başlat](../profiling/start.md) seçeneği profil oluşturucuyu başlatir.

     | | |
     |-------------------------------------| - |
     | **/start:eşzamanlılık** | Hem kaynak çekişmesi hem de iş parçacığı yürütme verilerinin toplanmasını sağlar. |
     | **/start:eşzamanlılık,kaynak yalnızca** | Yalnızca kaynak çekişme verilerinin toplanmasını sağlar. |
     | **/start:eşzamanlılık,iş parçacığı** | Yalnızca iş parçacığı yürütme verilerinin toplanmasını sağlar. |

   - [/output](../profiling/output.md)**:** `OutputFile` seçeneği **/start**ile gereklidir. `OutputFile`profil oluşturma verileri (.vsp) dosyasının adını ve konumunu belirtir.

     **/start:eşzamanlılık** seçeneği ile aşağıdaki seçeneklerden herhangi birini kullanabilirsiniz.

   | Seçenek | Açıklama |
   | - | - |
   | [/kullanıcı](../profiling/user-vsperfcmd.md) **:**[ ]`domain\``username` | Profiloluşturucuya erişim hakkı verilecek isteğe bağlı etki alanını ve hesabın kullanıcı adını belirtir. |
   | [/çapraz oturum](../profiling/crosssession.md) | Diğer oturum oturumlarında işlemlerin profilini çıkarmasağlar. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Yalnızca **/wincounter** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 ms'dir. |
   | [/olaylar](../profiling/events-vsperfcmd.md) **:**`Config` | Profil oluşturma sırasında toplanacak windows için olay izleme (ETW) olayı belirtir. ETW olayları ayrı bir şekilde toplanır (.* etl*) dosyası. |

3. Hedef uygulamayı başlatın. Şunu yazın:

    **VSPerfCmd**[/başlat](../profiling/launch.md) `Options` **:** `AppName` `Sample Event`[ ] ]  

    **/başlat** seçeneği ile aşağıdaki seçeneklerden herhangi birini kullanabilirsiniz.

   |Seçenek|Açıklama|
   |------------|-----------------|
   |[/args](../profiling/args.md) **:**`Arguments`|Hedef uygulamaya geçirilecek komut satırı bağımsız değişkenlerini içeren bir dize belirtir.|
   |[/konsol](../profiling/console.md)|Hedef komut satırı uygulamasını ayrı bir pencerede başlatır.|
   |[/targetclr](../profiling/targetclr.md) **:**`Version`|Bir uygulamada çalışma zamanının birden fazla sürümü yüklendiğinde, ortak dil çalışma zamanının (CLR) profilinin sürümünü belirtir.|

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hedef uygulama çalışırken, *VSPerfCmd.exe* seçeneklerini kullanarak dosyaya veri yazısını başlatıp durdurarak veri toplamayı denetleyebilirsiniz. Veri toplamayı denetlemek, uygulamanın başlatılması veya kapatılması gibi program yürütmesinin belirli bir bölümü için veri toplamanızı sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

1. Aşağıdaki *VSPerfCmd.exe* seçenekleri çiftleri veri toplamayı başlayıp durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Tüm işlemler için **(/globalon)** başlatır veya durur (**/globaloff**) veri toplama.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|İşlem Kimliği tarafından belirtilen işlem için **(/processon)** başlatır veya **(/processoff)** veri toplamayı durdurur (`PID`).|
    |[/ekle](../profiling/attach.md) **:**:`PID` `ProcName`{&#124;} [/ayırma](../profiling/detach.md) `ProcName`[**:**{`PID`&#124;}]|**/ekle** işlem kimliği (`PID`) veya işlem adı (ProcName) tarafından belirtilen işlem için veri toplamaya başlar. **/detach,** belirli bir işlem belirtilmemişse, belirtilen işlem veya tüm işlemler için veri toplamayı durdurur.|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sonlandırma
 Profil oluşturma oturumunu sona erdirmek için profil oluşturucunun veri toplamaması gerekir. Profilli uygulamayı kapatarak veya **VSPerfCmd /detach** seçeneğini çağırarak eşzamanlılık verileri toplamayı durdurabilirsiniz. Daha sonra profil oluşturucuyu kapatmak ve profil oluşturma veri dosyasını kapatmak için **VSPerfCmd /shutdown** seçeneğini çağırırsınız. **VSPerfClrEnv /off** komutu profil oluşturma ortamı değişkenlerini temizler.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdirmek için

1. Profiloluşturciyi hedef uygulamadan ayırmak için aşağıdakilerden birini yapın.

    - Hedef uygulamayı kapatın.

         -veya-

    - **VsPerfCmd /detach** yazın

2. Profil oluşturucuyu kapatma

     **VSPerfCmd**  [/kapatma](../profiling/shutdown.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)
