---
title: T4 İçe Aktarma Yönergesi
ms.date: 11/04/2016
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 74181ea3bb086688893749850adb697c75b6eac1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72606437"
---
# <a name="t4-import-directive"></a>T4 İçe Aktarma Yönergesi

Visual Studio T4 metin şablonunun kod blokları ' nda, `import` yönergesi, başka bir ad alanındaki öğelere tam nitelikli bir ad sağlamadan başvurabileceğiniz bir öğe sağlar. Bu, [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)] içinde C# veya `imports` `using` eşdeğerdir.

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

## <a name="see-also"></a>Ayrıca Bkz.

- [T4 Derleme Yönergesi](../modeling/t4-assembly-directive.md)