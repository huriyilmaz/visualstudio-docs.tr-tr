---
title: Çok İşlemli Ortamda Oturum Açma | Microsoft Dokümanlar
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
ms.openlocfilehash: 0c332fb67e96bdfea0059de11441da7c32871633
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633570"
---
# <a name="logging-in-a-multi-processor-environment"></a>Çok işlemcili ortamda günlüğe kaydetme

MSBuild'in birden çok işlemci kullanma yeteneği proje oluşturma süresini büyük ölçüde azaltabilir, ancak günlüğe kaydetmeye de karmaşıklık katar. Tek işlemcili bir ortamda, kaydedici gelen olayları, iletileri, uyarıları ve hataları öngörülebilir, sıralı bir şekilde işleyebilir. Ancak, çok işlemcili bir ortamda, çeşitli kaynaklardan gelen olaylar aynı anda veya sıra dışı gelebilir. MSBuild yeni bir çoklu işlemci farkında logger sağlar ve özel "yönlendirme loggers oluşturulmasını sağlar."

## <a name="log-multiple-processor-builds"></a>Birden çok işlemcili yapıyı günlüğe kaydetme

Çok işlemcili veya çok çekirdekli bir sistemde bir veya daha fazla proje oluşturduğunuzda, tüm projeler için MSBuild yapı olayları aynı anda oluşturulur. Olay verilerinin çığ aynı anda veya sıra dışında logger gelebilir. Bu logger bastırmak ve artan yapı süreleri, yanlış logger çıkışı, hatta kırık bir yapı neden olabilir. Bu sorunları gidermek için, MSBuild kaydedici sıra dışı olayları işleyebilir ve olayları ve kaynaklarını ilişkilendirebilir.

Özel bir yönlendirme kaydedici oluşturarak günlük verimliliğini daha da artırabilirsiniz. Özel iletme kaydedicisi, izlemeniz istediğiniz olayları oluşturmadan önce seçmenize izin vererek bir filtre görevi görür. Özel bir iletme kaydedicisi kullandığınızda, istenmeyen olaylar logger'ı bastırmaz, günlüklerinizi darmadağın etmez veya yavaş yapım süreleri.

### <a name="central-logging-model"></a>Merkezi günlük modeli

Çok işlemcili yapılar için MSBuild bir "merkezi günlük modeli" kullanır. Merkezi günlük modelinde, *MSBuild.exe* örneği birincil yapı işlemi veya "merkezi düğüm" olarak görev eder. *MSBuild.exe*veya "ikincil düğümler" ikincil örnekleri, merkezi düğümeklenir. Merkezi düğüme bağlı tüm ILogger tabanlı loggers "merkezi loggers" olarak bilinir ve ikincil düğümlere bağlı loggers "ikincil loggers" olarak bilinir.

Bir yapı oluştuğunda, ikincil kaydediciler olay trafiğini merkezi kaydedicilere yönlendirir. Olaylar birkaç ikincil düğümden kaynaklandığı için, veriler aynı anda merkezi düğüme aynı anda ancak ara sıra gelir. Olay-proje ve olay-hedef başvuruları çözmek için, olay bağımsız değişkenleri ek yapı olay bağlamı bilgileri içerir.

Yalnızca <xref:Microsoft.Build.Framework.ILogger> merkezi kaydedici tarafından uygulanması gerekmesine rağmen, merkezi kaydedicinin <xref:Microsoft.Build.Framework.INodeLogger> yapıya katılan düğüm sayısıyla birlikte başlatılmasını istiyorsanız da uygulamanızı öneririz. Yöntemin <xref:Microsoft.Build.Framework.ILogger.Initialize%2A> aşağıdaki aşırı yüklemesi, motor logger'ı başlattığında çağrılır:

```csharp
public interface INodeLogger: ILogger
{
    public void Initialize(IEventSource eventSource, int nodeCount);
}
```

### <a name="distributed-logging-model"></a>Dağıtılmış günlük modeli

Merkezi günlük modelinde, birçok projenin aynı anda oluşturması gibi çok fazla gelen ileti trafiği, sistemi vurgulayan ve yapı performansını düşüren merkezi düğümü bastırabilir.

Bu sorunu azaltmak için, MSBuild ayrıca ileti kaydedici kaydediciler oluşturmanıza izin vererek merkezi günlük modelini genişleten bir "dağıtılmış günlük modeli" sağlar. İkincil bir düğüme iletme kaydedicisi eklenir ve bu düğümden gelen yapı olayları alır. İletici kaydedici, olayları filtreleyip yalnızca istenilenleri merkezi düğüme iletebildiği dışında normal bir kaydedici gibidir. Bu, merkezi düğümdeki ileti trafiğini azaltır ve bu nedenle daha iyi performans sağlar.

 'den <xref:Microsoft.Build.Framework.IForwardingLogger> <xref:Microsoft.Build.Framework.ILogger>türeyen arabirimi uygulayarak bir iletme kaydedici oluşturabilirsiniz. Arabirim olarak tanımlanır:

```csharp
public interface IForwardingLogger: INodeLogger
{
    public IEventRedirector EventRedirector { get; set; }
    public int NodeId { get; set; }
}
```

Olayları bir iletme kaydedicisinde iletmek <xref:Microsoft.Build.Framework.IEventRedirector.ForwardEvent%2A> için arabirimin yöntemini <xref:Microsoft.Build.Framework.IEventRedirector> arayın. Parametre <xref:Microsoft.Build.Framework.BuildEventArgs>olarak uygun veya türevi geçirin.

Daha fazla bilgi için [bkz.](../msbuild/creating-forwarding-loggers.md)

### <a name="attaching-a-distributed-logger"></a>Dağıtılmış logger ekleme

Bir komut satırı yapısına dağıtılmış logger `-distributedlogger` eklemek `-dl` için (veya kısa süreli) anahtarı kullanın. Logger türlerinin ve sınıfların adlarını belirtme biçimi, dağıtılmış `-logger` bir günlüğe kaydetme sınıfının iki oturum açma türünden oluşması dışında, geçişiçin olanlarla aynıdır: ileti kaydedici ve merkezi kaydedici. Aşağıda dağıtılmış bir kaydedici ekleme örneği verilmiştir:

```cmd
msbuild.exe *.proj -distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,
Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,
Culture=neutral
```

Yıldız işareti (*) `-dl` anahtardaki iki kaydedici adını ayırır.

## <a name="see-also"></a>Ayrıca bkz.

- [Loggers oluşturun](../msbuild/build-loggers.md)
- [Yönlendirme kaydediciler oluşturma](../msbuild/creating-forwarding-loggers.md)
