---
title: Bellek verileri toplamak için profiloluşturcağı bir .NET uygulamasına takın
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 04dcf800074476b285a07e36db5a85fa3a366585
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779135"
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-stand-alone-application-to-collect-memory-data-by-using-the-command-line"></a>Nasıl kullanılır: Komut satırını kullanarak bellek verilerini toplamak için profil oluşturucuyu .NET Framework tek başına uygulamasına takın

Bu makalede, profil oluşturucuyu çalışan bir .NET Framework tek başına (istemci) uygulamasına eklemek ve bellek verilerini toplamak için Visual Studio Profil Oluşturma Araçları komut satırı araçlarının nasıl kullanılacağı açıklanmaktadır.

> [!NOTE]
> Profil oluşturma araçlarına giden yolu almak [için](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)bkz. 64 bit bilgisayarlarda, araçların hem 64 bit hem de 32 bit sürümleri kullanılabilir. Profil oluşturucu komut satırı araçlarını kullanmak için, komut istemi penceresinin PATH ortamı değişkenine araçlar yolunu eklemeniz veya komutun kendisine eklemeniz gerekir.

Bir .NET Framework uygulamasına eklemek ve bellek verilerini toplamak için, hedef uygulama başlamadan önce uygun ortam değişkenlerini başlatmak için [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) aracını kullanmanız gerekir. Profil oluşturucu uygulamaya iliştirildiğinde, veri toplamayı duraklatmak ve devam ettirmek için *VSPerfCmd.exe* aracını kullanabilirsiniz.

Profil oluşturma oturumunu sona erdirmek için profil oluşturucunun tüm profil işlemlerinden ayrılması ve profil oluşturucunun açıkça kapatılması gerekir. Çoğu durumda, oturumun sonunda profil oluşturma ortamı değişkenlerini temizlemenizi öneririz.

## <a name="attach-the-profiler"></a>Profil oluşturucuyu takın

### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Çalışan bir .NET Framework uygulamasına profil oluşturucu eklemek için

1. Bir komut istemi penceresi açın.

