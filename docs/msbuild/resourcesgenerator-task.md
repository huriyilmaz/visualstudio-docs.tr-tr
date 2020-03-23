---
title: ResourcesGenerator Görev | Microsoft Dokümanlar
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2b5aba45292aaa55a719eb19d6f0f6f115e8b477
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632517"
---
# <a name="resourcesgenerator-task"></a>ResourcesGenerator görevi

Görev, <xref:Microsoft.Build.Tasks.Windows.ResourcesGenerator> bir veya daha fazla kaynağı *(.jpg*, *.ico*, *.bmp*, ikili biçimde XAML ve diğer uzantı türleri) *bir .resources* dosyasına yerlebir eder.

## <a name="task-parameters"></a>Görev parametreleri

|Parametre|Açıklama|
|---------------|-----------------|
|`OutputPath`|Gerekli **String** parametresi.<br /><br /> Çıktı dizininin yolunu belirtir. Yol mutlak bir yol değilse, kök proje dizinine göre bir yol olarak kabul edilir.|
|`OutputResourcesFile`|Gerekli **ITaskItem[]** çıkış parametresi.<br /><br /> Oluşturulan *.resources* dosyasının yolunu ve adını belirtir. Yol mutlak bir yol değilse, *.kaynaklar* dosyası kök proje dizinine göre oluşturulur.|
|`ResourcesFiles`|Gerekli **ITaskItem[]** parametresi.<br /><br /> Oluşturulan *.resources* dosyasına katıştırmak için bir veya daha fazla kaynak belirtir.|

## <a name="example"></a>Örnek

 Aşağıdaki örnek, tek bir *.bmp* kaynağı olan bir *.resources* dosyası oluşturur. *.bmp* kaynağı, proje kök diziniyle göreli bir dizine oluşturulur.

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
- [WPF uygulaması (WPF) oluşturma](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)