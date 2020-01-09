---
title: Metin Şablonundan Visual Studio'ya veya diğer Ana Bilgisayarlara Erişme
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cd69ae5864df9cbddd204c45975736fc4aae49e5
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597262"
---
# <a name="access-visual-studio-or-other-hosts-from-a-text-template"></a>Metin şablonundan Visual Studio 'Ya veya diğer konaklara erişme

Metin şablonunda, yöntemleri ve şablonu yürütür ana bilgisayar tarafından gösterilen özelliklerin kullanabilirsiniz. Visual Studio, bir konak örneğidir.

> [!NOTE]
> Konak yöntemleri ve özellikleri normal metin şablonlarında kullanabilirsiniz, ancak değil *önceden işlenmiş* metin şablonları.

## <a name="obtain-access-to-the-host"></a>Konak erişim sağlamak

Konak erişmek için `hostspecific="true"` içinde `template` yönergesi. Artık [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))türüne sahip `this.Host`kullanabilirsiniz. [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) türü, dosya adlarını çözümlemek için kullanabileceğiniz üyelere ve örneğin günlük hatalarına sahiptir.

### <a name="resolve-file-names"></a>Dosya adlarını çözümleme

Metin şablonu göreli bir dosyanın tam yolunu bulmak için kullanın `this.Host.ResolvePath()`.

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

### <a name="display-error-messages"></a>Hata iletilerini görüntüleme

Bu örnekte, şablon dönüştürdüğünüzde iletileri günlüğe kaydeder. Visual Studio ana bilgisayar ise hataları eklenen **hata listesi**.

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

## <a name="use-the-visual-studio-api"></a>Visual Studio API kullanın

Visual Studio'da bir metin şablonu yürütme, kullanabileceğiniz `this.Host` Visual Studio ve paketleri veya yüklü uzantılar tarafından sağlanan Erişim Hizmetleri için.

Ayarlama hostspecific = "true" ve dönüştürme `this.Host` için <xref:System.IServiceProvider>.

Bu örnek, Visual Studio API alır <xref:EnvDTE.DTE>, hizmet olarak:

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

## <a name="use-hostspecific-with-template-inheritance"></a>Şablon kalıtım hostSpecific kullanın

Belirtin `hostspecific="trueFromBase"` da kullanıyorsanız `inherits` özniteliği ve belirten bir şablondan devralıyorsanız `hostspecific="true"`. Aksi takdirde, derleyici, uyarısı özelliği alabilirsiniz `Host` iki kez bildirilmiş.
