---
title: ResourcesGenerator görevi | Microsoft Docs
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
ms.openlocfilehash: 703cd7bc3d0dd0e2229365dde39418ff32ad0a3e
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579609"
---
# <a name="resourcesgenerator-task"></a>ResourcesGenerator görevi
<xref:Microsoft.Build.Tasks.Windows.ResourcesGenerator> görevi bir veya daha fazla kaynağı ( *. jpg*, *. ico*, *. bmp*, [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] ikili biçimde ve diğer uzantı türlerini) bir *. resources* dosyasına katıştırır.

## <a name="task-parameters"></a>Görev parametreleri

|Parametre|Açıklama|
|---------------|-----------------|
|`OutputPath`|Gerekli **dize** parametresi.<br /><br /> Çıkış dizininin yolunu belirtir. Yol mutlak bir yol değilse, kök proje diziniyle ilişkili bir yol olarak kabul edilir.|
|`OutputResourcesFile`|Gerekli **ITaskItem []** çıkış parametresi.<br /><br /> Oluşturulan *. resources* dosyasının yolunu ve adını belirtir. Yol mutlak bir yol değilse, *. resources* dosyası kök proje dizinine göre oluşturulur.|
|`ResourcesFiles`|Gerekli **ıtaskitem []** parametresi.<br /><br /> Oluşturulan *. resources* dosyasına eklemek için bir veya daha fazla kaynak belirtir.|

## <a name="example"></a>Örnek
 Aşağıdaki örnek, tek bir *. bmp* kaynağı ile bir *. resources* dosyası oluşturur. *. Bmp* kaynağı, proje kök dizinine göreli bir dizine üretilir.

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