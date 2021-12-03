---
title: Çözümlerle çalışma
description: çözümlerle çalışmak için İpuçları.
ms.date: 12/01/2021
ms.topic: conceptual
author: madskristensen
ms.author: madsk
manager: pchapman
ms.prod: visual-studio-windows
ms.technology: vs-ide-sdk
ms.custom: cookbook
ms.openlocfilehash: 1e485fbc60ae0ff2d2c3e1e63a0e87caef482138
ms.sourcegitcommit: a149b3a034bb555ad217656c0ec8bc1672b1e215
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "133516675"
---
# <a name="working-with-solutions-in-visual-studio-extensions"></a>Visual Studio uzantılarında çözümlerle çalışma

Aşağıda, çözümlerle çalışmanın farklı yollarla küçük kod örnekleri koleksiyonu verilmiştir.

## <a name="solution-events"></a>Çözüm olayları
Herhangi bir çözüm olayını dinleyin.

```csharp
VS.Events.SolutionEvents.OnAfterOpenProject += OnAfterOpenProject;

...

private void OnAfterOpenProject(Project obj)
{
    // Handle the event
}
```

## <a name="is-a-solution-open"></a>Bir çözüm açık mı?
Bir çözümün açık mı yoksa açılıyor mi olduğunu denetleyin.

```csharp

bool isOpen = await VS.Solutions.IsOpenAsync();
bool isOpening = await VS.Solutions.IsOpeningAsync();
```

## <a name="get-all-projects-in-solution"></a>Çözümdeki tüm projeleri al
Çözümdeki tüm projelerin bir listesini alın.

```csharp
var projects = await VS.Solutions.GetAllProjectsAsync();
```
