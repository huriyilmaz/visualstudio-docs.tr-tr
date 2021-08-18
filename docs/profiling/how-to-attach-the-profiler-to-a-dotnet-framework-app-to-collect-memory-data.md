---
title: Bellek verilerini toplamak için .NET'e profil oluşturma ekleme
description: Çalışan bir Visual Studio Profil Oluşturma Araçları (istemci) uygulamasına profil oluşturma eklemek ve bellek verilerini .NET Framework komut satırı araçlarını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 68854e9b3082ce017e4a8b41d9875a2f5610d278c45974a141095bc2f2e35cd6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121442209"
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-stand-alone-application-to-collect-memory-data-by-using-the-command-line"></a>Nasıl kullanılır: Komut satırı kullanarak bellek .NET Framework için tek başına bir uygulamanın profil oluşturma profili oluşturma

Bu makalede, çalışan bir Visual Studio Profil Oluşturma Araçları (istemci) uygulamasına profilleyici eklemek ve bellek verilerini toplamak için .NET Framework komut satırı araçlarının nasıl kullanımı açıklanmıştır.

> [!NOTE]
> Profil oluşturma araçlarının yolunu almak için [bkz. Komut satırı araçlarının yolunu belirtme.](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md) 64 bit bilgisayarlarda, araçların hem 64 bit hem de 32 bit sürümleri kullanılabilir. Profil oluşturma komut satırı araçlarını kullanmak için, araç yolunu Komut İstemi penceresinin PATH ortam değişkenine eklemeniz veya komutun kendisine eklemeniz gerekir.

Bir .NET Framework eklemek ve bellek verileri toplamak için, hedef uygulama başlatılmadan önce uygun ortam değişkenlerini başlatmak üzere [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) aracını kullanmalıdır. Profiler uygulamaya ekli olduğunda, veri toplamayı *duraklatmak veVSPerfCmd.exe* içinVSPerfCmd.exearacını kullanabilirsiniz.

Profil oluşturma oturumunu sona erdirmak için profil oluşturma işleminin tüm profili yapılan işlemlerden ayrılmaları ve profil oluşturma işleminin açıkça kapatılmış olması gerekir. Çoğu durumda, bir oturumun sonunda profil oluşturma ortam değişkenlerini temizlemenizi öneririz.

## <a name="attach-the-profiler"></a>Profilleyiciyi ekleme

### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Profilleyiciyi çalışan bir uygulamanın .NET Framework için

1. Bir komut istemi penceresi açın.

