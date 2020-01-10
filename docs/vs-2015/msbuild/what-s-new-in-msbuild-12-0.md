---
title: "&#39;MSBuild 12,0 ' deki yenilikler | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
ms.assetid: 9976a6ad-c052-4017-b848-35b5ae4a2f66
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ba733b7ef20c9a03ad19d9847a4046e4d72ebdef
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75844464"
---
# <a name="what39s-new-in-msbuild-120"></a>&#39;MSBuild 12,0 ' deki yenilikler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

MSBuild artık .NET Framework bir parçası yerine Visual Studio 'nun bir parçası olarak yüklenir. Geçerli MSBuild sürüm numarası 12,0 ' dir. MSBuild 'i ayrı olarak yüklemek isterseniz, yükleme paketini [MSBuild indirinden](https://www.microsoft.com/download/details.aspx?id=40760)indirin.  
  
## <a name="changed-path"></a>Değiştirilen yol  
 MSBuild artık *% ProgramFiles%* altında (örneğin, C:\Program files\msbuild\\) yüklenir.  
  
## <a name="changed-properties"></a>Değiştirilen özellikler  
 Aşağıdaki MSBuild özellikleri yeni sürüm numarası nedeniyle değiştirilmiştir:  
  
- araçların bu sürümü için `MSBuildToolsVersion` 12,0 ' dir.  
  
- `MSBuildToolsPath` artık 32 bit işletim sistemlerinde%ProgramFiles%\MSBuild\12.0\bin veya 64 bit işletim sistemlerinde%ProgramFiles%\MSBuild\12.0\bin\amd64.  
  
- `ToolsVersion` değerleri, 32 bit işletim sistemleri için Hklm\software\microsoft\msbuild\tools\versions\12.0 veya 64 bit işletim sistemleri için Hklm\software\wow6432node\microsoft\msbuild\tools\versions\12.0 ' da bulunabilir.  
  
- `SDK35ToolsPath` ve `SDK40ToolsPath` özellikleri, Visual Studio 'nun bu sürümüyle paketlenmiş .NET Framework SDK 'ya işaret noktasıdır (örneğin, 4. X araçları için 8.1 A).  
  
## <a name="new-properties"></a>Yeni özellikler  
  
- `MSBuildFrameworkToolsPath`, 32 bit işletim sistemlerinde%windir%\Microsoft.NET\Framework\v4.0.30319 veya 64 bit işletim sistemlerinde%windir%\Microsoft.NET\Framework64\v4.0.30319 değeri olan yeni bir özelliktir. Bu, .NET Framework araçları ve yardımcı programlarını işaret etmek için kullanılabilecek `MSBuildToolsPath` yerini alır.  
  
- `MSBuildToolsPath` ve `MSBuildFrameworkToolsPath` 32 bit eşdeğerlerine sahiptir —`MSBuildToolsPath32` ve `MSBuildFrameworkToolsPath32`— 32-bit veya 64 bit MSBuild 'in kullanılıp kullanılmadığına bakılmaksızın her zaman 32-bit konumunu işaret eden.

## <a name="see-also"></a>Ayrıca Bkz.
[MSBuild](msbuild.md)
