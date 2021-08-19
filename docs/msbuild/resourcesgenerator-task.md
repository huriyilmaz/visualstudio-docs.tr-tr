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
ms.openlocfilehash: 86bba77d8e8a46f65211bd10da45a5953f52daeb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122100575"
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