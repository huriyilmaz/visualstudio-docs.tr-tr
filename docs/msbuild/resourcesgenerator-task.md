---
title: ResourcesGenerator Görev | Microsoft Docs
description: Bir MSBuild veya daha fazla kaynağı bir .resources dosyasına eklemek için ResourcesGenerator görevini nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- embedding resources into a .resources file [WPF MSBuild]
- ResourcesGenerator task [WPF MSBuild]
- ResourcesGenerator task [WPF MSBuild], parameters
ms.assetid: e782bbac-9ee6-472b-8171-3ee008c77b4e
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 570563f7d42b2ddf5ed10e9357baa47c48789fee12c4407e45b4a179b5ac1d78
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121355860"
---
# <a name="resourcesgenerator-task"></a>ResourcesGenerator görevi

Görev <xref:Microsoft.Build.Tasks.Windows.ResourcesGenerator> bir *.resources* dosyasına bir veya daha fazla kaynak *(.jpg*, *.ico*, *.bmp*, XAML ikili biçiminde ve diğer uzantı türleri) katıştırır.

## <a name="task-parameters"></a>Görev parametreleri

|Parametre|Açıklama|
|---------------|-----------------|
|`OutputPath`|Gerekli **Dize** parametresi.<br /><br /> Çıkış dizininin yolunu belirtir. Yol mutlak bir yol değilse, kök proje dizinine göre bir yol olarak kabul edilir.|
|`OutputResourcesFile`|Gerekli **ITaskItem[]** çıkış parametresi.<br /><br /> Oluşturulan *.resources* dosyasının yolunu ve adını belirtir. Yol mutlak bir yol değilse, *.resources* dosyası kök proje dizinine göre oluşturulur.|
|`ResourcesFiles`|Gerekli **ITaskItem[]** parametresi.<br /><br /> Oluşturulan *.resources* dosyasına eklenecek bir veya daha fazla kaynağı belirtir.|

## <a name="example"></a>Örnek

 Aşağıdaki örnek, tek bir kaynak grubu olan *bir .resources* *.bmp* üretir. Kaynak *.bmp,* proje kök dizinine göre bir dizine oluşturulur.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.ResourcesGenerator"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="ResourcesGeneratorTask">
    <ResourcesGenerator
      ResourceFiles="Resource1.bmp"
      OutputPath="myresources"
      OutputResourcesFile="myresources\my.resources" />
  </Target>
</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [WPF MSBuild başvurusu](../msbuild/wpf-msbuild-reference.md)
- [Görev başvurusu](../msbuild/wpf-msbuild-task-reference.md)
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [WPF uygulaması oluşturma (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)