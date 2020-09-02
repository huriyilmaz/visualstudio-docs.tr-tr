---
title: GetWinFXPath görevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: da32f0bfce9edf652e19df6b68bc51ed92624d80
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65698999"
---
# <a name="getwinfxpath-task"></a>GetWinFXPath Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:Microsoft.Build.Tasks.Windows.GetWinFXPath>Görev, geçerli [!INCLUDE[TLA#tla_winfx](../includes/tlasharptla-winfx-md.md)] çalışma zamanının dizinini döndürür.  
  
## <a name="task-parameters"></a>Görev parametreleri  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`WinFXPath`|İsteğe bağlı **dize** çıkış parametresi.<br /><br /> Çalışma zamanının gerçek yolunu belirtir [!INCLUDE[TLA2#tla_winfx](../includes/tla2sharptla-winfx-md.md)] .|  
|`WinFXNativePath`|Gerekli **dize** parametresi.<br /><br /> Yerel [!INCLUDE[TLA2#tla_titlewinfx](../includes/tla2sharptla-titlewinfx-md.md)] çalışma zamanının yolunu belirtir.|  
|`WinFXWowPath`|Gerekli **dize** parametresi.<br /><br /> [!INCLUDE[TLA#tla_winfx](../includes/tlasharptla-winfx-md.md)]64 bit sistemlerde 32 bitlik **Windows** modülündeki derlemelerin yolunu belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Görev, <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> 64 bitlik bir işlemci üzerinde yürütülecede, **WinFXPath** parametresi **WinFXWowPath** parametresinde depolanan yola ayarlanır; Aksi takdirde **WinFXPath** parametresi **WinFXNativePath** parametresinde depolanan yola ayarlanır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, çalışma zamanının yerel yolunu algılamak için **GetWinFXPath** görevinin nasıl kullanılacağını gösterir [!INCLUDE[TLA2#tla_titlewinfx](../includes/tla2sharptla-titlewinfx-md.md)] .  
  
```  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF MSBuild başvurusu](../msbuild/wpf-msbuild-reference.md)   
 [Görev başvurusu](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild başvurusu](../msbuild/msbuild-reference.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)   
 [WPF Uygulaması Oluşturma (WPF)](https://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)
