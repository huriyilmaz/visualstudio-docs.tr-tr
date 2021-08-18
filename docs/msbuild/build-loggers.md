---
title: Günlükçüler oluşturun | Microsoft Docs
description: derleme çıktısını yönetmek ve özelleştirmek ve belirli derleme olaylarına yanıt olarak iletileri, hataları veya uyarıları göstermek için MSBuild günlükçüleri kullanın.
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
ms.openlocfilehash: a2ae63b8d658eff88a8da22123ca6aba40cf676a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122085227"
---
# <a name="build-loggers"></a>Günlükçüleri derleme

Günlükçüler, belirli derleme olaylarına yanıt olarak, derlemenize ait çıktıyı özelleştirmek ve iletileri, hataları veya uyarıları göstermek için bir yol sağlar. Her Günlükçü, <xref:Microsoft.Build.Framework.ILogger> *Microsoft.Build.Framework.dll* derlemesinde tanımlanan arabirimi uygulayan bir .NET sınıfı olarak uygulanır.

Günlükçü uygularken kullanabileceğiniz iki yaklaşım vardır:

- <xref:Microsoft.Build.Framework.ILogger>Arabirimi doğrudan uygulayın.
- <xref:Microsoft.Build.Utilities.Logger> *Microsoft.Build.Utilities.dll* derlemesinde tanımlanan yardımcı sınıfından sınıfınızı türetirsiniz. <xref:Microsoft.Build.Utilities.Logger><xref:Microsoft.Build.Framework.ILogger>, bazı üyelerin varsayılan uygulamalarını uygular ve sağlar <xref:Microsoft.Build.Framework.ILogger> .

  Bu konuda <xref:Microsoft.Build.Utilities.Logger> , belirli derleme olaylarına yanıt olarak, ' dan türetilen basit bir günlükçü yazma ve konsolundaki iletileri görüntüleme açıklanmaktadır.

## <a name="register-for-events"></a>Olaylara kaydolun

Günlükçü amacı, derleme altyapısı tarafından bildirildiği için derleme ilerlemesi hakkında bilgi toplamaktır ve daha sonra bu bilgileri faydalı bir şekilde bildirir. Tüm Günlükçüler <xref:Microsoft.Build.Utilities.Logger.Initialize%2A> , günlükçü 'nin olaylar için kaydettiği yöntemi geçersiz kılmalıdır. Bu örnekte, günlükçü <xref:Microsoft.Build.Framework.IEventSource.TargetStarted> ,, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> ve olaylarını kaydeder <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> .

:::code language="csharp" source="../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleConsoleLogger/CS/msbuild_SimpleConsoleLogger.cs" id="Snippet2":::

## <a name="respond-to-events"></a>Olaylara yanıt verme

Günlükçüler belirli olaylara kaydoldığına göre, bu olayları gerçekleştiğinde işlemek gerekir. <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>Ve olayları için, <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> günlükçü yalnızca kısa bir ifade ve olaya dahil olan proje dosyasının adını yazar. Günlükçü 'deki tüm iletiler konsol penceresine yazılır.

:::code language="csharp" source="../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleConsoleLogger/CS/msbuild_SimpleConsoleLogger.cs" id="Snippet3":::

## <a name="respond-to-logger-verbosity-values"></a>Günlükçü ayrıntı değerlerine yanıt verme

Bazı durumlarda, MSBuild.exe **ayrıntı** düzeyi anahtarı belirli bir değer içeriyorsa yalnızca bir olaydan bilgileri günlüğe kaydetmek isteyebilirsiniz. Bu örnekte, <xref:Microsoft.Build.Framework.IEventSource.TargetStarted> olay işleyicisi yalnızca <xref:Microsoft.Build.Utilities.Logger.Verbosity%2A> **-ayrıntı** anahtarı tarafından ayarlanan özellik öğesine eşitse bir iletiyi günlüğe kaydeder <xref:Microsoft.Build.Framework.LoggerVerbosity> `Detailed` .

:::code language="csharp" source="../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleConsoleLogger/CS/msbuild_SimpleConsoleLogger.cs" id="Snippet4":::

## <a name="specify-a-logger"></a>Günlükçü belirtin

günlükçü bir derlemeye derlendikten sonra, derlemeler sırasında bu günlükçüsü kullanmak için MSBuild söylemeniz gerekir. Bu işlem, *MSBuild.exe* ile **-günlükçü** anahtarı kullanılarak yapılır. *MSBuild.exe* için kullanılabilir anahtarlar hakkında daha fazla bilgi için bkz. [komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md).

Aşağıdaki komut satırı *MyProject. csproj* projesini oluşturur ve *SimpleLogger.dll* uygulanan günlükçü sınıfını kullanır. **-nologo** anahtarı başlık ve telif hakkı iletisini gizler ve **-noconsolegünlükçü** anahtarı varsayılan MSBuild konsol günlükçüsü 'yi devre dışı bırakır.

```cmd
MSBuild -nologo -noconsolelogger -logger:SimpleLogger.dll
```

Aşağıdaki komut satırı, projeyi aynı günlükçü ile, ancak `Verbosity` düzeyiyle oluşturur `Detailed` .

```cmd
MSBuild -nologo -noconsolelogger -logger:SimpleLogger.dll -verbosity:Detailed
```

## <a name="example-1"></a>Örnek 1

### <a name="description"></a>Açıklama

Aşağıdaki örnek, günlükçü için kodun tamamını içerir.

### <a name="code"></a>Kod

:::code language="csharp" source="../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleConsoleLogger/CS/msbuild_SimpleConsoleLogger.cs" id="Snippet1":::

## <a name="example-2"></a>Örnek 2

### <a name="description"></a>Açıklama

Aşağıdaki örnek, günlüğü konsol penceresinde görüntülemek yerine bir dosyaya yazan bir günlükçü nasıl uygulanacağını gösterir.

### <a name="code"></a>Kod

:::code language="csharp" source="../snippets/csharp/VS_Snippets_Misc/msbuild_BasicLogger/CS/msbuild_BasicLogger.cs" id="Snippet1":::

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme günlüklerini al](../msbuild/obtaining-build-logs-with-msbuild.md)
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
