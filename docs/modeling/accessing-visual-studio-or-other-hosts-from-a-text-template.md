---
title: Metin Şablonundan Visual Studio'ya veya diğer Ana Bilgisayarlara Erişme
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 068de3c14240bc7e13be0e2e564c2c4e6034f987
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85531423"
---
# <a name="access-visual-studio-or-other-hosts-from-a-text-template"></a>Metin şablonundan Visual Studio 'Ya veya diğer konaklara erişme

Bir metin şablonunda, şablonu yürüten ana bilgisayar tarafından sunulan yöntemleri ve özellikleri kullanabilirsiniz. Visual Studio, ana bilgisayar örneğidir.

> [!NOTE]
> Ana bilgisayar yöntemlerini ve özelliklerini normal metin şablonlarında kullanabilirsiniz, ancak *önceden işlenmiş* metin şablonlarında kullanamazsınız.

## <a name="obtain-access-to-the-host"></a>Konağa erişim elde edin

Konağa erişmek için `hostspecific="true"` `template` yönergesinde ayarlayın. Artık `this.Host` [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))türünde bir kullanabilirsiniz. [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) türü, dosya adlarını çözümlemek için kullanabileceğiniz üyelere ve örneğin günlük hatalarına sahiptir.

### <a name="resolve-file-names"></a>Dosya adlarını çözümle

Metin şablonuyla ilişkili bir dosyanın tam yolunu bulmak için kullanın `this.Host.ResolvePath()` .

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

Visual Studio 'da bir metin şablonu yürütüyorsanız, `this.Host` Visual Studio tarafından sunulan hizmetlere ve yüklenen paketlere ya da uzantılara erişmek için ' yi kullanabilirsiniz.

Hostspecific = "true" olarak ayarlayın ve ' a atayın `this.Host` <xref:System.IServiceProvider> .

Bu örnek, bir hizmet olarak Visual Studio API 'sini alır <xref:EnvDTE.DTE> :

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

`hostspecific="trueFromBase"`Özniteliğini de kullanıp kullanacağınızı `inherits` ve öğesini belirten bir şablondan devralmayı belirtin `hostspecific="true"` . Bunu yapmazsanız, özelliğin iki kez bildirildiği konusunda bir derleyici uyarısı alabilirsiniz `Host` .