2. Profil oluşturma ortamı değişkenlerini başlangıç olarak önleştirin. Şunu yazın:

     **VSPerfClrEnv** {**/samplegc** &#124; **/samplegclife**} [**/samplelineoff**]

    - **/samplegc** ve **/samplegclife** seçenekleri, yalnızca bellek ayırma verilerinin toplanıp toplanmayacağını veya hem bellek ayırma hem de nesne yaşam boyu verilerini toplayıp toplayamayacağını belirtir. Bir ve tek bir seçenek belirtilmelidir.

        |Seçenek|Açıklama|
        |------------|------------------|
        |**/samplegc**|Yalnızca bellek ayırma verilerini toplayın.|
        |**/samplegclife**|Hem bellek ayırma hem de nesne yaşam boyu verileri toplayın.|

    - **/samplelineoff** seçeneği kaynak kodu satırı numarası verilerinin toplanmasını devre dışı kılabilir.

3. Profilciyi çalıştırın. Şunu yazın:

     **VSPerfCmd /start:örnek /çıktı:** `OutputFile` [`Options`]

   - [/start](../profiling/start.md)**:örnek** seçeneği profil oluşturucuyu başlatir.

   - [/output](../profiling/output.md)**:** `OutputFile` seçeneği **/start**ile gereklidir. `OutputFile`profil oluşturma verileri (.vsp) dosyasının adını ve konumunu belirtir.

     **/start:sample** seçeneği ile aşağıdaki seçeneklerden herhangi birini kullanabilirsiniz.

     | Seçenek | Açıklama |
     | - | - |
     | [/kullanıcı](../profiling/user-vsperfcmd.md) **:**[ ]`Domain`**\\**`UserName` | Profilli işlemin sahibi hesabın etki alanını ve kullanıcı adını belirtir. Bu seçenek yalnızca işlem oturum açmış kullanıcı dışında bir kullanıcı olarak çalışıyorsa gereklidir. İşlem sahibi, Windows Görev Yöneticisi'nin İşlemler sekmesinde Kullanıcı Adı sütununda listelenir. |
     | [/crosssession &#124; /cs](../profiling/crosssession.md) | Diğer oturumlarda işlemlerin profilini çıkarma sağlar. Uygulama farklı bir oturumda çalışıyorsa bu seçenek gereklidir. Oturum tanımlayıcısı, Windows Görev Yöneticisi'nin İşlemler sekmesindeki Oturum Kimliği sütununda listelenir. **/CS** **/ crosssession**için bir kısaltma olarak belirtilebilir. |
     | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir. |
     | [/automark](../profiling/automark.md) **:**`Interval` | Yalnızca **/wincounter** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 ms'dir. |

4. Gerekirse, hedef uygulamayı tipik bir şekilde başlatın.

5. Profil oluşturucuyu hedef uygulamaya takın. Şunu yazın:

     **VSPerfCmd**[/ eklemek](../profiling/attach.md) `ProcName` **:**{`PID`&#124;} [ /[targetclr](../profiling/targetclr.md)**:**`Version`]  

    - `PID`hedef uygulamanın işlem kimliğini belirtir. `ProcessName`işlemin adını belirtir. Aynı ada `ProcessName` sahip birden çok işlem belirtirseniz ve birden çok işlem çalışıyorsa, sonuçların öngörülemez olduğunu unutmayın. Windows Görev Yöneticisi'nde çalışan tüm işlemlerin işlem lerini görüntüleyebilirsiniz.

    - **/targetclr:** `Version` bir uygulamada çalışma süresinin birden fazla sürümü yüklendiğinde, ortak dil çalışma zamanının (CLR) profilinin sürümünü belirtir. İsteğe bağlı.

## <a name="control-data-collection"></a>Veri toplamayı denetleme

Hedef uygulama çalışırken, *VSPerfCmd.exe* seçeneklerini kullanarak dosyaya veri yazısını başlatıp durdurarak veri toplamayı denetleyebilirsiniz. Veri toplamayı denetlemek, uygulamayı başlatma veya kapatma gibi program yürütmesinin belirli bir bölümü için veri toplamanızı sağlar.

### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki seçenek çiftleri veri toplamayı başlayıp durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Tüm işlemler için **(/globalon)** başlatır veya durur (**/globaloff**) veri toplama.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Tarafından belirtilen `PID`işlem için (**/processon)** başlatır veya durur (**/processoff**) veri toplama.|
    |[/ekle](../profiling/attach.md) **:**:`PID` `ProcName`{&#124;} [/ayırma](../profiling/detach.md) `ProcName`[**:**{`PID`&#124;}]|**/ekle** `PID` veya işlem adı (ProcName) tarafından belirtilen işlem için veri toplamaya başlar. **/detach,** belirli bir işlem belirtilmemişse, belirtilen işlem veya tüm işlemler için veri toplamayı durdurur.|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sonlandırma

Profil oluşturma oturumunu sona erdirmek için profil oluşturucunun tüm profil işlemlerinden ayrılması ve profil oluşturucunun açıkça kapatılması gerekir. Uygulamayı kapatarak veya **VSPerfCmd /detach** seçeneğini arayarak profil oluşturma yöntemini kullanarak profillenmiş bir uygulamadan profillendirebilirsiniz. Daha sonra profil oluşturucuyu kapatmak ve profil oluşturma veri dosyasını kapatmak için **VSPerfCmd /shutdown** seçeneğini arayın. **VSPerfClrEnv /off** komutu profil oluşturma ortamı değişkenlerini temizler.

### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdirmek için

1. Profiloluşturucuyu hedef uygulamadan ayırmak için aşağıdaki adımlardan birini gerçekleştirin:

    - **VsPerfCmd /detach** yazın

         -veya-

    - Hedef uygulamayı kapatın.

2. Profilciyi kapat. Şunu yazın:

     **VSPerfCmd**  [/kapatma](../profiling/shutdown.md)

3. (İsteğe bağlı) Profil oluşturma ortamı değişkenlerini temizleyin. Şunu yazın:

     **VSPerfCmd /kapalı**

## <a name="see-also"></a>Ayrıca bkz.

[Profil tek başına uygulamalar](../profiling/command-line-profiling-of-stand-alone-applications.md)
[.NET bellek veri görünümleri](../profiling/dotnet-memory-data-views.md)
