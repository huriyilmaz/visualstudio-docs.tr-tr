---
title: Çok Işlemcili oturum defterleri yazma | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, multi-proc aware loggers
- multi-proc loggers
- loggers, multi-proc
ms.assetid: ff987d1b-1798-4803-9ef6-cc8fcc263516
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 886e012b026ef17b512a7e134d080382744783ef
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77630753"
---
# <a name="write-multi-processor-aware-loggers"></a>Multi-Processor-Aware Günlükçüler yazma

MSBuild 'in birden çok işlemciyi destekleme yeteneği, proje derleme süresini azaltabilir, ancak olay günlüğü oluşturmak için karmaşıklık de ekler. Tek işlemcili bir ortamda, olaylar, iletiler, uyarılar ve hatalar günlükçü 'e öngörülebilir ve sıralı bir biçimde ulaşır. Ancak, çok işlemcili bir ortamda, farklı kaynaklardan gelen olaylar aynı anda veya sıra dışında gelebilir. Bunu sağlamak için, MSBuild çok işlemcili bir günlükçü ve yeni bir günlük modeli sağlar ve özel "iletme Günlükçüleri" oluşturmanıza imkan tanır.

## <a name="multi-processor-logging-challenges"></a>Çok işlemcili günlüğe kaydetme sorunları

 Çok işlemcili veya çok çekirdekli bir sistemde bir veya daha fazla proje oluşturduğunuzda, tüm projeler için MSBuild derleme olayları aynı anda oluşturulur. Olay iletilerinin bir Avalanche, günlükçü üzerinde aynı anda veya sıra dışında gelebilir. MSBuild 2,0 günlükçüsü bu durumu işleyecek şekilde tasarlanmadığı için, günlükçü 'yi açabilir ve derleme sürelerinin artmasına, yanlış günlükçü çıktısına veya hatta bozuk bir yapıya neden olabilir. Bu sorunları gidermek için, günlükçü (MSBuild 3,5 ' den başlayarak), dizi dışı olayları işleyebilir ve olayları ve bunların kaynaklarını ilişkilendirebilir.

 Özel bir iletme günlükçüsü oluşturarak günlüğe kaydetme verimliliğini daha da artırabilirsiniz. Özel bir iletme günlükçüsü, oluşturmadan önce, yalnızca izlemek istediğiniz olayları seçmenizi sağlayarak bir filtre işlevi görür. Özel bir iletme günlükçüsü kullandığınızda, istenmeyen olaylar günlükçü sayısını düşürebilir, günlüklerinizi kalabalıklığını veya yavaş derleme süreleriyle başa çıkıp.

## <a name="multi-processor-logging-models"></a>Çok işlemcili günlük modelleri

 MSBuild, çok işlemcili ilgili derleme sorunları için sağlamak üzere iki günlük modelini destekler, merkezi ve dağıtılır.

### <a name="central-logging-model"></a>Merkezi günlük modeli

 Merkezi günlük modelinde, *MSBuild. exe* ' nin tek bir örneği "Merkezi düğüm" olarak görev yapar ve merkezi düğümün ("ikincil düğümler") alt örnekleri, derleme görevlerini gerçekleştirmeye yardımcı olmak üzere merkezi düğüme iliştirilebilir.

 ![Merkezi günlükçü modeli](../msbuild/media/centralnode.png "Merkezileştirme düğümü")

 Merkezi düğüme eklenen çeşitli türlerin Günlükçüleri "Merkezi Günlükçüler" olarak bilinir. Her Günlükçü türünün yalnızca bir örneği merkezi düğüme aynı anda iliştirilebilir.

 Bir derleme gerçekleştiğinde, ikincil düğümler derleme olaylarını merkezi düğüme yönlendirir. Merkezi düğüm tüm olaylarını ve ayrıca ikincil düğümleri bir veya daha fazla bağlı merkezi Günlükçüler için yönlendirir. Günlükçüler daha sonra gelen verileri temel alan günlük dosyaları oluşturur.

 Merkezi günlükçü tarafından yalnızca <xref:Microsoft.Build.Framework.ILogger> uygulanması gerekli olsa da, merkezi günlükçü, yapıya katılan düğüm sayısıyla birlikte başlatılır, böylece <xref:Microsoft.Build.Framework.INodeLogger> uygulamanızı öneririz. <xref:Microsoft.Build.Framework.ILogger.Initialize%2A> yönteminin aşağıdaki aşırı yüklemesi, motor günlükçü 'yi başlattığında çağırır.

```csharp
public interface INodeLogger: ILogger
{
    public void Initialize(IEventSource eventSource, int nodeCount);
}
```

 Önceden varolan <xref:Microsoft.Build.Framework.ILogger>tabanlı Günlükçüler, merkezi Günlükçüler olarak davranabilir ve yapıya eklenebilir. Ancak, çok işlemcili günlük senaryolar ve sıra dışı olaylar için açık destek olmadan yazılan merkezi Günlükçüler bir derlemeyi bozabilir veya anlamsız bir çıkış üretebilir.

### <a name="distributed-logging-model"></a>Dağıtılmış günlük modeli

 Merkezi günlük modelinde, çok fazla gelen ileti trafiği merkezi düğümü, örneğin birçok projenin aynı anda ne zaman derlenebileceğini de açabilir. Bu, sistem kaynaklarını stres ve derleme performansını düşürebilir. Bu sorunu kolaylaştırmak için MSBuild, dağıtılmış bir günlük modelini destekler.

 ![Dağıtılmış günlük modeli](../msbuild/media/distnode.png "DistNode")

 Dağıtılmış günlük kaydı modeli, bir iletme günlükçüsü oluşturmanıza izin vererek Merkezi günlük modelini genişletir.

