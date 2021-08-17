---
title: Build Loggers | Microsoft Docs
description: Derlemenizin MSBuild yönetmek ve özelleştirmek ve belirli derleme olaylarına yanıt olarak iletileri, hataları veya uyarıları görüntülemek için günlük kayıt günlüklerini kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing loggers
- MSBuild, logging
- logging [MSBuild]
ms.assetid: fa34810d-185a-4d22-92bd-9852915e5f1d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 7ac40c5ab5f836fee3b0f98a0339138fbf02eb0fe0ce6e64f552f9c8e5c86a18
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121428646"
---
# <a name="build-loggers"></a>Günlükçüleri derleme

Günlükler, derlemenizin çıkışını özelleştirmenizi ve belirli derleme olaylarına yanıt olarak iletileri, hataları veya uyarıları görüntülemenizi sağlar. Her günlükleyici,Microsoft.Build.Framework.dllderlemesinde tanımlanan arabirimini uygulayan bir .NET <xref:Microsoft.Build.Framework.ILogger> *sınıfı olarak* uygulanır.

Günlükleyiciyi uygulamak için kullanabileceğiniz iki yaklaşım vardır:

- Arabirimi doğrudan <xref:Microsoft.Build.Framework.ILogger> uygulama.
- Sınıfını, derleme derlemesinde tanımlanan <xref:Microsoft.Build.Utilities.Logger> yardımcı sınıfından *Microsoft.Build.Utilities.dll* türetin. <xref:Microsoft.Build.Utilities.Logger> , bazı <xref:Microsoft.Build.Framework.ILogger> üyelerin varsayılan uygulamasını uygulayan ve <xref:Microsoft.Build.Framework.ILogger> sağlar.

  Bu konu başlığında, 'den türetilen ve belirli derleme olaylarına yanıt olarak konsolda iletileri görüntüleyen basit bir <xref:Microsoft.Build.Utilities.Logger> günlükleyicinin nasıl yaz olduğu açıklanmıştır.

## <a name="register-for-events"></a>Olaylara kaydolma

Günlükleyicinin amacı, derleme altyapısı tarafından bildirilen derleme ilerleme durumu hakkında bilgi toplamak ve ardından bu bilgileri yararlı bir şekilde rapor etmektir. Tüm günlükleyicilerin, <xref:Microsoft.Build.Utilities.Logger.Initialize%2A> günlükleyicinin olaylara kaydeden yöntemini geçersiz kılması gerekir. Bu örnekte, günlükleyici , ve olayları <xref:Microsoft.Build.Framework.IEventSource.TargetStarted> <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> için <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> kaydolr.

:::code language="csharp" source="../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleConsoleLogger/CS/msbuild_SimpleConsoleLogger.cs" id="Snippet2":::

## <a name="respond-to-events"></a>Olaylara yanıt verme

Günlükleyici belirli olaylar için kaydedilene göre, oluştuğunda bu olayları işlemesi gerekir. , <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> ve olayları için günlükleyici yalnızca kısa bir tümcecik ve olaya dahil <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> olan proje dosyasının adını yazar. Günlükleyiciden gelen tüm iletiler konsol penceresine yazılır.

:::code language="csharp" source="../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleConsoleLogger/CS/msbuild_SimpleConsoleLogger.cs" id="Snippet3":::

## <a name="respond-to-logger-verbosity-values"></a>Günlükçer ayrıntılı değerlerine yanıt verme

Bazı durumlarda, **yalnızca -verbosity** anahtarı belirli bir değer MSBuild.exe bir olaydan bilgileri günlüğe almak istiyor olabilir. Bu örnekte, olay <xref:Microsoft.Build.Framework.IEventSource.TargetStarted> işleyicisi yalnızca <xref:Microsoft.Build.Utilities.Logger.Verbosity%2A> **-verbosity** anahtarı tarafından ayarlanmış olan özelliği değerine eşitse bir ileti günlüğe <xref:Microsoft.Build.Framework.LoggerVerbosity> `Detailed` kaydeder.

:::code language="csharp" source="../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleConsoleLogger/CS/msbuild_SimpleConsoleLogger.cs" id="Snippet4":::

## <a name="specify-a-logger"></a>Günlükleyici belirtme

Günlükleyici bir derlemede derlenmiş olduktan sonra, derlemeler MSBuild günlükleyiciyi kullanmalarını söylemeniz gerekir. Bu, ile **-logger anahtarı** kullanılarak *MSBuild.exe.* için kullanılabilen anahtarlar hakkında daha fazla bilgi *MSBuild.exe* bkz. Komut [satırı başvurusu.](../msbuild/msbuild-command-line-reference.md)

Aşağıdaki komut *satırı, MyProject.csproj* projesini derlemek için *SimpleLogger.dll.* **-nologo** anahtarı başlık ve telif hakkı iletiyi gizler ve **-noconsolelogger** anahtarı, konsol günlük MSBuild devre dışı bırakmaktadır.

```cmd
MSBuild -nologo -noconsolelogger -logger:SimpleLogger.dll
```

Aşağıdaki komut satırı, projeyi aynı günlükleyici ile, ancak düzeyiyle `Verbosity` derleme. `Detailed`

```cmd
MSBuild -nologo -noconsolelogger -logger:SimpleLogger.dll -verbosity:Detailed
```

## <a name="example-1"></a>Örnek 1

### <a name="description"></a>Açıklama

Aşağıdaki örnek günlükleyicinin tam kodunu içerir.

### <a name="code"></a>Kod

:::code language="csharp" source="../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleConsoleLogger/CS/msbuild_SimpleConsoleLogger.cs" id="Snippet1":::

## <a name="example-2"></a>Örnek 2

### <a name="description"></a>Açıklama

Aşağıdaki örnek, günlüğü konsol penceresinde görüntülemek yerine bir dosyaya yazan günlükleyicinin nasıl uygulandığını gösterir.

### <a name="code"></a>Kod

:::code language="csharp" source="../snippets/csharp/VS_Snippets_Misc/msbuild_BasicLogger/CS/msbuild_BasicLogger.cs" id="Snippet1":::

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme günlüklerini alma](../msbuild/obtaining-build-logs-with-msbuild.md)
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
