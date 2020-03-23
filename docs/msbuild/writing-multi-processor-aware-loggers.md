---
title: Çok İşlemcili Kaydediciler Yazma | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77630753"
---
# <a name="write-multi-processor-aware-loggers"></a>Çok işlemcili bilgine duyarlı kaydediciler yazma

MSBuild'in birden çok işlemciden yararlanma yeteneği proje oluşturma süresini kısaltabilir, ancak olay günlüğe kaydetme oluşturmak için karmaşıklık da ekler. Tek işlemcili bir ortamda, olaylar, iletiler, uyarılar ve hatalar kaydediciye öngörülebilir, sıralı bir şekilde ulaşır. Ancak, çok işlemcili bir ortamda, farklı kaynaklardan gelen olaylar aynı anda veya sıra dışı gelebilir. Bunu sağlamak için, MSBuild çok işlemcili bir logger ve yeni bir günlük modeli sağlar ve özel "yönlendirme loggers oluşturmanıza olanak sağlar."

## <a name="multi-processor-logging-challenges"></a>Çok işlemcili günlük zorlukları

 Çok işlemcili veya çok çekirdekli bir sistemde bir veya daha fazla proje oluşturduğunuzda, tüm projeler için MSBuild yapı olayları aynı anda oluşturulur. Olay iletilerinin çığ aynı anda veya sıra dışında logger gelebilir. BIR MSBuild 2.0 kaydedici bu durumu işlemek için tasarlanmadığından, logger'ı bastırabilir ve daha fazla yapı sürelerine, yanlış kaydedici çıkışına ve hatta bozuk bir yapıya neden olabilir. Bu sorunları gidermek için logger (MSBuild 3.5'ten başlayarak) sıra dışı olayları işleyebilir ve olayları ve kaynaklarını ilişkilendirebilir.

 Özel bir yönlendirme kaydedici oluşturarak günlük verimliliğini daha da artırabilirsiniz. Özel bir iletme kaydedicisi, yalnızca izlemek istediğiniz olayları oluşturmadan önce seçmenize izin vererek bir filtre görevi görür. Özel bir iletme kaydedicisi kullandığınızda, istenmeyen olaylar logger'ı bastıramaz, günlüklerinizi yıkamaz veya yavaş yapım süreleri.

## <a name="multi-processor-logging-models"></a>Çok işlemcili günlük modelleri

 Çok işlemciyle ilgili yapı sorunlarını sağlamak için MSBuild, merkezi ve dağıtılmış iki günlük modelini destekler.

### <a name="central-logging-model"></a>Merkezi günlük modeli

 Merkezi günlük modelinde, *MSBuild.exe'nin* tek bir örneği "merkezi düğüm" olarak hareket eder ve merkezi düğümün alt örnekleri ("ikincil düğümler") yapı görevlerini gerçekleştirmesine yardımcı olmak için merkezi düğüme bağlanır.

 ![Merkezi Logger Modeli](../msbuild/media/centralnode.png "CentralNode")

 Merkezi düğüme iliştirilen çeşitli türlerdeki loggers "merkezi loggers" olarak bilinir. Her logger türünden yalnızca bir örnek aynı anda merkezi düğüme eklenebilir.

 Bir yapı oluştuğunda, ikincil düğümler yapı olaylarını merkezi düğüme yönlendirir. Merkezi düğüm, tüm olayları ve aynı zamanda ikincil düğümleri bağlı merkezi kaydedicilerden bir veya daha fazlasına yönlendirir. Kaydediciler daha sonra gelen verileri temel alan günlük dosyaları oluşturur.

 Yalnızca <xref:Microsoft.Build.Framework.ILogger> merkezi kaydedici tarafından uygulanması gerekmesine rağmen, merkezi kaydedicinin <xref:Microsoft.Build.Framework.INodeLogger> yapıya katılan düğüm sayısıyla birlikte başlatılmasını da öneririz. Yöntemin <xref:Microsoft.Build.Framework.ILogger.Initialize%2A> aşağıdaki aşırı yüklemesi, motor logger'ı başlattığında çağırır.

```csharp
public interface INodeLogger: ILogger
{
    public void Initialize(IEventSource eventSource, int nodeCount);
}
```

 Önceden varolan <xref:Microsoft.Build.Framework.ILogger>tabanlı loggers merkezi loggers olarak hareket edebilir ve yapı ekleyebilirsiniz. Ancak, çok işlemcili günlük senaryoları ve sıra dışı olaylar için açık destek olmadan yazılan merkezi kaydediciler bir yapıyı bozabilir veya anlamsız çıktı lar üretebilir.

### <a name="distributed-logging-model"></a>Dağıtılmış günlük modeli

 Merkezi günlüğe kaydetme modelinde, çok fazla gelen ileti trafiği, örneğin birçok proje aynı anda inşa edildiğinde, merkezi düğümü bastırabilir. Bu, sistem kaynaklarını strese alabilir ve yapı performansını düşürebilir. Bu sorunu hafifletmek için, MSBuild dağıtılmış bir günlük modelini destekler.

 ![Dağıtılmış Günlük Modeli](../msbuild/media/distnode.png "DistNode")

 Dağıtılmış günlük modeli, bir iletme kaydedici oluşturmanıza izin vererek merkezi günlük modelini genişletir.

