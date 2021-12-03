---
title: Projelerle çalışma
description: İpuçları ile çalışma hakkında daha fazla şey.
ms.date: 12/01/2021
ms.topic: conceptual
author: madskristensen
ms.author: madsk
manager: pchapman
ms.prod: visual-studio-windows
ms.technology: vs-ide-sdk
ms.custom: cookbook
ms.openlocfilehash: ba6a40469258f733cbf4f847de0d3a39bcfdde27
ms.sourcegitcommit: a149b3a034bb555ad217656c0ec8bc1672b1e215
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "133516680"
---
# <a name="working-with-projects-in-visual-studio-extensions"></a>Uzantılarda projelerle Visual Studio çalışma

Projelerle çalışmanın farklı yollarına yönelik küçük kod örneklerinin bir koleksiyonu burada ver.

## <a name="get-project-from-contained-file"></a>Projeyi içeren dosyadan al
Dosyalar bu şekilde projeden elde etmek için kullanılır.

```csharp
 string fileName = "c:\\file\\in\\project.txt";
 PhysicalFile item = await PhysicalFile.FromFileAsync(fileName);
 Project project = item.ContainingProject;
```

## <a name="add-files-to-project"></a>Projeye dosya ekleme
Diskten projeye dosya eklemek için aşağıdakiler kullanılır.

```csharp
Project project = await VS.Solutions.GetActiveProjectAsync();

var file1 = "c:\\file\\in\\project\\1.txt";
var file2 = "c:\\file\\in\\project\\2.txt";
var file3 = "c:\\file\\in\\project\\3.txt";

await project.AddExistingFilesAsync(file1, file2, file3);
```

## <a name="find-type-of-project"></a>Proje türünü bulma
Ne tür bir projeyle karşı karşıya olduğunu bulun.

```csharp
bool isCsharp = await project.IsKindAsync(ProjectTypes.CSHARP);
```
