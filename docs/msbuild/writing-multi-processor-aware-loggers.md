---
title: Çok İşlemcili Günlükleyiciler Yazma | Microsoft Docs
description: Çoklu işlemci MSBuild günlük kaydı ve günlüğe kaydetme modeli sağladığını ve özel "iletme günlükleyicileri" oluşturmanızı nasıl sağladığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, multi-proc aware loggers
- multi-proc loggers
- loggers, multi-proc
ms.assetid: ff987d1b-1798-4803-9ef6-cc8fcc263516
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 4b972eb1af16a922a9fe66081ada4467d39e27c7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122136618"
---
# <a name="write-multi-processor-aware-loggers"></a>Çok işlemcili günlükleyiciler yazma

Birden çok MSBuild işlemciden faydalanma becerisi, proje oluşturma sürelerini düşürenin yanı sıra olay günlüğü oluşturma karmaşıklığını da ekler. Tek işlemcili bir ortamda olaylar, iletiler, uyarılar ve hatalar günlükleyiciye tahmin edilebilir, sıralı bir şekilde gelir. Ancak, çok işlemcili bir ortamda, farklı kaynaklardan olaylar aynı anda veya sıra dışında varabilirsiniz. Bunu sağlamak için, MSBuild işlemcili bir günlük kaydı ve yeni bir günlük modeli sağlar ve özel "iletme günlükleyicileri" oluşturmanıza olanak sağlar.

