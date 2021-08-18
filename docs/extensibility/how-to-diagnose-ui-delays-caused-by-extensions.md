---
title: Visual Studio | Uzantı Kullanıcı arabirimi gecikmelerini tanılama Microsoft Docs
description: Visual Studio, kullanıcı arabirimi gecikmelerini bir uzantının neden olup olmadığını bildirir. Uzantı kodunuzda ne tür bir kullanıcı arabirimi gecikmesine neden olduğunu nasıl tanıleyeceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: conceptual
author: j-martens
ms.author: jmartens
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload: multiple
ms.openlocfilehash: 6309d014e2ec2c520a7cba24c8642c27fbb6f339
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122125016"
---
# <a name="how-to-diagnose-ui-delays-caused-by-extensions"></a>Nasıl yapılır: Uzantılardan kaynaklanan kullanıcı arabirimi gecikmelerini tanılama

uı yanıt vermediğinde Visual Studio, yaprak ile başlayıp temel doğru çalışarak uı iş parçacığının çağrı yığınını inceler. Visual Studio, bir çağrı yığını çerçevesinin yüklü ve etkinleştirilmiş bir uzantının parçası olan bir modüle ait olduğunu belirlerse, bir bildirim gösterir.

![UI gecikmesi (yanıt verme) bildirimi](media/ui-delay-notification-in-vs.png)

Bildirim, kullanıcıya kullanıcı ARABIRIMI gecikmesi (yani, Kullanıcı arabirimindeki yanıt verme) uzantısından kodun sonucu olabileceğini bildirir. Ayrıca, kullanıcıya uzantıyı devre dışı bırakma seçeneklerini veya bu uzantıya yönelik gelecekteki bildirimleri sağlar.

Bu belge, uzantı kodunuzda ne tür bir kullanıcı arabirimi gecikme bildirimlerine neden olduğunu nasıl tanılabileceğinizi açıklar.

> [!NOTE]
> uı gecikmelerini tanılamak için Visual Studio deneysel örneğini kullanmayın. UI gecikmesi bildirimleri için gereken çağrı yığını analizinin bazı kısımları deneysel örnek kullanılırken devre dışı bırakılmak, yani UI gecikmesi bildirimleri gösterilmeyebilir.

Tanılama işlemine genel bakış aşağıdaki gibidir:
1. Tetikleyici senaryosunu belirler.
2. Etkinlik günlüğü ile VS 'yi yeniden başlatın.
3. ETW izlemeyi Başlat.
4. Bildirimi tekrar görüntülenecek şekilde tetikleyin.
5. ETW izlemeyi durdurun.
6. Gecikme KIMLIĞINI almak için etkinlik günlüğünü inceleyin.
7. 6. adımdaki gecikme KIMLIĞINI kullanarak ETW izlemesini çözümleyin.

Aşağıdaki bölümlerde, bu adımları daha ayrıntılı bir şekilde inceleyeceğiz.

## <a name="identify-the-trigger-scenario"></a>Tetikleyici senaryosunu tanımla

uı gecikmesini tanılamak için, ilk olarak ne (eylem sırası) Visual Studio bildirimi göstermesini istediğinizi belirlemeniz gerekir. Bu, daha sonra oturum açma özelliği ile bildirimi tetikleyebilmek için kullanılır.

## <a name="restart-vs-with-activity-logging-on"></a>Etkinlik günlüğü ile VS 'yi yeniden Başlat

Visual Studio, sorun ayıklanırken yararlı bilgiler sağlayan bir "etkinlik günlüğü" oluşturabilir. etkinlik günlüğünü Visual Studio açmak için `/log` komut satırı seçeneği ile Visual Studio açın. Visual Studio başladıktan sonra, etkinlik günlüğü şu konumda depolanır:

```DOS
%APPDATA%\Microsoft\VisualStudio\<vs_instance_id>\ActivityLog.xml
```

VS örnek kimliğinizi nasıl bulabileceğiniz hakkında daha fazla bilgi edinmek için bkz. [Visual Studio örnekleri algılama ve yönetme araçları](../install/tools-for-managing-visual-studio-instances.md). UI gecikmeleri ve ilgili bildirimler hakkında daha fazla bilgi edinmek için bu etkinlik günlüğünü daha sonra kullanacağız.