2. Profil oluşturma ortam değişkenlerini başlatma. Şunu yazın:

     **VSPerfClrEnv** {**/samplegc** &#124; **/samplegclife**} [**/samplelineoff**]

    - **/samplegc** ve **/samplegclife** seçenekleri yalnızca bellek ayırma verilerini mi toplaymak yoksa hem bellek ayırma hem de nesne yaşam süresi verilerini toplamak için mi belirtebilirsiniz. Bir ve yalnızca bir seçenek belirtilmelidir.

        |Seçenek|Açıklama|
        |------------|------------------|
        |**/samplegc**|Yalnızca bellek ayırma verilerini toplayın.|
        |**/samplegclife**|Hem bellek ayırma hem de nesne yaşam süresi verilerini toplayın.|

    - **/samplelineoff seçeneği,** kaynak kod satırı numarası verilerini toplamayı devre dışı bırakıyor.

3. Profilleyiciyi başlatma. Şunu yazın:

     **VSPerfCmd /start:sample /output:** `OutputFile` [`Options`]

   - [/start](../profiling/start.md)**:sample** seçeneği profilleyiciyi başlatıyor.

   - [/output](../profiling/output.md)**: seçeneği** / start ile `OutputFile` **gereklidir.** `OutputFile` profil oluşturma verileri (.vsp) dosyasının adını ve konumunu belirtir.

     **/start:sample** seçeneğiyle aşağıdaki seçeneklerden herhangi birini kullanabilirsiniz.

     | Seçenek | Açıklama |
     | - | - |
     | [/user](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Profili yapılan işleme sahip olan hesabın etki alanını ve kullanıcı adını belirtir. Bu seçenek yalnızca işlem oturum açmış kullanıcıdan farklı bir kullanıcı olarak çalışıyorsa gereklidir. İşlem sahibi, Görev Yöneticisi'nin İşlemler sekmesindeki Kullanıcı Adı Windows listelenir. |
     | [/cs için /crosssession &#124;](../profiling/crosssession.md) | Diğer oturumlarda işlemlerin profilini oluşturmayı sağlar. Uygulama farklı bir oturumda çalışıyorsa bu seçenek gereklidir. Oturum kimliği, Görev Yöneticisi'nin İşlemler sekmesindeki Oturum Kimliği Windows listelenir. **/CS,** **/crosssession için bir kısaltma olarak belirtilebilir.** |
     | [/wincounter:](../profiling/wincounter.md) `WinCounterPath` | Profil oluşturma Windows toplanacak bir performans sayacı belirtir. |
     | [/automark:](../profiling/automark.md) `Interval` | Yalnızca **/wincounter ile** kullanın. Performans sayacı toplama olayları arasındaki milisaniye Windows sayısını belirtir. Varsayılan değer 500 ms'tir. |

4. Gerekirse, hedef uygulamayı tipik bir şekilde başlatabilirsiniz.

5. Profilleyiciyi hedef uygulamaya ekleme. Şunu yazın:

     **VSPerfCmd**[/attach:](../profiling/attach.md) {&#124;} `PID` [ `ProcName` [/targetclr](../profiling/targetclr.md)**:** `Version` ]  

    - `PID` hedef uygulamanın işlem kimliğini belirtir. `ProcessName` , işlem adını belirtir. belirttiğinizde ve aynı `ProcessName` adı içeren birden çok işlem çalışıyorsa, sonuçların tahmin edilemez olduğunu unutmayın. Görev Yöneticisi'nde çalışan tüm işlemlerin işlem kimliklerini Windows görüntüebilirsiniz.

    - **/targetclr:** `Version` bir uygulamada birden fazla çalışma zamanı sürümü yüklendiğinde profili oluşturmak için ortak dil çalışma zamanının (CLR) sürümünü belirtir. İsteğe bağlı.

## <a name="control-data-collection"></a>Veri toplamayı denetleme

Hedef uygulama çalıştıryken, veri toplama seçeneklerini kullanarak dosyada veri yazmayı başlatarak ve *durdurarak veriVSPerfCmd.exeyapabilirsiniz.* Veri toplamayı denetlemek, uygulamayı başlatma veya kapatma gibi program yürütmenin belirli bir bölümü için veri toplamaya olanak sağlar.

### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki seçenek çiftleri veri toplamayı başlat ve durdur. Her seçeneği ayrı bir komut satırı üzerinde belirtin. Veri toplamayı birden çok kez açabilirsiniz ve kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Tüm işlemler **için veri toplamayı** başlatır ( /globalon ) veya durdurur (**/globaloff).**|
    |[/processon:](../profiling/processon-and-processoff.md)  `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|tarafından belirtilen işlem için (**/processon**) veya durdurur (**/processoff**) veri toplamayı `PID` durdurur.|
    |[/attach:](../profiling/attach.md) { `PID`&#124;`ProcName` } [/detach](../profiling/detach.md)[**:**{ `PID`&#124;`ProcName` }]|**/attach,** veya işlem adı (ProcName) tarafından belirtilen işlem `PID` için veri toplamaya başlar. **/detach,** belirtilen işlem için veya belirli bir işlem belirtilmezse tüm işlemler için veri toplamayı durdurur.|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sona er

Profil oluşturma oturumunu sona erdirmak için profil oluşturma işleminin tüm profili yapılan işlemlerden ayrılmaları ve profil oluşturma işleminin açıkça kapatılmış olması gerekir. Uygulamayı kapatarak veya **VSPerfCmd /detach** seçeneğini çağırarak, örnekleme yöntemini kullanarak profil profili yapılan bir uygulamanın profillerini ayırabilirsiniz. Ardından **VSPerfCmd /shutdown** seçeneğini çağırarak profil oluşturma veri dosyasını kapatın. **VSPerfClrEnv /off** komutu profil oluşturma ortam değişkenlerini temizler.

### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdir

1. Profilleyiciyi hedef uygulamadan ayırmak için aşağıdaki adımlardan birini gerçekleştirin:

    - **VSPerfCmd /detach yazın**

         -veya-

    - Hedef uygulamayı kapatın.

2. Profilleyiciyi kapatın. Şunu yazın:

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)

3. (İsteğe bağlı) Profil oluşturma ortam değişkenlerini temizleme. Şunu yazın:

     **VSPerfCmd /off**

## <a name="see-also"></a>Ayrıca bkz.

[Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md) 
 [.NET bellek veri görünümleri](../profiling/dotnet-memory-data-views.md)
