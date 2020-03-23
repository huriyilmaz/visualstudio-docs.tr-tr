---
title: 'Profiler komut satırı: İstemci .NET Framework uygulamasını açın, bellek verilerini alın'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3bc53041-91b7-4ad0-8413-f8bf2c4b3f5e
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: c9ee0ae59fd32394e31acc75184d0e55aaae872d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74775366"
---
# <a name="how-to-launch-a-stand-alone-net-framework-application-with-the-profiler-to-collect-memory-data-by-using-the-command-line"></a>Nasıl kullanılır: Komut satırını kullanarak bellek verilerini toplamak için profiloluşturucu ile tek başına bir .NET Framework uygulaması başlatın
Bu konu, bir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .NET Framework tek başına (istemci) uygulamasını başlatmak ve bellek verilerini toplamak için Profil Oluşturma Araçları komut satırı araçlarının nasıl kullanılacağını açıklar.

 Profil oluşturma oturumu üç bölümden oluşur:

- Profil oluşturucuyu kullanarak uygulamayı başlatın.

- Profil oluşturma verileri toplama.

- Profil oluşturma oturumunu sonlandırma.

> [!NOTE]
> Profil oluşturma araçlarına giden yolu almak [için](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)bkz. 64 bit bilgisayarlarda, araçların hem 64 bit hem de 32 bit sürümleri kullanılabilir. Profil oluşturucu komut satırı araçlarını kullanmak için, komut istemi penceresinin PATH ortamı değişkenine araçlar yolunu eklemeniz veya komutun kendisine eklemeniz gerekir.

## <a name="start-the-application-with-the-profiler"></a>Uygulamayı profil oluşturucuyla başlatın
 Profil oluşturucuyu kullanarak hedef bir uygulama başlatmak için, profil oluşturucuyu başlatmak ve uygulamayı başlatmak için **VSPerfCmd.exe/start** ve **/başlat seçeneklerini** kullanırsınız. Tek bir komut satırında **/başlat** ve **/başlat** ve ilgili seçeneklerini belirtebilirsiniz.

 Hedef uygulamanın başında veri toplamayı duraklatmak için **/globaloff** seçeneklerini de ekleyebilirsiniz. Daha sonra veri toplamaya başlamak için **/globalon'u** kullanırsınız.

#### <a name="to-start-an-application-by-using-the-profiler"></a>Profil oluşturucuyu kullanarak bir uygulamayı başlatmak için

1. Bir komut istemi penceresi açın.

2. Profilciyi çalıştırın. Şunu yazın:

    **VSPerfCmd /start:örnek /çıktı:** `OutputFile` [`Options`]

   - [/start](../profiling/start.md)**:örnek** seçeneği profil oluşturucuyu başlatir.

   - [/output](../profiling/output.md)**:** `OutputFile` seçeneği **/start**ile gereklidir. `OutputFile`profil oluşturma verileri (.vsp) dosyasının adını ve konumunu belirtir.

     **/start:sample** seçeneği ile aşağıdaki seçeneklerden herhangi birini kullanabilirsiniz.

   | Seçenek | Açıklama |
   | - | - |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Yalnızca **/wincounter** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 ms'dir. |

3. Hedef uygulamayı başlatın. Şunu yazın:

    **VSPerfCmd**[/launch](../profiling/launch.md) **:** `appName` **/gc:**{`Options`**tahsis**&#124;ömür **boyu**}[ ]  

   - .NET Framework bellek verilerini toplamak için [/gc](../profiling/gc-vsperfcmd.md)**:** `Keyword` seçeneği gereklidir. Anahtar kelime parametresi, bellek ayırma verilerinin toplanıp toplanmayacağını veya hem bellek ayırma hem de nesne yaşam boyu verilerini toplayıp toplayamayacağını belirtir.

     |Anahtar kelime|Açıklama|
     |-------------|-----------------|
     |**Ayırma**|Yalnızca bellek ayırma verilerini toplayın.|
     |**Ömür boyu**|Hem bellek ayırma hem de nesne yaşam boyu verileri toplayın.|

     **/başlat** seçeneği ile aşağıdaki seçeneklerden herhangi birini kullanabilirsiniz.

   |Seçenek|Açıklama|
   |------------|-----------------|
   |[/args](../profiling/args.md) **:**`Arguments`|Hedef uygulamaya geçirilecek komut satırı bağımsız değişkenlerini içeren bir dize belirtir.|
   |[/konsol](../profiling/console.md)|Hedef komut satırı uygulamasını ayrı bir pencerede başlatır.|
   |[/olaylar](../profiling/events-vsperfcmd.md) **:**`Config`|Profil oluşturma sırasında toplanacak windows için olay izleme (ETW) olayı belirtir. ETW olayları ayrı bir (.etl) dosyada toplanır.|
   |[/targetclr](../profiling/targetclr.md) **:**`Version`|Bir uygulamada çalışma zamanının birden fazla sürümü yüklendiğinde, ortak dil çalışma zamanının (CLR) profilinin sürümünü belirtir.|

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hedef uygulama çalışırken, *VSPerfCmd.exe* seçeneklerini kullanarak dosyaya veri yazısını başlatıp durdurarak veri toplamayı denetleyebilirsiniz. Veri toplamayı denetlemek, uygulamayı başlatma veya kapatma gibi program yürütmesinin belirli bir bölümü için veri toplamanızı sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki seçenek çiftleri veri toplamayı başlayıp durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Tüm işlemler için **(/globalon)** başlatır veya durur (**/globaloff**) veri toplama.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [processoff](../profiling/processon-and-processoff.md) **:**`PID`|İşlem Kimliği () tarafından belirtilen işlem için **(/processon)** başlatır veya`PID`(**/processoff**) veri toplamayı durdurur .|
    |[/ekle](../profiling/attach.md) **:** `PID` [/detach](../profiling/detach.md)|**/attach** tarafından `PID` belirtilen işlem (işlem kimliği) için veri toplamaya başlar. **/detach** tüm işlemler için veri toplamayı durdurur.|

- Veri dosyasına profil işareti eklemek için **VSPerfCmd.exe**[/mark](../profiling/mark.md) seçeneğini de kullanabilirsiniz. **/işareti** komutu bir tanımlayıcı, bir zaman damgası ve isteğe bağlı kullanıcı tanımlı metin dizesi ekler. İşaretler verileri filtrelemek için kullanılabilir.

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sonlandırma
 Profil oluşturma oturumunu sona erdirmek için profil oluşturucunun tüm profil işlemlerinden ayrılması ve profil oluşturucunun açıkça kapatılması gerekir. Uygulamayı kapatarak veya **VSPerfCmd /detach** seçeneğini arayarak profil oluşturma yöntemini kullanarak profillenmiş bir uygulamadan profillendirebilirsiniz. Daha sonra profil oluşturucuyu kapatmak ve profil oluşturma veri dosyasını kapatmak için **VSPerfCmd /shutdown** seçeneğini arayın. **VSPerfClrEnv /off** komutu profil oluşturma ortamı değişkenlerini temizler.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdirmek için

1. Profiloluşturucuyu hedef uygulamadan ayırmak için aşağıdaki adımlardan birini gerçekleştirin:

    - Hedef uygulamayı kapatın.

         -veya-

    - **VsPerfCmd /detach** yazın

2. Profilciyi kapat. Şunu yazın:

     **VSPerfCmd**  [/kapatma](../profiling/shutdown.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Profil tek başına uygulamalar](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [.NET bellek veri görünümleri](../profiling/dotnet-memory-data-views.md)
