---
title: Yönlendirme Kaydediciler Oluşturma | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634311"
---
# <a name="create-forwarding-loggers"></a>Yönlendirme kaydediciler oluşturma

Yönlendirme kaydediciler, çok işlemcili bir sistemde proje oluştururken izlemek istediğiniz olayları seçmenize izin vererek günlük verimliliğini artırır. Yönlendirme kaydedicileri etkinleştirerek, istenmeyen olayların merkezi kaydediciyi ezmesini, oluşturma süresini yavaşlatmasını ve günlüğünüzün yığılmasını önleyebilirsiniz.

 Bir iletme kaydedici oluşturmak için, <xref:Microsoft.Build.Framework.IForwardingLogger> arabirimi uygulayabilir ve sonra yöntemlerini <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> el ile uygulayabilir veya sınıfı ve önceden yapılandırılmış yöntemlerini kullanabilirsiniz. (İkincisi çoğu uygulama için yeterli olacaktır.)

## <a name="register-events-and-respond-to-them"></a>Olayları kaydedin ve bunlara yanıt verin

 Bir iletme kaydedici, çok işlemcili bir sistem üzerinde bir yapı sırasında ana yapı işlemi tarafından oluşturulan bir alt işlem olan ikincil yapı altyapısı tarafından bildirilen yapı olayları hakkında bilgi toplar. Daha sonra ileti kaydedici, size vermiş olduğunuz yönergelere göre olayları merkezi kaydediciye iletecek şekilde seçer.

 İzlemek istediğiniz olayları işlemek için yönlendirme kaydediciler kaydetmeniz gerekir. Olaylara kaydolmak için loggers <xref:Microsoft.Build.Utilities.Logger.Initialize%2A> yöntemi geçersiz kılmak gerekir. Bu yöntem artık sistemdeki `nodecount`işlemci sayısına ayarlanabilen isteğe bağlı bir parametre içerir. (Varsayılan olarak, değer 1'dir.)

 İzleyebilirsiniz olaylara örnek <xref:Microsoft.Build.Framework.IEventSource.TargetStarted> <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>olarak <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>, ve .

 Çok işlemcili bir ortamda, olay iletilerinin sıra dışı alınması olasıdır. Bu nedenle, ileti kaydedici deki olay işleyicisini kullanarak olayları değerlendirmeniz ve merkezi kaydediciye iletmek üzere yeniden müdüre hangi olayların geçeceğinizi belirlemek için programlamanız gerekir. Bunu başarmak için, iletmek <xref:Microsoft.Build.Framework.BuildEventContext> istediğiniz olayları tanımlamaya yardımcı olmak ve sonra olayların adlarını <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> sınıfa (veya alt sınıfına) geçirmenize yardımcı olmak için her iletiye bağlı olan sınıfı kullanabilirsiniz. Bu yöntemi kullandığınızda, olayları iletmek için başka bir özel kodlama gerekmez.

## <a name="specify-a-forwarding-logger"></a>Bir iletme kaydedicisi belirtin

 Yönlendirme kaydedici bir derleme içine derlendikten sonra, msbuild'e yapılar sırasında kullanmasını söylemeniz gerekir. Bunu yapmak için, `-FileLogger` `-FileLoggerParameters` `-DistributedFileLogger` *MSBuild.exe*ile birlikte , ve anahtarları kullanın. Anahtar, `-FileLogger` *MSBuild.exe'ye* logger'ın doğrudan bağlı olduğunu söyler. Anahtar, `-DistributedFileLogger` düğüm başına bir günlük dosyası olduğu anlamına gelir. Parametreleri iletme kaydedicisine ayarlamak için `-FileLoggerParameters` anahtarı kullanın. Bu ve diğer *MSBuild.exe* anahtarları hakkında daha fazla bilgi için [Komut satırı başvurusuna](../msbuild/msbuild-command-line-reference.md)bakın.

## <a name="multi-processor-aware-loggers"></a>Çok işlemcili kaydediciler

 Çok işlemcili bir sistemde bir proje oluşturduğunuzda, her işlemciden gelen yapı iletileri otomatik olarak birleşik bir sırada ayrılmaz. Bunun yerine, her iletiye eklenen <xref:Microsoft.Build.Framework.BuildEventContext> sınıfı kullanarak bir ileti gruplandırma önceliği oluşturmanız gerekir. Çok işlemcili bina hakkında daha fazla bilgi için, [çok işlemcili ortamda günlüğe kaydetme'ye](../msbuild/logging-in-a-multi-processor-environment.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Yapı günlükleri edinme](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Loggers oluşturun](../msbuild/build-loggers.md)
- [Çok işlemcili ortamda günlüğe kaydetme](../msbuild/logging-in-a-multi-processor-environment.md)