#### <a name="forwarding-loggers"></a>Yönlendirme kaydediciler

 İletici kaydedici, ikincil bir düğüme bağlanan ve bu düğümden gelen yapı olayları alan bir olay filtresi olan ikincil, hafif bir kaydedicidir. Gelen olayları filtreler ve yalnızca merkezi düğüme belirttiğiniz olayları iletin. Bu, merkezi düğüme gönderilen ileti trafiğini azaltır ve genel yapı performansını artırır.

 Dağıtılmış günlüğe kaydetmeyi kullanmanın iki yolu vardır:

- Adlı <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger>önceden imal edilmiş yönlendirme kaydedicisini özelleştirin.

- Kendi özel yönlendirme kaydedicinizi yazın.

ConfigurableForwardingLogger'ı gereksinimlerinize uyacak şekilde değiştirebilirsiniz. Bunu yapmak için, *MSBuild.exe*kullanarak komut satırında logger arayın ve kaydedici merkezi düğüme iletmek istediğiniz yapı olayları listele.

Alternatif olarak, özel bir iletme kaydedici oluşturabilirsiniz. Özel bir iletme kaydedici oluşturarak, kaydedicinin davranışında ince ayar yapabilirsiniz. Ancak, özel bir iletme kaydedici oluşturma sadece ConfigurableForwardingLogger özelleştirme daha karmaşıktır. Daha fazla bilgi için [bkz.](../msbuild/creating-forwarding-loggers.md)

## <a name="using-the-configurableforwardinglogger-for-simple-distributed-logging"></a>Basit dağıtılmış günlük için ConfigurableForwardingLogger kullanma

 ConfigurableForwardingLogger veya özel bir iletme kaydedici eklemek `-distributedlogger` için,`-dl` anahtarı (kısaca) bir *MSBuild.exe* komut satırı yapısında kullanın. Logger türlerinin ve sınıfların adlarını belirtme biçimi, dağıtılmış `-logger` bir kaydedicinin her zaman bir yerine iki günlük sınıfı, ileti kaydedici kaydedici ve merkezi kaydedici olması dışında, geçiş için aynıdır. Aşağıda, XMLForwardingLogger adlı özel bir iletme kaydedicisinin nasıl eklenebildiğini gösteren bir örnek verilmiştir.

```cmd
msbuild.exe myproj.proj -distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,Culture=neutral
```

> [!NOTE]
> Yıldız işareti (*) `-dl` anahtardaki iki logger adını ayırmalıdır.

 ConfigurableForwardingLogger'ı kullanmak, tipik MSBuild logger yerine ConfigurableForwardingLogger logger'ı takmanız ve ConfigurableForwardingLogger'ın merkezi düğüme geçmesini istediğiniz olayları parametreler olarak belirtmeniz dışında, başka bir logger [(yapı günlüklerini edinmede](../msbuild/obtaining-build-logs-with-msbuild.md)belirtildiği gibi) kullanmak gibidir.

 Örneğin, yalnızca bir yapı başlayıp sona erdiğinde ve bir hata oluştuğunda, parametre `BUILDSTARTEDEVENT` `BUILDFINISHEDEVENT`olarak `ERROREVENT` , "geçeceği" bildirilir. Birden fazla parametre yarı-kolon ile ayırarak geçirilebilir. Aşağıdaki, ConfigurableForwardingLogger'ın yalnızca , `BUILDSTARTEDEVENT` `BUILDFINISHEDEVENT`ve `ERROREVENT` olayları iletmek için nasıl kullanılacağına bir örnektir.

```cmd
msbuild.exe myproj.proj -distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,Culture=neutral*ConfigureableForwardingLogger,C:\My.dll;BUILDSTARTEDEVENT; BUILDFINISHEDEVENT;ERROREVENT
```

 Aşağıdaki kullanılabilir ConfigurableForwardingLogger parametrelerinin bir listesidir.

|Yapılandırılabilir ForwardingLogger Parametreleri|
| - |
|BUILDSTARTEDEVENT|
|BUILDFINISHEDEVENT|
|PROJEYe BAŞLADI ETKINLIK|
|PROJELİ ETKİnLİk|
|HEDEF BAŞLATTI OLAY|
|HEDEFFINISHEDEVENT|
|TASKSTARTEDOLAY|
|TASKFINISHEDOLAY|
|Errorevent|
|UYARI OLAYI|
|HIGHMESSAGEOLAY|
|NORMALMESAJ OLAYI|
|LOWMESSAGEOLAY|
|CUSTOMEVENT|
|Commandline|
|PERFORMANS ÖZETİ|
|NOSUMMARY|
|SHOWCOMMANDLINE|

## <a name="see-also"></a>Ayrıca bkz.

- [Yönlendirme kaydediciler oluşturma](../msbuild/creating-forwarding-loggers.md)