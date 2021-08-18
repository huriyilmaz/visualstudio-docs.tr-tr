---
title: Metin Şablonundan Visual Studio'ya veya diğer Ana Bilgisayarlara Erişme
description: Şablonu yürüten konak tarafından ortaya çıkar bir metin şablonunda yöntemleri ve özellikleri nasıl kullanabileceğiniz hakkında bilgi.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 5a812279046bf1b2eb987719762098697ddd8eb1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122055724"
---
# <a name="access-visual-studio-or-other-hosts-from-a-text-template"></a>Metin Visual Studio veya diğer konaklara erişme

Bir metin şablonunda, şablonu yürüten konak tarafından ortaya çıkar kullanılan yöntemleri ve özellikleri kullanabilirsiniz. Visual Studio bir konak örneğidir.

> [!NOTE]
> Konak yöntemlerini ve özelliklerini normal metin şablonlarında kullanabilirsiniz, ancak önceden *işlenmemiş metin şablonlarında* kullanabilirsiniz.

## <a name="obtain-access-to-the-host"></a>Ana bilgisayar erişimi alma

Ana bilgisayar erişmek için `hostspecific="true"` yönergesinde `template` ayarlayın. Artık `this.Host` [ITextTemplatingEngineHost türüne sahip olan kullanabilirsiniz.](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) türü, örneğin dosya adlarını ve günlük hatalarını çözmek için kullanabileceğiniz üyelere sahip.

### <a name="resolve-file-names"></a>Dosya Adlarını Çözümleme

Metin şablonuna göre bir dosyanın tam yolunu bulmak için `this.Host.ResolvePath()` kullanın.

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

### <a name="display-error-messages"></a>Hata İletilerini Görüntüleme

Bu örnek, şablonu dönüştüren iletileri günlüğe kaydeder. Ana bilgisayar Visual Studio, hatalar Hata Listesine **eklenir.**

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

## <a name="use-the-visual-studio-api"></a>Visual Studio API'sini kullanma

Visual Studio'da bir metin şablonu Visual Studio, Visual Studio paketleri veya uzantıları tarafından sağlanan `this.Host` hizmetlere erişmek için kullanabilirsiniz.

hostspecific="true" olarak ayarlayın ve olarak `this.Host` <xref:System.IServiceProvider> ayarlayın.

Bu örnek, Visual Studio API'sini <xref:EnvDTE.DTE> alır:

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

özniteliğini `hostspecific="trueFromBase"` de kullansanız `inherits` ve belirten bir şablondan devralıyorsanız `hostspecific="true"` belirtin. Yoksa, özelliğin iki kez bildirildi hatasıyla `Host` ilgili bir derleyici uyarısıyla karşılayabilirsiniz.
