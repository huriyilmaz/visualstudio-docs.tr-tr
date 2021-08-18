---
title: GetWinFXPath Görev | Microsoft Docs
description: Geçerli .NET çalışma zamanının MSBuild döndüren GetWinFXPath görevini kullanmayı öğrenin.
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
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 5b94efabb17c0c88a962744e173efc155feca9d0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122108882"
---
# <a name="getwinfxpath-task"></a>GetWinFXPath görevi

Görev, <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> geçerli .NET çalışma zamanının dizinini döndürür.

## <a name="task-parameters"></a>Görev parametreleri

| Parametre | Açıklama |
|-------------------| - |
| `WinFXPath` | İsteğe **bağlı Dize** çıkış parametresi.<br /><br /> .NET çalışma zamanının gerçek yolunu belirtir. |
| `WinFXNativePath` | Gerekli **Dize** parametresi.<br /><br /> Yerel .NET çalışma zamanının yolunu belirtir. |
| `WinFXWowPath` | Gerekli **Dize** parametresi.<br /><br /> 64 bit sistemlerde bir modülde 32 bit **Windows .NET Windows** yolunu belirtir. |

## <a name="remarks"></a>Açıklamalar

 Görev <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> 64 bit işlemcide yürütiliyorsa, **WinFXPath** parametresi **WinFXWowPath** parametresinde depolanan yola ayarlanır; aksi takdirde **WinFXPath** parametresi **WinFXNativePath** parametresinde depolanan yola ayarlanır.

## <a name="example"></a>Örnek

 Aşağıdaki örnek, .NET çalışma zamanının yerel yolunu algılamak için **GetWinFXPath** görevinin nasıl kullanıla bir yolunu gösterir.

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
