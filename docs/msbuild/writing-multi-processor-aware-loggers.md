---
title: Çok Işlemcili oturum defterleri yazma | Microsoft Docs
description: MSBuild 'in çok işlemcili bir günlükçü ve günlüğe kaydetme modeli sağladığını ve özel "iletme Günlükçüleri" oluşturmanıza imkan tanır.
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
ms.workload:
- multiple
ms.openlocfilehash: 1e7cf5998645230f038c6de12c79b53b44c09dfc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847992"
---
# <a name="write-multi-processor-aware-loggers"></a>Multi-Processor-Aware Günlükçüler yazma

MSBuild 'in birden çok işlemciyi destekleme yeteneği, proje derleme süresini azaltabilir, ancak olay günlüğü oluşturmak için karmaşıklık de ekler. Tek işlemcili bir ortamda, olaylar, iletiler, uyarılar ve hatalar günlükçü 'e öngörülebilir ve sıralı bir biçimde ulaşır. Ancak, çok işlemcili bir ortamda, farklı kaynaklardan gelen olaylar aynı anda veya sıra dışında gelebilir. Bunu sağlamak için, MSBuild çok işlemcili bir günlükçü ve yeni bir günlük modeli sağlar ve özel "iletme Günlükçüleri" oluşturmanıza imkan tanır.

## <a name="multi-processor-logging-challenges"></a>Çok işlemcili günlüğe kaydetme sorunları

 Çok işlemcili veya çok çekirdekli bir sistemde bir veya daha fazla proje oluşturduğunuzda, tüm projeler için MSBuild derleme olayları aynı anda oluşturulur. Olay iletilerinin bir Avalanche, günlükçü üzerinde aynı anda veya sıra dışında gelebilir. MSBuild 2,0 günlükçüsü bu durumu işleyecek şekilde tasarlanmadığı için, günlükçü 'yi açabilir ve derleme sürelerinin artmasına, yanlış günlükçü çıktısına veya hatta bozuk bir yapıya neden olabilir. Bu sorunları gidermek için, günlükçü (MSBuild 3,5 ' den başlayarak), dizi dışı olayları işleyebilir ve olayları ve bunların kaynaklarını ilişkilendirebilir.

 Özel bir iletme günlükçüsü oluşturarak günlüğe kaydetme verimliliğini daha da artırabilirsiniz. Özel bir iletme günlükçüsü, oluşturmadan önce, yalnızca izlemek istediğiniz olayları seçmenizi sağlayarak bir filtre işlevi görür. Özel bir iletme günlükçüsü kullandığınızda, istenmeyen olaylar günlükçü sayısını düşürebilir, günlüklerinizi kalabalıklığını veya yavaş derleme süreleriyle başa çıkıp.

## <a name="multi-processor-logging-models"></a>Çok işlemcili günlük modelleri

 MSBuild, çok işlemcili ilgili derleme sorunları için sağlamak üzere iki günlük modelini destekler, merkezi ve dağıtılır.

### <a name="central-logging-model"></a>Merkezi günlük modeli

 Merkezi günlük modelinde, tek bir *MSBuild.exe* örneği "Merkezi düğüm" olarak hareket eder ve merkezi düğümün ("ikincil düğümler") alt örnekleri, derleme görevlerini gerçekleştirmeye yardımcı olmak üzere merkezi düğüme iliştirilemiyor.

 ![Merkezi günlükçü modeli](../msbuild/media/centralnode.png "Merkezileştirme düğümü")

 Merkezi düğüme eklenen çeşitli türlerin Günlükçüleri "Merkezi Günlükçüler" olarak bilinir. Her Günlükçü türünün yalnızca bir örneği merkezi düğüme aynı anda iliştirilebilir.

 Bir derleme gerçekleştiğinde, ikincil düğümler derleme olaylarını merkezi düğüme yönlendirir. Merkezi düğüm tüm olaylarını ve ayrıca ikincil düğümleri bir veya daha fazla bağlı merkezi Günlükçüler için yönlendirir. Günlükçüler daha sonra gelen verileri temel alan günlük dosyaları oluşturur.

 Yalnızca <xref:Microsoft.Build.Framework.ILogger> merkezi günlükçü tarafından uygulanması gerekse de, <xref:Microsoft.Build.Framework.INodeLogger> merkezi günlükçü 'nin yapıya katılan düğüm sayısıyla başlatılması için de uygulamanızı öneririz. Aşağıdaki yöntem aşırı yüklemesi, <xref:Microsoft.Build.Framework.ILogger.Initialize%2A> motor günlükçü başlattığında çağırır.

