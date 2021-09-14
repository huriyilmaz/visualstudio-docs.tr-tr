---
title: Kullanıcı arabiriminde uzantı kullanıcı arabirimi gecikmelerini Visual Studio| Microsoft Docs
description: Visual Studio kullanıcı arabirimi gecikmeleri bir uzantıdan kaynaklanmış olabilirse size bilgi sağlar. Uzantı kodunda kullanıcı arabirimi gecikme sürelerini neyin neden olduğunu tanılamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: conceptual
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload: multiple
ms.openlocfilehash: 8ddb58405125b53c955324be55ccb5eec93000e4
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626259"
---
# <a name="how-to-diagnose-ui-delays-caused-by-extensions"></a>Nasıl yapılır: Uzantılardan kaynaklanan kullanıcı arabirimi gecikmelerini tanılama

Kullanıcı arabirimi yanıt vermemeye Visual Studio, yaprakla başlayarak ve temele doğru çalışarak kullanıcı arabirimi iş parçacığının çağrı yığınını inceler. Çağrı Visual Studio çerçevesinin yüklü ve etkinleştirilmiş bir uzantının parçası olan bir modüle ait olduğunu belirlerse bir bildirim gösterir.

![Kullanıcı arabirimi gecikmesi (yanıt vermiyor) Bildirimi](media/ui-delay-notification-in-vs.png)

Bildirim kullanıcıya kullanıcı arabirimi gecikmesi (yani kullanıcı arabiriminde yanıt vermiyor) uzantısından gelen kodun sonucu olabileceğini bildirebilir. Ayrıca kullanıcıya uzantıyı devre dışı bırakma seçenekleri veya bu uzantı için gelecekteki bildirimler de sağlar.

Bu belgede, uzantı kodunda kullanıcı arabirimi gecikme bildirimlerine neden olan öğeleri nasıl tanıyabilirsiniz?

> [!NOTE]
> Kullanıcı arabirimi gecikmelerini tanılamak Visual Studio için deneysel bir örneği kullanmayın. Deneysel örnek kullanırken kullanıcı arabirimi gecikme bildirimleri için gereken çağrı yığını analizinin bazı bölümleri kapalıdır, yani kullanıcı arabirimi gecikme bildirimleri gösterilmez.

Tanılama sürecine genel bir bakış şu şekildedir:
1. Tetikleyici senaryosunu tanımlama.
2. Etkinlik günlüğüyle VS'i yeniden başlatın.
3. ETW izlemeyi başlatma.
4. Bildirimin yeniden görünmesini tetikler.
5. ETW izlemeyi durdurun.
6. Gecikme kimliğini almak için etkinlik günlüğünü inceleme.
7. 6. adımdaki gecikme kimliğini kullanarak ETW izlemesi analiz edin.

Aşağıdaki bölümlerde bu adımları daha ayrıntılı bir şekilde inceleacağız.

## <a name="identify-the-trigger-scenario"></a>Tetikleyici senaryosunu tanımlama

Kullanıcı arabirimi gecikmesini tanılamak için ilk olarak bildirimi göstermenin neden olduğu Visual Studio (eylem dizisi) belirlemelisiniz. Bu, daha sonra günlüğe kaydetme açıkken bildirimi tetikleyleyebilirsiniz.

## <a name="restart-vs-with-activity-logging-on"></a>Etkinlik günlüğüyle VS'i yeniden başlatma

Visual Studio hata ayıklarken yararlı bilgiler sağlayan bir "etkinlik günlüğü" oluşturmasını sağlar. Oturum açmada etkinlik günlüğünü Visual Studio için Visual Studio satırı `/log` seçeneğiyle oturum açın. Etkinlik Visual Studio başladıktan sonra etkinlik günlüğü aşağıdaki konumda depolanır:

```DOS
%APPDATA%\Microsoft\VisualStudio\<vs_instance_id>\ActivityLog.xml
```

VS örnek kimliğinizi nasıl bulamanız hakkında daha fazla bilgi edinmek için bkz. Visual Studio [örnekleri algılama ve yönetme araçları.](../install/tools-for-managing-visual-studio-instances.md) Bu etkinlik günlüğünü daha sonra kullanıcı arabirimi gecikmeleri ve ilgili bildirimler hakkında daha fazla bilgi bulmak için kullanacağız.

