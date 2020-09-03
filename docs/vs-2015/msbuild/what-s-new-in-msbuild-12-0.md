---
title: MSBuild 12,0 ' deki yenilikler&#39;| Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75844464"
---
# <a name="what39s-new-in-msbuild-120"></a>MSBuild 12,0 ' deki yenilikler&#39;
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

MSBuild artık .NET Framework bir parçası yerine Visual Studio 'nun bir parçası olarak yüklenir. Geçerli MSBuild sürüm numarası 12,0 ' dir. MSBuild 'i ayrı olarak yüklemek isterseniz, yükleme paketini [MSBuild indirinden](https://www.microsoft.com/download/details.aspx?id=40760)indirin.  
  
## <a name="changed-path"></a>Değiştirilen yol  
 MSBuild artık *% ProgramFiles%* altında (örneğin, C:\Program files\msbuild) yüklenir \\ .  
  
## <a name="changed-properties"></a>Değiştirilen özellikler  
 Aşağıdaki MSBuild özellikleri yeni sürüm numarası nedeniyle değiştirilmiştir:  
  
- `MSBuildToolsVersion` Bu araçların sürümü için 12,0.  
  
- `MSBuildToolsPath` Artık 32 bit işletim sistemlerinde%ProgramFiles%\MSBuild\12.0\bin veya 64 bit işletim sistemlerinde%ProgramFiles%\MSBuild\12.0\bin\amd64.  
  
- `ToolsVersion` 32 bit işletim sistemleri için Hklm\software\microsoft\msbuild\tools\versions\12.0 veya 64 bit işletim sistemleri için Hklm\software\wow6432node\microsoft\msbuild\tools\versions\12.0 içinde değerler bulunabilir.  
  
- `SDK35ToolsPath`Ve `SDK40ToolsPath` Özellikleri, Visual Studio 'nun bu sürümüyle PAKETLENMIŞ .NET Framework SDK 'ye işaret noktasıdır (örneğin, 4. X araçları Için 8.1 a).  
  
## <a name="new-properties"></a>Yeni özellikler  
  
- `MSBuildFrameworkToolsPath` , 32 bit işletim sistemlerinde%windir%\Microsoft.NET\Framework\v4.0.30319 değeri veya 64 bit işletim sistemlerinde%windir%\Microsoft.NET\Framework64\v4.0.30319 olan yeni bir özelliktir. Bu `MSBuildToolsPath` , .NET Framework araçları ve yardımcı programlarını işaret etmek için kullanılabilecek bir yerini alır.  
  
- `MSBuildToolsPath` ve `MSBuildFrameworkToolsPath` 32 bit eşdeğerleri vardır — `MSBuildToolsPath32` ve `MSBuildFrameworkToolsPath32` Bu her zaman, 32-bit veya 64 bit MSBuild kullanılıp kullanılmadığına bakılmaksızın 32 bit konumunu işaret edin.

## <a name="see-also"></a>Ayrıca Bkz.
[MSBUILD](msbuild.md)
