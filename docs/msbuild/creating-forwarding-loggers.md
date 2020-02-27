---
title: Iletme Günlükçüleri oluşturma | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, forwarding loggers
- MSBuild, logging
ms.assetid: 3aebf9c8-b62c-4cb2-b2d6-8cdfcd369a24
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 852b783129f130316de88580020e0139925ffb37
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634311"
---
# <a name="create-forwarding-loggers"></a>İletme Günlükçüleri oluşturma

Günlükçüleri iletme, çok işlemcili bir sistemde proje oluştururken izlemek istediğiniz olayları seçmenizi sağlayarak günlük verimliliğini geliştirir. Yönlendirme günlüklerini etkinleştirerek, istenmeyen olayların merkezi günlükçü 'yi önlemesini, derleme süresini yavaşlatmasını ve günlüklerinizi karışıklık almasını engelleyebilirsiniz.

 Bir iletme günlükçüsü oluşturmak için <xref:Microsoft.Build.Framework.IForwardingLogger> arabirimini uygulayabilir ve sonra yöntemlerini el ile uygulayabilir ya da <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> sınıfını ve önceden yapılandırılmış yöntemlerini kullanabilirsiniz. (İkincisi çoğu uygulama için yeterli olacaktır.)

## <a name="register-events-and-respond-to-them"></a>Olayları kaydetme ve onlara yanıt verme

 Bir iletme günlükçüsü, çok işlemcili bir sistemde derleme sırasında ana yapı işlemi tarafından oluşturulan bir çalışan işlem olan ikincil derleme altyapısı tarafından bildirildikleri için derleme olayları hakkında bilgi toplar. Ardından, iletme günlükçüsü, verdiğiniz yönergelere göre merkezi günlükçü 'ye iletmek üzere olayları seçer.

 İzlemek istediğiniz olayları işlemek için iletme Günlükçüleri kaydetmeniz gerekir. Olaylara kaydolmak için Günlükçüler <xref:Microsoft.Build.Utilities.Logger.Initialize%2A> yöntemi geçersiz kılmalıdır. Bu yöntem artık sistemdeki işlemci sayısına ayarlanabilir `nodecount`isteğe bağlı bir parametre içerir. (Varsayılan olarak 1 ' dir.)

 İzleyebilmeniz için kullanabileceğiniz olayların örnekleri <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>ve <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>.

 Çok işlemcili bir ortamda, olay iletilerinin sıra dışında alınması olasıdır. Bu nedenle, iletme günlükçüsü ' nde olay işleyicisini kullanarak olayları değerlendirmeli ve merkezi günlükçü 'ye iletmek üzere yeniden yönlendiriciye hangi olayların geçirileceğini belirlemelisiniz. Bunu gerçekleştirmek için her iletiye eklenen <xref:Microsoft.Build.Framework.BuildEventContext> sınıfını kullanarak iletmek istediğiniz olayları tanımlayabilir ve ardından olayların adlarını <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> sınıfına (veya bunun bir alt sınıfına) geçirebilirsiniz. Bu yöntemi kullandığınızda, olayları iletmek için başka bir özel kodlama gerekmez.

## <a name="specify-a-forwarding-logger"></a>Bir iletme günlükçüsü belirtin

 İletme günlükçüsü bir derlemeye derlendikten sonra, MSBuild sırasında bunu kullanmak için MSBuild 'e bildirmeniz gerekir. Bunu yapmak için, `-FileLogger`, `-FileLoggerParameters`ve `-DistributedFileLogger` anahtarlarını *MSBuild. exe*ile birlikte kullanın. `-FileLogger` anahtarı *MSBuild. exe* ' ye günlükçü 'nin doğrudan bağlı olduğunu söyler. `-DistributedFileLogger` anahtarı, düğüm başına bir günlük dosyası olduğu anlamına gelir. İletme günlükçü üzerindeki parametreleri ayarlamak için `-FileLoggerParameters` anahtarını kullanın. Bu ve diğer *MSBuild. exe* anahtarları hakkında daha fazla bilgi için bkz. [komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md).

## <a name="multi-processor-aware-loggers"></a>Çok işlemcili oturum defterleri

 Çok işlemcili bir sistemde bir proje oluşturduğunuzda, her işlemcideki yapı iletileri birleştirilmiş bir dizide otomatik olarak araya eklemeli. Bunun yerine, her iletiye iliştirilmiş <xref:Microsoft.Build.Framework.BuildEventContext> sınıfını kullanarak bir ileti gruplama önceliği oluşturmanız gerekir. Çok işlemcili derleme hakkında daha fazla bilgi için bkz. [Multi-Processor ortamında günlüğe kaydetme](../msbuild/logging-in-a-multi-processor-environment.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme günlüklerini al](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Günlükçüler oluşturun](../msbuild/build-loggers.md)
- [Çok işlemcili bir ortamda oturum açma](../msbuild/logging-in-a-multi-processor-environment.md)