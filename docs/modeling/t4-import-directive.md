---
title: T4 İçe Aktarma Yönergesi
description: Visual Studio T4 metin şablonunda içeri aktarma yönergesinin, tam nitelikli ad sağlamadan başka bir ad alanındaki öğelere başvurabileceğiniz hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d0d441ec5a62dfa5266a17a06ac8fe33941136c6
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386325"
---
# <a name="t4-import-directive"></a>T4 İçe Aktarma Yönergesi

Visual Studio T4 metin şablonunun kod blokları ' nda, yönerge, bir `import` diğer ad alanındaki öğelere tam nitelikli bir ad sağlamadan başvurabileceğiniz bir öğe sağlar. Bu, `using` C# veya içinde ' ın eşdeğeridir `imports` [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)] .

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
