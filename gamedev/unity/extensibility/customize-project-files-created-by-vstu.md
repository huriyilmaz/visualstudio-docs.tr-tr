---
title: VSTU Project Oluşturulan Dosyaları Özelleştirme | Microsoft Docs
description: Unity için Visual Studio Araçları (VSTU) tarafından oluşturulan proje dosyalarını özelleştirmeyi öğrenin. C# kod örneğini gözden geçirme.
ms.date: 04/19/2021
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: conceptual
ms.assetid: 60b8cc1d-cacc-404d-b768-77e81bc354f8
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: db8d09f5b181796b3cb333963bec2772394728ff
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129972810"
---
# <a name="customize-project-files-created-by-vstu"></a>VSTU tarafından oluşturulan proje dosyalarını özelleştirme
Unity, proje dosyası oluşturma sırasında geri çağırmalar sağlar. Projeyi `OnGeneratedSlnSolution` `OnGeneratedCSProject` veya çözüm dosyasını her [`AssetPostprocessor`](https://docs.unity3d.com/ScriptReference/AssetPostprocessor.html) yeniden edere değiştirmek için ve yöntemlerini kullanın.

## <a name="demonstrates"></a>Gösteriler
Unity için Visual Studio Araçları tarafından Visual Studio proje dosyalarını Unity için Visual Studio Araçları.

## <a name="example"></a>Örnek

```csharp
using System;
using UnityEditor;
using UnityEngine;

public class ProjectFilePostprocessor : AssetPostprocessor
{
  public static string OnGeneratedSlnSolution(string path, string content)
  {
    // TODO: process solution content
    return content;
  }

  public static string OnGeneratedCSProject(string path, string content)
  {
    // TODO: process project content
    return content;
  }
}
```
