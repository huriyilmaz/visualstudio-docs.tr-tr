---
title: Günlük Kayıt | Oluşturma Microsoft Docs
description: Proje MSBuild izlemek istediğiniz olayları seçmenize olanak vererek günlük verimliliğini artırmak için günlük kaydı günlüklerini iletme günlüklerini oluşturun.
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
ms.openlocfilehash: c4f8cc9ec0658ffcfaa9be8bc971222d77d14373
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122054814"
---
# <a name="create-forwarding-loggers"></a>Yönlendirme günlüklerini oluşturma

Günlüğe kaydetme, çok işlemcili bir sistemde proje derleme sırasında izlemek istediğiniz olayları seçmenize olanak vererek günlüğe kaydetme verimliliğini artırır. Günlükleyicileri ileterek istenmeyen olayların merkezi günlükleyiciye aşırı yığılması, derleme zamanını yavaşlatması ve günlüğün karmaşık hale etkinleştirilmesini önlenebilir.

 Bir iletme günlükleyicisi oluşturmak için arabirimini uygulayarak yöntemlerini el ile veya sınıfını ve önceden yapılandırılmış yöntemlerini <xref:Microsoft.Build.Framework.IForwardingLogger> <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> kullanabilirsiniz. (İkinci seçenek çoğu uygulama için yeterli olacaktır.)

## <a name="register-events-and-respond-to-them"></a>Olayları kaydetme ve yanıtlama

 Bir iletme günlükleyicisi, çok işlemcili bir sistem üzerinde derleme sırasında ana derleme işlemi tarafından oluşturulan bir çalışan işlemi olan ikincil derleme altyapısı tarafından bildirilen derleme olayları hakkında bilgi toplar. Ardından, iletme günlükleyicisi, merkezi günlükleyiciye iletilebilecek olayları, size verilen yönergelere göre seçer.

 İzlemek istediğiniz olayları işlemek için iletme günlüklerini kaydetmelisiniz. Olaylara kaydolmak için günlükçilerin yöntemini geçersiz kılması <xref:Microsoft.Build.Utilities.Logger.Initialize%2A> gerekir. Bu yöntem artık sistemde işlemci `nodecount` sayısına ayarlanabiliyor isteğe bağlı parametresini içerir. (Varsayılan olarak değer 1'tir.)

 , ve gibi olayları <xref:Microsoft.Build.Framework.IEventSource.TargetStarted> <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> izleyebilirsiniz.

 Çok işlemcili bir ortamda, olay iletilerinin büyük olasılıkla sırasız olarak alınmalıdır. Bu nedenle, olayları, iletme günlükleyicisinde olay işleyicisini kullanarak değerlendirmeli ve merkezi günlükleyiciye iletilmesi için yeniden yönlendiriciye hangi olayların geçileceğini belirlemek üzere programlanız. Bunu gerçekleştirmek için, iletilen olayları tanımlamaya yardımcı olmak için her iletiye eklenen sınıfını kullanabilir ve ardından olayların adlarını sınıfa (veya bunun alt <xref:Microsoft.Build.Framework.BuildEventContext> <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> sınıfına) iletebilirsiniz. Bu yöntemi kullanarak olayları iletebilirsiniz.

## <a name="specify-a-forwarding-logger"></a>Bir iletme günlükleyicisi belirtme

 Iletme günlükleyicisi bir derlemeye derledikten sonra, MSBuild derlemeler sırasında bunu kullanmalarını söylemeniz gerekir. Bunu yapmak için , `-FileLogger` ve `-FileLoggerParameters` anahtarlarını `-DistributedFileLogger` kullanarakMSBuild.exe. ** `-FileLogger`anahtarı, *MSBuild.exe* günlükleyicinin doğrudan ekli olduğunu söyler. anahtarı, `-DistributedFileLogger` düğüm başına bir günlük dosyası olduğu anlamına gelir. Iletme günlükleyicide parametreleri ayarlamak için anahtarını `-FileLoggerParameters` kullanın. Bunlar ve diğer anahtar anahtarları hakkında *dahaMSBuild.exe* için [bkz. Komut satırı başvurusu.](../msbuild/msbuild-command-line-reference.md)

## <a name="multi-processor-aware-loggers"></a>Çok işlemcili günlükleyiciler

 Çok işlemcili bir sistemde proje derlemeniz, her işlemciden gelen derleme iletileri otomatik olarak birleşik bir dizide araya eklenir. Bunun yerine, her iletiye eklenen sınıfı kullanarak <xref:Microsoft.Build.Framework.BuildEventContext> bir ileti gruplama önceliği kurmanız gerekir. Çok işlemcili bina hakkında daha fazla bilgi için [bkz. Çok işlemcili bir ortamda günlüğe kaydetme.](../msbuild/logging-in-a-multi-processor-environment.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme günlüklerini alma](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Günlükçüleri derleme](../msbuild/build-loggers.md)
- [Birden çok işlemcili ortamda oturum açma](../msbuild/logging-in-a-multi-processor-environment.md)