## <a name="multi-processor-logging-challenges"></a>Çok işlemcili günlüğe kaydetme zorlukları

 Çok işlemcili veya çok çekirdekli bir sistemde bir veya daha fazla proje derlemeniz MSBuild projelerin derleme olayları aynı anda oluşturulur. Olay iletilerinin bir anda günlükleyiciye gelmesi veya sıranın dışında olması. Bir MSBuild 2.0 günlükleyicisi bu durumu işlemek üzere tasarlanmaysa da, günlükleyiciyi bunaltarak derleme sürelerini, yanlış günlükçer çıkışını ve hatta bozuk bir derlemeye neden olabilir. Bu sorunları ele etmek için günlükç (MSBuild 3.5'te başlayarak) sıra dışında olayları işleyenin ve olayları ve kaynaklarının arasında ilişki olabilir.

 Özel bir iletme günlükleyicisi oluşturarak günlük verimliliğini daha da geliştirin. Özel iletme günlükleyicisi, oluşturmadan önce yalnızca izlemek istediğiniz olayları seçmenize izin vererek bir filtre olarak davranır. Özel bir iletme günlükçleyicisi kullanırken, istenmeyen olaylar günlükçeri zora, günlüklerinizi karmaşık hale zorlar veya derleme sürelerini yavaşlatamaz.

## <a name="multi-processor-logging-models"></a>Çok işlemcili günlük modelleri

 Birden çok işlemciyle ilgili derleme sorunları sağlamak için MSBuild ve dağıtılmış olmak kaydı iki modeli destekler.

### <a name="central-logging-model"></a>Merkezi günlük modeli

 Merkezi günlük modelinde, tek bir *MSBuild.exe* örneği "merkezi düğüm" olarak hareket eder ve derleme görevlerini gerçekleştirmeye yardımcı olmak için merkezi düğümün alt örnekleri ("ikincil düğümler") merkezi düğüme iliştirılır.

 ![Merkezi Günlükçi Modeli](../msbuild/media/centralnode.png "CentralNode")

 Merkezi düğüme iliştirilen çeşitli türlerde günlükler", "merkezi günlükçiler" olarak bilinir. Aynı anda merkezi düğüme her günlükleyici türünün yalnızca bir örneği iliştirilmiş olabilir.

 Bir derleme oluştuğunda, ikincil düğümler derleme olaylarını merkezi düğüme yönlendirer. Merkezi düğüm tüm olaylarını ve aynı zamanda ikincil düğümlerin olaylarını bağlı merkezi günlüklerden bir veya daha fazlası için yönlendirer. Günlükler daha sonra gelen verileri temel alan günlük dosyaları oluşturun.

 Yalnızca merkezi günlükleyici tarafından uygulanması gerekse de, merkezi günlükleyicinin derlemeye katılan düğüm sayısıyla başlatılması için de uygulamanız <xref:Microsoft.Build.Framework.ILogger> <xref:Microsoft.Build.Framework.INodeLogger> önerilir. Yöntemin aşağıdaki aşırı <xref:Microsoft.Build.Framework.ILogger.Initialize%2A> yüklemesi, altyapı günlükçer'i başlatıyor olduğunda çağrılır.

```csharp
public interface INodeLogger: ILogger
{
    public void Initialize(IEventSource eventSource, int nodeCount);
}
```

 Önceden var olan <xref:Microsoft.Build.Framework.ILogger> tüm günlükçiler merkezi günlükçiler gibi davranarak derlemeye iliştir olabilir. Ancak, çok işlemcili günlük senaryoları ve sıra dışı olaylar için açıkça destek olmadan yazılan merkezi günlükleyiciler bir derlemeyi bozarak veya anlamsız çıkışlar üretebilir.

### <a name="distributed-logging-model"></a>Dağıtılmış günlük modeli

 Merkezi günlük modelinde çok fazla gelen ileti trafiği, örneğin aynı anda çok fazla proje derlemesi olduğunda merkezi düğümü zora zorlar. Bu, sistem kaynaklarını baskı altında bulundurarak derleme performansını düşürebilir. Bu sorunu kolaylaştırmak için MSBuild günlük modelini destekler.

 ![Dağıtılmış Günlük Modeli](../msbuild/media/distnode.png "DistNode")

 Dağıtılmış günlük modeli, bir iletme günlükleyicisi oluşturmanıza izin vererek merkezi günlük modelini genişlettir.

#### <a name="forwarding-loggers"></a>Günlükçileri iletme

 Bir iletme günlükleyicisi, ikincil bir düğüme iliştirilen ve bu düğümden gelen derleme olaylarını alan bir olay filtresine sahip olan ikincil, basit bir günlükleyicidir. Gelen olayları filtreler ve yalnızca belirttiğiniz olayları merkezi düğüme iletir. Bu, merkezi düğüme gönderilen ileti trafiğini azaltır ve genel derleme performansını artırır.

 Dağıtılmış günlüğü kullanmanın iki yolu vardır:

- adlı önceden ileriye doğru iletme günlükleyiciyi <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> özelleştirin.

- Kendi özel iletme günlükleyicinizi yazın.

ConfigurableForwardingLogger'ı gereksinimlerinize uyacak şekilde değiştirebilirsiniz. Bunu yapmak için, *MSBuild.exe* kullanarak komut satırına günlükleyiciyi çağırarak ve günlükleyicinin merkezi düğüme iletmesi istediğiniz derleme olaylarını listele.

Alternatif olarak, özel bir iletme günlükleyicisi oluşturabilirsiniz. Özel bir iletme günlükleyicisi oluşturarak günlükleyicinin davranışında ince ayar oluşturabilirsiniz. Ancak, özel bir iletme günlükleyicisi oluşturmak yalnızca ConfigurableForwardingLogger'ı özelleştirmekten daha karmaşıktır. Daha fazla bilgi için, [bkz. Creating forwarding loggers](../msbuild/creating-forwarding-loggers.md).

## <a name="using-the-configurableforwardinglogger-for-simple-distributed-logging"></a>Basit dağıtılmış günlük kaydı için ConfigurableForwardingLogger kullanma

 ConfigurableForwardingLogger veya özel bir iletme günlükleyicisi eklemek için bir komut satırı derlemesinde `-distributedlogger` anahtarını ( `-dl` *kısaca)MSBuild.exe* kullanın. Günlükleyici türlerinin ve sınıflarının adlarını belirtme biçimi anahtarıyla aynıdır, ancak dağıtılmış günlükte her zaman bir yerine iki günlük sınıfı vardır: iletme günlükleyicisi ve `-logger` merkezi günlükleyici. Aşağıda, XMLForwardingLogger adlı özel bir iletme günlükleyicisi eklemeye bir örnek ve ardından ve bir örnek ve ardından ve bir örnek ve bir kez daha ve daha fazla bilgi ve daha fazla bilgi için bkz.

```cmd
msbuild.exe myproj.proj -distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,Culture=neutral
```

> [!NOTE]
> Yıldız işareti (*) anahtarda iki günlük kullanıcı adı `-dl` ayırmalı.

 ConfigurableForwardingLogger'ın kullanımı, normal MSBuild günlükleyicisi [](../msbuild/obtaining-build-logs-with-msbuild.md)yerine ConfigurableForwardingLogger günlükleyicisi ekleme ve ConfigurableForwardingLogger'ın merkezi düğüme geçişünü istediğiniz olaylar için parametre olarak belirtmeniz dışında, diğer günlükleyicileri (derleme günlüklerini alma'da özetlenen şekilde) kullanmak gibi olur.

 Örneğin, yalnızca bir derleme başlatıldığında ve sona erdiğinde ve bir hata oluştuğunda, , ve parametrelerini `BUILDSTARTEDEVENT` `BUILDFINISHEDEVENT` `ERROREVENT` iletirsiniz. Bunları noktalı virgülle ayırarak birden çok parametre geçiri. Aşağıda yalnızca , ve olaylarını iletmek için ConfigurableForwardingLogger'ın nasıl kullanabileceğine `BUILDSTARTEDEVENT` bir örnek ve ardından ve ve `BUILDFINISHEDEVENT` `ERROREVENT` değiştirilebilir.

```cmd
msbuild.exe myproj.proj -distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,Culture=neutral*ConfigureableForwardingLogger,C:\My.dll;BUILDSTARTEDEVENT; BUILDFINISHEDEVENT;ERROREVENT
```

 Aşağıda, kullanılabilir ConfigurableForwardingLogger parametrelerinin bir listesi yer almaktadır.

|ConfigurableForwardingLogger Parametreleri|
| - |
|BUILDSTARTEDEVENT|
|BUILDFINISHEDEVENT|
|PROJECTSTARTEDEVENT|
|PROJECTFINISHEDEVENT|
|TARGETSTARTEDEVENT|
|TARGETFINISHEDEVENT|
|TASKSTARTEDEVENT|
|TASKFINISHEDEVENT|
|Errorevent|
|WARNINGEVENT|
|HIGHMESSAGEEVENT|
|NORMALMESSAGEEVENT|
|LOWMESSAGEEVENT|
|CUSTOMEVENT|
|Commandline|
|PERFORMANCESUMMARY|
|NOSUMMARY|
|SHOWCOMMANDLINE|

## <a name="see-also"></a>Ayrıca bkz.

- [İletme günlükçüleri oluşturma](../msbuild/creating-forwarding-loggers.md)