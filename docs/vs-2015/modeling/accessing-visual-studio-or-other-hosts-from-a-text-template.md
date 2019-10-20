---
title: Metin şablonundan Visual Studio 2015 veya diğer konaklara erişme | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: a68886da-7416-4785-8145-3796bb382cba
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0e8cedc66d6b52f80239364a3e51b73e93a69aa4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655335"
---
# <a name="accessing-visual-studio-or-other-hosts-from-a-text-template"></a>Metin Şablonundan Visual Studio'ya veya diğer Ana Bilgisayarlara Erişme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir metin şablonunda, şablonu yürüten ana bilgisayar tarafından kullanıma sunulan yöntemleri ve özellikleri (örneğin, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]) kullanabilirsiniz.

 Bu, önceden işlenmemiş metin şablonları için normal metin şablonları için geçerlidir.

## <a name="obtaining-access-to-the-host"></a>Konağa erişim sağlama

@No__t_1 yönergesinde `hostspecific="true"` ayarlayın. Bu, [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))türünde `this.Host` kullanmanıza olanak sağlar. Bu tür, örneğin, dosya adlarını çözümlemek ve hataları günlüğe kaydetmek için kullanabileceğiniz üyelere sahiptir.

### <a name="resolving-file-names"></a>Dosya adlarını çözme
 Metin şablonuyla ilişkili bir dosyanın tam yolunu bulmak için bunu kullanın. Host. ResolvePath ().

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="System.IO" #>
<#
 // Find a path within the same project as the text template:
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));
#>
Content of myFile is:
<#= myFile #>

```

### <a name="displaying-error-messages"></a>Hata Iletilerini görüntüleme
 Bu örnek, şablonu dönüştürdüğünüzde iletileri günlüğe kaydeder. Ana bilgisayar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], hata penceresine eklenir.

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="System.CodeDom.Compiler" #>
<#
  string message = "test message";
  this.Host.LogErrors(new CompilerErrorCollection()
    { new CompilerError(
       this.Host.TemplateFile, // Identify the source of the error.
       0, 0, "0",   // Line, column, error ID.
       message) }); // Message displayed in error window.
#>

```

## <a name="using-the-visual-studio-api"></a>Visual Studio API 'sini kullanma
 @No__t_0 içinde bir metin şablonu yürütüyorsunuz, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ve yüklenen paketler ya da uzantılar tarafından sunulan hizmetlere erişmek için `this.Host` kullanabilirsiniz.

 Hostspecific = "true" ve cast `this.Host` <xref:System.IServiceProvider> olarak ayarlayın.

 Bu örnek, hizmet olarak <xref:EnvDTE.DTE> [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] API 'sini alır:

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="EnvDTE" #>
<#
 IServiceProvider serviceProvider = (IServiceProvider)this.Host;
 DTE dte = serviceProvider.GetService(typeof(DTE)) as DTE;
#>
Number of projects in this solution: <#=  dte.Solution.Projects.Count #>

```

## <a name="using-hostspecific-with-template-inheritance"></a>Şablon devralma ile hostSpecific kullanma
 @No__t_1 özniteliğini de kullanıyorsanız ve `hostspecific="true"` belirten bir şablondan kalýtýmla alıyorsanız `hostspecific="trueFromBase"` belirtin. Bu, özelliğin `Host` iki kez bildirildiği etkiye yönelik bir derleyici uyarısını önler.