```csharp
public interface INodeLogger: ILogger
{
    public void Initialize(IEventSource eventSource, int nodeCount);
}
```

 Önceden var olan tüm <xref:Microsoft.Build.Framework.ILogger> oturum defterleri, merkezi Günlükçüler olarak davranabilir ve yapıya eklenebilir. Ancak, çok işlemcili günlük senaryolar ve sıra dışı olaylar için açık destek olmadan yazılan merkezi Günlükçüler bir derlemeyi bozabilir veya anlamsız bir çıkış üretebilir.

### <a name="distributed-logging-model"></a>Dağıtılmış günlük modeli

 Merkezi günlük modelinde, çok fazla gelen ileti trafiği merkezi düğümü, örneğin birçok projenin aynı anda ne zaman derlenebileceğini de açabilir. Bu, sistem kaynaklarını stres ve derleme performansını düşürebilir. Bu sorunu kolaylaştırmak için MSBuild, dağıtılmış bir günlük modelini destekler.

 ![Dağıtılmış günlük modeli](../msbuild/media/distnode.png "DistNode")

 Dağıtılmış günlük kaydı modeli, bir iletme günlükçüsü oluşturmanıza izin vererek Merkezi günlük modelini genişletir.

#### <a name="forwarding-loggers"></a>Günlükçüleri iletme

 Bir iletme günlükçüsü, ikincil bir düğüme bağlanan ve gelen derleme olaylarını bu düğümden alan bir olay filtresi olan ikincil, hafif bir günlükçüdür. Gelen olayları filtreler ve yalnızca belirttiğiniz olanları merkezi düğüme iletir. Bu, merkezi düğüme gönderilen ileti trafiğini azaltır ve genel derleme performansını geliştirir.

 Dağıtılmış günlük kullanmanın iki yolu şunlardır:

- Adlı önceden fabriciletme günlükçüsü ' ni özelleştirin <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> .

- Kendi özel iletme günlüklerinizi yazın.

Configurableforwardinggünlükçü ' i gereksinimlerinize uyacak şekilde değiştirebilirsiniz. Bunu yapmak için, komut satırında *MSBuild.exe* kullanarak günlükçü çağırın ve günlükçü 'nin merkezi düğüme iletilmesini istediğiniz derleme olaylarını listeleyin.

Alternatif olarak, özel bir iletme günlükçüsü oluşturabilirsiniz. Özel bir iletme günlükçüsü oluşturarak, günlükçü davranışını hassas şekilde ayarlayabilirsiniz. Ancak, özel bir iletme günlükçü oluşturmak yalnızca Configurableforwardinggünlükçü özelleştirilerek daha karmaşıktır. Daha fazla bilgi için bkz. [iletme Günlükçüleri oluşturma](../msbuild/creating-forwarding-loggers.md).

## <a name="using-the-configurableforwardinglogger-for-simple-distributed-logging"></a>Basit Dağıtılmış günlük için Configurableforwardinggünlükçü kullanma

 Bir Configurableforwardinggünlükçü veya özel bir iletme günlükçüsü eklemek için `-distributedlogger` `-dl` *MSBuild.exe* komut satırı derlemesinde anahtarı (Short için) kullanın. Bir `-logger` Dağıtılmış günlükçü her zaman bir yerine iki günlük sınıfı, iletme günlükçüsü ve merkezi günlükçüsü olmak üzere, günlükçü türleri ve sınıflarının adlarını belirtme biçimi, anahtar ile aynıdır. Aşağıda, Xmlforwardinggünlükçü adlı özel bir iletme günlükçüsü eklemenin bir örneği verilmiştir.

```cmd
msbuild.exe myproj.proj -distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,Culture=neutral
```

> [!NOTE]
> Bir yıldız işareti (*), anahtardaki iki günlükçü adını ayırmalıdır `-dl` .

 Configurableforwardinggünlükçü kullanılması, tipik MSBuild günlükçüsü yerine Configurableforwardinggünlükçü günlükçüsü 'yi iliştirmeniz ve ardından parametre olarak, Configurableforwardinggünlükçü 'nin merkezi düğüme geçmesini istediğiniz olayları belirtmeniz dışında, başka bir günlükçü ( [derleme günlükleri alma](../msbuild/obtaining-build-logs-with-msbuild.md)bölümünde açıklandığı gibi) kullanma gibidir.

 Örneğin, yalnızca bir derleme başladığında ve sona erdiğinde bildirim almak istiyorsanız ve bir hata oluştuğunda,, `BUILDSTARTEDEVENT` `BUILDFINISHEDEVENT` ve parametreleri olarak ' i geçitirsiniz `ERROREVENT` . Çoklu parametreler, noktalı virgülle ayırarak geçirilebilir. Aşağıda `BUILDSTARTEDEVENT` ,, `BUILDFINISHEDEVENT` , ve olaylarını Iletmek Için Configurableforwardinggünlükçü kullanmanın bir örneği verilmiştir `ERROREVENT` .

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

- [İletme günlükçüleri oluşturma](../msbuild/creating-forwarding-loggers.md)