## <a name="starting-etw-tracing"></a>ETW izleme başlatılıyor

Bir ETW izlemesi toplamak için [PerfView](https://github.com/Microsoft/perfview/) kullanabilirsiniz. PerfView, ETW izlemenin toplanması ve analiz edilmesi için kullanımı kolay bir arabirim sağlar. Bir izlemeyi toplamak için aşağıdaki komutu kullanın:

```DOS
Perfview.exe collect C:\trace.etl /BufferSizeMB=1024 -CircularMB:2048 -Merge:true -Providers:*Microsoft-VisualStudio:@StacksEnabled=true -NoV2Rundown /kernelEvents=default+FileIOInit+ContextSwitch+Dispatcher
```

bu, sağlayıcının Visual Studio kullanıcı arabirimi gecikmesi bildirimleri ile ilgili olaylar için kullandığı "Microsoft-VisualStudio" sağlayıcısı 'nı sağlar. Ayrıca, PerfView 'un **Iş parçacığı zaman yığınları** görünümünü oluşturmak için kullanabileceği çekirdek sağlayıcının anahtar sözcüğünü belirtir.

## <a name="trigger-the-notification-to-appear-again"></a>Bildirimi tekrar görüntülenecek şekilde Tetikle

PerfView izleme toplamayı başlatduktan sonra, bildirimin tekrar görünmesi için tetikleyici eylem sırasını (1. adımdan) kullanabilirsiniz. Bildirim gösterildiğinde, PerfView için izleme koleksiyonunu, çıkış izleme dosyasını işlemek ve oluşturmak üzere durdurabilirsiniz.

## <a name="stop-etw-tracing"></a>ETW İzlemeyi Durdur

İzleme toplamasını durdurmak için PerfView penceresindeki **koleksiyonu durdur** düğmesini kullanmanız yeterlidir. İzleme toplamasını durdurduktan sonra PerfView, ETW olaylarını otomatik olarak işleyecek ve bir çıkış izleme dosyası oluşturacaktır.

## <a name="examine-the-activity-log-to-get-the-delay-id"></a>Gecikme KIMLIĞINI almak için etkinlik günlüğünü inceleyin

Daha önce bahsedildiği gibi, etkinlik günlüğünü *%AppData%\microsoft\visualstudio \<vs_instance_id>\ActivityLog.xml* adresinde bulabilirsiniz. Visual Studio uzantı kullanıcı arabirimi gecikmesini her algıladığında, kaynak olarak etkinlik günlüğüne bir düğüm yazar `UIDelayNotifications` . Bu düğüm, UI gecikmesi hakkında dört bilgi içerir:

- Bir VS oturumunda UI gecikmesini benzersiz bir şekilde tanımlayan ardışık bir sayı olan UI gecikme KIMLIĞI
- Visual Studio oturumunuzu baştan kapatmaya benzersiz şekilde tanımlayan oturum kimliği
- UI gecikmesi için bir bildirimin gösterilip gösterilmediğini belirtir
- Büyük olasılıkla UI gecikmesine neden olan uzantı

```xml
<entry>
  <record>271</record>
  <time>2018/02/03 12:02:52.867</time>
  <type>Information</type>
  <source>UIDelayNotifications</source>
  <description>A UI delay (Delay ID = 0) has been detected. (Session ID=16e49d4b-26c2-4247-ad1c-488edeb185e0; Blamed extension="UIDelayR2"; Notification shown? Yes.)</description>
</entry>
```

> [!NOTE]
> Tüm UI gecikmeleri bir bildirime neden olur. Bu nedenle, doğru Kullanıcı arabirimi gecikmesini doğru şekilde belirlemek için, **belirtilen bildirimi** her zaman bir değere denetlemeniz gerekir.

Etkinlik günlüğünde doğru UI gecikmesini bulduktan sonra düğümde belirtilen UI gecikmesi KIMLIĞINI yazın. KIMLIĞI, bir sonraki adımda karşılık gelen ETW olayını aramak için kullanacaksınız.

## <a name="analyze-the-etw-trace"></a>ETW izlemesini çözümle

Sonra, izleme dosyasını açın. Bunu, aynı PerfView örneğini kullanarak ya da yeni bir örnek başlatıp pencerenin sol tarafındaki geçerli klasör yolunu izleme dosyasının konumuna ayarlayarak yapabilirsiniz.

![PerfView 'da klasör yolunu ayarlama](media/perfview-set-path.png)

Ardından, sol bölmedeki izleme dosyasını seçin ve sağ tıklama ya da bağlam menüsünden **Aç** ' ı seçerek dosyayı açın.

> [!NOTE]
> Varsayılan olarak PerfView bir ZIP arşivi verir. *trace.zip* açtığınızda, Arşivi otomatik olarak açar ve izlemeyi açar. Bu, izleme koleksiyonu sırasında **ZIP** kutusunun işaretini kaldırarak atlayabilirsiniz. Ancak, farklı makinelerde izlemeleri aktarmayı ve kullanmayı planlıyorsanız, **ZIP** kutusunun denetlenmesini kesinlikle öneririz. Bu seçenek olmadan, Ngen derlemeleri için gerekli pdb 'leri, izlemeye eşlik etmez ve bu nedenle, Ngen derlemelerinin sembolleri hedef makinede çözümlenmeyecektir. (Ngen derlemeleri için pdb 'leri hakkında daha fazla bilgi için [Bu blog gönderisine](https://devblogs.microsoft.com/devops/creating-ngen-pdbs-for-profiling-reports/) bakın.)

PerfView 'in izlemeyi işlemesi ve açması birkaç dakika sürebilir. İzleme açıkken, altında çeşitli "görünümler" listesi görüntülenir.

![PerfView İzleme Özeti Görünümü](media/perfview-summary-view-events-selected.png)

Kullanıcı arabirimi gecikmesi zaman aralığını almak için önce **Olaylar** görünümünü kullanacağız:

1.  `Events` İzleme altındaki düğüm ' i seçerek ve sağ tıklama veya bağlam menüsünden **Aç** ' ı seçerek Olaylar görünümünü açın.
2. `Microsoft-VisualStudio/ExtensionUIUnresponsiveness`Sol bölmede "" seçeneğini belirleyin.
3. ENTER tuşuna basın

Seçim uygulanır ve tüm `ExtensionUIUnresponsiveness` Olaylar sağ bölmede görüntülenir.

![Olaylar görünümünde olayları seçme](media/perfview-event-selection.png)

Sağ bölmedeki her satır bir UI gecikmesine karşılık gelir. Bu olay, 6. adımdaki etkinlik günlüğündeki gecikme KIMLIĞIYLE eşleşmesi gereken bir "gecikme KIMLIĞI" değeri içerir. `ExtensionUIUnresponsiveness`UI gecikmesi sonunda tetiklendiğinden, olayın zaman damgası (kabaca) UI gecikmesi bitiş saatini işaretler. Olay gecikme süresini de içerir. UI gecikmesi başladığında zaman damgasını elde etmek için bitiş zaman damgasından süreyi çıkartabiliriz.

![UI gecikmesi zaman aralığını hesaplama](media/ui-delay-time-range.png)

Önceki ekran görüntüsünde, örneğin olay zaman damgası 12.125,679, gecikme süresi 6.143,085 (MS) olur. Bu nedenle,
* Gecikme başlangıcı 12.125,679-6.143,085 = 5.982,594.
* UI gecikmesi zaman aralığı 5.982,594, 12.125,679 ' dir.

Zaman aralığına sahip olduktan sonra, **olay** görünümünü kapatabilir ve **iş parçacığı zamanı (StartStop etkinlikleri ile) yığınları** görünümüyle açabilirsiniz. Bu görünüm özellikle yararlıdır çünkü genellikle UI iş parçacığını engelleyen uzantılar yalnızca diğer iş parçacıkları veya g/ç 'ye bağlı bir işlem üzerinde bekliyor. Bu nedenle, çoğu durum için Git seçeneği olan **CPU yığını** görünümü, bu süre boyunca CPU kullanmadığından, iş parçacığının bloke edilme süresini yakalamayabilir. **Iş parçacığı zaman yığınları** , engellenme süresini düzgün şekilde göstererek bu sorunu çözer.

![PerfView Özet görünümündeki iş parçacığı süresi (StartStop etkinlikleri ile) yığınları düğümü](media/perfview-thread-time-with-startstop-activities-stacks.png)

**Iş parçacığı zaman yığınları** görünümünü açarken Analize Başlamak için **devenv** işlemini seçin.

![UI gecikme analizi için iş parçacığı zaman yığınları görünümü](media/ui-delay-thread-time-stacks.png)

**Iş parçacığı zaman yığınları** görünümünde, sayfanın sol üst kısmında, zaman aralığını önceki adımda hesapladığımız değerlerle ayarlayabilirsiniz ve yığınların o zaman aralığına ayarlanabilmesi için **ENTER** tuşuna basın.

> [!NOTE]
> Visual Studio zaten açık olduktan sonra izleme koleksiyonu başlatılırsa, kullanıcı arabirimi (başlangıç) iş parçacığının hangi iş parçacığı tarafından belirlenebileceği belirlenir. Ancak, Kullanıcı arabirimi (başlangıç) iş parçacığının yığındaki ilk öğe, en olası işletim sistemi dll 'lardır (*ntdll.dll* ve *kernel32.dll*) `devenv!?` ve ardından ve sonra `msenv!?` . Bu sıra, UI iş parçacığını belirlemenize yardımcı olabilir.

 ![Başlangıç iş parçacığını tanımlama](media/ui-delay-startup-thread.png)

Ayrıca, bu görünümü yalnızca paketinizdeki modüller içeren yığınlar dahil ederek de filtreleyebilirsiniz.

* Varsayılan olarak eklenen tüm Gruplandırmayı kaldırmak için **Grouppats** 'leri boş metin olarak ayarlayın.
* **Inpats** 'yi, var olan işlem filtresine ek olarak, derleme adınızın bir kısmını içerecek şekilde ayarlayın. Bu durumda, **devenv olmalıdır; UIDelayR2**.

![İş Parçacığı Zaman Yığınları görünümünde GroupPath ve IncPath'i ayarlama](media/perfview-tts-group-path-inc-path.png)

PerfView, Yardım **menüsünün** altında koddaki performans sorunlarını belirlemek için kullanabileceğiniz ayrıntılı kılavuza sahip. Ayrıca, aşağıdaki bağlantılar kodunuzu iyileştirmek için iş parçacığı api'Visual Studio kullanma hakkında daha fazla bilgi sağlar:

* [https://github.com/Microsoft/vs-threading/blob/master/doc/index.md](https://github.com/Microsoft/vs-threading/blob/master/doc/index.md)
* [https://github.com/Microsoft/vs-threading/blob/master/doc/cookbook_vs.md](https://github.com/Microsoft/vs-threading/blob/master/doc/cookbook_vs.md)

Ayrıca, etkili uzantılar yazmaya Visual Studio en iyi yöntemlerle ilgili rehberlik sağlayan uzantılar (burada NuGet [paketi)](https://www.nuget.org/packages/microsoft.visualstudio.sdk.analyzers)için yeni statik çözümleyicileri de kullanabilirsiniz. VS SDK [çözümleyicilerinin ve iş parçacığı](https://github.com/Microsoft/VSSDK-Analyzers/blob/master/doc/index.md) [çözümleyicilerinin listesine bakın.](https://github.com/Microsoft/vs-threading/blob/master/doc/analyzers/index.md)

> [!NOTE]
> Üzerinde denetime sahip olmadığınız bağımlılıklar nedeniyle yanıt vermemeye devam ediyorsanız (örneğin, uzantınız kullanıcı arabirimi iş parçacığında zaman uyumlu VS hizmetlerini çağırıyorsa) bunu bilmek istiyoruz. İş Ortağı programımızın bir Visual Studio, geliştirici destek isteği göndererek bizimle iletişim kurabilirsiniz. Aksi takdirde, geri bildiriminizi göndermek ve başlığına eklemek için 'Sorun Bildir' `"Extension UI Delay Notifications"` aracını kullanın. Ayrıca analizinizin ayrıntılı açıklamasını da dahil edin.
