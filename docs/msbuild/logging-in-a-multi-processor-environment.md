---
title: Çok Işlemcili bir ortamda oturum açma | Microsoft Docs
description: MSBuild 'in çok işlemcili bir günlükçü nasıl sağladığını ve özel "iletme Günlükçüleri" oluşturma işlemini nasıl sağladığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, multi-processor logging
- MSBuild, logging
ms.assetid: dd4dae65-ed04-4883-b48d-59bcb891c4dc
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d58f9f29d88d7988b4ead3c2d96eadbbf95a8f46
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966272"
---
# <a name="logging-in-a-multi-processor-environment"></a>Birden çok işlemcili ortamda oturum açma

MSBuild 'in birden çok işlemciyi kullanma yeteneği, proje derleme süresini büyük ölçüde azaltabilir, ancak günlüğe kaydetmeye karmaşıklık de ekler. Tek işlemcili bir ortamda, günlükçü gelen olayları, iletileri, uyarıları ve hataları öngörülebilir ve sıralı bir şekilde işleyebilir. Ancak, çok işlemcili bir ortamda, çeşitli kaynaklardan gelen olaylar aynı anda veya sıra dışında gelebilir. MSBuild, yeni bir çok işlemcili Günlükçü sağlar ve özel "iletme Günlükçüleri" oluşturmayı sağlar.

## <a name="log-multiple-processor-builds"></a>Birden çok işlemci derlemelerini günlüğe kaydet

Çok işlemcili veya çok çekirdekli bir sistemde bir veya daha fazla proje oluşturduğunuzda, tüm projeler için MSBuild derleme olayları aynı anda oluşturulur. Olay verilerinin bir Avalanche, günlükçü üzerinde aynı anda veya sıra dışında gelebilir. Bu, günlükçü 'yi açabilir ve derleme sürelerinin artmasına, yanlış günlükçü çıktısına ya da bozuk bir yapıya neden olabilir. Bu sorunları gidermek için, MSBuild günlükçüsü sıra dışı olayları işleyebilir ve olayları ve bunların kaynaklarını ilişkilendirebilir.

Özel bir iletme günlükçüsü oluşturarak günlüğe kaydetme verimliliğini daha da artırabilirsiniz. Özel iletme günlükçüsü, izlemek istediğiniz olayları, yapılandırmadan önce seçmenize izin vererek bir filtre görevi görür. Özel bir iletme günlükçüsü kullandığınızda, istenmeyen olaylar günlükçüyü etkilemez, günlüklerinizi kalabalıklığı veya yavaş derleme süreleriyle başa çıkıyor.

### <a name="central-logging-model"></a>Merkezi günlük modeli

MSBuild, çok işlemcili yapılar için "Merkezi günlük model" kullanır. Merkezi günlük modelinde, bir *MSBuild.exe* örneği, birincil derleme işlemi veya "Merkezi düğüm" gibi davranır. *MSBuild.exe* ikincil örnekleri veya "ikincil düğümler" merkezi düğüme eklenir. Merkezi düğüme bağlı olan tüm ILogger tabanlı Günlükçüler, "Merkezi oturum defterleri" olarak bilinir ve ikincil düğümlere bağlı olan Günlükçüler "ikincil günlüğe kaydetme" olarak bilinir.

Bir derleme gerçekleştiğinde, ikincil Günlükçüler kendi olay trafiğini merkezi günlükçülere yönlendirir. Olaylar birkaç ikincil düğümden kaynaklandığından, veriler merkezi düğüme aynı anda ulaşır ancak araya eklemeli. Olaydan projeye ve olaydan hedefe başvuruları çözümlemek için, olay bağımsız değişkenleri ek derleme olay bağlamı bilgilerini içerir.

Yalnızca <xref:Microsoft.Build.Framework.ILogger> merkezi günlükçü tarafından uygulanması gerekse de, <xref:Microsoft.Build.Framework.INodeLogger> merkezi günlükçü 'nin yapıya katılan düğüm sayısıyla başlatılmasını istiyorsanız aşağıdakileri de uygulamanız önerilir. <xref:Microsoft.Build.Framework.ILogger.Initialize%2A>Motor günlükçü başlattığında yöntemin aşağıdaki aşırı yüklemesi çağrılır:

```csharp
public interface INodeLogger: ILogger
{
    public void Initialize(IEventSource eventSource, int nodeCount);
}
```

### <a name="distributed-logging-model"></a>Dağıtılmış günlük modeli

Merkezi günlük modelinde çok fazla sayıda proje oluşturulduğunda olduğu gibi, çok fazla gelen ileti trafiği, sistemi takip eden ve derleme performansını azaltan merkezi düğümü tahmin edebilir.

Bu sorunu azaltmak için, MSBuild Ayrıca, iletme Günlükçüleri oluşturmanıza izin vererek Merkezi günlük modelini genişleten bir "Dağıtılmış günlük modeli" sağlar. Bir iletme günlükçüsü, ikincil düğüme iliştirilir ve gelen derleme olaylarını bu düğümden alır. İletme günlükçüsü, olayları filtreleyebilmesi ve sonra yalnızca istenen olanları merkezi düğüme iletmesinin dışında normal bir günlükçü gibi olur. Bu, merkezi düğümdeki ileti trafiğini azaltır ve bu nedenle daha iyi performans sunar.

 Öğesinden türetilen arabirimini uygulayarak bir iletme günlükçüsü oluşturabilirsiniz <xref:Microsoft.Build.Framework.IForwardingLogger> <xref:Microsoft.Build.Framework.ILogger> . Arabirim şöyle tanımlanır:

```csharp
public interface IForwardingLogger: INodeLogger
{
    public IEventRedirector EventRedirector { get; set; }
    public int NodeId { get; set; }
}
```

Bir iletme günlükçüsü içindeki olayları iletmek için <xref:Microsoft.Build.Framework.IEventRedirector.ForwardEvent%2A> arabirimin yöntemini çağırın <xref:Microsoft.Build.Framework.IEventRedirector> . <xref:Microsoft.Build.Framework.BuildEventArgs>Parametresi olarak uygun veya bir türev geçirin.

Daha fazla bilgi için bkz. [iletme Günlükçüleri oluşturma](../msbuild/creating-forwarding-loggers.md).

### <a name="attaching-a-distributed-logger"></a>Dağıtılmış günlükçü iliştirme

Bir komut satırı derlemesinde dağıtılmış bir günlükçü eklemek için `-distributedlogger` (veya, `-dl` Short için) anahtarını kullanın. `-logger`Bir dağıtılmış günlükçü iki günlük sınıfından oluşur: bir iletme günlükçüsü ve bir merkezi günlükçü olmak üzere, günlükçü türlerinin ve sınıflarının adlarını belirtme biçimi, anahtarla aynıdır. Aşağıda, dağıtılmış bir günlükçü ekleme örneği verilmiştir:

```cmd
msbuild.exe *.proj -distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,
Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,
Culture=neutral
```

Bir yıldız işareti (*), anahtardaki iki günlükçü adını ayırır `-dl` .

## <a name="see-also"></a>Ayrıca bkz.

- [Günlükçüleri derleme](../msbuild/build-loggers.md)
- [İletme Günlükçüleri oluşturma](../msbuild/creating-forwarding-loggers.md)
