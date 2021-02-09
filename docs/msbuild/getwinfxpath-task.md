---
title: GetWinFXPath görevi | Microsoft Docs
description: Geçerli .NET çalışma zamanının dizinini döndüren MSBuild GetWinFXPath görevini nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- getting the directory of the current .NET Framework runtime [WPF MSBuild]
- GetWinFXPath task [WPF MSBuild], parameters
- GetWinFXPath task [WPF MSBuild]
- obtaining the path to the current .NET Framework runtime [WPF MSBuild]
ms.assetid: b1dfb467-f3d3-47f3-83ef-af7b0e33a772
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 164f9f91eda1d81db00d25bb4e18a6cbb352e41e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914628"
---
# <a name="getwinfxpath-task"></a>GetWinFXPath görevi

<xref:Microsoft.Build.Tasks.Windows.GetWinFXPath>Görev, geçerli .NET çalışma zamanının dizinini döndürür.

## <a name="task-parameters"></a>Görev parametreleri

| Parametre | Açıklama |
|-------------------| - |
| `WinFXPath` | İsteğe bağlı **dize** çıkış parametresi.<br /><br /> .NET çalışma zamanının gerçek yolunu belirtir. |
| `WinFXNativePath` | Gerekli **dize** parametresi.<br /><br /> Yerel .NET çalışma zamanının yolunu belirtir. |
| `WinFXWowPath` | Gerekli **dize** parametresi.<br /><br /> 64 bit sistemlerde 32 bitlik **Windows** modülündeki .net derlemelerinin yolunu belirtir. |

## <a name="remarks"></a>Açıklamalar

 Görev, <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> 64 bitlik bir işlemci üzerinde yürütülecede, **WinFXPath** parametresi **WinFXWowPath** parametresinde depolanan yola ayarlanır; Aksi takdirde **WinFXPath** parametresi **WinFXNativePath** parametresinde depolanan yola ayarlanır.

## <a name="example"></a>Örnek

 Aşağıdaki örnekte, .NET çalışma zamanına ait yerel yolu algılamak için **GetWinFXPath** görevinin nasıl kullanılacağı gösterilmektedir.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.GetWinFXPath"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="GetWinFXPathTask">
    <GetWinFXPath
      WinFXNativePath="c:\WinFXNative"
      WinFXWowPath="c:\WinFXWowNative" />
  </Target>
  <Import Project="$(MSBuildBinPath)\Microsoft.WinFX.targets" />
</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [WPF MSBuild başvurusu](../msbuild/wpf-msbuild-reference.md)
- [Görev başvurusu](../msbuild/wpf-msbuild-task-reference.md)
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [WPF uygulaması oluşturma (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
