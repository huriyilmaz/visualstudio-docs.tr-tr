---
title: Günlükçüler oluşturun | Microsoft Docs
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
ms.openlocfilehash: 2c82b7456e0fc497b753c87f7a4d6808c81d5ab2
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593414"
---
# <a name="build-loggers"></a>Günlükçüler oluşturun
Günlükçüler, belirli derleme olaylarına yanıt olarak, derlemenize ait çıktıyı özelleştirmek ve iletileri, hataları veya uyarıları göstermek için bir yol sağlar. Her Günlükçü, *Microsoft. Build. Framework. dll* derlemesinde tanımlanan <xref:Microsoft.Build.Framework.ILogger> arabirimini uygulayan bir .NET sınıfı olarak uygulanır.

Günlükçü uygularken kullanabileceğiniz iki yaklaşım vardır:

- <xref:Microsoft.Build.Framework.ILogger> arabirimini doğrudan uygulayın.
- *Microsoft. Build. Utilities. dll* derlemesinde tanımlanan <xref:Microsoft.Build.Utilities.Logger>yardımcı sınıfından sınıfınızı türetirsiniz. <xref:Microsoft.Build.Utilities.Logger>, <xref:Microsoft.Build.Framework.ILogger> uygular ve bazı <xref:Microsoft.Build.Framework.ILogger> üyelerin varsayılan uygulamalarını sağlar.

  Bu konu, <xref:Microsoft.Build.Utilities.Logger>türetilen basit bir günlükçü yazmayı açıklar ve belirli derleme olaylarına yanıt olarak konsolda iletileri görüntüler.

## <a name="register-for-events"></a>Olaylara kaydolun
Günlükçü amacı, derleme altyapısı tarafından bildirildiği için derleme ilerlemesi hakkında bilgi toplamaktır ve daha sonra bu bilgileri faydalı bir şekilde bildirir. Tüm Günlükçüler, günlükçü olayları kaydeden <xref:Microsoft.Build.Utilities.Logger.Initialize%2A> yöntemi geçersiz kılmalıdır. Bu örnekte, günlükçü <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>ve <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> olaylarını kaydeder.

[!code-csharp[msbuild_SimpleConsoleLogger#2](../msbuild/codesnippet/CSharp/build-loggers_1.cs)]

## <a name="respond-to-events"></a>Olaylara yanıt verme
Günlükçüler belirli olaylara kaydoldığına göre, bu olayları gerçekleştiğinde işlemek gerekir. <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>ve <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> olaylar için, günlükçü yalnızca kısa bir ifade ve olayda yer alan proje dosyasının adını yazar. Günlükçü 'deki tüm iletiler konsol penceresine yazılır.

[!code-csharp[msbuild_SimpleConsoleLogger#3](../msbuild/codesnippet/CSharp/build-loggers_2.cs)]

## <a name="respond-to-logger-verbosity-values"></a>Günlükçü ayrıntı değerlerine yanıt verme
Bazı durumlarda, MSBuild. exe **-ayrıntı** anahtarı belirli bir değer içeriyorsa yalnızca bir olaydan bilgileri günlüğe kaydetmek isteyebilirsiniz. Bu örnekte, <xref:Microsoft.Build.Framework.IEventSource.TargetStarted> olay işleyicisi yalnızca **-ayrıntı** anahtarı tarafından ayarlanan <xref:Microsoft.Build.Utilities.Logger.Verbosity%2A> özelliği <xref:Microsoft.Build.Framework.LoggerVerbosity>`Detailed`eşitse bir iletiyi günlüğe kaydeder.

[!code-csharp[msbuild_SimpleConsoleLogger#4](../msbuild/codesnippet/CSharp/build-loggers_3.cs)]

## <a name="specify-a-logger"></a>Günlükçü belirtin
Günlükçü bir derlemeye derlendikten sonra, derlemeler sırasında bu günlükçüsü kullanmak için [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] söylemeniz gerekir. Bu işlem, *MSBuild. exe*ile **-günlükçü** anahtarı kullanılarak yapılır. *MSBuild. exe*için kullanılabilen anahtarlar hakkında daha fazla bilgi için bkz. [komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md).

Aşağıdaki komut satırı *MyProject. csproj* projesini oluşturur ve *simplegünlükçü. dll*dosyasında uygulanan günlükçü sınıfını kullanır. **-Nologo** anahtarı başlık ve telif hakkı iletisini gizler ve **-noconsolegünlükçü** anahtarı varsayılan [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] konsol günlükçüsü 'yi devre dışı bırakır.

```cmd
MSBuild -nologo -noconsolelogger -logger:SimpleLogger.dll
```

Aşağıdaki komut satırı, projeyi aynı günlükçü ile, ancak bir `Detailed``Verbosity` düzeyiyle oluşturur.

```cmd
MSBuild -nologo -noconsolelogger -logger:SimpleLogger.dll -verbosity:Detailed
```

## <a name="example"></a>Örnek

### <a name="description"></a>Açıklama
Aşağıdaki örnek, günlükçü için kodun tamamını içerir.

### <a name="code"></a>Kod
[!code-csharp[msbuild_SimpleConsoleLogger#1](../msbuild/codesnippet/CSharp/build-loggers_4.cs)]

## <a name="example"></a>Örnek

### <a name="description"></a>Açıklama
Aşağıdaki örnek, günlüğü konsol penceresinde görüntülemek yerine bir dosyaya yazan bir günlükçü nasıl uygulanacağını gösterir.

### <a name="code"></a>Kod
[!code-csharp[msbuild_BasicLogger#1](../msbuild/codesnippet/CSharp/build-loggers_5.cs)]

## <a name="see-also"></a>Ayrıca bkz.
- [Derleme günlüklerini al](../msbuild/obtaining-build-logs-with-msbuild.md)
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