#### <a name="forwarding-loggers"></a>Günlükçüleri iletme

 Bir iletme günlükçüsü, ikincil bir düğüme bağlanan ve gelen derleme olaylarını bu düğümden alan bir olay filtresi olan ikincil, hafif bir günlükçüdür. Gelen olayları filtreler ve yalnızca belirttiğiniz olanları merkezi düğüme iletir. Bu, merkezi düğüme gönderilen ileti trafiğini azaltır ve genel derleme performansını geliştirir.

 Dağıtılmış günlük kullanmanın iki yolu şunlardır:

- <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger>adlı önceden fabriciletme günlükçüsü ' ni özelleştirin.

- Kendi özel iletme günlüklerinizi yazın.

Configurableforwardinggünlükçü ' i gereksinimlerinize uyacak şekilde değiştirebilirsiniz. Bunu yapmak için, *MSBuild. exe*' yi kullanarak komut satırındaki günlükçü 'yi çağırın ve günlükçü 'nin merkezi düğüme iletmesini istediğiniz derleme olaylarını listeleyin.

Alternatif olarak, özel bir iletme günlükçüsü oluşturabilirsiniz. Özel bir iletme günlükçüsü oluşturarak, günlükçü davranışını hassas şekilde ayarlayabilirsiniz. Ancak, özel bir iletme günlükçü oluşturmak yalnızca Configurableforwardinggünlükçü özelleştirilerek daha karmaşıktır. Daha fazla bilgi için bkz. [iletme Günlükçüleri oluşturma](../msbuild/creating-forwarding-loggers.md).

## <a name="using-the-configurableforwardinglogger-for-simple-distributed-logging"></a>Basit Dağıtılmış günlük için Configurableforwardinggünlükçü kullanma

 Bir Configurableforwardinggünlükçü veya özel bir iletme günlükçüsü eklemek için, *MSBuild. exe* komut satırı derlemesinde `-distributedlogger` anahtarını (short için`-dl`) kullanın. Günlükçü türlerinin ve sınıflarının adlarını belirtme biçimi `-logger` anahtarıyla aynıdır, ancak dağıtılmış bir günlükçü her zaman bir yerine iki günlük sınıfı, iletme günlükçüsü ve merkezi günlükçüsü olur. Aşağıda, Xmlforwardinggünlükçü adlı özel bir iletme günlükçüsü eklemenin bir örneği verilmiştir.

```cmd
msbuild.exe myproj.proj -distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,Culture=neutral
```

> [!NOTE]
> Bir yıldız işareti (*) `-dl` anahtarındaki iki günlükçü adını ayırmalıdır.

 Configurableforwardinggünlükçü kullanılması, tipik MSBuild günlükçüsü yerine Configurableforwardinggünlükçü günlükçüsü 'yi iliştirmeniz ve ardından parametre olarak, Configurableforwardinggünlükçü 'nin merkezi düğüme geçmesini istediğiniz olayları belirtmeniz dışında, başka bir günlükçü ( [derleme günlükleri alma](../msbuild/obtaining-build-logs-with-msbuild.md)bölümünde açıklandığı gibi) kullanma gibidir.

 Örneğin, yalnızca bir derleme başladığında ve sona erdiğinde bildirim almak istiyorsanız ve bir hata oluştuğunda, `BUILDSTARTEDEVENT`, `BUILDFINISHEDEVENT`ve `ERROREVENT` parametre olarak geçirin. Çoklu parametreler, noktalı virgülle ayırarak geçirilebilir. Aşağıda, yalnızca `BUILDSTARTEDEVENT`, `BUILDFINISHEDEVENT`ve `ERROREVENT` olaylarını iletmek için Configurableforwardinggünlükçü kullanma örneği verilmiştir.

```cmd
msbuild.exe myproj.proj -distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,Culture=neutral*ConfigureableForwardingLogger,C:\My.dll;BUILDSTARTEDEVENT; BUILDFINISHEDEVENT;ERROREVENT
```

 Aşağıda, kullanılabilir Configurableforwardinggünlükçü parametrelerinin bir listesi verilmiştir.

|Configurableforwardinggünlükçü parametreleri|
| - |
|BUILDSTARTEDEVENT|
|BUILDSONLANDıRHEDEVENT|
|PROJECTSTARTEDEVENT|
|PROJECTSONLANDıRHEDEVENT|
|TARGETSTARTEDEVENT|
|TARGETSONLANDıRHEDEVENT|
|TASKSTARTEDEVENT|
|TASKSONLANDıRHEDEVENT|
|ERROREVENT|
|WARNINGEVENT|
|HIGHMESSAGEEVENT|
|NORMALMESSAGEEVENT|
|LOWMESSAGEEVENT|
|CUSTOMEVENT|
|KOMUT SATıRı|
|PERFORMANSLı gün|
|NOSUMMARY|
|SHOWCOMMANDLINE|

## <a name="see-also"></a>Ayrıca bkz.

- [İletme Günlükçüleri oluşturma](../msbuild/creating-forwarding-loggers.md)