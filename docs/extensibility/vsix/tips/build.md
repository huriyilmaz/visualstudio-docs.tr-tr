---
title: Derlemelerle çalışma
description: İpuçları ile çalışma hakkında daha fazla şey.
ms.date: 12/01/2021
ms.topic: conceptual
author: madskristensen
ms.author: madsk
manager: pchapman
ms.prod: visual-studio-windows
ms.technology: vs-ide-sdk
ms.custom: cookbook
ms.openlocfilehash: f530c1ec5cbe10152f6877877f8886a98e4892d9
ms.sourcegitcommit: a149b3a034bb555ad217656c0ec8bc1672b1e215
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "133516590"
---
# <a name="working-with-builds-in-visual-studio-extensions"></a>Uzantılarda derlemelerle Visual Studio çalışma 

Derlemelerle çalışmanın farklı yollarına sahip küçük kod örnekleri koleksiyonu burada vetir.

## <a name="build-solution"></a>Çözüm oluşturma
Çözümün tamamını oluşturmak için yöntemini `BuildAsync()` çağırma.

```csharp
bool buildStarted = await VS.Build.BuildSolutionAsync(BuildAction.Build);
```

## <a name="build-project"></a>Proje oluşturma
Herhangi bir projeyi yöntemine aktararak derlemek için kullanabilirsiniz.

```csharp
Project project = await VS.Solutions.GetActiveProjectAsync();
await project.BuildAsync(BuildAction.Rebuild);
```

## <a name="set-build-property"></a>Derleme özelliğini ayarlama
Proje üzerinde derleme özelliğini ayarlamayı gösterir.

```csharp
Project project = await VS.Solutions.GetActiveProjectAsync();
bool succeeded = await project.TrySetAttributeAsync("propertyName", "value");
```

## <a name="get-build-property"></a>Derleme özelliğini al
Herhangi bir projenin veya proje öğesinin derleme özelliğinin nasıl elde etmek olduğunu gösterir.

```csharp
Project item = await VS.Solutions.GetActiveProjectAsync();
string value = await item.GetAttributeAsync("propertyName");
```
