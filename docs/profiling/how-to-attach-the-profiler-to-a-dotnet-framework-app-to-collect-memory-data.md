---
title: Bellek verileri toplamak için profil oluşturucuyu bir .NET uygulamasına ekleyin
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779135"
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-stand-alone-application-to-collect-memory-data-by-using-the-command-line"></a>Nasıl yapılır: komut satırını kullanarak bellek verileri toplamak için profil oluşturucuyu .NET Framework tek başına bir uygulamaya Iliştirme

Bu makalede, profil oluşturucuyu çalışan bir .NET Framework tek başına (istemci) uygulamasına eklemek ve bellek verileri toplamak için Visual Studio Profil Oluşturma Araçları komut satırı araçlarının nasıl kullanılacağı açıklanır.

> [!NOTE]
> Profil oluşturma araçlarının yolunu almak için, bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). 64 bit bilgisayarlarda, araçların her ikisi de 64-bit ve 32 bit sürümleri mevcuttur. Profil oluşturucu komut satırı araçlarını kullanmak için araçlar yolunu komut Istemi penceresinin PATH ortam değişkenine eklemeniz ya da komutun kendisine eklemeniz gerekir.

Bir .NET Framework uygulamasına eklemek ve bellek verileri toplamak için, hedef uygulama başlamadan önce uygun ortam değişkenlerini başlatmak üzere [VSPerfCLREnv. cmd](../profiling/vsperfclrenv.md) aracını kullanmanız gerekir. Profil Oluşturucu uygulamaya eklendiğinde, veri toplamayı duraklatmak ve devam ettirmeyi sağlamak için *VSPerfCmd. exe* aracını kullanabilirsiniz.

Profil oluşturma oturumunu sonlandırmak için, profil oluşturucunun profili oluşturulmuş tüm işlemlerden ayrılması ve profil oluşturucunun açıkça kapatılması gerekir. Çoğu durumda, bir oturumun sonunda profil oluşturma ortam değişkenlerini temizlemeniz önerilir.

## <a name="attach-the-profiler"></a>Profil oluşturucuyu iliştirme

### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Profil oluşturucuyu çalışan bir .NET Framework uygulamasına eklemek için

1. Bir Komut İstemi penceresi açın.

