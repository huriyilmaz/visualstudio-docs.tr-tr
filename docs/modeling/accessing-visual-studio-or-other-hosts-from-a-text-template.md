---
title: Metin Şablonundan Visual Studio'ya veya diğer Ana Bilgisayarlara Erişme
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 752b9d9e69eee26f267927f03c4b83c68740100b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652371"
---
# <a name="access-visual-studio-or-other-hosts-from-a-text-template"></a>Metin şablonundan Visual Studio 'Ya veya diğer konaklara erişme

Bir metin şablonunda, şablonu yürüten ana bilgisayar tarafından sunulan yöntemleri ve özellikleri kullanabilirsiniz. Visual Studio, ana bilgisayar örneğidir.

> [!NOTE]
> Ana bilgisayar yöntemlerini ve özelliklerini normal metin şablonlarında kullanabilirsiniz, ancak *önceden işlenmiş* metin şablonlarında kullanamazsınız.

## <a name="obtain-access-to-the-host"></a>Konağa erişim elde edin

Konağa erişmek için `template` yönergesindeki `hostspecific="true"` ayarlayın. Artık [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))türüne sahip `this.Host` kullanabilirsiniz. [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) türü, dosya adlarını çözümlemek için kullanabileceğiniz üyelere ve örneğin günlük hatalarına sahiptir.

### <a name="resolve-file-names"></a>Dosya adlarını çözümle

Metin şablonuyla ilişkili bir dosyanın tam yolunu bulmak için `this.Host.ResolvePath()` kullanın.

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

### <a name="display-error-messages"></a>Hata Iletilerini görüntüle

Bu örnek, şablonu dönüştürdüğünüzde iletileri günlüğe kaydeder. Konak Visual Studio ise, hatalar **hata listesi**eklenir.

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

## <a name="use-the-visual-studio-api"></a>Visual Studio API 'sini kullanma

Visual Studio 'da bir metin şablonu yürütüyorsanız, Visual Studio tarafından sunulan hizmetlere ve yüklenen paketlere ya da uzantılara erişmek için `this.Host` kullanabilirsiniz.

Hostspecific = "true" ve cast `this.Host` <xref:System.IServiceProvider> olarak ayarlayın.

Bu örnek, bir hizmet olarak <xref:EnvDTE.DTE> Visual Studio API 'sini alır:

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

## <a name="use-hostspecific-with-template-inheritance"></a>Şablon devralma ile hostSpecific kullanma

@No__t_1 özniteliğini de kullanıyorsanız ve `hostspecific="true"` belirten bir şablondan kalýtýmla alıyorsanız `hostspecific="trueFromBase"` belirtin. Bunu yapmazsanız, özelliğin `Host` iki kez bildirildiği bir derleyici uyarısı alabilirsiniz.