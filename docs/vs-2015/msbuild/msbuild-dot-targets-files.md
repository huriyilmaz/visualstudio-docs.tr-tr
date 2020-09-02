---
title: MSBUILD. Hedef dosyalar | Microsoft Docs
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
- .Targets files
- MSBuild, .Targets files
ms.assetid: f6d98eb4-d2fa-49b7-8e3c-bae1ca3cf596
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bab229a3246ac91eaa652be67e98a68aab40e820
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64811144"
---
# <a name="msbuild-targets-files"></a>MSBuild .Targets Dosyaları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] ortak senaryolar için öğeleri, özellikleri, hedefleri ve görevleri içeren birkaç. targets dosyası içerir. Bu dosyalar, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bakım ve okunabilirlik işlemlerini basitleştirmek üzere çoğu proje dosyasına otomatik olarak aktarılır.  
  
 Projeler genellikle derleme işlemlerini tanımlamak için bir veya daha fazla. targets dosyasını içeri aktarır. Örneğin [!INCLUDE[csprcs](../includes/csprcs-md.md)] , tarafından oluşturulan bir proje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Microsoft. Common. targets 'ı Içeri aktaran Microsoft. CSharp. targets içeri aktarır. [!INCLUDE[csprcs](../includes/csprcs-md.md)]Projenin kendisi bu projeye özgü öğeleri ve özellikleri tanımlar, ancak projenin standart yapı kuralları [!INCLUDE[csprcs](../includes/csprcs-md.md)] içeri aktarılan. targets dosyalarında tanımlanır.  
  
 `$(MSBuildToolsPath)`Değer, bu ortak. targets dosyalarının yolunu belirtir. `ToolsVersion`4,0 ise, dosyalar aşağıdaki konumdadır:`WindowsInstallationPath\Microsoft.NET\Framework\v4.0.30319\`  
  
> [!NOTE]
> Kendi hedeflerinizi oluşturma hakkında daha fazla bilgi için bkz. [targets](../msbuild/msbuild-targets.md). Bir `Import` Proje dosyasını başka bir proje dosyasına eklemek için öğesinin nasıl kullanılacağı hakkında bilgi için, bkz. [Import element (MSBuild)](../msbuild/import-element-msbuild.md) ve [nasıl yapılır: birden çok proje dosyasında aynı hedefi kullanma](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md).  
  
## <a name="common-targets-files"></a>Birçok. Hedef dosyalar  
  
|. Hedef dosya|Description|  
|-------------------|-----------------|  
|Microsoft. Common. targets|Ve projeleri için standart derleme işlemindeki adımları tanımlar [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] [!INCLUDE[csprcs](../includes/csprcs-md.md)] .<br /><br /> Aşağıdaki ifadeyi içeren Microsoft. CSharp. targets ve Microsoft. VisualBasic. targets dosyaları tarafından içeri aktarılır: `<Import Project="Microsoft.Common.targets" />`|  
|Microsoft. CSharp. targets|Visual C# projeleri için standart derleme işlemindeki adımları tanımlar.<br /><br /> Aşağıdaki ifadeyi içeren Visual C# proje dosyaları (. csproj) tarafından içeri aktarıldı: `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`|  
|Microsoft. VisualBasic. targets|Visual Basic projeleri için standart derleme işlemindeki adımları tanımlar.<br /><br /> Aşağıdaki ifadeyi içeren Visual Basic proje dosyaları (. vbproj) tarafından içeri aktarıldı: `<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İçeri aktarma öğesi (MSBuild)](../msbuild/import-element-msbuild.md)   
 [MSBuild başvurusu](../msbuild/msbuild-reference.md)  
 [MSBUILD](msbuild.md)
