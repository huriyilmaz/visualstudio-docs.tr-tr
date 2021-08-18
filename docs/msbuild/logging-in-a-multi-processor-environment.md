---
title: Çok Işlemcili bir ortamda oturum açma | Microsoft Docs
description: MSBuild, çok işlemcili bir günlükçü sağlar ve özel "iletme günlükçüleri" oluşturmayı sağlar.
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
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: c4eade469104fae968fbc91939266964cae7869e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122108687"
---
# <a name="logging-in-a-multi-processor-environment"></a>Birden çok işlemcili ortamda oturum açma

birden çok işlemciyi kullanma MSBuild özelliği, proje derleme süresini büyük ölçüde azaltabilir, ancak günlüğe kaydetmeye karmaşıklık de ekler. Tek işlemcili bir ortamda, günlükçü gelen olayları, iletileri, uyarıları ve hataları öngörülebilir ve sıralı bir şekilde işleyebilir. Ancak, çok işlemcili bir ortamda, çeşitli kaynaklardan gelen olaylar aynı anda veya sıra dışında gelebilir. MSBuild, yeni bir çok işlemcili günlükçü sağlar ve özel "iletme günlükçüleri" oluşturulmasını sağlar.

## <a name="log-multiple-processor-builds"></a>Birden çok işlemci derlemelerini günlüğe kaydet

çok işlemcili veya çok çekirdekli bir sistemde bir veya daha fazla proje oluşturduğunuzda, tüm projeler için MSBuild oluşturma olayları aynı anda oluşturulur. Olay verilerinin bir Avalanche, günlükçü üzerinde aynı anda veya sıra dışında gelebilir. Bu, günlükçü 'yi açabilir ve derleme sürelerinin artmasına, yanlış günlükçü çıktısına ya da bozuk bir yapıya neden olabilir. MSBuild günlükçüsü, bu sorunları gidermek için sıra dışı olayları işleyebilir ve olayları ve bunların kaynaklarını ilişkilendirebilir.

Özel bir iletme günlükçüsü oluşturarak günlüğe kaydetme verimliliğini daha da artırabilirsiniz. Özel iletme günlükçüsü, izlemek istediğiniz olayları, yapılandırmadan önce seçmenize izin vererek bir filtre görevi görür. Özel bir iletme günlükçüsü kullandığınızda, istenmeyen olaylar günlükçüyü etkilemez, günlüklerinizi kalabalıklığı veya yavaş derleme süreleriyle başa çıkıyor.

### <a name="central-logging-model"></a>Merkezi günlük modeli

çok işlemcili yapılar için, MSBuild bir "merkezi günlük model" kullanır. Merkezi günlük modelinde, bir *MSBuild.exe* örneği, birincil derleme işlemi veya "Merkezi düğüm" gibi davranır. *MSBuild.exe* ikincil örnekleri veya "ikincil düğümler" merkezi düğüme eklenir. Merkezi düğüme bağlı olan tüm ILogger tabanlı Günlükçüler, "Merkezi oturum defterleri" olarak bilinir ve ikincil düğümlere bağlı olan Günlükçüler "ikincil günlüğe kaydetme" olarak bilinir.

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

bu sorunu azaltmak için MSBuild ayrıca, iletme günlükçüleri oluşturmanıza izin vererek merkezi günlük modelini genişleten bir "dağıtılmış günlük modeli" sağlar. Bir iletme günlükçüsü, ikincil düğüme iliştirilir ve gelen derleme olaylarını bu düğümden alır. İletme günlükçüsü, olayları filtreleyebilmesi ve sonra yalnızca istenen olanları merkezi düğüme iletmesinin dışında normal bir günlükçü gibi olur. Bu, merkezi düğümdeki ileti trafiğini azaltır ve bu nedenle daha iyi performans sunar.

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