2. Profil oluşturma ortamı değişkenlerini başlatın. Tür:

     **VSPerfCLREnv** { **/samplegc** &#124; **/örnekleclife**} [ **/samplelineoff**]

    - **/Samplegc** ve **/samplegclife** seçenekleri yalnızca bellek ayırma verilerinin mi toplanacağını yoksa hem bellek ayırma hem de nesne yaşam süresi verilerinin mi toplanacağını belirtir. Tek bir ve yalnızca bir seçenek belirtilmelidir.

        |Seçenek|Tanımlar|
        |------------|------------------|
        |**/samplegc**|Yalnızca bellek ayırma verilerini toplayın.|
        |**/samplegclife**|Hem bellek ayırma hem de nesne yaşam süresi verilerini toplayın.|

    - **/Samplelineoff** seçeneği, kaynak kodu satır numarası verileri koleksiyonunu devre dışı bırakır.

3. Profil oluşturucuyu başlatın. Tür:

     **VSPerfCmd/start: örnek/output:** `OutputFile` [`Options`]

   - [/Start](../profiling/start.md) **: örnek** seçeneği, profil oluşturucuyu başlatır.

   - [/Output](../profiling/output.md) **:** `OutputFile` seçeneği, **/Start**ile gereklidir. `OutputFile` profil oluşturma verileri (. vsp) dosyasının adını ve konumunu belirtir.

     Aşağıdaki seçeneklerden herhangi birini, **/Start: Sample** seçeneğiyle kullanabilirsiniz.

     | Seçenek | Açıklama |
     | - | - |
     | [/User](../profiling/user-vsperfcmd.md) **:** [`Domain` **\\** ]`UserName` | Profili oluşturulan işlemin sahibi olan hesabın etki alanını ve Kullanıcı adını belirtir. Bu seçenek yalnızca, işlem oturum açan kullanıcıdan farklı bir kullanıcı olarak çalışıyorsa gereklidir. İşlem sahibi, Windows Görev Yöneticisi 'nin Işlemler sekmesinde Kullanıcı adı sütununda listelenir. |
     | [/CrossSession &#124; /CS](../profiling/crosssession.md) | Diğer oturumlardaki işlemlerin profilini oluşturmaya izin vermez. Uygulama farklı bir oturumda çalışıyorsa, bu seçenek gereklidir. Oturum kimliği, Windows Görev Yöneticisi 'nin süreçler sekmesindeki oturum kimliği sütununda listelenir. **/CS** , **/CrossSession**için bir kısaltma olarak belirtilebilir. |
     | [/WINCOUNTER](../profiling/wincounter.md) **:** `WinCounterPath` | Profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir. |
     | [/AutoMark](../profiling/automark.md) **:** `Interval` | Yalnızca **/WINCOUNTER** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 MS 'dir. |

4. Gerekirse, hedef uygulamayı normal şekilde başlatın.

5. Profil oluşturucuyu hedef uygulamaya ekleyin. Tür:

     **VSPerfCmd**[/Attach](../profiling/attach.md) **:** {`PID`&#124;`ProcName`} [[/targetclr](../profiling/targetclr.md) **:** `Version`]

    - `PID` hedef uygulamanın işlem KIMLIĞINI belirtir. `ProcessName` işlemin adını belirtir. `ProcessName` belirtirseniz ve aynı ada sahip birden çok işlem çalışıyorsa, sonuçların tahmin edilemez olduğunu unutmayın. Windows Görev Yöneticisi 'nde çalışan tüm işlemlerin işlem kimliklerini görüntüleyebilirsiniz.

    - **/targetclr:** `Version` bir uygulamaya çalışma zamanının birden fazla sürümü yüklendiğinde profil için ortak dil çalışma ZAMANıNıN (CLR) sürümünü belirtir. İsteğe bağlı.

## <a name="control-data-collection"></a>Veri toplamayı denetleme

Hedef uygulama çalışırken, *VSPerfCmd. exe* seçeneklerini kullanarak verileri dosyaya yazmayı başlatıp durdurarak veri toplamayı kontrol edebilirsiniz. Veri toplamayı denetlemek, program yürütmesinin, uygulamayı başlatma veya kapatma gibi belirli bir bölümü için veri toplamanızı sağlar.

### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki seçenek çiftleri veri toplamayı başlatır ve durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Tüm süreçler için veri toplamayı başlatır ( **/GlobalOn**) veya Durdur ( **/globaloff**).|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:** `PID`|`PID`tarafından belirtilen işlem için veri toplamayı başlatır ( **/ProcessOn**) veya duraklar ( **/ProcessOff**).|
    |[/Attach](../profiling/attach.md) **:** {`PID`&#124;`ProcName`} [/Detach](../profiling/detach.md)[ **:** {`PID`&#124;`ProcName`}]|**/Attach** , `PID` veya işlem adı (ProcName) tarafından belirtilen işlem için veri toplamaya başlar. **/Detach** belirtilen işlem veya belirli bir işlem belirtilmemişse tüm işlemler için veri toplamayı durduruyor.|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu Sonlandır

Profil oluşturma oturumunu sonlandırmak için, profil oluşturucunun profili oluşturulmuş tüm işlemlerden ayrılması ve profil oluşturucunun açıkça kapatılması gerekir. Profil oluşturucuyu, uygulamayı kapatarak veya **VSPerfCmd/detach** seçeneğini çağırarak örnekleme yöntemini kullanarak profili oluşturulmuş bir uygulamadan ayırabilirsiniz. Ardından, profil oluşturucuyu kapatmak ve profil oluşturma veri dosyasını kapatmak için **VSPerfCmd/shutdown** seçeneğini çağırın. **VSPerfCLREnv/off** komutu profil oluşturma ortam değişkenlerini temizler.

### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sonlandırmak için

1. Profil oluşturucuyu hedef uygulamadan ayırmak için aşağıdaki adımlardan birini gerçekleştirin:

    - **VSPerfCmd/detach** yazın

         veya

    - Hedef uygulamayı kapatın.

2. Profil oluşturucuyu kapatın. Tür:

     **VSPerfCmd**  [/Shutdown](../profiling/shutdown.md)

3. Seçim Profil oluşturma ortamı değişkenlerini temizleyin. Tür:

     **VSPerfCmd/off**

## <a name="see-also"></a>Ayrıca bkz.

[.Net bellek verileri görünümlerini](../profiling/dotnet-memory-data-views.md)
[tek başına uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)
