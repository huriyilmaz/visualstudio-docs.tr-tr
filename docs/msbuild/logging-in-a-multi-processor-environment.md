---
title: Çok Işlemcili bir ortamda oturum açma | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, multi-processor logging
- MSBuild, logging
ms.assetid: dd4dae65-ed04-4883-b48d-59bcb891c4dc
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 65f0558e26583961d94ce380b59a60ecca45987b
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578527"
---
# <a name="logging-in-a-multi-processor-environment"></a>Çok işlemcili bir ortamda oturum açma
MSBuild 'in birden çok işlemciyi kullanma yeteneği, proje derleme süresini büyük ölçüde azaltabilir, ancak günlüğe kaydetmeye karmaşıklık de ekler. Tek işlemcili bir ortamda, günlükçü gelen olayları, iletileri, uyarıları ve hataları öngörülebilir ve sıralı bir şekilde işleyebilir. Ancak, çok işlemcili bir ortamda, çeşitli kaynaklardan gelen olaylar aynı anda veya sıra dışında gelebilir. MSBuild, yeni bir çok işlemcili Günlükçü sağlar ve özel "iletme Günlükçüleri" oluşturmayı sağlar.

## <a name="log-multiple-processor-builds"></a>Birden çok işlemci derlemelerini günlüğe kaydet
Çok işlemcili veya çok çekirdekli bir sistemde bir veya daha fazla proje oluşturduğunuzda, tüm projeler için MSBuild derleme olayları aynı anda oluşturulur. Olay verilerinin bir Avalanche, günlükçü üzerinde aynı anda veya sıra dışında gelebilir. Bu, günlükçü 'yi açabilir ve derleme sürelerinin artmasına, yanlış günlükçü çıktısına ya da bozuk bir yapıya neden olabilir. Bu sorunları gidermek için, MSBuild günlükçüsü sıra dışı olayları işleyebilir ve olayları ve bunların kaynaklarını ilişkilendirebilir.

Özel bir iletme günlükçüsü oluşturarak günlüğe kaydetme verimliliğini daha da artırabilirsiniz. Özel iletme günlükçüsü, izlemek istediğiniz olayları, yapılandırmadan önce seçmenize izin vererek bir filtre görevi görür. Özel bir iletme günlükçüsü kullandığınızda, istenmeyen olaylar günlükçüyü etkilemez, günlüklerinizi kalabalıklığı veya yavaş derleme süreleriyle başa çıkıyor.

### <a name="central-logging-model"></a>Merkezi günlük modeli
MSBuild, çok işlemcili yapılar için "Merkezi günlük model" kullanır. Merkezi günlük modelinde, *MSBuild. exe* ' nin bir örneği, birincil derleme işlemi veya "Merkezi düğüm" olarak görev yapar. *MSBuild. exe*' nin veya "ikincil düğümlerin" ikincil örnekleri merkezi düğüme eklenir. Merkezi düğüme bağlı olan tüm ILogger tabanlı Günlükçüler, "Merkezi oturum defterleri" olarak bilinir ve ikincil düğümlere bağlı olan Günlükçüler "ikincil günlüğe kaydetme" olarak bilinir.

Bir derleme gerçekleştiğinde, ikincil Günlükçüler kendi olay trafiğini merkezi günlükçülere yönlendirir. Olaylar birkaç ikincil düğümden kaynaklandığından, veriler merkezi düğüme aynı anda ulaşır ancak araya eklemeli. Olaydan projeye ve olaydan hedefe başvuruları çözümlemek için, olay bağımsız değişkenleri ek derleme olay bağlamı bilgilerini içerir.

Merkezi günlükçü tarafından yalnızca <xref:Microsoft.Build.Framework.ILogger> uygulanması gerekli olsa da, merkezi günlükçü 'nın yapıya katılan düğüm sayısıyla başlatılmasını istiyorsanız <xref:Microsoft.Build.Framework.INodeLogger> uygulamanızı öneririz. Motor günlükçü başlatıldığında <xref:Microsoft.Build.Framework.ILogger.Initialize%2A> yönteminin aşağıdaki aşırı yüklemesi çağrılır:

```csharp
public interface INodeLogger: ILogger
{
    public void Initialize(IEventSource eventSource, int nodeCount);
}
```

### <a name="distributed-logging-model"></a>Dağıtılmış günlük modeli
Merkezi günlük modelinde çok fazla sayıda proje oluşturulduğunda olduğu gibi, çok fazla gelen ileti trafiği, sistemi takip eden ve derleme performansını azaltan merkezi düğümü tahmin edebilir.

Bu sorunu azaltmak için, MSBuild Ayrıca, iletme Günlükçüleri oluşturmanıza izin vererek Merkezi günlük modelini genişleten bir "Dağıtılmış günlük modeli" sağlar. Bir iletme günlükçüsü, ikincil düğüme iliştirilir ve gelen derleme olaylarını bu düğümden alır. İletme günlükçüsü, olayları filtreleyebilmesi ve sonra yalnızca istenen olanları merkezi düğüme iletmesinin dışında normal bir günlükçü gibi olur. Bu, merkezi düğümdeki ileti trafiğini azaltır ve bu nedenle daha iyi performans sunar.

 <xref:Microsoft.Build.Framework.ILogger>türetilen <xref:Microsoft.Build.Framework.IForwardingLogger> arabirimini uygulayarak bir iletme günlükçüsü oluşturabilirsiniz. Arabirim şöyle tanımlanır:

```csharp
public interface IForwardingLogger: INodeLogger
{
    public IEventRedirector EventRedirector { get; set; }
    public int NodeId { get; set; }
}
```

Bir iletme günlükçüsü içindeki olayları iletmek için <xref:Microsoft.Build.Framework.IEventRedirector> arabiriminin <xref:Microsoft.Build.Framework.IEventRedirector.ForwardEvent%2A> yöntemini çağırın. Uygun <xref:Microsoft.Build.Framework.BuildEventArgs>veya bir türeme parametresini parametre olarak geçirin.

Daha fazla bilgi için bkz. [iletme Günlükçüleri oluşturma](../msbuild/creating-forwarding-loggers.md).

### <a name="attaching-a-distributed-logger"></a>Dağıtılmış günlükçü iliştirme
Bir komut satırı derlemesinde dağıtılmış bir günlükçü eklemek için `-distributedlogger` (ya da Short için `-dl`) anahtarını kullanın. Günlükçü türleri ve sınıflarının adlarını belirtme biçimi, dağıtılmış bir günlükçü iki günlük sınıfından oluşur: bir iletme günlükçüsü ve bir merkezi günlükçüsü olması dışında `-logger` anahtarıyla aynıdır. Aşağıda, dağıtılmış bir günlükçü ekleme örneği verilmiştir:

```cmd
msbuild.exe *.proj -distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,
Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,
Culture=neutral
```

Bir yıldız işareti (*) `-dl` anahtarındaki iki günlükçü adını ayırır.

## <a name="see-also"></a>Ayrıca bkz.
- [Günlükçüler oluşturun](../msbuild/build-loggers.md)
- [İletme Günlükçüleri oluşturma](../msbuild/creating-forwarding-loggers.md)
