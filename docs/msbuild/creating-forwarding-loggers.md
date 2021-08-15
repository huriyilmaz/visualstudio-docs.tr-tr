---
title: Iletme Günlükçüleri oluşturma | Microsoft Docs
description: projeleri oluştururken izlemek istediğiniz olayları seçmenize izin vererek günlük verimliliğini artırmak için MSBuild iletme günlükçüler oluşturun.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, forwarding loggers
- MSBuild, logging
ms.assetid: 3aebf9c8-b62c-4cb2-b2d6-8cdfcd369a24
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: e70edc25bc27b8c113b6d3bf52b6a43cf1dc0d7637a9ffc3dbfd1c4817dfd09b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121370339"
---
# <a name="create-forwarding-loggers"></a>İletme Günlükçüleri oluşturma

Günlükçüleri iletme, çok işlemcili bir sistemde proje oluştururken izlemek istediğiniz olayları seçmenizi sağlayarak günlük verimliliğini geliştirir. Yönlendirme günlüklerini etkinleştirerek, istenmeyen olayların merkezi günlükçü 'yi önlemesini, derleme süresini yavaşlatmasını ve günlüklerinizi karışıklık almasını engelleyebilirsiniz.

 Bir iletme günlükçüsü oluşturmak için, <xref:Microsoft.Build.Framework.IForwardingLogger> arabirimi uygulayabilir ve sonra yöntemlerini el ile uygulayabilir ya da <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> sınıfını ve önceden yapılandırılmış yöntemlerini kullanabilirsiniz. (İkincisi çoğu uygulama için yeterli olacaktır.)

## <a name="register-events-and-respond-to-them"></a>Olayları kaydetme ve onlara yanıt verme

 Bir iletme günlükçüsü, çok işlemcili bir sistemde derleme sırasında ana yapı işlemi tarafından oluşturulan bir çalışan işlem olan ikincil derleme altyapısı tarafından bildirildikleri için derleme olayları hakkında bilgi toplar. Ardından, iletme günlükçüsü, verdiğiniz yönergelere göre merkezi günlükçü 'ye iletmek üzere olayları seçer.

 İzlemek istediğiniz olayları işlemek için iletme Günlükçüleri kaydetmeniz gerekir. Olaylara kaydolmak için Günlükçüler yöntemi geçersiz kılmalıdır <xref:Microsoft.Build.Utilities.Logger.Initialize%2A> . Bu yöntem artık `nodecount` , sistemdeki işlemci sayısına ayarlanandan sonra isteğe bağlı bir parametre içerir. (Varsayılan olarak 1 ' dir.)

 İzleyebilmeniz için kullanabileceğiniz olaylara örnekler, <xref:Microsoft.Build.Framework.IEventSource.TargetStarted> <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> ve <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> .

 Çok işlemcili bir ortamda, olay iletilerinin sıra dışında alınması olasıdır. Bu nedenle, iletme günlükçüsü ' nde olay işleyicisini kullanarak olayları değerlendirmeli ve merkezi günlükçü 'ye iletmek üzere yeniden yönlendiriciye hangi olayların geçirileceğini belirlemelisiniz. Bunu gerçekleştirmek için, <xref:Microsoft.Build.Framework.BuildEventContext> iletmek istediğiniz olayları tanımlamanızı ve sonra olayların adlarını <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> sınıfa (veya bunun bir alt sınıfına) geçirmek için her iletiye eklenen sınıfını kullanabilirsiniz. Bu yöntemi kullandığınızda, olayları iletmek için başka bir özel kodlama gerekmez.

## <a name="specify-a-forwarding-logger"></a>Bir iletme günlükçüsü belirtin

 iletme günlükçüsü bir derlemeye derlendikten sonra, MSBuild derlemeler sırasında kullanmak üzere söylemeniz gerekir. Bunu yapmak için `-FileLogger` ,, `-FileLoggerParameters` ve `-DistributedFileLogger` *MSBuild.exe* ile birlikte anahtarları kullanın. `-FileLogger`Anahtar, günlükçü 'nin doğrudan bağlı olduğunu *MSBuild.exe* söyler. `-DistributedFileLogger`Anahtar, düğüm başına bir günlük dosyası olduğu anlamına gelir. İletme günlükçü üzerindeki parametreleri ayarlamak için `-FileLoggerParameters` anahtarını kullanın. Bu ve diğer *MSBuild.exe* anahtarları hakkında daha fazla bilgi için bkz. [komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md).

## <a name="multi-processor-aware-loggers"></a>Çok işlemcili oturum defterleri

 Çok işlemcili bir sistemde bir proje oluşturduğunuzda, her işlemcideki yapı iletileri birleştirilmiş bir dizide otomatik olarak araya eklemeli. Bunun yerine, <xref:Microsoft.Build.Framework.BuildEventContext> her iletiye iliştirilmiş sınıfı kullanarak bir ileti gruplama önceliği oluşturmanız gerekir. Çok işlemcili derleme hakkında daha fazla bilgi için bkz. [Multi-Processor ortamında günlüğe kaydetme](../msbuild/logging-in-a-multi-processor-environment.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme günlüklerini al](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Günlükçüleri derleme](../msbuild/build-loggers.md)
- [Birden çok işlemcili ortamda oturum açma](../msbuild/logging-in-a-multi-processor-environment.md)