## <a name="starting-etw-tracing"></a>ETW izlemeyi başlatma

[EtW izlemesi toplamak için PerfView](https://github.com/Microsoft/perfview/) kullanabilirsiniz. PerfView, bir ETW izlemesi toplamak ve analiz etmek için kullanımı kolay bir arabirim sağlar. İzleme toplamak için aşağıdaki komutu kullanın:

```DOS
Perfview.exe collect C:\trace.etl /BufferSizeMB=1024 -CircularMB:2048 -Merge:true -Providers:*Microsoft-VisualStudio:@StacksEnabled=true -NoV2Rundown /kernelEvents=default+FileIOInit+ContextSwitch+Dispatcher
```

Bu, kullanıcı arabirimi gecikme bildirimleriyle ilgili olaylar için Visual Studio sağlayıcı olan "Microsoft-VisualStudio" sağlayıcısını sağlar. Ayrıca PerfView'ın İş Parçacığı Zaman Yığınları görünümünü oluşturmak için kullanabileceği çekirdek sağlayıcısı **için anahtar sözcüğünü** belirtir.

## <a name="trigger-the-notification-to-appear-again"></a>Bildirimin yeniden görünmesini tetikle

PerfView izleme toplamayı başlattıktan sonra bildirimin yeniden görünmesi için tetikleyici eylem dizisini (1. adımdan) kullanabilirsiniz. Bildirim gösterildiktan sonra PerfView'ın çıkış izleme dosyasını işlemesi ve oluşturması için izleme koleksiyonunu durdurabilirsiniz.

## <a name="stop-etw-tracing"></a>ETW izlemeyi durdurma

İzleme koleksiyonunu durdurmak için PerfView **penceresindeki** Koleksiyonu durdur düğmesini kullanın. İzleme koleksiyonunu durduran PerfView, ETW olaylarını otomatik olarak işler ve bir çıkış izleme dosyası oluşturur.

## <a name="examine-the-activity-log-to-get-the-delay-id"></a>Gecikme kimliğini almak için etkinlik günlüğünü inceleme

Daha önce belirtildiği gibi etkinlik günlüğünü *%APPDATA%\Microsoft\VisualStudio konumunda \<vs_instance_id> bulabilirsiniz\ActivityLog.xml.* Uzantı Visual Studio kullanıcı arabirimi gecikmesi algılayan her durumda, kaynak olarak ile etkinlik günlüğüne `UIDelayNotifications` bir düğüm yazar. Bu düğüm, kullanıcı arabirimi gecikmesi hakkında dört bilgi içerir:

- KULLANıCı arabirimi gecikme kimliği, VS oturumunda kullanıcı arabirimi gecikmesi benzersiz olarak tanımlayan sıralı bir sayı
- Oturum kimliğini, oturumdan Visual Studio benzersiz olarak tanımlar
- Kullanıcı arabirimi gecikmesi için bir bildirim göster olup olmadığı
- Büyük olasılıkla kullanıcı arabirimi gecikmesi neden olan uzantı

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
> Tüm kullanıcı arabirimi gecikmeleri bir bildirimle sonuçlanmaz. Bu nedenle, doğru kullanıcı arabirimi gecikmelerini doğru şekilde tanımlamak için her zaman Notification **shown?** değerini denetlemeniz gerekir.

Etkinlik günlüğünde doğru kullanıcı arabirimi gecikmesi buduktan sonra düğümde belirtilen kullanıcı arabirimi gecikme kimliğini not edin. Bir sonraki adımda ilgili ETW olayına bakmak için kimliği kullanılır.

## <a name="analyze-the-etw-trace"></a>ETW izlemesi analiz etme

Ardından izleme dosyasını açın. Bunu aynı PerfView örneğini kullanarak veya yeni bir örnek başlatarak ve pencerenin sol üst kısmında yer alan geçerli klasör yolunu izleme dosyasının konumu olarak ayarlayarak bunu yapabiliriz.

![Perfview'da klasör yolunu ayarlama](media/perfview-set-path.png)

Ardından sol bölmede izleme dosyasını seçin ve sağ tıklama veya bağlam **menüsünden** Aç'ı seçerek dosyayı açın.

> [!NOTE]
> Varsayılan olarak PerfView bir Zip arşivi oluşturur. dosya *trace.zip,* arşivi otomatik olarak açar ve izlemeyi açar. İzleme koleksiyonu sırasında Zip kutusunun işaretini **kaldırarak bunu** atlayabilirsiniz. Ancak, izlemeleri farklı makineler arasında aktarmayı ve kullanmayı planlıyorsanız, Zip kutusunun işaretinin kaldırılmış olarak **işaretlenmelerini kesinlikle** öneririz. Bu seçenek olmadan, Ngen derlemeleri için gerekli PDB'ler izlemeye eşlik eder ve bu nedenle Ngen derlemelerinden gelen semboller hedef makinede çözümlenmezse. (Ngen [derlemeleri için](https://devblogs.microsoft.com/devops/creating-ngen-pdbs-for-profiling-reports/) PDB'ler hakkında daha fazla bilgi için bu blog gönderisi'ne bakın.)

PerfView'ın izlemeyi işlemesi ve açması birkaç dakika sürebilir. İzleme açıldıktan sonra altında çeşitli "görünümler" listesi görünür.

![PerfView izleme özeti görünümü](media/perfview-summary-view-events-selected.png)

Kullanıcı arabirimi **gecikmesi zaman** aralığını elde etmek için öncelikle Olaylar görünümünü kullanmalıdır:

1. İzlemenin **altında** düğüm seçerek ve sağ tıklama veya bağlam menüsünden `Events` Aç'ı seçerek Olaylar görünümünü açın. 
2. Sol `Microsoft-VisualStudio/ExtensionUIUnresponsiveness` bölmede " " öğesini seçin.
3. Enter tuşuna basın

Seçim uygulanır ve `ExtensionUIUnresponsiveness` tüm olaylar sağ bölmede görüntülenir.

![Olaylar görünümünde olayları seçme](media/perfview-event-selection.png)

Sağ bölmede yer alan her satır bir kullanıcı arabirimi gecikme süresine karşılık geliyor. Olay, 6. adımdaki etkinlik günlüğünde gecikme kimliğiyle eşleşmesi gereken bir "Gecikme Kimliği" değeri içerir. Kullanıcı arabirimi gecikmesi sonundan itibaren, olayın zaman damgası (kabaca) kullanıcı arabirimi `ExtensionUIUnresponsiveness` gecikmesi bitiş saatlerini işaretler. Olay ayrıca gecikme süresini de içerir. Kullanıcı arabirimi gecikmesi başladığı zaman damgasını elde etmek için bitiş zaman damgasından süreyi çıkarılır.

![Kullanıcı arabirimi gecikmesi zaman aralığını hesaplama](media/ui-delay-time-range.png)

Örneğin önceki ekran görüntüsünde olayın zaman damgası 12.125.679, gecikme süresi ise 6.143.085 'tir (ms). Bu nedenle,
* Gecikme başlangıcı 12.125.679 - 6.143.085 = 5.982.594'tir.
* KULLANıCı arabirimi gecikme süresi aralığı 5.982.594 ile 12.125.679'dır.

Zaman aralığına sahip olduktan sonra Olaylar  görünümünü kapatıp İş Parçacığı Süresi **(StartStop Etkinlikleri ile) Yığınlar görünümünü açabiliriz.** Kullanıcı arabirimi iş parçacığını engelleyen uzantılar genellikle yalnızca diğer iş parçacıklarını veya bir I/O'ya bağlı işlemi beklediği için bu görünüm özellikle kullanışlıdır. Bu nedenle, çoğu durumda git seçeneği olan CPU Yığını görünümü, bu süre boyunca **CPU'yu** kullanmayarak iş parçacığının engellemeye harcadığı zamanı yakalamaz. İş **Parçacığı Zaman Yığınları** engellenen zamanı düzgün göstererek bu sorunu çözer.

![PerfView özet görünümünde İş Parçacığı Süresi (StartStop Etkinlikleri ile) Yığınlar düğümü](media/perfview-thread-time-with-startstop-activities-stacks.png)

İş Parçacığı **Zaman Yığınları görünümünü** a açma sırasında analizi başlatmak için **devenv** işlemini seçin.

![UI gecikme analizi için İş Parçacığı Zaman Yığınları görünümü](media/ui-delay-thread-time-stacks.png)

İş **Parçacığı Zaman** Yığınları görünümünde, sayfanın sol üst kısmında, zaman aralığını önceki adımda hesaplanmış değerlere ayarlayabilir ve **yığınların** bu zaman aralığına göre ayarlanması için Enter tuşuna basabilirsiniz.

> [!NOTE]
> Kullanıcı arabirimi (başlangıç) iş parçacığının hangi iş parçacığı olduğunu belirlemek, izleme koleksiyonu zaten açık olduktan sonra Visual Studio uygun olabilir. Ancak, kullanıcı arabirimi (başlangıç) iş parçacığı yığınında ilk öğeler büyük olasılıkla her zaman işletim sistemi DLL'leridir (*ntdll.dll* ve *kernel32.dll*) ve `devenv!?` ardından `msenv!?` . Bu dizi, kullanıcı arabirimi iş parçacığını tanımlamaya yardımcı olabilir.

 ![Başlangıç iş parçacığını tanımlama](media/ui-delay-startup-thread.png)

Ayrıca, bu görünümü yalnızca paketinizin modüllerini içeren yığınları dahil edersiniz.

* Varsayılan olarak eklenen tüm gruplamaları kaldırmak için **GroupPats'ı** boş metin olarak ayarlayın.
* **IncPats'i** mevcut işlem filtresine ek olarak derleme adının bir kısmını içerecek şekilde ayarlayın. Bu durumda, **devenv olması gerekir; UIDelayR2**.

![İş Parçacığı Zaman Yığınları görünümünde GroupPath ve IncPath'i ayarlama](media/perfview-tts-group-path-inc-path.png)

PerfView, Yardım **menüsünün** altında koddaki performans sorunlarını belirlemek için kullanabileceğiniz ayrıntılı kılavuza sahip. Ayrıca, aşağıdaki bağlantılar kodunuzu iyileştirmek için iş parçacığı API'Visual Studio kullanma hakkında daha fazla bilgi sağlar:

* [https://github.com/Microsoft/vs-threading/blob/master/doc/index.md](https://github.com/Microsoft/vs-threading/blob/master/doc/index.md)
* [https://github.com/Microsoft/vs-threading/blob/master/doc/cookbook_vs.md](https://github.com/Microsoft/vs-threading/blob/master/doc/cookbook_vs.md)

Ayrıca, etkili uzantılar yazmaya Visual Studio en iyi yöntemlerle ilgili rehberlik [](https://www.nuget.org/packages/microsoft.visualstudio.sdk.analyzers)sağlayan uzantılar (burada NuGet paketi) için yeni statik çözümleyicileri de kullanabilirsiniz. VS SDK [çözümleyicilerinin ve iş parçacığı](https://github.com/Microsoft/VSSDK-Analyzers/blob/master/doc/index.md) [çözümleyicilerinin listesine bakın.](https://github.com/Microsoft/vs-threading/blob/master/doc/analyzers/index.md)

> [!NOTE]
> Üzerinde denetime sahip olmadığınız bağımlılıklar nedeniyle yanıt vermemeye devam ediyorsanız (örneğin, uzantınız kullanıcı arabirimi iş parçacığında zaman uyumlu VS hizmetlerini çağırıyorsa) bunu bilmek istiyoruz. İş Ortağı programımızın bir Visual Studio, geliştirici destek isteği göndererek bizimle iletişim kurabilirsiniz. Aksi takdirde, geri bildiriminizi göndermek ve baş unvanına eklemek için 'Sorun Bildirin' `"Extension UI Delay Notifications"` aracını kullanın. Ayrıca analizinizin ayrıntılı açıklamasını da dahil edin.
