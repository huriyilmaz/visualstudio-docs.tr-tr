---
title: T4 İçe Aktarma Yönergesi
description: Visual Studio T4 metin şablonunda içeri aktarma yönergesinin, tam nitelikli ad sağlamadan başka bir ad alanındaki öğelere başvurabileceğiniz hakkında bilgi edinin.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122034012"
---
# <a name="t4-import-directive"></a>T4 İçe Aktarma Yönergesi

Visual Studio T4 metin şablonunun kod blokları içinde, yönerge, bir `import` tam adı sağlamadan başka bir ad alanındaki öğelere başvurgirmenize olanak sağlar. Bu, `using` C# veya içinde ' ın eşdeğeridir `imports` [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)] .

T4 Metin şablonları yazma hakkında genel bir bakış için bkz. [T4 metin şablonu yazma](../modeling/writing-a-t4-text-template.md).

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

- DSL ad alanı

## <a name="see-also"></a>Ayrıca bkz.

- [T4 Derleme Yönergesi](../modeling/t4-assembly-directive.md)
