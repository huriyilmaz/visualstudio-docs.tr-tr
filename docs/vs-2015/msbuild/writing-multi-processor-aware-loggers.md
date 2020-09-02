---
title: Çok Işlemcili oturum defterleri yazma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, multi-proc aware loggers
- multi-proc loggers
- loggers, multi-proc
ms.assetid: ff987d1b-1798-4803-9ef6-cc8fcc263516
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0d2eaf41ac66cd1bdf680145bef43b17cc29a505
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64802075"
---
# <a name="writing-multi-processor-aware-loggers"></a>Birden Çok İşlemciye Duyarlı Günlükçüler Yazılıyor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]Birden çok işlemciyi kullanmanın yeteneği, proje derleme süresini azaltabilir, ancak olay günlüğü oluşturmak için karmaşıklık de ekler. Tek işlemcili bir ortamda, olaylar, iletiler, uyarılar ve hatalar günlükçü 'e öngörülebilir ve sıralı bir biçimde ulaşır. Ancak, çok işlemcili bir ortamda, farklı kaynaklardan gelen olaylar aynı anda veya sıra dışında gelebilir. Bunu sağlamak için, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] çok işlemcili bir günlükçü ve yeni bir günlük modeli sağlar ve özel "iletme Günlükçüleri" oluşturmanızı sağlar.  
  
## <a name="multi-processor-logging-challenges"></a>Çok Işlemcili günlüğe kaydetme sorunları  
 Çok işlemcili veya çok çekirdekli bir sistemde bir veya daha fazla proje oluşturduğunuzda, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] tüm projelere yönelik derleme olayları aynı anda oluşturulur. Olay iletilerinin bir Avalanche, günlükçü üzerinde aynı anda veya sıra dışında gelebilir. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]2,0 günlükçüsü bu durumu işleyecek şekilde tasarlanmadığından, günlükçü 'yi açabilir ve derleme sürelerinin artmasına, yanlış günlükçü çıktısına veya hatta bozuk bir yapıya neden olabilir. Bu sorunları gidermek için, günlükçü (3,5 ' den başlayarak [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] ), dizi dışı olayları işleyebilir ve olayları ve bunların kaynaklarını ilişkilendirebilir.  
  
 Özel bir iletme günlükçüsü oluşturarak günlüğe kaydetme verimliliğini daha da artırabilirsiniz. Özel bir iletme günlükçüsü, oluşturmadan önce, yalnızca izlemek istediğiniz olayları seçmenizi sağlayarak bir filtre işlevi görür. Özel bir iletme günlükçüsü kullandığınızda, istenmeyen olaylar günlükçü sayısını düşürebilir, günlüklerinizi kalabalıklığını veya yavaş derleme süreleriyle başa çıkıp.  
  
## <a name="multi-processor-logging-models"></a>Çok Işlemcili günlük modelleri  
 Multi-Processor ile ilgili oluşturma sorunlarını sağlamak için, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Merkezi ve dağıtılmış iki günlük modelini destekler.  
  
### <a name="central-logging-model"></a>Merkezi günlük modeli  
 Merkezi günlük modelinde, tek bir MSBuild.exe örneği "Merkezi düğüm" olarak hareket eder ve merkezi düğümün ("ikincil düğümler") alt örnekleri, derleme görevlerini gerçekleştirmeye yardımcı olmak üzere merkezi düğüme iliştirilemiyor.  
  
 ![Merkezi günlükçü modeli](../msbuild/media/centralnode.png "Merkezileştirme düğümü")  
  
 Merkezi düğüme eklenen çeşitli türlerin Günlükçüleri "Merkezi Günlükçüler" olarak bilinir. Her Günlükçü türünün yalnızca bir örneği merkezi düğüme aynı anda iliştirilebilir.  
  
 Bir derleme gerçekleştiğinde, ikincil düğümler derleme olaylarını merkezi düğüme yönlendirir. Merkezi düğüm tüm olaylarını ve ayrıca ikincil düğümleri bir veya daha fazla bağlı merkezi Günlükçüler için yönlendirir. Günlükçüler daha sonra gelen verileri temel alan günlük dosyaları oluşturur.  
  
 Yalnızca <xref:Microsoft.Build.Framework.ILogger> merkezi günlükçü tarafından uygulanması gerekse de, <xref:Microsoft.Build.Framework.INodeLogger> merkezi günlükçü 'nin yapıya katılan düğüm sayısıyla başlatılması için de uygulamanızı öneririz. Aşağıdaki yöntem aşırı yüklemesi, <xref:Microsoft.Build.Framework.ILogger.Initialize%2A> motor günlükçü başlattığında çağırır.  
  
```  
public interface INodeLogger: ILogger  
{  
    public void Initialize(IEventSource eventSource, int nodeCount);  
}  
```  
  
 Önceden var olan tüm <xref:Microsoft.Build.Framework.ILogger> oturum defterleri, merkezi Günlükçüler olarak davranabilir ve yapıya eklenebilir. Ancak, çok işlemcili günlük senaryolar ve sıra dışı olaylar için açık destek olmadan yazılan merkezi Günlükçüler bir derlemeyi bozabilir veya anlamsız bir çıkış üretebilir.  
  
