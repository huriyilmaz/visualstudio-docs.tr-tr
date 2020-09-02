---
title: MSBuild hedef çerçevesi ve hedef platform | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
ms.assetid: df6517c5-edd6-4cc4-97ad-b3cdfc78e799
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1a550b4a6634604594da0893e3f420fd9c38ca3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68181025"
---
# <a name="msbuild-target-framework-and-target-platform"></a>MSBuild Hedef Çerçevesi ve Hedef Platformu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir proje, .NET Framework belirli bir sürümü ve belirli bir yazılım mimarisi olan bir *hedef platform*olan bir *hedef çerçeve*üzerinde çalışmak üzere oluşturulabilir.  Örneğin, 2,0 bitlik bir platformda .NET Framework ' de çalışacak bir uygulamayı, 802x86 işlemci ailesi ("x86") ile uyumlu 32 bir şekilde hedefleyebilirsiniz. Hedef Framework ve hedef platformun birleşimi *hedef bağlam*olarak bilinir.  
  
## <a name="target-framework-and-profile"></a>Hedef çerçeve ve profil  
 Hedef çerçeve, [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] projenizin üzerinde çalışmak üzere oluşturulduğu belirli bir sürümdür. Bir hedef Framework belirtimi, bu Framework sürümü için özel derleyici özellikleri ve derleme başvuruları sağladığından gereklidir.  
  
 Şu anda .NET Framework aşağıdaki sürümleri kullanılabilir:  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]2,0 (Visual Studio 2005 ' de bulunur)  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]3,0 (içinde bulunur [!INCLUDE[wiprlhext](../includes/wiprlhext-md.md)] )  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]3,5 (içinde bulunur [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)] )  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]4 (Visual Studio 2010 ' de bulunur)  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]4,5 (içinde bulunur [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] )  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]4.5.1 (içinde bulunur [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] )  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]4.5.2  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]4,6 (içinde bulunur [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] )  
  
  .NET Framework sürümleri, her birinin başvuru için kullanılabilir hale getiren derlemeler listesinde diğerinden farklıdır. Örneğin, projeniz .NET Framework sürüm 3,0 veya üzerini hedeflediğinden, Windows Presentation Foundation (WPF) uygulamaları derlenemez.  
  
  Hedef çerçeve, `TargetFrameworkVersion` Proje dosyasındaki özelliğinde belirtilmiştir. Visual Studio tümleşik geliştirme ortamındaki (IDE) proje özelliği sayfalarını kullanarak bir projenin hedef çerçevesini değiştirebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: .NET Framework bir sürümünü hedefleme](../ide/how-to-target-a-version-of-the-dotnet-framework.md). İçin kullanılabilir değerler,,,,,, `TargetFrameworkVersion` `v2.0` `v3.0` `v3.5` `v4.0` `v4.5` `v4.5.1` `v4.5.2` ve `v4.6` .  
  
```  
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>  
```  
  
 *Hedef profil* , hedef Framework 'ün bir alt kümesidir. Örneğin, .NET Framework 4 Istemci profili MSBuild derlemelerine başvuruları içermez.  
  
 Hedef profil, `TargetFrameworkProfile` bir proje dosyasındaki özelliğinde belirtilmiştir. IDE 'deki proje özelliği sayfalarında Target-Framework denetimini kullanarak hedef profilini değiştirebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: .NET Framework bir sürümünü hedefleme](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
```  
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>  
<TargetFrameworkProfile>Client</TargetFrameworkProfile>  
```  
  
## <a name="target-platform"></a>Hedef platform  
 *Platform* , belirli bir çalışma zamanı ortamını tanımlayan donanım ve yazılım birleşimidir. Örneğin,  
  
- `x86` Intel 80x86 işlemcisi üzerinde veya eşdeğeri olan 32 bitlik bir Windows işletim sistemi belirler.  
  
- `Xbox` Microsoft Xbox 360 platformunu belirtir.  
  
  *Hedef platform* , projenizin üzerinde çalışmak üzere oluşturulduğu özel platformdur. Hedef platform `Platform` bir proje dosyasındaki Build özelliğinde belirtilmiştir. Hedef platformu, proje özelliği sayfalarını veya IDE 'deki **Configuration Manager** kullanarak değiştirebilirsiniz.  
  
```  
<PropertyGroup>  
   <Platform>x86</Platform>  
</PropertyGroup>  
  
```  
  
 *Hedef yapılandırma* , hedef platformun bir alt kümesidir. Örneğin, `x86``Debug` yapılandırma çoğu kod iyileştirmesini içermez. Hedef yapılandırma `Configuration` bir proje dosyasındaki Build özelliğinde belirtilir. Proje özellik sayfaları veya **Configuration Manager**kullanarak hedef yapılandırmayı değiştirebilirsiniz.  
  
```  
<PropertyGroup>  
   <Platform>x86</Platform>  
   <Configuration>Debug</Configuration>  
<PropertyGroup>  
  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çoklu sürüm desteği](../msbuild/msbuild-multitargeting-overview.md)
