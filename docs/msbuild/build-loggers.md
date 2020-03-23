---
title: Loggers yap | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing loggers
- MSBuild, logging
- logging [MSBuild]
ms.assetid: fa34810d-185a-4d22-92bd-9852915e5f1d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a00bbb8ce239275ff140dbedf2157e4cdc41d44c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634532"
---
# <a name="build-loggers"></a>Loggers oluşturun

Loggers, belirli yapı olaylarına yanıt olarak yapınızın çıktısını özelleştirmeniz ve iletileri, hataları veya uyarıları görüntülemeniz için bir yol sağlar. Her kaydedici, <xref:Microsoft.Build.Framework.ILogger> *Microsoft.Build.Framework.dll* derlemesinde tanımlanan arabirimi uygulayan bir .NET sınıfı olarak uygulanır.

Logger uygularken kullanabileceğiniz iki yaklaşım vardır:

- Arayüzü <xref:Microsoft.Build.Framework.ILogger> doğrudan uygulayın.
- *Microsoft.Build.Utilities.dll* <xref:Microsoft.Build.Utilities.Logger>derlemesinde tanımlanan yardımcı sınıftan sınıfınızı türetin. <xref:Microsoft.Build.Utilities.Logger>bazı <xref:Microsoft.Build.Framework.ILogger> <xref:Microsoft.Build.Framework.ILogger> üyelerin varsayılan uygulamalarını uygular ve sağlar.

  Bu <xref:Microsoft.Build.Utilities.Logger>konu, belirli yapı olaylarına yanıt olarak konsolda iletileri görüntüleyen basit bir logger'ın nasıl yazılması gerektiğini açıklar.

## <a name="register-for-events"></a>Etkinlikler için kaydolun

Logger'ın amacı, yapı altyapısı tarafından bildirilen yapı ilerlemesi hakkında bilgi toplamak ve bu bilgileri yararlı bir şekilde bildirmektir. Tüm kaydediciler, logger olaylar için kaydeder yöntemi geçersiz kılmak <xref:Microsoft.Build.Utilities.Logger.Initialize%2A> gerekir. Bu örnekte, logger <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>, , <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>ve <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> olaylar için kaydeder.

[!code-csharp[msbuild_SimpleConsoleLogger#2](../msbuild/codesnippet/CSharp/build-loggers_1.cs)]

## <a name="respond-to-events"></a>Olaylara yanıt verme

Logger belirli olaylar için kayıtlı olduğundan, bu olaylar gerçekleştiğinde işlemek gerekir. , <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>ve <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> olaylar için, kaydedici sadece kısa bir ifade ve olay dahil proje dosyasının adını yazar. Kaydediciden gelen tüm iletiler konsol penceresine yazılır.

[!code-csharp[msbuild_SimpleConsoleLogger#3](../msbuild/codesnippet/CSharp/build-loggers_2.cs)]

## <a name="respond-to-logger-verbosity-values"></a>Logger ayrıntılı lık değerlerine yanıt verme

Bazı durumlarda, msbuild.exe **-verbosity** anahtarı belirli bir değer içeriyorsa, yalnızca bir olaydan gelen bilgileri günlüğe kaydetmek isteyebilirsiniz. Bu örnekte, <xref:Microsoft.Build.Framework.IEventSource.TargetStarted> olay işleyicisi yalnızca <xref:Microsoft.Build.Utilities.Logger.Verbosity%2A> **-ayrıntılı lık** anahtarı tarafından ayarlanan özellik eşitse <xref:Microsoft.Build.Framework.LoggerVerbosity> `Detailed`bir iletiyi günlüğe kaydeder.

[!code-csharp[msbuild_SimpleConsoleLogger#4](../msbuild/codesnippet/CSharp/build-loggers_3.cs)]

## <a name="specify-a-logger"></a>Bir logger belirtin

Logger bir derleme içine derlenir sonra, msbuild bu logger kullanırsanız oluşturmasırasında söylemek gerekir. Bu *MSBuild.exe*ile **-logger** anahtarı kullanılarak yapılır. *MSBuild.exe*için mevcut anahtarlar hakkında daha fazla bilgi için Bkz. [Komut satırı başvurusu.](../msbuild/msbuild-command-line-reference.md)

Aşağıdaki komut satırı *myProject.csproj* projesini oluşturur ve *SimpleLogger.dll'de*uygulanan logger sınıfını kullanır. **-nologo** anahtarı banner ve telif hakkı iletisini gizler ve **-noconsolelogger** anahtarı varsayılan MSBuild konsol logger devre dışı kalır.

```cmd
MSBuild -nologo -noconsolelogger -logger:SimpleLogger.dll
```

Aşağıdaki komut satırı, projeyi aynı kaydedici ile, `Verbosity` ancak `Detailed`.

```cmd
MSBuild -nologo -noconsolelogger -logger:SimpleLogger.dll -verbosity:Detailed
```

## <a name="example"></a>Örnek

### <a name="description"></a>Açıklama

Aşağıdaki örnek, kaydedici için tam kodu içerir.

### <a name="code"></a>Kod

[!code-csharp[msbuild_SimpleConsoleLogger#1](../msbuild/codesnippet/CSharp/build-loggers_4.cs)]

## <a name="example"></a>Örnek

### <a name="description"></a>Açıklama

Aşağıdaki örnek, günlüğü konsol penceresinde görüntülemek yerine bir dosyaya yazan bir kaydedicinin nasıl uygulanacağını gösterir.

### <a name="code"></a>Kod

[!code-csharp[msbuild_BasicLogger#1](../msbuild/codesnippet/CSharp/build-loggers_5.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- [Yapı günlükleri edinme](../msbuild/obtaining-build-logs-with-msbuild.md)
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
