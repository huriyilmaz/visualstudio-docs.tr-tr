---
title: Günlükçüler oluşturun | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing loggers
- MSBuild, logging
- logging [MSBuild]
ms.assetid: fa34810d-185a-4d22-92bd-9852915e5f1d
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2908c8217070196de1b2d3cd4f1c5f8d8f2868a5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160437"
---
# <a name="build-loggers"></a>Günlükçüleri Derleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Günlükçüler, belirli derleme olaylarına yanıt olarak, derlemenize ait çıktıyı özelleştirmek ve iletileri, hataları veya uyarıları göstermek için bir yol sağlar. Her Günlükçü, <xref:Microsoft.Build.Framework.ILogger> Microsoft.Build.Framework.dll derlemesinde tanımlanan arabirimi uygulayan bir .NET sınıfı olarak uygulanır.  
  
 Günlükçü uygularken kullanabileceğiniz iki yaklaşım vardır:  
  
- <xref:Microsoft.Build.Framework.ILogger>Arabirimi doğrudan uygulayın.  
  
- Microsoft.Build.Utilities.dll derlemesinde tanımlanan yardımcı sınıfından sınıfınızı türetirsiniz <xref:Microsoft.Build.Utilities.Logger> . <xref:Microsoft.Build.Utilities.Logger><xref:Microsoft.Build.Framework.ILogger>, bazı üyelerin varsayılan uygulamalarını uygular ve sağlar <xref:Microsoft.Build.Framework.ILogger> .  
  
  Bu konuda <xref:Microsoft.Build.Utilities.Logger> , belirli derleme olaylarına yanıt olarak, ' dan türetilen basit bir günlükçü yazma ve konsolundaki iletileri görüntüleme açıklanmaktadır.  
  
## <a name="registering-for-events"></a>Olaylara kaydolma  
 Günlükçü amacı, derleme altyapısı tarafından bildirildiği için derleme ilerlemesi hakkında bilgi toplamaktır ve daha sonra bu bilgileri faydalı bir şekilde bildirir. Tüm Günlükçüler <xref:Microsoft.Build.Utilities.Logger.Initialize%2A> , günlükçü 'nin olaylar için kaydettiği yöntemi geçersiz kılmalıdır. Bu örnekte, günlükçü <xref:Microsoft.Build.Framework.IEventSource.TargetStarted> ,, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> ve olaylarını kaydeder <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> .  
  
 [!code-csharp[msbuild_SimpleConsoleLogger#2](../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleConsoleLogger/CS/msbuild_SimpleConsoleLogger.cs#2)]  
  
## <a name="responding-to-events"></a>Olaylara yanıt verme  
 Günlükçüler belirli olaylara kaydoldığına göre, bu olayları gerçekleştiğinde işlemek gerekir. <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>Ve olayları için, <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> günlükçü yalnızca kısa bir ifade ve olaya dahil olan proje dosyasının adını yazar. Günlükçü 'deki tüm iletiler konsol penceresine yazılır.  
  
 [!code-csharp[msbuild_SimpleConsoleLogger#3](../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleConsoleLogger/CS/msbuild_SimpleConsoleLogger.cs#3)]  
  
## <a name="responding-to-logger-verbosity-values"></a>Günlükçü ayrıntı değerlerine yanıt verme  
 Bazı durumlarda, MSBuild.exe **/ayrıntı** anahtarı belirli bir değer içeriyorsa yalnızca bir olaydan bilgileri günlüğe kaydetmek isteyebilirsiniz. Bu örnekte, <xref:Microsoft.Build.Framework.IEventSource.TargetStarted> olay işleyicisi yalnızca <xref:Microsoft.Build.Utilities.Logger.Verbosity%2A> **/ayrıntı** anahtarı tarafından ayarlanan özellik değerine eşitse bir iletiyi günlüğe kaydeder <xref:Microsoft.Build.Framework.LoggerVerbosity> `Detailed` .  
  
 [!code-csharp[msbuild_SimpleConsoleLogger#4](../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleConsoleLogger/CS/msbuild_SimpleConsoleLogger.cs#4)]  
  
## <a name="specifying-a-logger"></a>Günlükçü belirtme  
 Günlükçü bir derlemeye derlendikten sonra, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Bu günlükçüsü derlemeler sırasında kullanmayı söylemeniz gerekir. Bu, MSBuild.exe ile **/günlükçü** anahtarı kullanılarak yapılır. MSBuild.exe için kullanılabilir anahtarlar hakkında daha fazla bilgi için bkz. [komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md).  
  
 Aşağıdaki komut satırı, projeyi oluşturur `MyProject.csproj` ve ' de uygulanan günlükçü sınıfını kullanır `SimpleLogger.dll` . **/Nologo** anahtarı başlık ve telif hakkı iletisini gizler ve **/noconsolegünlükçü** anahtarı varsayılan konsol günlükçüsü 'yi devre dışı bırakır [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] .  
  
```  
MSBuild /nologo /noconsolelogger /logger:SimpleLogger.dll  
```  
  
 Aşağıdaki komut satırı, projeyi aynı günlükçü ile, ancak `Verbosity` düzeyiyle oluşturur `Detailed` .  
  
```  
MSBuild /nologo /noconsolelogger /logger:SimpleLogger.dll /verbosity:Detailed  
```  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Description  
 Aşağıdaki örnek, günlükçü için kodun tamamını içerir.  
  
### <a name="code"></a>Kod  
 [!code-csharp[msbuild_SimpleConsoleLogger#1](../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleConsoleLogger/CS/msbuild_SimpleConsoleLogger.cs#1)]  
  
### <a name="comments"></a>Yorumlar  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Description  
 Aşağıdaki örnek, günlüğü konsol penceresinde görüntülemek yerine bir dosyaya yazan bir günlükçü nasıl uygulanacağını gösterir.  
  
### <a name="code"></a>Kod  
 [!code-csharp[msbuild_BasicLogger#1](../snippets/csharp/VS_Snippets_Misc/msbuild_BasicLogger/CS/msbuild_BasicLogger.cs#1)]  
  
### <a name="comments"></a>Yorumlar  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Derleme günlükleri alma](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [MSBuild kavramları](../msbuild/msbuild-concepts.md)
