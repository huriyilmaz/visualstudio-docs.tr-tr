---
title: T4 İçe Aktarma Yönergesi
description: T4 metin Visual Studio şablonunda, içeri aktarma yönergesi ile tam ad sağlamadan başka bir ad alanı öğelerine başvurabilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 3f8f34f45e18000de9cea09c8c58a6e021b52134
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637385"
---
# <a name="t4-import-directive"></a>T4 İçe Aktarma Yönergesi

Visual Studio T4 metin şablonunun kod bloklarında yönergesi, tam ad sağlamadan başka bir ad alanındaki `import` öğelere başvurabilirsiniz. C# veya içinde `using` ile `imports` [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)] eşdeğerdir.

T4 metin şablonları yazmaya genel bir genel bakış için [bkz. T4 Metin Şablonu Yazma.](../modeling/writing-a-t4-text-template.md)

## <a name="using-the-import-directive"></a>İçeri Aktarma Yönergesini Kullanma

```
<#@ import namespace="namespace" #>
```

 Bu örnekte, şablonu kodu, System.IO üyeleri için açık ad alanını atlayabilir:

```
<#@ import namespace="System.IO" #>
<#
   string fileContent = File.ReadAllText("C:\x.txt"); // System.IO.File
#>
The file contains: <#=  fileContent #>
```

## <a name="standard-imports"></a>Standart İçeri Aktarmalar
 Aşağıdaki ad alanı otomatik olarak içeri aktarılır, böylece onun için içeri aktarma yönergesi yazmanıza gerek kalmaz:

- `System`

  Ayrıca, özel yönerge kullanıyorsanız, yönerge işlemcisi bazı ad alanlarını otomatik olarak içeri aktarabilir.

  Örneğin, etki alanına özgü dil (DSL) için şablonlar yazarsanız, aşağıdaki ad alanları için içeri aktarma yönergeleri yazmak gerekmez:

- `Microsoft.VisualStudio.Modeling`

- DSL'nizin ad alanı

## <a name="see-also"></a>Ayrıca bkz.

- [T4 Derleme Yönergesi](../modeling/t4-assembly-directive.md)
