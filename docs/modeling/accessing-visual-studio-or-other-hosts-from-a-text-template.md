---
title: Metin Şablonundan Visual Studio'ya veya diğer Ana Bilgisayarlara Erişme
description: Bir şablonu yürüten ana bilgisayar tarafından açığa çıkarılan bir metin şablonunda yöntemleri ve özellikleri nasıl kullanabileceğinizi öğrenin.
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
ms.openlocfilehash: 355ffad6f00929fe3413af64fe94c8eab5427e7c1d33191586d66dc2cdd42403
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121386049"
---
# <a name="access-visual-studio-or-other-hosts-from-a-text-template"></a>metin şablonundan Visual Studio veya diğer konaklara erişim

Bir metin şablonunda, şablonu yürüten ana bilgisayar tarafından sunulan yöntemleri ve özellikleri kullanabilirsiniz. Visual Studio ana bilgisayar örneğidir.

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

Bu örnek, şablonu dönüştürdüğünüzde iletileri günlüğe kaydeder. ana bilgisayar Visual Studio, hatalar **Hata Listesi** eklenir.

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

## <a name="use-the-visual-studio-api"></a>Visual Studio apı 'sini kullanma

Visual Studio içinde bir metin şablonu yürütüyorsanız, `this.Host` Visual Studio tarafından sunulan hizmetlere ve yüklenen paketlere ya da uzantılara erişmek için ' yi kullanabilirsiniz.

Hostspecific = "true" olarak ayarlayın ve ' a atayın `this.Host` <xref:System.IServiceProvider> .

bu örnek, hizmet olarak Visual Studio apı 'sini alır <xref:EnvDTE.DTE> :

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
