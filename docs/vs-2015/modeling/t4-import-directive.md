---
title: T4 Içeri aktarma yönergesi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 713ca975-b9aa-4210-bf6d-b7660f5b193b
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c4a931ca05f8b12175deded8b316d0177d8f8c74
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72661813"
---
# <a name="t4-import-directive"></a>T4 İçe Aktarma Yönergesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] T4 metin şablonunun kod blokları içinde, `import` yönerge, tam olarak nitelenmiş bir ad sağlamadan başka bir ad alanındaki öğelere başvurabileceğiniz bir öğe sağlar. Bu, `using` C# veya içinde ' ın eşdeğeridir `imports` [!INCLUDE[vb_current_short](../includes/vb-current-short-md.md)] .

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

- DSL'nizin ad alanı

## <a name="see-also"></a>Ayrıca Bkz.
 [T4 Derleme Yönergesi](../modeling/t4-assembly-directive.md)