### <a name="distributed-logging-model"></a>Dağıtılmış günlük modeli  
 Merkezi günlük modelinde, çok fazla gelen ileti trafiği merkezi düğümü, örneğin birçok projenin aynı anda ne zaman derlenebileceğini de açabilir. Bu, sistem kaynaklarını stres ve derleme performansını düşürebilir. Bu sorunu kolaylaştırmak için [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Dağıtılmış bir günlük modelini destekler.  
  
 ![Dağıtılmış günlük modeli](../msbuild/media/distnode.png "DistNode")  
  
 Dağıtılmış günlük kaydı modeli, bir iletme günlükçüsü oluşturmanıza izin vererek Merkezi günlük modelini genişletir.  
  
#### <a name="forwarding-loggers"></a>Günlükçüleri iletme  
 Bir iletme günlükçüsü, ikincil bir düğüme bağlanan ve gelen derleme olaylarını bu düğümden alan bir olay filtresi olan ikincil, hafif bir günlükçüdür. Gelen olayları filtreler ve yalnızca belirttiğiniz olanları merkezi düğüme iletir. Bu, merkezi düğüme gönderilen ileti trafiğini azaltır ve genel derleme performansını geliştirir.  
  
 Dağıtılmış günlük kullanmanın iki yolu şunlardır:  
  
- Adlı önceden fabriciletme günlükçüsü ' ni özelleştirin <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> .  
  
- Kendi özel iletme günlüklerinizi yazın.  
  
  Configurableforwardinggünlükçü ' i gereksinimlerinize uyacak şekilde değiştirebilirsiniz. Bunu yapmak için, komut satırında MSBuild.exe kullanarak günlükçü çağırın ve günlükçü 'nin merkezi düğüme iletilmesini istediğiniz derleme olaylarını listeleyin.  
  
  Alternatif olarak, özel bir iletme günlükçüsü oluşturabilirsiniz. Özel bir iletme günlükçüsü oluşturarak, günlükçü davranışını hassas şekilde ayarlayabilirsiniz. Ancak, özel bir iletme günlükçü oluşturmak yalnızca Configurableforwardinggünlükçü özelleştirilerek daha karmaşıktır. Daha fazla bilgi için bkz. [Iletme Günlükçüleri oluşturma](../msbuild/creating-forwarding-loggers.md).  
  
## <a name="using-the-configurableforwardinglogger-for-simple-distributed-logging"></a>Basit Dağıtılmış günlük için Configurableforwardinggünlükçü kullanma  
 Bir Configurableforwardinggünlükçü veya özel bir iletme günlükçüsü eklemek için `/distributedlogger` `/dl` MSBuild.exe komut satırı derlemesinde anahtarı (Short için) kullanın. Bir `/logger` Dağıtılmış günlükçü her zaman bir yerine iki günlük sınıfı, iletme günlükçüsü ve merkezi günlükçüsü olmak üzere, günlükçü türleri ve sınıflarının adlarını belirtme biçimi, anahtar ile aynıdır. Aşağıda, Xmlforwardinggünlükçü adlı özel bir iletme günlükçüsü eklemenin bir örneği verilmiştir.  
  
```  
msbuild.exe myproj.proj/distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,Culture=neutral  
```  
  
> [!NOTE]
> Bir yıldız işareti (*), anahtardaki iki günlükçü adını ayırmalıdır `/dl` .  
  
 Configurableforwardinggünlükçü kullanılması, tipik günlükçü yerine Configurableforwardinggünlükçü günlükçüsü 'yi iliştirmeniz ve bir parametre olarak, Configurableforwardinggünlükçü 'nin merkezi düğüme geçmesini istediğiniz olayları belirtmeniz dışında, başka bir günlükçü ( [derleme günlükleri alma](../msbuild/obtaining-build-logs-with-msbuild.md)bölümünde açıklandığı gibi) kullanma gibidir [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] .  
  
 Örneğin, yalnızca bir derleme başladığında ve sona erdiğinde bildirim almak istiyorsanız ve bir hata oluştuğunda,, `BUILDSTARTEDEVENT` `BUILDFINISHEDEVENT` ve parametreleri olarak ' i geçitirsiniz `ERROREVENT` . Çoklu parametreler, noktalı virgülle ayırarak geçirilebilir. Aşağıda `BUILDSTARTEDEVENT` ,, `BUILDFINISHEDEVENT` , ve olaylarını Iletmek Için Configurableforwardinggünlükçü kullanmanın bir örneği verilmiştir `ERROREVENT` .  
  
```  
msbuild.exe myproj.proj /distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,Culture=neutral*ConfigureableForwardingLogger,C:\My.dll;BUILDSTARTEDEVENT; BUILDFINISHEDEVENT;ERROREVENT  
```  
  
 Aşağıda, kullanılabilir Configurableforwardinggünlükçü parametrelerinin bir listesi verilmiştir.  
  
|Configurableforwardinggünlükçü parametreleri|  
|---------------------------------------------|  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iletme Günlükçüleri oluşturma](../msbuild/creating-forwarding-loggers.md)
